---
title: "Grub2 issues, Grub rescue, lvm2"
date: 2011-03-02
forum: General Help
---

### Post by jerome1232 on 2011-03-02
I took a disk out of my server and I now get dumped at a grub rescue prompt.

If I use ls it tells me I have 2 partitions. But it's not recognizing the filesystems.

```

grub rescue> ls
(hd0) (hd0,1)
grub rescue> ls (hd0)
error: unknown filesystem
grub rescue> ls (hd0,1)
unknown filesystem


```


Which sounds right if I remember correctly (hd0) should be /boot and (hd0,1) should be my physical volume for lvm. If I try to ls on those partitions it tells me unrecognized file-system. I believe that /boot was ext2, I may have left it as ext4 though. I really hope I didn't botch on removing that disc.

What can I do to figure this out, there is no cd-drive connected and I can't easily connect one.



-----long version-------
Okay so I took a disc out of my Mumble server, I removed all logical volumes from it and took it out of the volume group. Removed the disc, put it in a usb enclosure and ZAP! Put the wrong power source into the usb enclosure and fried it. (doh!)

I thought fine everything should be fine on my machine, and left it alone for a few weeks. I just got back to it and after some fiddling with jumpers to get the drive recognized I get dumped to a grub rescue screen.

---

### Post by Krytarik on 2011-03-02
First of all, poor you, honestly!;)

Then about your devices:

(hd0)  means, scaled down, just the MBR in your case, that's why you get an error about the filesystem

(hd0,1)  is the actual (first) partition, there should also be /boot located, if you didn't choose a different setup, and if it is not even more messed up

I'm really not an expert in booting the kernel for the Grub command line. It may become a bit complicated, try to follow this guide:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode")

Greetings and good luck!

---

### Post by jerome1232 on 2011-03-03
Oh yeah... lol... I wasn't thinking (hd0) is the disk/mbr and (hd0,1) being the partition (which should be a physical volume for lvm)


I'm thinking that either A) the disk I took out had /boot on it or B) my lvm has the kernel on it.

Fishing around the grub2 page I didn't understand how one would boot a lvm from the grub-rescue prompt although I'm sure it's possible I can't remember what the volume group is called on this machine to even give it a try....

So I'm going to have to find a pata (all of mine are sata) cd-rom drive and see if I can repair from that.

---

