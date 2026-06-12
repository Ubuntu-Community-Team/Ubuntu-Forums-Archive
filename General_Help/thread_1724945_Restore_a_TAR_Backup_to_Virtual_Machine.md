---
title: "Restore a TAR Backup to Virtual Machine"
date: 2011-04-09
forum: General Help
---

### Post by KratosCrux on 2011-04-09
So, I'm trying to use this tutorial ([http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)) to backup my Ubuntu 10.10 (ext3) operating system. I've successfully gotten it into a TAR file on my external hard-drive, but inside the archive are 2 folders: sda5 and media (/media/sda5/), sda5 ofcourse containing my operating system.

I run VMWare as my virtual machine software, but I could easily run Virtual Box if the situation calls for it.

On my virtual machine I created an Extended partition, made a 2GB swap space and the rest is ext3 (ext3 space is mounted as sda1) (at this point, Swap is OFF)

here is what I've tried to do inside the virtual machine to restore:



```
sudo -s
mkdir /media/FROM/
mkdir /media/TO/

mount /dev/sdb1 /media/FROM/
(sdb1 is the drive that has the tar file on it)

mount /dev/sda1 /media/TO/
(sda1 is the new ubuntu filesystem in the VM)

cd /

tar -xvpzf /media/FROM/Bac_201/KC201_Bac.tar.gz media/sda5/ -C /media/TO/
(Bac_201 is the folder on my external harddrive where KC201_Bac.tar.gz is located)

```
this is apparently supposed to extract the contents of /media/sda5 (a folder inside the tar file) to sda1 (the virtual hard drive)

but instead it just creates the directory sda5 under media of the live ubuntu cd


Do I need to CHRoot in these conditions? 

AFTER I get the files successfully into the virtual machine, **how do I go about restoring the grub2 bootloader?**

Right now I haven't tried to restore grub on my hardware, but I would be interested in doing so. There are a vast immense amount of forum posts about this subject, but all are to mixed results. Can anybody tell me the absolute definite way to restore grub2 successfully, I don't want to try something if it's going to mess up my install, whether I've backed up or not. Just point me in the right direction please :D



for further reference, here is a link to the previous (failed) thread I made about this same subject:

[http://ubuntuforums.org/showthread.php?t=1713169](http://ubuntuforums.org/showthread.php?t=1713169)

---

### Post by jerenept on 2011-04-09
I don't understand a few things here:
1. why not backup just your personal files?
2. ```
tar -xvpzf /media/FROM/Bac_201/KC201_Bac.tar.gz media/sda5/ -C /media/TO/

```
this command seems incorrect somehow.... will get back to you on that.

---

### Post by jerenept on 2011-04-09
and, uh, installing grub....
just boot an ubuntu LiveCD, open a terminal and run 'sudo grub-install'

---

### Post by KratosCrux on 2011-04-09
> **jerenept said:**
> I don't understand a few things here:
1. why not backup just your personal files?


I have backed up all of my personal files, but it is the personal settings I want restored, such as logins in chrome, passwords accross various programs, and the OPML list in Miro I haven't exported recently.

> **jerenept said:**
> 
2. this command seems incorrect somehow.... will get back to you on that.

Yeah I know something similar worked for me before but I must not have written that one down. I think it's interpreting media/sda5 as the location to extract to, instead of the location inside the tar itself; I don't know how to extract a certain directory in a tar archive apparently >.<

---

### Post by KratosCrux on 2011-04-28
OK, new info:

1.) There is no way for me to boot into the Windows XP restore partition without a boot menu

2.) I've found that I am in-fact running Grub Legacy (I did install 10.04 fresh so I was assuming I had grub2 the whole time; not the case) running "grub-install -v" in Knoppix returns 0.97

3.) I AM MISSING 'STAGE1'!!

I tried several times but I just don't have the Stage1 files on my computer at all, they aren't in the backup either, so I guess they died when I re-installed windows on my hardware

I've been following this tutorial, and it tells you how the (hd0,0) part translates: root (hdA,B)
The coordinates A,B are where 'A' is the hard-drive number, starting at 0, and 'B' is the partition number, starting at 0. For example, if Ubuntu was installed on the second partition of the first hard-drive, the command should be "root (hd0,1)" -- anyway, it's somewhat useless if I don't have the stage1 files

[https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier](https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier)

unfortunately I can't continue from this point on my hardware.

Is there any way to overwrite grub legacy with grub2? I'm used to grub2 and how it works more than I am with grub legacy, so It'd be a plus to have grub2 instead. if not, I need to be able to at-least recover grub legacy on my hardware to re-install windows XP.


[Edit, I found the correct command to take things out of a TAR file
```
cd /temp
tar -xvpzf /source/tarfile.tgz media/sda5
```
^that's what I ran, but I'm assuming if I continued that and put 
```
tar -xvpzf /source/tarfile.tgz media/sda5 -C /directory_i_want_sda5_files_on
```
 then it would work even better (this created the directory temp/media/sda5 where i wanted the sda5 files inside /temp only)]

when I'm backing up to a Virtual Machine, nothing has worked sofar, even after successfully purging and re-installing grub (yes, I did run the command to remove grub legacy aswell)
after I purged it was still un-bootable, so I installed ubuntu 10.04 onto the VM and it boots just fine.

what I was thinking of doing was installing ubuntu (10.04 or 10.10) and then replacing /opt and /usr and /home with the backup files from my TAR archive. would this work? what other directories should I overwrite with my old ones?

also note, I installed 10.04 (in my VM) and plan to overwrite the files with my 10.10 versions, I don't know if that will work but I don't have access to a 10.10 CD at the moment so 10.04 was the best I had. If this fails I'm going to download and boot from the 10.10 iso.

---

