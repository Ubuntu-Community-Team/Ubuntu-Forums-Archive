---
title: "Installing windows 7 on top of ubuntu..."
date: 2011-11-08
forum: General Help
---

### Post by renegadeandy on 2011-11-08
Hey guys.

I currently have 11.10 installed, and now I need to install windows 7.

I open up gparted to make an NTFS partition for windows 7 - and it says that Linux unified key setup encryption is not yet supported - and i dont appear to be able to resize that partition to make room for this new NTFS partition.

Assuming somebody can help me with that - i want grub to maintain the bootloader segment, yet i assume windows 7 when installing well override that. How can i stop this / or fix it once it happens?

Cheers:):)

---

### Post by skullriot on 2011-11-08
Hiya
 I just did a windows 7 dual boot with 11.10 myself, but what i did was install windows FIRST, and then 11.10. I used the windows install partition editor to set up 3 partitions, and then windows told me it needed a small one in the one i told it to use, and then ubuntu set up itself at the other end of my hard drive. As far as i know, windows is touchy about how its installed, so it needs to be installed first usually. Just do a web search for dual boot windows ubuntu or something along those lines and you will get a hit on the main article and a few others that have good information.

---

### Post by renegadeandy on 2011-11-08
Yeah but i cannot scrub my existing linux install - too much on here - too valuable. So it has to be this way round im afraid.

I thikn i have a guide - but i need to be able to make a new partition and gparted doesnt appear to be able to help me because of the encryption. Help!

---

### Post by Megaptera on 2011-11-08
Don't forget to back up everything important on your existing linux install to external media, if you haven't already done so .... just in case!

---

### Post by BillyBoa on 2011-11-08
I guess you used gparted from a live cd to have the drive unmounted.
Installing Win 7 it's impossible to make partitions on a ext4 drive so it's going to format everything.
So try to make the partitions with gparted.

---

### Post by renegadeandy on 2011-11-08
No - i used gparted by going into it from my linux install im booted into - but its got a warning light with what i quoted on the original post.

Do you think it would work if i tried it from a flash drive boot?

Cheers

---

### Post by renegadeandy on 2011-11-08
Help please.... i dont know how to make the NTFS partition when gparted sees my sda2 partition it says it has a warning and complans that it cannot touch it because of LUKS...?

---

### Post by Superdarion on 2011-11-08
Quick google search resulted in this:

[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)


Basically:

> Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.

At this time, the crypt must be re-sized from a live CD in multiple steps, manually, from the command line.

It should go without saying, resizing your crypt may result in data loss  Be sure to BACK UP your data first. 


---

### Post by techvish81 on 2011-11-08
on what u r on to do, i think u r going to loose ur data and also , u may not be able to boot to linux, or i can say , u may have to repair your linux installation , so be sure to backup everything important, 

and atlast if you r ready to backup everything important , why to fall in this unholy mess? just format ur hdd, install win7 and then install ubuntu. it will be very easy than anything you can do from here. you can backup ur ubuntu apps by copying your var/apt/archives folder to anywhere safe, it will give an error while copying but just press skip, and it will copy everything except something which is "locked"???? , i don't know what is it but it is not much important, i've done it many times, after doing so, when ur ready with ur final ubuntu installation, just copy that folder to your download folder in home dir , and select "add downloaded packages" from the synaptic package manager menu( u will have to install synaptic as it doesnt come by default..) and point it to the folder where u have put your "archives" folder.
after that it will give u an error that " u have held broken packages" , dont panic , just update cache( u need a working internet connection, but it will not take much of your bandwidth) by pressing reload button and then click on "fix broken packages" by magic... they will be fixed and u will have everything u downloaded,installed and kept in "var" (not intentionally selected to delete everything after installation) .. 

so this may help you, best of luck! 

Cheers!!:guitar:

---

### Post by audiomick on 2011-11-08
> **renegadeandy said:**
> No - i used gparted by going into it from my linux install im booted into - but its got a warning light with what i quoted on the original post.

Do you think it would work if i tried it from a flash drive boot?

Cheers
Wont work, you can't change a partition that is mounted. The easy way is to boot into a live CD and use gparted from there.

Have you read this yet? It deals with Windows after Ubuntu in the second half of the page.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by renegadeandy on 2011-11-08
techvis your reply was not helpful - sorry.

Is it possible to remove LUKS, resize partition, install windows 7, restore mbr back to grub, voila.

---

### Post by techvish81 on 2011-11-08
resizing the partition in which the grub is located, may result in failure to boot...
i am sorry! if you are hurt by my  previous post..

---

### Post by satanselbow on 2011-11-08
> **renegadeandy said:**
> 
Is it possible to remove LUKS, resize partition, install windows 7, restore mbr back to grub, voila.

Have you read the article Superdarion posted: [http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

It is a pretty well written article with some good information directly related to your current query ;) 

There is also some good related info here: [http://domesdomain.de/blog/2010/06/09/howto-decrypt-luks-partition-with-keyfile-or-password/](http://domesdomain.de/blog/2010/06/09/howto-decrypt-luks-partition-with-keyfile-or-password/)

---

### Post by audiomick on 2011-11-08
> **renegadeandy said:**
> techvis your reply was not helpful - sorry.

Is it possible to remove LUKS, resize partition, install windows 7, restore mbr back to grub, voila.
What I don't know is if you can de-encrypt the file system, sorry. The rest of those steps are exactly how it should go. Not being able to change a mounted partition still applies, though. I always do partitioning from a live CD or USB.

If you can't undo the encryption, and I hope someone will show up who knows about that, you may have to copy out the contents of your /home (and any other data  partitions, but not / ) onto another drive and then put them back into a new install. If you do this right, you should get back to the state you have now.

---

