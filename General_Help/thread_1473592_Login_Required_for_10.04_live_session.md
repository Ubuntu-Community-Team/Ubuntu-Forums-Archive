---
title: "Login Required for 10.04 live session"
date: 2010-05-05
forum: General Help
---

### Post by str8chat4u on 2010-05-05
I have run "ubuntu-10.04-desktop-i386" on two different PCs using the facility to try running from the CD without installing on the hard drive. The first machine, with an Athlon CPU, 1GB of memory and an internal CD drive had no problems. The second machine with a Via CPU, 512 MB of memory and a USB CD drive stopped loading at a "Login" prompt. I guessed at the username "ubuntu" and no password, and it then completed its loading and ran from the CD.

The previous version I tried (9.04) loads on this second machine without requiring a username to be entered.

I guess that since the "live" run from CD works without logging in on my Athlon system, then this is how it is meant to be. Perhaps there should be something on the website to say that with certain systems, it may be necessary to login manually with version 10.04, and what the username is. If it is already on the website I did not find it.

Has anyone else experienced this problem? Is it due to the CD drive being connected by USB, or the type of CPU, or something else?

I have now installed it on my hard drive on my Via system and that is working as expected.

---

### Post by ubunterooster on 2010-05-05
Likely it allows you to choose between "ubuntu" and "root"

Edit: some of my old ubuntu CDs had that option. It's more useful for LiveCD administration

---

### Post by str8chat4u on 2010-05-05
Possibly, but if this was the case, it should have done the same on both my PCs. Also, for a "try before you install" option, it is not logical to offer a choice of login to the prospective user.

---

### Post by sisco311 on 2010-05-05
> **str8chat4u said:**
> Has anyone else experienced this problem? 

Yes, possible causes are:
[list]
[*]corrupted iso;
[*]bad burn;
[*]a faulty CD;
[*]a failing CDROM drive;
[*]bad karma :) (an unexpected i/o error).
[/list]

---

### Post by str8chat4u on 2010-05-06
I don't believe there is anything wrong with the CD as the same disk works differently in the two machines. Also, both machines give the same sum check for the CD.
 
My suspicion is that there is something in the initial file system contained in the initrd.lz file that is reacting differently to IDE connected CD drives compared with USB connected drives. When I get time, I will dig further into the CD and see if I can find the initrd.lz file, and look inside it.

---

