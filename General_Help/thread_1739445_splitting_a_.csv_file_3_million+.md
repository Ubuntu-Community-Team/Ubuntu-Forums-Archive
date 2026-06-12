---
title: "splitting a .csv file? 3 million+"
date: 2011-04-25
forum: General Help
---

### Post by webcabbie on 2011-04-25
So I have a .csv file that has over 3 million lines in like 5 columns. 

I want to see all 3 million line in one of the columns and have it in a text file with no duplicates. Any help here? When you open a .csv it only shows the first million entries.

---

### Post by HermanAB on 2011-04-26
The usual trio:
$ man split
$ man sed
$ man awk

---

### Post by Ryan Dwyer on 2011-04-26
Untested:

```

#!/usr/bin/php
<?php
$fp = fopen('file.csv','r'); // Open the file for reading
$output = array(); // Declare an empty array
while ($row = fgetcsv($fp)) { // Read each line of the file into the $row array
$output[] = $row[0]; // Add the first column of this row to our $output array
}

fclose($fp); // Close the file

$output = array_unique($output); // Remove duplicates
echo implode("\n", $output); // Display output

```

Stick that in a file (eg. "fixcsv").
Make it executable: chmod +x fixcsv
Install php5-cli if it isn't already: sudo apt-get install php5-cli
Run the script: ./fixcsv > output.txt

The result will be in output.txt.

If you have problems, you can also upload the CSV somewhere and I'll sort it out for you.

---

