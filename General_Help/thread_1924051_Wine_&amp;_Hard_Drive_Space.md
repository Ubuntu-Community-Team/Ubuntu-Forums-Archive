---
title: "Wine &amp; Hard Drive Space"
date: 2012-02-11
forum: General Help
---

### Post by kraziyk on 2012-02-11
Hey all,

I am brand new to Ubuntu. I have had it for about a week. I love it and all. I am using wine to run a windows program. Ubuntu 11.10 is installed on my OS hard drive which is roughly 50GB. I want to keep as much stuff off that hard drive as possible. Is there a way to install a program through wine onto my secondary hard drive that is 500GB? If so how do I do that. 

Again I am new to Ubuntu, and but am fairly tech savy. I have no programming background, just fyi.

Thanks for the help.

---

### Post by fantab on 2012-02-11
> **kraziyk said:**
> Hey all,

I am brand new to Ubuntu. I have had it for about a week. I love it and all. I am using wine to run a windows program. Ubuntu 11.10 is installed on my OS hard drive which is roughly 50GB. I want to keep as much stuff off that hard drive as possible. Is there a way to install a program through wine onto my secondary hard drive that is 500GB? If so how do I do that. 

Wine installs all its installations in its own folder which is in "/" and in /home if you have any.. I am not sure if you can install any thing in any other partition which is not "/". 

 I conclude from your post that you have two hard drives, is that right? 
Do you have separate /home? If you have a separate /home then 50GB for '/' is plenty more than enough to install more things than you need.

If you have another Hard Drive which is 500GB then you should not be really worried for space.  You can use it save your Data and use 50GB for OS Files.

---

### Post by kraziyk on 2012-02-11
I only have the /home that the ubuntu dvd installed. I know 50GB is fine, I just prefer to keep the 50GB drive for my OS only, or as little on it as possible.

And yes I have two hard drives. One 50GB (OS) and a 500GB where I typically put programs, photos, docs, etc.

---

### Post by Toz on 2012-02-12
Here are 2 ways that you can run wine with the wine files on the second drive:

1. Use WINEPREFIX to specify the location of the wine virtual environment on the second drive. See: [http://wiki.jswindle.com/index.php/WINEPREFIX]("http://wiki.jswindle.com/index.php/WINEPREFIX").

2. Move your ~/.wine directory to the second drive and create a link to it on the first drive. Assuming the second drive is mounted at /media/DRIVE2:
```
mv ~/.wine /media/DRIVE2
ln -s /media/DRIVE2/.wine ~/.wine
```
Everything will work as it does now, only the files will exist on the second drive and be referenced (accessed) via the link on the first drive.

---

