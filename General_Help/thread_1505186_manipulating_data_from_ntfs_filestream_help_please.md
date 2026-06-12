---
title: "manipulating data from ntfs filestream help please :)"
date: 2010-06-08
forum: General Help
---

### Post by ToFue on 2010-06-08
Hi, an operator saved a file with a ':' in it, creating a file stream (new concept to me). I'm wondering if anyone with wisdom can point me to know how to get the data from that file piped into another file.. i.e. he saved as "wrong file: rest of wrong file title.wmv" 

so first, can this be salvaged in ubuntu? ..how? .. :confused: 

I figure I'd need the orig. hdd, maybe..:
```

cat "wrong file: rest of wrong file title.wmv" | cat > rightFile.wmv

```

dunno.. Am I grasping, or am I on right track?

this is for work, so I'm not at liberty to tinker & possibly mess it up more than it is..  the encoder's log also lists ":$DATA" after the rest of the file after the colon

if anyone can assist, that would be a complete God-send!!

---

### Post by ToFue on 2010-06-11
Weeeeell   though I didn't find a linux solution per se' this is very insightful to ntfs, which is 'supported' by ubuntu- meaning that ubuntu supports ntfs from fresh install...

...I found this that helped me out:
 
[click for tools to manipulate file streams in cmd for *doze](http://www.flexhex.com/docs/articles/alternate-streams.phtml#cmdline)


basically file streams are... subfiles of files, like directories, except without directory attribute.  if the parent file is empty, that doesn't mean that there is no information there- a child file can have gigs of info and it wouldn't register as taking up space at first glance, giving a file size of whatever the parent contains, only.    

I suppose a use of storing info like this would be to hide sensitive files from view; out of sight, out of mind. I'm curious if it could work with encrypted || compressed files, and I could see a potential use for hiding system files that way, preserving the security features already in place.. food for my thought..  I haven't had time to see if ext2(3,4) supports streams & bash functions to be available to manipulate them yet, but it wouldn't surprise  me if it did.. after all, media files keep meta-data.

---

### Post by bodhi.zazen on 2010-06-11
You have two issues, the : and the space in the title. Linux does not like spaces.

> touch 'fil:e title.wmv'
ls  
fil:e title.wmv

mv fil:e\ title.wmv file\ title.wmv
ls
file title.wmv

So , best to use the tab key for tab completion.

start to type a file name, type the first letter or two, and hit the tab key.

Otherwise use the escape (as above) \ before a space or special character.

Or use quotes "file with space.txt" or 'file with space.txt'

When you have time , you can look at the bash man page to learn all this and the difference between ' , " , and `

I do not think file names with a : in them are a problem:

```
touch file:name:with:colon:.txt
ls                                          
file:name:with:colon:.txt

mv file:name:with:colon:.txt file.txt       
ls                                          
file.txt
```:twisted:

---

