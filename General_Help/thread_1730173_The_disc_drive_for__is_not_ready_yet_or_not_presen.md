---
title: "The disc drive for / is not ready yet or not present"
date: 2011-04-15
forum: General Help
---

### Post by davemar on 2011-04-15
I've got a laptop with 10.04 installed, and it has suddenly decided to report the error:
```
The disc drive for / is not ready yet or not present
```
on start-up. 
It gives me the option to either manually fix it or skip. So when I select 'M' it gives me a root login to / , but it is mounted read-only, so I can't actually change anything that may have gone wrong.

I've tried using a LiveCD to access the /dev/sda1 partition (where / is mounted) so I can change it, but it does not want to boot from the CD drive. I've made sure the BIOS boots from CD first, but it seems to ignore it. Maybe the CD drive is faulty now (the LiveCD reads fine in my other PC).

So I'm pretty stuck with trying to fix this. I think the trigger was when it was working fine it was doing an update and the power got accidentally cut, so maybe some installation files were left hanging.

Also it doesn't seem to go through the grub menu either, so there's no option to select anything else.

Has anyone got any suggestions to get out of this one? I don't really want to buy another CD drive for it. Is there anything I can do via the network port?

---

### Post by Dutch70 on 2011-04-15
Can you boot to a usb stick & do you have one?

It sounds like there is a problem in your fstab (file system table), but you'll have to boot to something to fix it.

If you can get it to boot to cd,usb stick, or recovery, post the output of...
```
sudo gedit /etc/fstab
```
Please paste it between [CODE][ /CODE] tags by using the "#" symbol in the toolbar to keep the formatting.

---

### Post by davemar on 2011-04-16
Here's the contents of /etc/fstab (copied by hand, so I removed comments):
```

proc     /proc    proc    defaults      0      0
UUID=57145095-619f-4be2-b68e-6253602b1528   /   ext3   errors=remount-r0  0  1
UUID=0a7a11dd-a7a6-4600-9989-557cd4087daf  /data   ext3  defaults   0  2
UUID=e685dcea-aa96-444b-8580-24660916e7e2  none   swap  sw   0   0
/dev/sdc0   /media/cdrom0    udf,iso9660 user,noauto,exec,utf8 0   0
/dev/fd0    /media/floppy0   autio    rw,user,noauto,exec,utf8 0   0

```
Here's when I do blkid /dev/sda1:
```

/dev/sda1: UUID="57145095-619f-4be2-b68e-6253602b1528" SEC_TYPE="ext2" TYPE="ext3"

```

There's nothing there that looks out of place to me?

I can't boot from USB stick either, it's not an option in the BIOS (it's quite an old laptop).

---

### Post by Dutch70 on 2011-04-16
Why did you have to copy it by hand? It's difficult to tell anything really.

---

### Post by davemar on 2011-04-16
No USB stick reading, no network or internet, only what's on the screen in front of me. Not much option really!

---

### Post by WorMzy on 2011-04-16
Since you think this was caused by a power outage, chances are the filesystem is slightly corrupted. Boot to the liveCD and run fsck on the partition to (hopefully) fix it.

```
sudo fsck.ext4 -fc /dev/sda1
```


[QUOTE=Dutch70]```
sudo gedit /etc/fstab
```[/QUOTE]
Just so you know, you should never use "sudo" for a graphical application. It doesn't matter so much on a LiveCD, but you should try to remember to use **gksu** or **gksudo** instead. Using "sudo" for graphical apps can cause a lot of problems in your home folder.

---

### Post by davemar on 2011-04-17
I can't boot to a LiveCD, that's my whole problem! I need to get it to boot some other way, but my CD drive seems to be either faulty or just being ignored.

---

### Post by WorMzy on 2011-04-17
If you can take the hard drive out of the PC, you could connect it to the other PC and fsck it from there. If that's not an option either, then you're pretty stuck.

---

### Post by davemar on 2011-04-17
...or not so stuck ;)

I followed instructions on [https://help.ubuntu.com/community/Installation/LocalNet]("https://help.ubuntu.com/community/Installation/LocalNet") so I could boot via the network, and it seems to like that. Currently reinstalling 10.04 as I speak.

Fingers crossed this has got me unstuck.

---

### Post by cms2337 on 2011-05-06
> **WorMzy said:**
> 
Just so you know, you should never use "sudo" for a graphical application. It doesn't matter so much on a LiveCD, but you should try to remember to use **gksu** or **gksudo** instead. Using "sudo" for graphical apps can cause a lot of problems in your home folder.

Why is that? What is the difference?

---

### Post by matt_symes on 2011-05-06
Hi

> **cms2337 said:**
> Why is that? What is the difference?

For a good explanation read this

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

KInd regards

---

