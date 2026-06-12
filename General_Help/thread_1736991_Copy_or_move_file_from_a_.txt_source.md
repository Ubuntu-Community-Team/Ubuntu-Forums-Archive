---
title: "Copy or move file from a .txt source"
date: 2011-04-22
forum: General Help
---

### Post by samihaxor on 2011-04-22
Hi there guys!

Im usign photorec to recover some files that i lost during a format to my hard drive.

The program works like a charm but put all the files on differents folders. i use the find command to put on a list the jpg files but how i use the cp or the mv command to move that files in the list to another folder?

---

### Post by dearingj on 2011-04-22
Maybe this command line will help. I found it in [this thread]("https://www.linuxquestions.org/questions/linux-newbie-8/command-to-select-and-move-mutiple-files-from-list-in-text-file-386372/") on linuxquestions.org:
```
for i in `cat filename`;do mv "$i" destination; done
```

Be sure to use "the right thingie": ` not '
and replace the word destination with wherever you want the files moved to, and filename with the name of the text file

---

### Post by oldfred on 2011-04-23
I did this mulitple times for each file type. The above little command will do the same thing if set up correctly.

```
#!/bin/baods
# move files

cd /home/fred/recover
mkdir ods
find /home/fred/recover/recup_dir.1 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.2 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.3 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.4 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.5 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.6 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.7 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.8 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.9 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.10 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.11 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
find /home/fred/recover/recup_dir.12 -name "*.ods" | xargs -i mv {} /home/fred/recover/ods/ 
```

The I found scripts for photos & Flacs to rename them from the internal ids.

---

### Post by samihaxor on 2011-04-23
> **dearingj said:**
> Maybe this command line will help. I found it in [this thread]("https://www.linuxquestions.org/questions/linux-newbie-8/command-to-select-and-move-mutiple-files-from-list-in-text-file-386372/") on linuxquestions.org:
```
for i in `cat filename`;do mv "$i" destination; done
```

Be sure to use "the right thingie": ` not '
and replace the word destination with wherever you want the files moved to, and filename with the name of the text file

Thank you very much! 

i use:

```
find /home/sam/recover2/ -name '*.jpg' -a -size +1M > output.txt
```

to create a file name output.txt that contain all the files larger than 1 mb. Then i use 

```
for i in `cat output.txt`;do cp "$i" /home/sam/imagesr/; done
```

and i move all the files listed on the output.txt to /home/sam/imaesr

i hope this can help another person.

Thank for your support!

---

### Post by Vaphell on 2011-04-23
you could have skipped the file part
find allows to perform an action on each found item

```
find <criteria> -exec mv "{}" <destination> \;
```

---

