---
title: "Script or Command to move files to a directory of the same name"
date: 2010-03-12
forum: General Help
---

### Post by cbaughman on 2010-03-12
Hello all, 

First of all i'm new to scripting and this is a good learning project but i'm stuck.

I'm doing a little work on my media center and the scrappers seem to do a much better job when each movie is in a directory with the name of the movie. However that's not how i have things set up.

I have a few hundred avi files i need moved to directory named the same as the avi file.

for file ls *avi; do
     mkdir (ok this is where i'm stuck)

      
Any help would be great, and thank you.

---

### Post by cjhabs on 2010-03-12
> **cbaughman said:**
> Hello all, 

First of all i'm new to scripting and this is a good learning project but i'm stuck.

I'm doing a little work on my media center and the scrappers seem to do a much better job when each movie is in a directory with the name of the movie. However that's not how i have things set up.

I have a few hundred avi files i need moved to directory named the same as the avi file.

for file ls *avi; do
     mkdir (ok this is where i'm stuck)

      
Any help would be great, and thank you.

mkdir /path_to_root_of_avi/$file
mv $file /path_to_root_of_avi/$file

It won't work if there are spaces in the name.
Are there spaces in any of the names?
You could use "tr" to change spaces to "_" before creating the folder and doing the move.

---

### Post by sisco311 on 2010-03-12
```
for file in *.avi; do 
  mkdir "${file%.avi}"
  mv "${file}" "${file%.avi}"
done
```

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_10_03.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_10_03.html)

---

### Post by cbaughman on 2010-03-12
Great Thanks this work.

---

