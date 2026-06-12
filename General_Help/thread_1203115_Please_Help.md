---
title: "Please Help"
date: 2009-07-02
forum: General Help
---

### Post by zach12307 on 2009-07-02
Every time put my 1 Gig sd card in I get this message "can not get volume fstype.alternative" I  dont know what to do can some body help me out so I can access my card thanks please email me your response [EMAIL="zmattson@gmail.com"]zmattson@gmail.com[/EMAIL]

---

### Post by HermanAB on 2009-07-03
Howdy,

It sounds like you need to reformat the device.  These devices are usually formatted with DOS VFAT, but you can use Ext3 if it is only used on a Linux machine.  The problem is that you have to be absolutely sure that you have identified the correct device, else you can reformat one of your hard disks and lose data.

First see what you got mounted using the commands 'mount' and 'df':
$ mount
$ df

Now use the program 'dmesg' to get the device name:

$ dmesg

Plug the SD card in.

$ dmesg

You should see something about device sdX being detected - where X is something that you did NOT see with mount or df before.

Once sure what the device name is, you can reformat it with:
$ sudo mkfs.vfat -L label /dev/sdX

Once reformatted, you should be able to remove and re-insert it and it should get mounted.

Hope that helps!

---

