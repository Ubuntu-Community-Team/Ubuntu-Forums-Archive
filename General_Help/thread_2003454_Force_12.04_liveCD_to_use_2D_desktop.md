---
title: "Force 12.04 liveCD to use 2D desktop"
date: 2012-06-14
forum: General Help
---

### Post by christh on 2012-06-14
Hi all

My Grub menu is fried so I'm trying to fix using the liveCD however it insists on booting into the 3D desktop which my computer does not support - when the livecd boots, I get a blank white desktop that sits on top of any programmes that I open (terminal etc) rather that falling back into 2D like it should.

The top panel is visible so I can logout/in to change to the 2D desktop however that then requires a username & password to get back in.

Any suggestions?

Thanks

Chris

---

### Post by jahst on 2012-06-27
Logout.
Change to 2D.

The username on a live cd is "ubuntu" press enter
leave the password blank (dont type anything) then press enter.

As far as forcing the live CD to boot directly into 2D, I am still wondering the same thing... anyone.

---

### Post by jmfal on 2012-06-27
Check this out go down to "Boot Display Behaviour"  and 'Hidden", you might be able to get into low graphics or repair grub from a shell:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

