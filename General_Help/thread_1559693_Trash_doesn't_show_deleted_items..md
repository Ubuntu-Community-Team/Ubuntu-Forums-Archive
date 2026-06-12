---
title: "Trash doesn't show deleted items."
date: 2010-08-23
forum: General Help
---

### Post by buelligan on 2010-08-23
I have the same symptoms as some other postings, however the posted solutions (re-booting, reinstalling nautilus and re-booting, and installing nautilus-gksu and re-booting) have all failed to resolve the problem.

More specifically, (I just now noticed) when I mouse over the trash icon in the lower right corner, it shows 25 items in trash.  When I click on the icon and keep the mouse pointer in the trash window, I get nothing except the pinwheel (please wait) cursor for one minute.  Then it seems to give up and just shows a blank screen. 

Any help would be appreciated,

buelligan

---

### Post by erilidon on 2010-08-23
try deleting  the files folder located at "/home/<username>/.local/share/Trash/" and rebooting.

---

### Post by buelligan on 2010-08-23
Dear Erilidon,

Thanks for your reply.  I should have warned you I'm a n00b and computers, in general, and Linux, in particular, hate my guts. Tonight the feeling is mutual.  I should also have let you know I'm now running 10.04, not  Hardy like my profile said.

I tried navigating to the directory you specified with the following result:

henry@henry-desktop:~$ pwd
/home/henry
henry@henry-desktop:~$ ls
Desktop    examples.desktop  Public                         Ubuntu One
Documents  Music             RainbowedWorld1600x12004.jpeg  Videos
Downloads  Pictures          Templates
henry@henry-desktop:~$ cd /.local
bash: cd: /.local: No such file or directory
henry@henry-desktop:~$ sudo cd /.local/share
[sudo] password for henry: 
sudo: cd: command not found

It would save me a minor hassle if I could recover the files in the trash, but I'd happily sacrifice them if it will result in a stable fix.

Thanks,
buelligan 

p.s. I verified the md5 checksum of my installer file and it was OK

---

### Post by mc4man on 2010-08-23
Navigate there graphically
Open your home folder (Places -> Home Folder

Then click on the View tab, look down and you'll see "Show Hidden Files"
Click on that, then scroll down a bit and you'll see .local

Open that, and go into share -> Trash -> files
Drag any files you wish to keep, (if any), somewhere, a folder on desktop will do, then delete the rest.
You could also then go into the 'info' folder and delete everything inside.

( if you wanted to list the files from a terminal then this would do
ls  -R ~/.local/share/Trash

---

