---
title: "Shell Script Help"
date: 2011-08-04
forum: General Help
---

### Post by Guffmeister on 2011-08-04
Hi all,

I'm trying to write a shell script, both as practice as I've never written one before, and also to convert a whole load of .eps image files into .pdf for LaTeX purposes.

So...I have a script, which doesn't work. I actually copied most of it from what I've found online, but for some reason it won't work and I want to know why.

So this is my script...

#!/bin/bash 
filelist=`(find . -name \*.eps)` 
for file in $filelist; 
do 
ps2pdf -dEPSCrop $file 
echo 'Converted $file into pdf.' 
done 

which finds a list of files ending in .eps, and then runs a for loop, converting each one in turn. 

I get a complaint that the for loop fails on line 3. If I debug the script, the filelist appears to pick up the files in the folder, but when it lists them it looks like this...

filelist = './a.eps
./b.eps
./c.eps
'/d.eps (that apostrophe is intentional)

Since I don't know much about writing shell scripts, I don't know what is causing the problem. Presumably the for loop doesn't like the form that I've given the files in. The 'misplaced' apostrophe looks suspect to me, but again, I don't know if that's normal.

Thanks for your help in advance.

---

### Post by Lars Noodén on 2011-08-04
Take it fewer steps at a time, but the problem is probably with ps2pdf.  Does it exist?

```

#!/bin/bash
filelist=`(find . -name \*.eps)`
for file in $filelist;
do
**ps2pdf -dEPSCrop $file && echo 'Converted $file into pdf.' || echo "Conversion of $file failed."**
done 

```

---

### Post by Guffmeister on 2011-08-04
Yes, ps2pdf exists and works. If I run the command itself then I can convert each file at a time.

---

### Post by djc12536 on 2012-10-23
Try,

#!/bin/bash 
filelist=`(find . -name \*.eps)` 

for file in $filelist; 
do 
epstopdf $file 
echo 'Converted '$file' into pdf.' 
done

---

### Post by Abhinav Kumar on 2012-10-27
Try this one

#!/bin/bash 
for file in *.eps
do 
ps2pdf -dEPSCrop $file 
echo 'Converted $file into pdf.' 
done

---

