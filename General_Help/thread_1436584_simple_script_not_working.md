---
title: "simple script not working"
date: 2010-03-22
forum: General Help
---

### Post by ttallos on 2010-03-22
I am trying to make a simple script. The first part works to untar a file. When I try to CD from within my simple script.sh file to the new directory just untared and run the setup commands it just errors out and says something about having no directory or something and saying that it cant make without configuring or something.

#!/bin/bash
for file in *.tar.gz
do
     tar -xvzf $file
done

cd some-directory
./configure 
make 
make install

---

### Post by gordintoronto on 2010-03-22
You mean some-directory does not exist?  Check the spelling, and note that folder and file names are case-sensitive in Linux, so Desktop and desktop are not the same thing.

---

