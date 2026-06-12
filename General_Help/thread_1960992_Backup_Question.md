---
title: "Backup Question"
date: 2012-04-18
forum: General Help
---

### Post by yaacovk on 2012-04-18
Hi.
what will happen when i'll restore the home folder
into a new installation (exist ver. or in new ver of ubuntu)?

Yaacov.

---

### Post by raja.genupula on 2012-04-18
Actually Home folder consists of lot of things , for example Application data ,i mean how you have configured that application and the settings of it . all will be there it self . 

so if you have taken a back up and if you restore it the all the old configuration files be loaded instead of new .

like that all files get replaced by the backup files . its a best way to keep the information of home folder as a backup .

---

### Post by codemaniac on 2012-04-18
Hello yaacovk , if you have a archived your previous /home and restore it to new installation , you should keep in mind that your applications config are there in your /home .Now suppose in your earlier version of Ubuntu if a particular application was not installed you might lose some of the application configurations .Say irssi was not installed in your earlier installation , now if you restore home , ~/.irssi folder will be missing and you will loose all your present irssi settings .Did i explain correctly ?

---

### Post by cortman on 2012-04-18
I would only restore your personal documents and your ~/bin folder, if you have one. The rest is old settings- you could keep them for reference if you want to set current settings similarly. But don't restore them as your new /home folder.

---

### Post by ajgreeny on 2012-04-18
It's always worth considering making a separate /home partition when you install your OS as it means you can largely forget about this question.

However, particularly with the last OS update from 11.04 to 11.10, which moved from gnome-2 to gnome-3, it is possible that some of the configurations that are stored in your home as hidden named folders, will not work totally as you expect.  It is generally fairly easy to put things right after any such problems, however, and a separate /home is definitely recommended in my opinion.
[Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by Roasted on 2012-04-18
Splitting root and home is always a great way to set up your system. I haven't lost any personal data or had to back anything up when doing a fresh install since 2007 when I first started this.

The only trick is, you need to be comfortable in the advanced partitioning menu. I follow the same process each time I do a new disk setup as well as a new install.
[B]
Disk Prep (When you have personal data backed up with nothing to lose on the drive and you're just setting up your partition scheme)[/B]
Advanced Partitioning
Create SWAP space (equal to RAM amount normally)
Create 15GB partition, format to EXT4, mount as /    (/ means root)
Create a partition the size of the remainder of the disk, format to EXT4, mount as /home
Install Ubuntu
[B]
Disk Prep done, a new version of Ubuntu comes out, you want to install it but not lose your home directory[/B]
Advanced Partitioning
Select 15GB partition you used for /, select EXT4 as file system, mount as /, check format (since you'll be formatting your older Ubuntu OS and installing the new one)
Select the large partition you used for home, select EXT4 as file system, mount as /home, **[COLOR="Red"]BUT DO NOT CHECK FORMAT[/COLOR]**
Continue through the rest of the process
Install Ubuntu

Upon entering your new install, your personal data that was in /home should still be there. If you want an extra security blanket, back your stuff up first, THEN go through installing the new Ubuntu version in the 2nd step. That way your data is backed up so you won't have a panic attack during the installation. I had my data backed up the first time I did this and now I can blaze through the partitioning menu without a hitch. Of course, before I hit continue, I study the checkbox for "format" next to /home and make sure 400 times over it is indeed unchecked. One little checkbox could = a very bad day if you don't double/triple/quadruple check. ;)

---

### Post by mkstallings1 on 2012-04-18
That was a really great explanation of taking advantage of a seperate /home partition when installing a new version of Ubuntu.  Thanks for that.

---

### Post by Roasted on 2012-04-18
> **mkstallings1 said:**
> That was a really great explanation of taking advantage of a seperate /home partition when installing a new version of Ubuntu.  Thanks for that.

Of course. Further adding to it is a video... I had forgotten I made this video as it's on my old YouTube channel I no longer use once Google switched some things around.

[http://www.youtube.com/watch?v=-XyPJcLcbE8&feature=plcp&context=C4f76ab5VDvjVQa1PpcFNd6ugpwVv7D8zCpKwM9BP5ffIJEs2UB74%3D](http://www.youtube.com/watch?v=-XyPJcLcbE8&feature=plcp&context=C4f76ab5VDvjVQa1PpcFNd6ugpwVv7D8zCpKwM9BP5ffIJEs2UB74%3D)

Note: That video was for the drive's "building stage" as I notated above in the beginning of my post. That's why the /home directory defaulted to check "format". If you've already done this and you're just installing a newer version of Ubuntu without changing the partitioning structure, you have the option of checking or unchecking "format" for /home. Again, [COLOR="Red"]**Do Not Check Format For /home!**[/COLOR]

Enjoy. ;)

---

### Post by yaacovk on 2012-04-20
Thank you all, it was very helpful.
i'll make some tests to see what is will be the best way for me.

very thanks.

Yaacov.

---

