---
title: "Deleted Windows 7 Partition, now ubuntu won't boot"
date: 2009-09-04
forum: General Help
---

### Post by slapnutz on 2009-09-04
Alright so I hate asking for help, I usually try to exhaust every other effort before I do this, but this seems to be the only way. I've seen a lot of topics similar to this one all over the net, so I'll try to provide as much as I can.

So yesterday I decided I was going to go Linux full time and say forget having windows on a separate partition. Being the 'jump into it' guy I am I just expanded my current Ubuntu install (/dev/sda3) over the windows install (/dev/sda1)...takes about an hour and then reboot.

Somehow I ended up with the same grub version that I usually had [ I started with WUBI and used LVPM to migrate it ]. Alright thats fine, boot to ubuntu, nothing. I then booted to partedmagic and poked around for awhile. Long story short I re-installed on a 2 gig partition which is what I am on now [/dev/sda1].


Things I have tried so far:

From a livecd: invoke grub
root (hd0,2)
setup (hd0)
reboot [no dice]

mount the drive frrom a live cd:
grub-install --root-directory=/media/disk /dev/sda3
grub-update 

however grub update wasn't working, so I moved /boot to /boot2 on the 'in memory' os of the livecd and made a sym link from /boot to /media/disk/boot and sure enough menu.lst got created

After this I rebooted, try to jump into ubuntu and kept getting dropped into busybox with complaints about root= and rootdelay or something along those lines. So I proceeded to see if I could mount /dev/sda3 in busybox to see if the issue would be there, and I was able to without a problem.

Please please please if anyone has an idea let me know, I am willing to try ANYTHING including just migrating that install over to this one, but I'm not sure that will work cause this is Hardy and the original was Intrepid [Both x64]


Thanks again in advance and sorry for not being terse,

~Mike

---

### Post by mikewhatever on 2009-09-04
I suspect the initial boot problem happened because you resized the Ubuntu partition, thus changing its UUID. If that's the case, you can fix it by editing UUID of the root partition in the menu.lst.
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

Not quite sure what's the deal with the 2GB partition. That's way too small for Ubuntu.

---

