---
title: "can't boot with wubi"
date: 2010-01-07
forum: General Help
---

### Post by mfrag on 2010-01-07
We have a computer lab at school that ITS is trying to get ready before the semester starts.  ITS is willing to put a wubi install on all the windows 7 machines in the lab after some faculty asked for a linux option.  However they don't really support linux and basically need our help if any problems arise.  

After getting one machine to boot up nicely they used symantec ghost to make an image and put it on all the machines (I don't know the details on this but this is what I gather).  However, no machine will boot into Ubuntu 9.10 unless one edits the boot options upon choosing Ubuntu from the windows 7 bootloader.  I suspect there is a subtle problem that lies from ghosting the one machine.  Anyhow if I change 

```
root=/dev/sdb2
``` 

to 

```
root=/dev/sda2
```

in the boot options Ubuntu 9.10 boots up just fine and everything is in order.  However one has to do this every time they boot into linux.

My question is what do I do to these machines so that the students/faculty don't have to make this change every time they wish to use linux?

I think 9.10 uses GRUB2 from what I've been reading but it is unclear what file I need to edit to make the needed change.  Is there a file in C:\ubuntu\??? that I can edit?  Or do I need to first boot into ubuntu and then edit some file in /boot/grub/???

Thanks for any help!!

---

### Post by yktula on 2010-05-31
I'm going to make the assumption that you're unfamiliar with vi/vim, so I'll just provide step-by-step instructions. If you are familiar with an editor: what you're looking for is located at */etc/default/grub*. If this causes any problems, feel free to reply. Choose I) or II) at your option, both from within Ubuntu.

I) USING GEDIT:
ALT+F2
sudo gedit /etc/default/grub
change */root=/dev/sdb2* to */root=/dev/sda2*
file->save
close the window
restart

II) USING VI:
1) open a terminal
2) type sudo vi /etc/default/grub
2) type the following (read the newlines as [ENTER] and interpret text like this as instructions):
```
/root=
$

```type h until you reach the *b* in */root=/dev/sdb2*
then type the following:
```
ra:wq
```type exit (in the terminal)
restart

---

