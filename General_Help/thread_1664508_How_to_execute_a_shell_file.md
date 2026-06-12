---
title: "How to execute a shell file"
date: 2011-01-11
forum: General Help
---

### Post by raunhar on 2011-01-11
Ubuntu version  10.10
File location  inside a folder on Desktop
File extn  :  .sh

I need to run this file in terminal console, but what path to be given is the question.

Please suggest.

---

### Post by Nightslay on 2011-01-11
What is the purpose of the script

for running (may need sudo or root permissions)
/bin/sh ~/Desktop/file.sh
user@desk:~/Desktop$ ./file.sh

but again depends on how the script is made and what the purpose is.

---

### Post by WorMzy on 2011-01-11
Like Nightslay said, a lot depends on the script. If the script uses relative paths, then you will need to cd into the directory containing it, then run it with
```
./scriptname.sh
```
If the script uses absolute paths, then cd'ing to the directory is not necessary, and the script can be executed by typing it's address into the terminal:
```
/home/raunhar/Desktop/script/scriptname.sh
```
If the script needs to edit a file in the system directories, then you will need to prepend "sudo" to whichever method is required.

e.g.
```
sudo /home/raunhar/Desktop/script/scriptname.sh
```

---

### Post by raunhar on 2011-01-11
punnvs@punnvs:~$ /home/punnvs/Desktop/com_sobi2new/clone_sobi.sh
bash: /home/punnvs/Desktop/com_sobi2new/clone_sobi.sh: Permission denied
punnvs@punnvs:~$ sudo /home/punnvs/Desktop/com_sobi2new/clone_sobi.sh
[sudo] password for punnvs: 
sudo: /home/punnvs/Desktop/com_sobi2new/clone_sobi.sh: command not found


The file is to create a clone of component SOBI2 for joomla.
Under 9.04, when we double click on the .sh file, it asks to open in terminal or view. This is not so in 10.10

---

### Post by WorMzy on 2011-01-11
Is it marked as executable?

```
chmod +x /home/punnvs/Desktop/com_sobi2new/clone_sobi.sh
```

Then try again.

---

### Post by raunhar on 2011-01-11
Thanks a lot, it worked.

---

