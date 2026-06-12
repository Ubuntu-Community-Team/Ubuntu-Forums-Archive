---
title: "dual boot and xp in vbox, help."
date: 2009-07-14
forum: General Help
---

### Post by wcasper4 on 2009-07-14
I dual boot XP Professional (SP3) and Ubuntu 9.04 because I need some Windows programs (iTunes, Office, MATLAB, Maple, etc.) 
I have successfully loaded the existing copy of my xp into virtualbox. However, whenever I open XP, I have to reactivate it over the phone... and when I boot to XP natively I have to reactivate it again. 
It pretty much has defeated the purpose of virtualbox, as it is easier to just boot natively so I don't have to reactivate everytime. 
Has anyone found any inkling of hope or resolution to this problem... it has to be out there somewhere??

I first cloned my hardware profile in windows, so I have a Virtual and Physical. 

Then in linux ran:

$ sudo apt-get install mbr
$ cd ~
$ install-mbr --force .VirtualBox/vboxmbr.mbr
 <<this created the new MBR>>

<<To create my virtual machine>>
$ sudo VBoxManage internalcommands createrawvmdk -filename /home/walter/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 1 -mbr /home/walter/.VirtualBox/vboxmbr.mbr -relative -register

<<Then I created it in VBOX>>
$ sudo chown walter .VirtualBox/WindowsXP.vmdk .VirtualBox/WindowsXP-pt.vmdk

In vbox I added this vmdk as a virtual hard disk and then created my virtual machine using my existing hard disk partition of XP.

it was based off of this blog I read on it [http://anderstornvig.dk/2008/06/03/r...u/#comment-142]("http://anderstornvig.dk/2008/06/03/running-existing-windows-in-virtualbox-on-ubuntu/#comment-142") and the blog in this forum.

did I do something wrong, or is there a better way of doing this where I won't have to reactivate?
I've read numerous blogs on this issue, but none that work because of sp3 and xp pro, someone must know how??
Thank you.

---

