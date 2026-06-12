---
title: "script for moving filetype"
date: 2011-03-01
forum: General Help
---

### Post by glittleman on 2011-03-01
So I'm using photorec to recover files on a formatted external hard drive. And it just bunches the files together by 500's and throws them all in  folders in the directory you tell it to. I have recovered over 80,000 files. I don't need any .txt files or java or html etc. But I want to have seperate music, picture, document, etc folders. I don't really want to cut and paste and I am a newb at using bash so I'd like some help. I know that

 > find - /home/username/Desktop/recovery -type f  will list the files that I recovered and if I add

 >  -name "/*.mp3"than it will find only mp3's

> -exec mv... is the start of move, but I don't know how to make the output of find the src of mv

and from there I am lost. 


Basically I would like  if .mp3 .wav .wmv .asf move to /home/username/Desktop/music_recovered

if .doc .ppt. .pptx .xps .pdf .docx .rtf move to /documents_recovered

if .mpg .mp4 .avi .wmv move to /video_recovered

if .jpg .gif move to /pictures_recovered

if .exe move to /programs_recovered

Any takers on helping me out?

Thanks for your help. I'll appreciate it alot.

btw I will need detailed instructions on how to execute this as well.

---

### Post by zenwalker on 2011-03-01
I believe, you dont need to do the find step itself. You can use the mv command to do the finding (regular expression matching) and move the file if found. 

mv *.mp3 /home 

Does the moving part of all the mp3 files.

---

### Post by glittleman on 2011-03-01
cool man thanks so they are inn a bunch of subfolders

  > mv -r /home/user/Desktop/recovery/*.mp3 /home/user/Desktop/music-recoveredthe problem is the folder ther would be in is /home/user/Desktop/recovery/dir.1  then /dir.2 then /dir.3 etc.   Does -r work with mv???


-edit thats what I thought... that is just as slow as copying and pasting when I have 100 folders to grab files from. to have to do that for each folder, and then for each filetype... I need a script.. But I don't know enough to write my own.

--edit mv is not recursive I need something that will find filetype .mp3 from 100's of subdirectories below a main directory then let me move just those files to a single folder. If its only one filetype at a time, I can handle that.. I can't do one folder at a time.

---

### Post by zenwalker on 2011-03-01
-r just recursively copies and dumps into the destination. You wont get the same hierarchy of folders in the destination as well

---

### Post by glittleman on 2011-03-01
-r doesn't work with mv

---

### Post by nothingspecial on 2011-03-01
use the -o option for different extensions then use exec like so mv '{}' destination

so for your music
```

find -type f -name *.mp3 -o -name *.wav -o -name *.wmv -o -name *.asf -exec mv '{}' /home/user/Desktop/music-recovered \;
```

or do them one type at a time.

---

### Post by tnc on 2011-03-01
Hiya.

I had exactly the same situation you are in.  Copy paste is simply not realistic.

Here is the thread I posted for help:

[http://ubuntuforums.org/showthread.php?t=1692117&goto=newpost](http://ubuntuforums.org/showthread.php?t=1692117&goto=newpost)

Maybe helps you as well?  Also be happy to share anything else I learned that you need.  Post away!

Tim

---

### Post by sisco311 on 2011-03-01
> **nothingspecial said:**
> use the -o option for different extensions then use exec like so mv '{}' destination


or a posix extended regular expression:
```
find ./ -regextype posix-extended -regex ".*\.(mp3|wav|wmv|afs) -exec mv -i -t dest -- '{}' +
```

or in bash:
```
shopt -s globstar
cd ~user/Desktop/recovery
mv -i -t ~user/Desktop/music-recovered -- **/*.{mp3,wav,wmv,afs}
```

---

### Post by glittleman on 2011-03-01
Thanks for all the help guys... I am using the help on Tim's thread 

 [http://ubuntuforums.org/showthread.p...7&goto=newpost]("http://ubuntuforums.org/showthread.php?t=1692117&goto=newpost")

it looks like this 

> sudo find /home/user/Desktop/recovery -iname "*.mp3" -print0 | xargs -0 sudo mv -t /home/user/Desktop/music-recovered

photorec works in sudo so the files were created by root which is why mv is run as root


I'm doing one filetype at a time.

---

