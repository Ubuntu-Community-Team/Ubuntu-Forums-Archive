---
title: "Windows problems -.-"
date: 2009-10-20
forum: General Help
---

### Post by Son of MaxVK on 2009-10-20
Today when I tried to start up windows XP I got to the desktop and it froze completely. My computer is normally slow but for it to freeze completely is strange, even more worrying is that the My Documents folder opens by itself (and it looks weird the same as an unresponsive window) and then my desk top freezes.

I have spoken to my dad about this and he think that I have a virus. Right now I am asking around to find out if anyone else has had this problem using my Ubuntu duel boot. Ubuntu has been on this PC with windows for a while now so I am pretty sure that is not causing a problem.

So right now I am hopeing that someone will know how to fix a problem like this in Ubuntu.

Any help would be a great help.

---

### Post by fluffman86 on 2009-10-20
Access your windows files from Ubuntu, copy them over, and just forget about windows altogether.  :)

If you really need to repair it, check out ubcd4win.  It's great at cleaning up Windows, but pretty tricky to get working.  Otherwise, just wipe and reinstall windows...that's the only surefire way of getting it working again.

---

### Post by Son of MaxVK on 2009-10-20
Is there some way I could virus check the files first?

---

### Post by junglist313 on 2009-10-20
You could try running clamscan on the windows partition.

---

### Post by P4man on 2009-10-20
You can rest assured its not ubuntu causing it. If you did a wubi install, the opposite is possible, as a windows virus might render ubuntu unbootable (and even if you installed ubuntu on a seperate partition, in theory its possible a windows virus would wipe that partition, but thats not likely)

 if you reinstall windows, you will no longer have a bootable ubuntu. If you did a wubi install, and you format your drive as you probably should, it will also format the ubuntu wubi install. If you had ubuntu on a different partition, you'll still need to boot a live cd to reinstall grub bootloader for the dualboot,but you will not lose your installation provided you dont format it accidentally.

Anyway, thanks for reminding us why many of us ditched windows. good luck getting it fixed,

---

### Post by OpenGuard on 2009-10-20
Install Avast and scan your windows partition - if it's a virus, it'll remove it ( otherwise, as others suggested, backup your files and reinstall ).

---

