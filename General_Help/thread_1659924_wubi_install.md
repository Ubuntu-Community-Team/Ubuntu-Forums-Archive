---
title: "wubi install"
date: 2011-01-04
forum: General Help
---

### Post by MN_DANGER on 2011-01-04
There is a reason my middle name is: danger
 
Greeting friends I have yet to make!  Bought a Toshiba M200 off craigslist (already sounds destined for craptastic...).  Long story short, the product key did not work and now I hate microsoft.  Thank God for wubi, I barely installed ubuntu before windoze locked me out. I think it was LL, may have been MM....
 
Well one good thing about this ordeal is that I found Ubuntu and this community!
 
Anyway, I am like a monkey with a pistol, just learning everything about Ubuntu.  I was poking around the ubuntuguide.org/wiki and 'updated' something, now Ubuntu wont load.
 
Opening screen gives option of Microsoft Windows XP Pro or Ubuntu
 
Before when I chose 'ubuntu'...aside from the heavens opening up with the sounds of harp music, I would get a desktop.
 
Now when I choose Ubuntu.. I get this:
 
GNU GRUB VERSION 1.98-1ubuntu6
Minimal BASH-like line editing is supported.  For the first word TAB lists possible command completion.  Anywhere else TAB llists possible device or file completion
grub>
 
Ok, so I hit 'TAB' and get a bunch of possible commands.
 
I tried: grub>boot which gave me this: error: no loaded kernel
 
I tried: grub>exit which gave me this: INsert system disk in drive, press any key when ready
 
Ok, so am I totally screwed?  Is there anything I can put in the command line that will load Ubuntu?
 
Reloading OS at this point is going to be very hard...#-o

---

### Post by TeoBigusGeekus on 2011-01-04
Hmm... not an expert on wubi, but... can ubuntu (on wubi) still boot if windows is unbootable?
Why don't you attempt a full installation?

---

### Post by MN_DANGER on 2011-01-04
I believe everything was fully installed.  I was able to load a clean desktop successfully until I ran some line code to 'update' my installer (at least that is what I remember).

Now I have to do something with grub> because it won't let me do anything....

---

### Post by Krytarik on 2011-01-04
It seems like the config file for GRUB is missing or at least GRUB doesn't find it.

Try this: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You may also check if the grub.cfg is present, by using the cat command at the grub>-prompt:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode)

Having done this you may also try to load the kernel manually, by using the initrd and linux commands. And after that re-install GRUB from within your install.

---

### Post by oldfred on 2011-01-04
If you are still running wubi, there is a grub install bug that installs grub to the MBR where wubi still has to boot with the windows boot loader. Wubi runs inside the windows NTFS partition and uses the windows boot loader. It is intended as a longer test for windows users that are not sure they want to stay with Ubuntu.

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Fix for 10.04 upgrade fail bcbc copy wubildr or edit grub.cfg
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

Full install info:
Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by Krytarik on 2011-01-04
I'm also no export of wubi. But as far as I know, the front boot menu -where to choose Windows or Ubuntu- is located at the MBR. When choosing Ubuntu in that menu, the second menu comes up -with the kernel options and other entries-, this one is located at the beginning of the partition where Ubuntu has been installed.

According to the initial post the first menu shows up fine, the second menu fails. Thus you have to try to fix those by the options I've posted above.

---

### Post by bcbc on 2011-01-05
Enter the following at the grub prompt:
```
search -s -f -n /ubuntu/disks/root.disk
echo $root
```

Post back what it tells you. Should be hd0,2 or hd0,1 - something like that - and I can tell you how to boot it.

---

