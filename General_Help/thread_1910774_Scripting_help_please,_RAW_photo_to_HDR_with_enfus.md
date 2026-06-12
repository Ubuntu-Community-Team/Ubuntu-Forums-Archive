---
title: "Scripting help please, RAW photo to HDR with enfuse"
date: 2012-01-17
forum: General Help
---

### Post by Sharpie1 on 2012-01-17
Hi 
I came across a script on this forum, for taking a RAW image file from a digital camera and running it through ufraw, and then enfuse to create a pseudo  HDR image that works really well. I would like to figure out a way of running the script on a whole folder full of RAW images.
The script is on this guide:
[http://ubuntuforums.org/showthread.php?t=741161](http://ubuntuforums.org/showthread.php?t=741161)
and below is the script

```
#!/bin/bash  if [ ! "$1" ] then     echo "Please specify filename."     exit 1 fi  if [ ! -f "$1" ] then     echo "Error: file does not exist"     exit 1 fi   # extract the filename without extension filename=`basename "$1" | sed 's/\.\([^\/\.]*$\)//'`   # check lower limit param if [ $2 ] then     lower_limit="$2" else     lower_limit=-3 fi  # check upper limit param if [ $3 ] then     upper_limit="$3" else     upper_limit=3 fi  # make sure lower limit < upper limit if [ $upper_limit -le $lower_limit ] then     echo "Error: upper limit is smaller than lower limit."     exit 1 fi   echo "Processing from $lower_limit to $upper_limit."   file_list=""  # should we use -3 exposure from RAW if [ $lower_limit -lt -2 ] then     if [ ! -f "${filename}_N3.tiff" ]     then         ufraw-batch  --wb=camera --exposure=-3 --out-type=tiff8  --output=${filename}_N3.tiff "$1"     fi     file_list="${filename}_N3.tiff" fi  # should we use -2 exposure from RAW if [ $lower_limit -le -2 -a $upper_limit -ge -2 ] then     if [ ! -f ${filename}_N2.tiff ]     then         ufraw-batch  --wb=camera --exposure=-2 --out-type=tiff8  --output=${filename}_N2.tiff "$1"     fi     file_list="${file_list} ${filename}_N2.tiff" fi   # should we use -1 exposure from RAW if [ $lower_limit -le -1 -a $upper_limit -ge -1 ] then     if [ ! -f ${filename}_N1.tiff ]     then         ufraw-batch  --wb=camera --exposure=-1 --out-type=tiff8  --output=${filename}_N1.tiff "$1"     fi     file_list="${file_list} ${filename}_N1.tiff" fi  # should we use 0 exposure from RAW if [ $lower_limit -le 0 -a $upper_limit -ge 0 ] then     if [ ! -f ${filename}_0.tiff ]     then         ufraw-batch  --wb=camera --exposure=0 --out-type=tiff8  --output=${filename}_0.tiff "$1"     fi     file_list="${file_list} ${filename}_0.tiff" fi  # should we use +1 exposure from RAW if [ $lower_limit -le 1 -a $upper_limit -ge 1 ] then     if [ ! -f ${filename}_P1.tiff ]     then         ufraw-batch  --wb=camera --exposure=1 --out-type=tiff8  --output=${filename}_P1.tiff "$1"     fi     file_list="${file_list} ${filename}_P1.tiff" fi  # should we use +2 exposure from RAW if [ $lower_limit -le 2 -a $upper_limit -ge 2 ] then     if [ ! -f ${filename}_P2.tiff ]     then         ufraw-batch  --wb=camera --exposure=2 --out-type=tiff8  --output=${filename}_P2.tiff "$1"     fi     file_list="${file_list} ${filename}_P2.tiff" fi  # should we use +3 exposure from RAW if [ $upper_limit -gt 2 ] then     if [ ! -f ${filename}_P3.tiff ]     then         ufraw-batch  --wb=camera --exposure=3 --out-type=tiff8  --output=${filename}_P3.tiff "$1"     fi     file_list="${file_list} ${filename}_P3.tiff" fi  # run enfuse with default parameter, edit this line for more advance enfuse options enfuse ${file_list} -o ${filename}_enfused.tiff $4 $5 $6 $7 $8 $9  # uncomment the next line to auto clean up, else just leave the temp files to experiment more #rm ${file_list}  echo "Done: final output file is ${filename}_enfused.tiff" exit 0
```I tried invoking with
```
/home/sharpie/hdr/ufenfuse.sh /home/sharpie/hdr/crf/ *.CR2
```but get a "file not found" error

any ideas ?

thanks

Sharpie1

---

### Post by mutley89 on 2012-01-20
You have a space before "*.CR2".  This will expand to "/home/sharpie/hdr/crf/" followed by any file in the current directory that ends in ".CR2".
Looking at the script linked to, it only accepts one file name as an argument. Use a for loop to run it for each file found:
```

for file in /home/sharpie/hdr/crf/*.CR2
do /home/sharpie/hdr/ufenfuse.sh "$file"
done

```If you need to search recursively through subdirectories you can use find -exec:
```
find /home/sharpie/hdr/crf/ -name "*.CR2" -exec /home/sharpie/hdr/ufenfuse.sh {} \; 
```The "{}" is replaced with each file that is found by find.

---

### Post by Sharpie1 on 2012-01-28
Thanks I will give that a try..
I actually managed to do it with
```
find . -type f -maxdepth 1 -name "*.CR2*" -exec ./ufenfuse.sh {} \;
```
which did the trick
but I will try yours too

thanks
not sure how to mark this thread solved, but it is !

Sharpie1

---

