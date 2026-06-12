---
title: "Save /home to a folder in a partition"
date: 2010-02-05
forum: General Help
---

### Post by AmpersUK on 2010-02-05
Hi Folks,

Only need a **yes **or **no **answer here.

To save hours of searching, can anyone tell me if the following is possible.

I have a **dual boot** machine. I have changed "My Documents" in Windows 7 to my G **partition** to the **folder **"G/Windows data"

I have just bought a Buffalo networked 1TB LinkStation backup drive for our two desktops and notebook, and the backup software is useless for Linux and Windows 7 - won't install with anything later than XP! So I will want a linux program to backup the two folders in Drive G to the LinkStation every day, automatically - if that is possible.

I now want to change my /Home drive to another ***_[COLOR="Red"]folder[/COLOR]_*** in the G drive called "G/Ubuntu data"

Is this possible, yes or no?

Ampers.

---

### Post by audiomick on 2010-02-05
Just to be sure: I am talking about a "real" install, not a  wubi. When you say this
> I now want to change my /Home drive to another ***_[COLOR=Red]folder[/COLOR]_*** in the G drive called "G/Ubuntu data"
it makes me suspect a wubi install, as that is windows nomeclature.

What you are intending should be possible as far as I know.
There is info about moving your /home here
[https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
a bit sketchy, but it will get you started

For your backups, look at rsnyc.
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by AmpersUK on 2010-02-05
> **audiomick said:**
> Just to be sure: I am talking about a "real" install, not a  wubi. When you say this
it makes me suspect a wubi install, as that is windows nomeclature.

I have a dual boot machine with Windows 7 and Ubuntu 9.10.

I do ***_not_*** use Wubi at all.

Mind you, I am slowly moving all my software over to Ubuntu, the last major movement is InDesign desktop publishing. I looked at Scribe and decided it was not up to serious work, until someone persuaded me to get the original Scribus book from Amazon UK. I did and, having read it cover to cover, I am now convinced it will do everything I want so there will soon not be a need for dual booting, although I will need Windows in VBox for my poker :-)

Ampers

---

### Post by AmpersUK on 2010-02-05
Took a look at the first two links and they talk about partitions, and not about folders in partitions :-(

I really don't want the data on separate partitions. :-( :-(

---

### Post by audiomick on 2010-02-05
> **AmpersUK said:**
> Took a look at the first two links and they talk about partitions, and not about folders in partitions :-(

I really don't want the data on separate partitions. :-( :-(
It is, to an extent, a moot point.
If you have a partition mounted at /any/mount/point, as far as the file system is concerned, it is a directory (folder).
As far as I can tell, the only practical difference is that any directory that is on a partition of it's own can be re-mounted "as is" in the case of a new install.

---

### Post by AmpersUK on 2010-02-05
> **audiomick said:**
> It is, to an extent, a moot point.
If you have a partition mounted at /any/mount/point, as far as the file system is concerned, it is a directory (folder).
As far as I can tell, the only practical difference is that any directory that is on a partition of it's own can be re-mounted "as is" in the case of a new install.

OK I'll read up a little more and try do do that. At present, I have used a quick fix by using rsync to make a mirror image on that drive.

I am old and not a computer expert :-)

Ampers

---

### Post by audiomick on 2010-02-05
> **AmpersUK said:**
> 
I am old and not a computer expert :-)

Ampers
I am, at 46, just young enough to have known computers all my adult life. In my first or second year at Uni, macs and pcs appeared on the market.
I am really glad I am not 10 years older. ;)

---

### Post by oldfred on 2010-02-05
Your /home in ubuntu has to be a linux formated partition for permissions to be set correctly for all the hidden files and folders. But all your data does not actually have to be in /home. I have two data partitions one NTFS for sharing firefox and thunderbird profiles with windows so our main apps were the same in both as we converted and now a ext3 partition for all my other data. All the default folders plus several others are converted to links.
I have linked those data partitions into /home and home is now less than 1GB with 3 years of history in some of the hidden folders.

Using links for data from linux partition but data can be NTFS
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.htm](http://blog.linuxtoday.com/blog/2009/08/painless-linux.htm)

I mounted my ext3 data partition where the file browser would not see it. and used this in home to link.
ln -s /usr/local/fred/data/Music
etc for every folder in my data directory which has all the default folders in home plus a few more.


Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

---

### Post by AmpersUK on 2010-02-05
I was 38 when the Commodore PET came out in 1977.

---

### Post by AmpersUK on 2010-02-05
> **oldfred said:**
> Your /home in ubuntu has to be a linux formated partition for permissions to be set correctly for all the hidden files and folders. []("http://ubuntuforums.org/showthread.php?t=1397508")

I formatted Drive G with Fat32, should that be OK for everything should I manage to get /Home in a folder?

I have a terabyte drive with four 250gb Partitions at present, and can always do that.

I did want them both in the same partition for backing up to my LinkStation Live drive, but I can always write a routine to do this, or even get rsync to do it.

First I have to get Ubuntu to actually see the LinkStation Drive, Windows can.

Ampers.

---

### Post by audiomick on 2010-02-05
> **AmpersUK said:**
> I was 38 when the Commodore PET came out in 1977.
That makes you a year or two younger than my dad. He uses a computer, but I couldn't imagine him even thinking about doing things like partitioning himself...

---

### Post by oldfred on 2010-02-05
Be careful of FAT32. It has a 4GB limit. I orginally was running my backups the a FAT partition and every one was 4GB for about 2 years. Then I converted to ext3 and the backup was much larger. I never had a good backup. Some media files video are larger the 4GB also.

NTFS is prefered for sharing with windows. 

NTFS and Fat info:
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

---

### Post by AmpersUK on 2010-02-05
I may be seventy but I edit and publish a community newspaper in Finchley (Finchley Arrow) have a blog, a website, a humour group on Google, write occasionally for the press, and if you came in to my office at home and saw all my kit and wiring you'd have a seizure :-)

---

### Post by AmpersUK on 2010-02-05
> **oldfred said:**
> Be careful of FAT32. It has a 4GB limit. I orginally was running my backups the a FAT partition and every one was 4GB for about 2 years. Then I converted to ext3 and the backup was much larger. I never had a good backup. Some media files video are larger the 4GB also.

NTFS is prefered for sharing with windows. 

NTFS and Fat info:
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

Hmmmmm... OK, I am not going to get exactly what I want - I wanted to avoid logical partitions, but I am going to have to rethink my whole strategy.

I think I might leave things for a little while. I am moving my dtp from InDesign to Scribus (I bought the Scribus book on Amazon and then realised it was more powerful than I thought.

Once that is done, I can get rid of the windows dual boot, and make the whole computer Linux - a month or so.

Then I'll put Win7 on VBox as I will still need it for supplementing my income (I play poker) ;-) VBox will be sufficient for Poker.

Ampers

Thanks to all for your help, and it has been helpful as it has stopped me wasting time searching for something I am not going to find. Some things are a success if it redirects your thoughts.

Ampers.

---

### Post by audiomick on 2010-02-05
> **AmpersUK said:**
> .... and if you came in to my office at home and saw all my kit and wiring you'd have a seizure :-)
probably. I am a sound engineer, so I am a bit funny about how cables are run.;)

There is no reason that I am aware of to not use logical partitions. The four partition limit is an archaic restriction dating back to a time when no-one could imagine needing more than four. The extended/logical mechanism was developed to get around this limitation. It is quite possible with a linux only system to have only one extended partition and everything in logical partitions inside that; up to 64 logicals, I believe.

---

### Post by AmpersUK on 2010-02-05
> **audiomick said:**
> There is no reason that I am aware of to not use logical partitions. The four partition limit is an archaic restriction dating back to a time when no-one could imagine needing more than four. The extended/logical mechanism was developed to get around this limitation. It is quite possible with a linux only system to have only one extended partition and everything in logical partitions inside that; up to 64 logicals, I believe.

OK, I will have a play around, thanks for your help - talking about sound, my X-Fi was working well in 32-bit but since I got 64-bit - nada... But it's no problem, I just port the files over to Windows for next time I go in.

---

### Post by audiomick on 2010-02-05
Yes, have a look at it. Take your time, maybe make a partition plan before you start.

I am afraid I have very little idea about sound on the computer. In my old fashioned mind, the computer is not a "real" sound system, and I haven't really looked into it much. Sorry I can't help.

---

