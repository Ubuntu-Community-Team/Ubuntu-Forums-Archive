---
title: "Unable to install ubuntu 9.04 or 9.10"
date: 2009-10-13
forum: General Help
---

### Post by mungiki on 2009-10-13
Hi,

I'm new to ubuntu and I'm have issues installing it on my system.  I have downloaded the iso images and burnt to cd however I keep getting all sorts of errors.  these include an "uncompression error", "corrupt syslinux file" and other times it just freezes and doesnt do anything.

I have downloaded several copies of images (about 6 times each for 9.04 and 9.10beta) all from the ubuntu site, checked the hashes for the images which all turned out ok, burnt images on a total of 11 discs all of which were unable to install due to one reason or another, I have also tried installing within windows vista using wubi but still get an error corrupt file.  I have downloaded using my home computer and my office computer at work and still get issues.  

I have burnt images using different makes of CD and slowest speeds possible ensuring cd is finalised (i.e. burnt at once cannot append files later) and nothing seems to work! burnt using nero, roxio easy media, vista and cdxp.

I also tried creating a bootable USB (using unetboot) which managed to get to the partitioner on install then failed (cant remember the error message exactly but it said some file was corrupt).

I eventually decided to try openSUSE and downloaded the dvd image, worked perfectly the first time without any issues what-so-ever.  I also installed a copy of vista on one of my hard discs just to make sure that its go nothing to do with my dvd drive or hard discs, and that worked perfect as well.

I later found an iso image of a modified ubuntu from PCUser magazine, it installed ok but was so modified I didnt like it and it messed up my windows vista boot, grub f'ed up and though i could select vista it would not boot into vista (also tried EasyBCD and neogrub to create dual boot but didnt work). so I had to partition one of my hard discs, install another copy of vista, boot into that and create a dual boot of vista, which allowed me to get into my old vista install and fix the booting issue and remove the new install and the messed up ubuntu.

I would really like to install ubuntu but just cant figure it out.  Can anyone help with this issue or have you experienced such an issue and resolved it?  I've been at it for about two weeks now and have decided that it cant be a problem with my hardware, must be the image (currently downloading iso image via torrents as a last resort).

I have put a lot of effort into this and would like to succeed so please help me out here.

---

### Post by mungiki on 2009-10-14
**UPDATE... SOLVED** :)(Somewhat) posting this in case anyone out there has a similar scenario...

I managed to get a work around this issue.  I found an ISO image on the cd cover of PCUSER magazine, burnt that on cd and it worked perfectly.  I decided to install ubuntu within windows coz it gave me issues with GRUB booting, causing a boot error.  Though not the ideal solution by installing within vista, it works perfectly as i can choose which OS to load on boot.

I also managed to install OpenSUSE as well, all three are on the same hard disc, though its a bit funny, when booting it goes to opensuse grub, when i select windows, it goes to the windows boot loader which then asks me to decide if i want to load vista or ubuntu, a two step process, but everything loads up perfectly!  i have managed to update ubuntu security and install packages without any hassles so far.  I havent even noticed any decrease in performance while in ubuntu.

My next task will be to point the openSUSE grub to ubuntu directly and remove the option from the vista bootloader....

**CONCLUSION**
There appears to be issues with either the iso images (though the HASH check was perfect for all the ISO's i downloaded):confused: or, there is therefore a ghost in the machine....
I also found out I cant actually have triple boot on the same hard disc (via grub hence install of ubuntu within windows) as cant have more than 4partitions - 1 vista, 1 ubuntu, 1 openSUSE and 2 swap one each for ubuntu and opensuse.... though i have several hard discs, i want to use only one for operating systems, all my documents and files on the other discs in case the os crashes and i need to reinstall and wipe everything ont he hard disc...

---

