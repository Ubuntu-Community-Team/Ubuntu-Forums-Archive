---
title: "TAR Exclude everything in folder except this folder"
date: 2012-04-29
forum: General Help
---

### Post by rationalthinker1 on 2012-04-29
Hello, I want to create a backup of my Home folder. Here's what I've done.

```

GZIP=-9
time=`date "+%y.%m.%d.%H.%M.%S"`
tar cvzf "/home/raza/Ubuntu One/$time.backup.tar.gz" \
--exclude="*.tmp" \
--exclude-caches-all \
--exclude="/home/raza/backup.sh" \
--exclude="/home/raza/*[Cc]ache*" \
--exclude="/home/raza/*[Tt]humbnails*" \
--exclude="/home/raza/*[Ii]cons?*" \
--exclude="/home/raza/*[Ll]ogs?*" \
--exclude="/home/raza/.opera/vps" \
--exclude="/home/raza/.opera/temporary_downloads" \
--exclude="/home/raza/Downloads" \
--exclude="/home/raza/Ubuntu One" \
--exclude="/home/raza/.local/share/Trash" \
"/home/raza/" > fileSaved.txt

```

There's a folder called /home/raza/.config/sublime-text-2/ that I want to exclude EXCEPT this this directory /home/raza/.config/sublime-text-2/Packages/User.

How do I do that?

Thank You.

---

### Post by rationalthinker1 on 2012-04-29
Bump?

---

### Post by josephmills on 2012-04-29
> **rationalthinker1 said:**
> Hello, I want to create a backup of my Home folder. Here's what I've done.

```

GZIP=-9
time=$(date "+%y.%m.%d.%H.%M.%S")
tar cvzf "/home/raza/Ubuntu One/$time.backup.tar.gz" \
--exclude="*.tmp" \
--exclude-caches-all \
--exclude="/home/raza/backup.sh" \
--exclude="/home/raza/*[Cc]ache*" \
--exclude="/home/raza/*[Tt]humbnails*" \
--exclude="/home/raza/*[Ii]cons?*" \
--exclude="/home/raza/*[Ll]ogs?*" \
--exclude="/home/raza/.opera/vps" \
--exclude="/home/raza/.opera/temporary_downloads" \
--exclude="/home/raza/Downloads" \
--exclude="/home/raza/Ubuntu One" \
--exclude="/home/raza/.local/share/Trash" \
"/home/raza/" > fileSaved.txt

```

There's a folder called /home/raza/.config/sublime-text-2/ that I want to exclude EXCEPT this this directory /home/raza/.config/sublime-text-2/Packages/User.

How do I do that?

Thank You.



[COLOR="Black"][SIZE="3"]THIS IS NOT TESTED [/SIZE][/COLOR]

the idea is in the code in comments I am sure that there are other ways. 

```
#!/usr/bin/env bash 
## backup script
##
##      This has not been tested 
##
#set gzip 
GZIP=-9
## move too the home directory 
cd 
## run the function and grep out the things that you do not want sedndign them too a file called somefile.txt  then cd too the one that you want then send too the ##bottom of the list
function lists(){
find . |grep -v ~/*.tmp |grep -v ~/backup.sh  |grep -v ~/*[Cc]ache*|grep -v ~/*[Tt]humbnails*|grep -v ~/*[Ii]cons?*|grep -v ~/*[Ll]ogs?*|grep -v ~/.opera/vps|grep -v ~/.opera/temporary_downloads|grep -v ~/Downloads|grep -v ~/Ubuntu One|grep -v ~/.local/share/Trash > ~/somefile.txt
cd ~/.config/sublime-text-2/Packages/User/
find . >> ~/somefile.txt
cd
}
## run the function 
lists
## make backup dir 
mkdir ~/.backup 
## cat the somefile and read line by line copying each one to the dir ~/.backup 
cat somefile.txt | while read -r line;do  
cp $line ~/.backup/ ;
done 
##make the tar ball 
tar cvzf ~/.backup /home/raza/Ubuntu One/$(date).backup.tgz 

```

---

### Post by rationalthinker1 on 2012-04-30
Hello,
thank you. I got it to work. Unfortunately, I didn't use yours.

What I did was simply update the tar file with another directory.

```

 GZIP=-9
 time=`date "+%y.%m.%d.%H.%M.%S"`
 tar cvpf "/home/raza/Ubuntu One/$time.backup.tar" \
 --exclude="*.tmp" \
 --exclude-caches-all \
 --exclude="/home/raza/*[Cc]ache*" \
 --exclude="/home/raza/*[Tt]humbnails*" \
 --exclude="/home/raza/*[Ii]cons?*" \
 --exclude="/home/raza/*[Ll]ogs?*" \
 --exclude="/home/raza/.opera/vps" \
 --exclude="/home/raza/.opera/temporary_downloads" \
 --exclude="/home/raza/Downloads" \
 --exclude="/home/raza/Ubuntu One" \
 --exclude="/home/raza/.local/share/Trash" \
 --exclude="/home/raza/.config/sublime-text-2" \
 --exclude="/home/raza/.thunderbird/*/ImapMail" \
 "/home/raza/" > fileSaved.txt

 tar rvpf "/home/raza/Ubuntu One/$time.backup.tar" \
 "/home/raza/.config/sublime-text-2/Packages/User" \
 >> fileSaved.txt

 gzip -9 "/home/raza/Ubuntu One/$time.backup.tar"

```

---

