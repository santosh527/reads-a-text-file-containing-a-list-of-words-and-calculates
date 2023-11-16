# reads-a-text-file-containing-a-list-of-words-and-calculates
Assignment
 <?php

function Statistics($filename) {
   
    $content = file_get_contents($filename);

   
    $words = str_word_count(strtolower($content), 1);

   
    $totalWords = count($words);

   
    $uniqueWords = count(array_unique($words));

    
    $wordFrequencies = array_count_values($words);

    
    arsort($wordFrequencies);

  
    $top5CommonWords = array_slice($wordFrequencies, 0, 5);

    usort($words, function ($a, $b) {
        return strlen($b) - strlen($a);
    });

    $top5LongestWords = array_slice($words, 0, 5);

    
    echo "Total number of words: $totalWords\n";
    echo "Total number of unique words: $uniqueWords\n";

    echo "\nTop 5 most common words and their frequencies:\n";
    foreach ($top5CommonWords as $word => $frequency) {
        echo "$word: $frequency\n";
    }

    echo "\nTop 5 longest words:\n";
    foreach ($top5LongestWords as $word) {
        echo "$word\n";
    }
}


Statistics('your_file.txt');

?>

