---
title: "Counting the entries in a large number of files"
date: 2010-05-14
forum: General Help
---

### Post by nandugopan on 2010-05-14
Hi all,

This is releated to a previous thread that I had posted. I have over 10000 files each numbered in order as 1,2,3,....10000. Each of these files contains a few entries(nubers like 2.56, 4.55 etc.) printed in a single column. I need to count the number of such entries in each file and create an output file that will have a format 

1                      5
2                      1
3                      4
...........................
10000               9
where 5,1,4 and 9 are the number of entries in files 1,2,3 and 10000 respectively.

Any help as to how to go about this?

---

### Post by kaibob on 2010-05-14
The following should do what you want. 

```
#!/bin/bash

for file in * ; do
   lines=$(sed '/^\s*$/d' "$file" | wc -l)
   echo "$file" $lines >> /home/kaibob/summary.txt
done
```

In the above, you can use wc -l without sed, but this would count the number of newlines, which may or may not be the number of lines with text. 

REFERENCE
[http://stackoverflow.com/questions/114814/count-non-blank-lines-of-code-in-bash](http://stackoverflow.com/questions/114814/count-non-blank-lines-of-code-in-bash)

---

### Post by nandugopan on 2010-05-15
Thank you kaibob....that did the job:KS
But in the output after 1000 comes 10000 and 10010 and son...I was wondering if it was possible to have it in the proper orde. You know 1000, 1010,.....10000.

---

### Post by kaibob on 2010-05-15
You can try the following, which numerically sorts the data files before processing. People object to the use of ls in shell scripts, but in this case it does appear to work.

As an aside, I noticed a problem with the following and the previous shell script. If the last number in a data file is not followed by a newline, that number will not be included in the line count. You probably should check to insure that this is not the case with your data files.

```
#!/bin/bash

ls | sort -n | while read file ; do
   lines=$(sed '/^\s*$/d' "$file" | wc -l)
   echo "$file" $lines >> /home/bob/summary.txt
done
```

---

### Post by nandugopan on 2010-05-16
kaibob,

Thanks for your reply. But it still doesnt solve the problem. 7000 comes after 69900...

---

### Post by Snow986 on 2010-05-16
It seems a C++ program may be best suited for this. Something like:

```

#include <iostream>
#include <fstream>
#include <cmath>
#include <string>

using namespace std;

ifstream in;
ofstream out;

void main(){

string outFileName = "NumEntries";
out.open(outFileName);

     for (int i = 0; i < 10000; i++){

           string inFileName = i;
            in.open(inFileName);
             int numEntries = 0;
             double dummy = 0;  
             while( ! in.eof() ){
                   in >> dummy;
                   numEntries++;
                   }
              in.close()   
               out << inFileName << "  " << numEntries << endl;

        }

out.close()
return 0;

}
                 

```

Thats a quick go but should work.  Then compile and run with gcc.  The only thing is some compilers might take issue with converting the int to string. It might have to be a cstring.

---

