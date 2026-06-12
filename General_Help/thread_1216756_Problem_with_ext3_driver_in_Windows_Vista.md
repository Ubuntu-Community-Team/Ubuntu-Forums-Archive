---
title: "Problem with ext3 driver in Windows Vista"
date: 2009-07-18
forum: General Help
---

### Post by os56k on 2009-07-18
I installed the driver for ext3 from [http://www.fs-driver.org](http://www.fs-driver.org)

I formated my partitions with GParted from Live Ubuntu 9.04 and I think because the inode is 256, I receive the error "The disk is not formatted ". 

On the [http://www.fs-driver.org/relnotes.html](http://www.fs-driver.org/relnotes.html) is said to run the command mkfs.ext3 with -I 128 switch.

Now I don't know where to run this command from ? Is all my partition deleted when I change inode size ?

---

### Post by Jose Catre-Vandis on 2009-07-20
Try using Ext2Fsd instead, this works with inode = 256

look [here]("http://www.google.co.uk/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fext2fsd%2F&ei=zZ1kStP4BM3RjAfMp_j9Dw&usg=AFQjCNEX7893SYRkZbFlnzq2YRB49yYLDw&sig2=qbEL72IUaJuDkB6TZ5XepQ") for download

---

### Post by os56k on 2009-07-20
I tried Ext2fsd latest version and I enabled the option during install like below :
[IMG][[IMG]http://thumb2.webshots.net/t/55/555/4/83/75/2078483750105377042nzqWhx_th.jpg[/IMG]](http://travel.webshots.com/photo/2078483750105377042nzqWhx)[/IMG]
but at the end of installing I see the following error :

[IMG][[IMG]http://thumb2.webshots.net/t/96/96/3/35/63/2069335630105377042nDfoKB_th.jpg[/IMG]](http://travel.webshots.com/photo/2069335630105377042nDfoKB)[/IMG]

after I set the drive letter of my /home partition and I double'click it on My computer I see the following error :

[IMG][[IMG]http://thumb2.webshots.net/t/96/96/0/84/23/2551084230105377042eOeSqE_th.jpg[/IMG]](http://travel.webshots.com/photo/2551084230105377042eOeSqE)[/IMG]

---

### Post by Jose Catre-Vandis on 2009-07-21
And after a reboot?

It did work for me straight away on Windows 7 RC. I used the 0.46a version of Ext2fsd.

Have you still got Ext2 IFS installed? This might be getting in the way?

---

### Post by os56k on 2009-07-23
I downloaded th latest version from [http://sourceforge.net/projects/ext2fsd/files/](http://sourceforge.net/projects/ext2fsd/files/) .
I downloaded the first file which is 2.5 MiB and I installed it. It must be installed from the windows command prompt but again I see the driver signature error in the command prompt.
I disable signature check when Windows boots by pressing F8 and then choosing "Disable Driver Signature Check Enforcement" and I can see my ext3 partitions.
But I must always press F8 and do like above unless I see the "Do you want to format it" error.

In the zip file I downloaded there was a driver certificate and installing it did not solve my problem. I am using Windows Vista Service Pack 2.

---

### Post by os56k on 2009-07-27
Just released Ext2Fsd 0.48. One of the major changes is getting driver signed for Vista / Server 2008 systems.

[http://sourceforge.net/projects/ext2fsd/files/Ext2fsd/0.48/Ext2Fsd-0.48.exe/download](http://sourceforge.net/projects/ext2fsd/files/Ext2fsd/0.48/Ext2Fsd-0.48.exe/download)

It's fantastic. My problem is solved.
I now have no problem with Windows Vista driver signature test.   :D:D:D:D:D:popcorn:

---

