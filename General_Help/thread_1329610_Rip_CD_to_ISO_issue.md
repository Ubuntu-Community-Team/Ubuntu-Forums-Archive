---
title: "Rip CD to ISO issue"
date: 2009-11-17
forum: General Help
---

### Post by pearldrums on 2009-11-17
for some time now I've been having issues ripping ISO files with Brasero. Finally I decided to do something about it, and installed multiple different programs to do the job, none of them worked. I did see that you could use the disc dump command in the terminal to create an ISO, but I'd like a simpler gui way of doing this. Heres the awkward thing, when I put in a DVD I am able to make an ISO, but when I put in a CD, the option to change from TOC to ISO is just not existent. Anyone have any clue what might be happening?

---

### Post by arnab_das on 2009-11-17
try k3b.

---

### Post by SuperSonic4 on 2009-11-17
K3b works well for me

---

### Post by Aubergines on 2009-11-17
If dumping the image is too complicated to remember you can simply make a script to do it for you. Here's how to set it up in 60 seconds. The script is super easy all it does is launches a terminal which just prompts you to give the iso a name. That's it. It'll then rip the cd and put the iso on your desktop.

```
#!/bin/bash
echo -n "Give the iso a name: "
read isoname
dd if=/dev/cdrom of=/home/`whoami`/Desktop/$isoname
```

Save it as a file, call it a name like like "isorip" and make the file executable:

```
chmod +x isorip
```

Move the script to a logical place like /usr/local/bin/

Then just make a shortcut on the gnome menu by going to "Main Menu" found in System > Preferences on the gnome menu. Adding a new item as type "Application in Terminal" and put the script in the command box. You can then simply run it like any other app from the menu.

---

### Post by HermanAB on 2009-11-17
Geez, all these complicated solutions...

Here kitty, here kitty, kitty:
$ cat /dev/cdrom > filename.iso

---

### Post by pearldrums on 2009-11-17
thank you very much for info on making a script... thats where I would have been going next. Mostly I don't want to mess around with commands where if I make a mistake I can write over parts of my disk. Although I'm going to use this option for now, I'd still like to make my brasero work and I'm going to leave this thread as unsolved. The big problem is... that I don't know what the problem is!

I've tried k3b as well... didn't work.

---

### Post by pearldrums on 2009-11-18
One more thing Aubergines, if I have 2 CD drives will it ask me which drive, or how will that all work?

---

### Post by Aubergines on 2009-11-18
The above script will just rip the cd from /dev/cdrom which is the first cdrom on a system.

If you did something like this, it'll ask you whether you want to rip from cdrom1 or cdrom2.

```
#!/bin/bash
echo -n "Give the iso a name: "
read isoname
echo -n "Rip from cdrom1 or cdrom2? "
read cdnum
if [ $cdnum -eq 1 ]; then
        dd if=/dev/cdrom of=/home/`whoami`/Desktop/$isoname
else
        dd if=/dev/cdrom1 of=/home/`whoami`/Desktop/$isoname
fi
```

Assuming that when you have 2 cdroms linux will still call the first one "cdrom" and the second drive as "cdrom1". It could be "cdrom0" and "cdrom1" not 100% sure. You can check by typing

```
ls /dev/cd*
```

---

### Post by pearldrums on 2009-11-18
this is frustrating, I might actually be having a global issue on creating ISOs. I tried dd in a regular terminal and got this:
```
levi@Levi-Ubuntu-HQ:~$ dd if=/dev/cdrom1 of=/home/whatever.iso
dd: opening `/home/whatever.iso': Permission denied
```
I tried it with both cdrom and cdrom2 and both of them said "no such file or directory"

So then I tried sudo...
```
levi@Levi-Ubuntu-HQ:~$ sudo dd if=/dev/cdrom1 of=/home/whatever.iso
[sudo] password for levi: 
dd: reading `/dev/cdrom1': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00146716 s, 0.0 kB/s
```

hmmm, this looks like [a thread from 2008]("http://ubuntuforums.org/showthread.php?t=747197") unfortunately that guy didn't get any useful solutions.

---

### Post by bluelamp999 on 2009-11-18
Or just use Nautilus?

Mount the CD, select Copy Disk..., you can then set the resulting file as an ISO. 

Works perfectly for me in 9.10

---

### Post by BQAggie2006 on 2009-11-18
What kind of CD is it? Audio or Data?

---

### Post by Aubergines on 2009-11-19
[https://help.ubuntu.com/community/CreateIsoFromCDorDVD](https://help.ubuntu.com/community/CreateIsoFromCDorDVD)

---

### Post by falconindy on 2009-11-19
> **pearldrums said:**
> this is frustrating, I might actually be having a global issue on creating ISOs. I tried dd in a regular terminal and got this:
```
levi@Levi-Ubuntu-HQ:~$ dd if=/dev/cdrom1 of=/home/whatever.iso
dd: opening `/home/whatever.iso': Permission denied
```
I tried it with both cdrom and cdrom2 and both of them said "no such file or directory"

So then I tried sudo...
```
levi@Levi-Ubuntu-HQ:~$ sudo dd if=/dev/cdrom1 of=/home/whatever.iso
[sudo] password for levi: 
dd: reading `/dev/cdrom1': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00146716 s, 0.0 kB/s
```

hmmm, this looks like [a thread from 2008]("http://ubuntuforums.org/showthread.php?t=747197") unfortunately that guy didn't get any useful solutions.
On the first try, you're getting access denied because you're writing to home's root, and not **your** home. You omitted the `whoami` section of the script, which would have resolved your user name and written to the proper location.

Second try, /dev/cdrom1 isn't being found. I suspect /dev/cdrom or /dev/cdrom0 would work. What do you see if you do the following:
```
ls -l /dev/cdrom*
```

---

