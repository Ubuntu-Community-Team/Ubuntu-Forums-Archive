---
title: "Help with shift command in little batch file. . ."
date: 2010-02-11
forum: General Help
---

### Post by elmagno on 2010-02-11
I want to be able to enter multiple filenames after this bash file on the command line--- file1.rm, file2.rm by putting a shift command in this file?
Or even better, for this bash file to take a line by line pipe from a text file. Excuse my atechnicalness.


file: rm2avi.sh:


#!/bin/bash
cd /media/212EXT/data/download/convert
OLD=$1
NEW=`basename $OLD`

mencoder $1.rm -o $1.avi -ovc xvid -xvidencopts fixed_quant=5 -oac mp3lame -lameopts abr:br=128

---

### Post by Satoru-san on 2010-02-11
A thread very simmilar to this was just solved.

[http://ubuntuforums.org/showthread.php?t=1403706](http://ubuntuforums.org/showthread.php?t=1403706)

you might want to see if this will help you, I am not sure quite what you are asking, but I believe they will do simmilar things. The only difference is that one ^ will do all your *.rm files so you dont have to put them all in manually.

---

### Post by elmagno on 2010-02-11
Wow, I think a little less I might handle. 

I'd just like to be able to enter "sh ./rm2avi.sh" on the command line, and then the filenames  bogart.rm bacall.rm highsierra.rm and have my file process those one after the other. I hope that explains it better.

---

### Post by falconindy on 2010-02-11
You can use shift or a for loop here. Either will work provided that you quote any arguments that contain spaces or other special characters.

Using shift:
```
#!/bin/bash

while [[ $# -gt 0 ]]; do
    ./rm2avi.sh "$1"
done
```

Using a for loop:
```
#!/bin/bash

for file in "$@"; do
    ./rm2avi.sh "$file"
done
```

You might consider removing the .rm from the $1 in your script, as you want to be able to pass the true names of the files to your script, so that you're not required to mangle them in transit. Better yet, this can all be done in one script...

```
#!/bin/bash
cd /media/212EXT/data/download/convert

for file in "$@"; do
    file=${file##*/}
    mencoder $file -o ${file//.rm}.avi -ovc xvid -xvidencopts fixed_quant=5 -oac mp3lame -lameopts abr:br=128
done
```

${file##*/} and ${file//.rm} are string manipulation in Bash. Rather than call external programs like basename or sed, you can just use the power of Bash.

---

### Post by elmagno on 2010-02-11
If I do the first example as an executable I get:

./rm.sh: 5: [[: not found

If I add the while statement above my mencoder statement in rm2avi.sh, it does just the first file and quits quietly.

---

### Post by elmagno on 2010-02-11
I didnt see your third example. I'm off to try it now. Thanks very much.

---

### Post by elmagno on 2010-02-11
Falconindy,

Thanks again for your help. When I executed a file that says:

#!/bin/bash
cd /media/212EXT/data/download/convert

for file in "$@"; do
    file=${file##*/}
    mencoder $file -o ${file//.rm}.avi -ovc xvid -xvidencopts fixed_quant=5 -oac mp3lame -lameopts abr:br=128
done

I get this:
./rm.sh: 7: Bad substitution


I am following the executable with filenames like "Samson.rm" etc. I have also tried leaving off the file extensions, but same error.

---

### Post by t4thfavor on 2010-02-11
Use code tags on your script, it allows us to read it much easier.

It's one of the ${variable}'s thats causeing the error most likely, Is there a 7 filename by chance?


EDIT:7 is likely the line number....

---

### Post by elmagno on 2010-02-11
No, no 7 filename. Sorry I dont know what code tags are.

---

### Post by falconindy on 2010-02-11
I notice in the 3rd post, you're executing the scripts with 'sh'. You absolutely **must** use bash to execute these scripts, either by setting the executable bit:
```
chmod +x script.sh;./script.sh
```
...or calling bash to run the script:
```
bash script.sh
```
If the above accurately describes how you are calling the script, then please post the full execution, including the arguments provided to the script.

---

### Post by elmagno on 2010-02-12
Falconindy!!!

I tried the same script but led with "bash" and voila! It's working. I don't quite know why but I am happy, I will sort this out in the morning and get educated, and I will mark this thread solved. You have really helped me out--Thank You.

elmagno

---

