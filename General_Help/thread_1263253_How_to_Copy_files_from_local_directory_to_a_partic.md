---
title: "How to Copy files from local directory to a particular directory using alias"
date: 2009-09-10
forum: General Help
---

### Post by dynamics on 2009-09-10
Hi 

Sorry for posting this in Ubuntu forum. This is a general linux topic.

I want to copy files **and** folders from my current directory to a particular directory say target. How can I accomplish this using aliases?

Example:

The file to be copied is at this location
~/dir1/dir2/dir3/myfile.txt

The target directory where I want to copy the file is 
~/fol1/fol2/fol3/target_dir

I know how to do it using this command assuming that my current location (pwd) is **dir3**

$cp myfile.txt ~/fol1/fol2/fol3/target_dir/.

What I want is something like this

$cp myfile.txt target_dir

What I tried is :
In .bashrc I created this alias:
alias cpt='cp $1 ~/fol1/fol2/fol3/target_dir'

then in the current folder I run
$cpt myfile.txt 

But this is not working. I tried replacing the single quotes ' with double ones ". No use.

How can I do this?

Thanks in advance....

---

