---
title: "Can't mount my floppy drive anymore"
date: 2010-04-10
forum: General Help
---

### Post by TheAlien on 2010-04-10
I've used the **mount /dev/fd0** command to mount floppies in the terminal, and then I get a floppy icon on my Desktop so I can access my floppy disks.

Now it suddenly doesn't work anymore. My floppy drive is working after I write the command in the terminal, and no error messages appear, but no floppy icon shows up on my desktop. The **mount -l** command show that no floppy drive is really mounted either.

This is very strange since it recently worked and nothing has really changed on my system except for system updates.

Help is much appreciated.

---

### Post by no2498 on 2010-04-10
if it is plugged in with a usb cable unplug it
restart the computer
plug it back in see if that helps

is just a guess hope it helps

---

### Post by oOarthurOo on 2010-04-10
This [technology]("http://www.newegg.com/store/SubCategory.aspx?SubCategory=522&Tpk=flash%20drive"), which was recently made available, might help sort out your problem.

---

### Post by TheAlien on 2010-04-11
> **oOarthurOo said:**
> This [technology]("http://www.newegg.com/store/SubCategory.aspx?SubCategory=522&Tpk=flash%20drive"), which was recently made available, might help sort out your problem.

rotfl!

---

### Post by KeyserSoze93 on 2010-04-11
> **oOarthurOo said:**
> This [technology]("http://www.newegg.com/store/SubCategory.aspx?SubCategory=522&Tpk=flash%20drive"), which was recently made available, might help sort out your problem.

It does help on some occasions, however there's really no reason why Ubuntu should suddenly stop working with perfectly serviceable technology - that's the kind of the Microsoft would get away with.

---

### Post by mycroft34 on 2010-04-12
> **oOarthurOo said:**
> This [technology]("http://www.newegg.com/store/SubCategory.aspx?SubCategory=522&Tpk=flash%20drive"), which was recently made available, might help sort out your problem.
This kind of answer is useless to anyone who MUST use floppies; for example when exchanging data with an apparatus that has only a floppy drive; and there are still many in labs (like mine).
I have had the same problem for several days, following apparently a system update (before I could mount my floppies; now I cannot anymore, and it's a pain to find each time another computer available to transfer from the floppy to an usb device). I add that the device fd0 exists in /dev, that the modules is apparently correctly mounted, and that the entry in fstab is OK. So if anyone could tell me where to search next to correct that problem
it would be appreciated.
Thanks in advance for any help,

---

### Post by ron999 on 2010-04-12
Hi
I have this problem too.
Previously I could use command **mount /dev/fd0**.
Not any more.
:confused: :(:

---

### Post by mycroft34 on 2010-04-12
Hi everybody,
Still looking for an access to my floppy drive; and I have had the idea to look for error on the floppy; below is the result; the floppy is indeed recognized by fsck, but still cannot be mounted; is it possible that the problem come from the mount command ? What could I look for to check that ? Thanks for any idea.

```
patrick@patrick-desktop:/dev$ sudo fsck -a -t vfat /dev/fd0
[sudo] password for patrick: 
fsck de util-linux-ng 2.16
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
/dev/fd0: 0 files, 0/2847 clusters
patrick@patrick-desktop:/dev$ sudo mount /dev/fd0 /media/floppy0 -t vfat
patrick@patrick-desktop:/dev$ sudo umount /dev/fd0
umount: /dev/fd0: n'est pas monté
patrick@patrick-desktop:/dev$ sudo mount /dev/fd0 /media/floppy0 -t msdos
patrick@patrick-desktop:/dev$ sudo umount /dev/fd0
umount: /dev/fd0: n'est pas monté
patrick@patrick-desktop:/dev$ 

```

ps: "n'est pas monté" means not mounted,

---

### Post by ron999 on 2010-04-15
There's a solution in this thread here:-[http://ubuntuforums.org/showthread.php?t=1453956]("http://ubuntuforums.org/showthread.php?t=1453956")

---

### Post by kpoole on 2010-07-07
> **mycroft34 said:**
> This kind of answer is useless to anyone who MUST use floppies; for example when exchanging data with an apparatus that has only a floppy drive; and there are still many in labs (like mine).
I have had the same problem for several days, following apparently a system update (before I could mount my floppies; now I cannot anymore, and it's a pain to find each time another computer available to transfer from the floppy to an usb device). I add that the device fd0 exists in /dev, that the modules is apparently correctly mounted, and that the entry in fstab is OK. So if anyone could tell me where to search next to correct that problem
it would be appreciated.
Thanks in advance for any help,

I must say that you were kinder to oOarthurOo than he deserved.  I'm glad I read your response before I left one of my own.

@ oOarthurOo:  I'll leave it to your imagination what my response to you would have been and, while it would have called into question your intelligence, your parentage and whether or not you ever could make a meaningful comment here, it wouldn't have used a single instance of foul language.  Almost a shame you missed it.

---

### Post by robsoles on 2010-07-11
Yup, oOarthOo is being a bit of a prat there _**BUT**_ there is such a thing as solid state FDD which uses USB memory sticks formatted as as many as 100 floppies per stick.

Before anyone jumps down my throat - I've replaced two old FDDs in two surface mounting machines being used by the electronics company I am Production & IT Manager for - these units have me highly praised by the SMT ops on a regular basis because they used to cry a lot over the high mortality rate of floppy disks not reading after one last successful write in a PC mounted FDD.


On another note, I am now hunting for why my old USB FDD drive won't mount under 10.04 :)

---

### Post by oOarthurOo on 2010-07-14
What a bunch of humourless nancies are weighing in on this thread, with nothing useful to say other than "I look down on you Arthur, from atop my white steed Hye".

OP laughed, so I'm not sure why you think you need to rescue him from the big bad me. 

In any event, had any of you read the op's post, you'd see that mycroft is thread-jacking, because op doesn't have problems mounting the floppy, just with it showing up on the desktop. Or at least, that's how I take this line to mean "My floppy drive is working after I write the command in the terminal"

@ OP, if you're still having problems, report back what desktop you're using, what version of Ubuntu, and the contents of fstab. 

The problem you describe can sometimes be seen when mounting disks outside of /media. Moving the floppy to /media/flippy may be all that's required.

As for further troubleshooting, you might post the output of fdisk -l when the floppy drive is connected and explain how it is connected to the system. 

Or we can just wait for more white knights to weigh in explaining how much moral restraint and greatness it took not to call me names and ignoring your original question altogether. That might work too.

---

