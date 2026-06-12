---
title: "installing applications into secondary partitions"
date: 2009-12-29
forum: General Help
---

### Post by mdmill9999 on 2009-12-29
[I am triing to approach a problem discussed in an old (closed) thread, but in a new way...I hope the Moderators will be tolerant, thanks]
 
Linux OS root partitions cannot allways be simply expanded...especially in "many"-boot systems. My original question was: Is there a way of installing new software packages to a secondary (ext3) data partition (~50GB). This will save room in my root partition for system files and allow me to expand my apps indefinitely.
This is easy to do in XP or W98...ie simply specify the logical drive to install to!
 
You may think this goal inappropriate for a linux OS, but humor me...Do you think the following would work?
 
First, assume that the data partition is permanantly mounted to _/media/datext3/_ and 
a folder has been created in there named "usrUBU" ie _/media/datext3/usrUBU/_.
 
Also, most user apps are installed into the "usr" folder (I understand), so...
 
rename _/usr_ to _/usr-old_
 
create a symbolic folder (soft) link named "usr" in the root ... ie use command
 
"ln -s /media/datext3/usrUBU/ /usr"
 
copy _/usr-old_ to _/usr_ ie copy all files and subfolders using the -d option (ie copy any symbolic links literally-do not follow them), and maintaining all old attributes.
[what would be the command line to do this?]
 
Wouldn't all system read and writes to _/usr_ actually be performed in the _usrUBU_ folder in the data partition? Would this work?
 
I know this is a difficult question to answer, but maybe one of you more expert would have an idea.... Thanks M D Mill

---

### Post by michy99 on 2009-12-29
I'm certainly no expert, but it sounds like it would work. Another way to go would be to create a new partition and mount it at /usr. I think that is how I would do it.

---

### Post by john newbuntu on 2009-12-29
I too think that would work.  But /usr is a heavily used filesystem and would involve a symlink lookup for every call made to it.  I agree with michy99 in allocating a separate partition for it.

---

### Post by mdmill9999 on 2009-12-29
I cannot "afford" to create an extra partition for every OS on my computer (10 or more) [all my swap files are also created internal to the root partition].  Therefore I would create a folder (eg /usrUBU, /usrKub, /usrSuS, etc) for every linux OS; and they will all be placed in the single _datext3_ partition.
 
Therefore I only have to deal with one secondary partition, which may be quite large.

---

### Post by mdmill9999 on 2010-01-01
[FONT=Arial Black][SIZE=4]I would like to reiterate my request for experienced Linux users to contemplate the [/SIZE][/FONT]
[FONT=Arial Black][SIZE=4]feasability of installing applications into a seconday partition [folder], as described in the original posting...do you see any (hidden) flaws or problems.[/SIZE][/FONT]
[FONT=Arial Black][SIZE=4]This would seem a very worthwhile operation, in some instances, for the reasons given there. thanks.[/SIZE][/FONT]

---

