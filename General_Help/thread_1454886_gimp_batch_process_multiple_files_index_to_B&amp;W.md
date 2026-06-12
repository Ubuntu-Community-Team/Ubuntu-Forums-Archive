---
title: "gimp batch process multiple files index to B&amp;W"
date: 2010-04-15
forum: General Help
---

### Post by sdowney717 on 2010-04-15
I scanned hundreds of pages in gray scale and would like to batch process them to B&W. You can do this using the gimp GUI. what it does is get rid of all the gray shading from reflections off the paper when scanned. So you get crisp white backgrounds with black text and diagrams. 
I would like to simply do this to the entire group directory at one time as it would be quite a lot of effort to open them and do them one by one.

---

### Post by Arand on 2010-04-15
imagemagick is a common way to do image manipulation in batch, see the "threshold" option:
[http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=11279](http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=11279)

- Arand

---

### Post by sdowney717 on 2010-04-15
The commandline  
convert -threshold 35000 in.pnm black.pnm

creates a pretty good result

[http://webcache.googleusercontent.com/search?q=cache:MMA7L-8-dWIJ:web.njit.edu/all_topics/Prog_Lang_Docs/html/imagemagick/www/command-line-options.html+imagemagick+threshhold+black+white&cd=4&hl=en&ct=clnk&gl=us&client=ubuntu](http://webcache.googleusercontent.com/search?q=cache:MMA7L-8-dWIJ:web.njit.edu/all_topics/Prog_Lang_Docs/html/imagemagick/www/command-line-options.html+imagemagick+threshhold+black+white&cd=4&hl=en&ct=clnk&gl=us&client=ubuntu)

Now I just need to figure out the batching of the directory

---

### Post by sdowney717 on 2010-04-15
> #!/bin/sh
cd ~/eggharbor37/test
for i in *.pnm
do convert -threshold 35000 "$i" "`basename "$i" .pnm`.pnm"
#do convert -threshold 35000 in.pnm black.pnm
done

believe it or not, this shell script takes the pnm images in that directory (/eggharbor37/test) and converts them all in a batch
it will replace all the files with the converted files
take the text, put it in a text file and make it executable.
got the idea from here
[http://www.linuxquestions.org/questions/programming-9/run-script-on-every-file-contained-within-a-parent-directory-and-its-subdirectories-444565/](http://www.linuxquestions.org/questions/programming-9/run-script-on-every-file-contained-within-a-parent-directory-and-its-subdirectories-444565/)


adjust the number 35000 greater for blacker text. Some of my scans looked better with it set to 45000

---

