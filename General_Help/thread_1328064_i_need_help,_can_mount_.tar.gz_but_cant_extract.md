---
title: "i need help, can mount .tar.gz but cant extract"
date: 2009-11-16
forum: General Help
---

### Post by qwerty2009 on 2009-11-16
Hi i need help, for some reason every time i try to extract a tar.gz file i get an error saying 

[LIST]
[*]tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
[/LIST]
i can mount the file and browse it once its mounted but i still cant drag and drop from the folder 

ive never had this problem before im running karmic btw no problems whatsoever apart from this

ive checked if i have permission by right clicking the file selecting the permission tab and using my group as the group n selecting read and write on all boxes

any help appreciated :P

---

### Post by qwerty2009 on 2009-11-16
has anyone els had this issue ? im sure theres away to do it i just cant manage it

---

### Post by qwerty2009 on 2009-11-16
sorry to be pain but this is kindah important

---

### Post by kjohri on 2009-11-16
Using the command line,

*file <tar archive>*

See what the file command says about the archive.

Also, try to extract using the command line,

tar -xvzf <tar archive>

---

### Post by qwerty2009 on 2009-11-16
hi cheers for helping out 

when i try to extract in terminal it just says the exact same thing
 (tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors)

i can install themes and extract themes from tar.gz, but im trying to extract a xplash 

i no the file isnt correupt because any xplash i try to extract fails ??

---

### Post by realzippy on 2009-11-16
Link to that file?

---

### Post by qwerty2009 on 2009-11-16
[http://www.gnome-look.org/content/show.php/Xsplash+-+Crunchy+Branch?content=115543](http://www.gnome-look.org/content/show.php/Xsplash+-+Crunchy+Branch?content=115543)

other ones also dont let me extract em

---

### Post by kjohri on 2009-11-16
Maybe it is not a tar gz archive. But if you give the command

file <tar.gz.archive>

it should give an indication as to what kind of file it is.

---

### Post by realzippy on 2009-11-16
Have you installed gzip ?

**sudo apt-get install gzip**

If done you just need to rightclick and extract...

---

### Post by qwerty2009 on 2009-11-16
> **kjohri said:**
> Maybe it is not a tar gz archive. But if you give the command

file <tar.gz.archive>

it should give an indication as to what kind of file it is.

how do i do that ? could you give me the steps please?

---

### Post by qwerty2009 on 2009-11-16
i renamed the file to (NAME).tar but could not extract it but i tried mounting it and it let me copy the contents to my home folder :) so it look like it was the wrong format  could you please let me no how to check the correct format just incase this happens in the future lol :D cheers for ur help

---

### Post by kjohri on 2009-11-16
Go to the directory where the tar-gz-archive is present. For example it may be in Desktop directory. So in the terminal type (~ is for the HOME directory)

cd ~/Desktop

file <tar - gz - archive filename>

This will give an indication of what kind of file it is.

---

### Post by qwerty2009 on 2009-11-16
> **kjohri said:**
> Maybe it is not a tar gz archive. But if you give the command

file <tar.gz.archive>

it should give an indication as to what kind of file it is.

> **kjohri said:**
> Go to the directory where the tar-gz-archive is present. For example it may be in Desktop directory. So in the terminal type (~ is for the HOME directory)

cd ~/Desktop

file <tar - gz - archive filename>

This will give an indication of what kind of file it is.

Cheers mate uve been a great help :P :P

---

### Post by juicehill on 2009-11-22
I was having the same problem and using some of the info here i have solved my problem

# file filename.tar
# filename.tar: RAR archive data, vld, os: win32

seeing that it was RAR i searched for how-to open RAR, as follows

# sudo apt-get install unrar

# unrar e filename.tar

and presto my archive was extracted, thank you very much for the first part :)

Cheers :D

---

