---
title: "GParted Deleted Wrong HDD Partition"
date: 2011-03-17
forum: General Help
---

### Post by TonyFordz on 2011-03-17
Hello,

Most times I use my brain but some how I really screwed up with deleting the wrong hdd's partition which was an 500GB NTFS with all of my custom programs, art, web design & so on which can not be replaced. Is there a way to reverse this process? Keep in mind I am not Linux friendly being I do not know the commands & so on so any copy paste commands with good detail on what it does would be greatly appreciated!

I used GParted to delete & already hit the accept but no other changes have been made on the HDD after that. I am currently running in Live mode as I was going to install on the 80GB which is the one I meant to delete but instead had a nice moment of insanity & deleted the 500 instead!

Please let me know!

Thanks,
Tony

---

### Post by pqwoerituytrueiwoq on 2011-03-17
testDisk is probably your best bet for getting stuff back
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
if you do/did not put anything where it (the partition) was you should be ok
EDIT:
600 beans

---

### Post by TonyFordz on 2011-03-17
Thank you for the link,

So I downloaded them 2 different ones but I dont know how to use the content because its not something that just installs.

- Linux, kernel 2.6.x i386/x86_64
[http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2](http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2)

&

- Linux i386 RPM
[http://www.cgsecurity.org/testdisk-6.11.3-1.i386.rpm](http://www.cgsecurity.org/testdisk-6.11.3-1.i386.rpm)

Seams that both Ubuntu & I both have no clue what to do with these file types though I do understand that they are both archive files.

When I open the tar with the manager it has files & folders but as I said I am not Linux Friendly being I have no clue how to use the files with in.

Any words of wisdom? Like perhaps go back to Windows?

---

### Post by pqwoerituytrueiwoq on 2011-03-17
rpm is fedora
you want the Linux, **kernel 2.6.x** i386/x86_64
remember in the boot menu seeing entries like 
Ubuntu 10.04.2 LTS, **kernel 2.6.**32-29-generic
BTW google and youtube can be useful
[http://lmgtfy.com/?q=site%3Ayoutube.com+testdisk]("http://lmgtfy.com/?q=site%3Ayoutube.com+testdisk")
also readme files are useful

there are 2 executable files in the linux folder

---

### Post by TonyFordz on 2011-03-17
Aright,

As I said I downloaded both & the tar is the one I can open but it doesn't install anything & I have no clue how to use the files in the archive. Is it a command line program? Is there not a program I can use that installs & runs like GParted?

---

### Post by pqwoerituytrueiwoq on 2011-03-17
it is a command line gui 
like a xp install disk is at the beginning
depends on which you want to use

sudo /path/to/testDisk/linux/photorec_static

sudo /path/to/testDisk/linux/testdisk_static

there is a program called alien that can be used to make deb files from rpm file (fedoria installer to ubuntu installer)

---

### Post by srs5694 on 2011-03-18
TestDisk is in the Ubuntu repositories; you can install it using various GUI package tools or by typing the following in a Terminal window:

```

sudo apt-get install synaptic

```

Although TestDisk is probably the easiest way to recover that partition, it's not always 100% reliable. Since you haven't yet rebooted, there may be a more reliable way to recover that partition, as described [here.](http://ubuntuforums.org/showpost.php?p=10364557&postcount=34) This process is tedious, and if GParted convinced the kernel to begin using its modified partition table, it probably won't work; but if the kernel continues to use the old partition table and if you're careful, you can recover the old partition this way. If you're very careful in what you do, this method is more likely to work; but if you're sloppy, TestDisk will be safer.

---

### Post by pqwoerituytrueiwoq on 2011-03-18
"TestDisk is in the Ubuntu repositories;"
say wha---
i thought i checked for it in there and did not see it...
](*,)

---

