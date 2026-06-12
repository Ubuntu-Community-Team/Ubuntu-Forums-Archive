---
title: "How to re-install Ubuntu"
date: 2011-10-22
forum: General Help
---

### Post by getagrip on 2011-10-22
I have been happily running Ubuntu on a Net-book. A few days ago I logged in and can't find my icons ....and almost unable to navigate anywhere. I tried google several help threads for this issue....but nothing works.

My net book is pretty much ...just that ...I have no personal files or sensitive information...so I don't mind doing a re-installation. It only have Ubuntu ...this is not a dual boot set up.

I can only do so with a jump-drive (No DISK Drive) ..I downloaded the latest release and burned the ISO to the jump drive....made sure booting from the jump drive is preferred in the BIOS.....but it will not re-install.

I know a re-install will wipe away my current files ...and thats no problem.
Let me just ask...is WUBI only for windows? 

Finally how do I fix this .....how do I re-install Ubuntu if I can't fix it?

Thanks for your help

P.S.

---

### Post by mörgæs on 2011-10-22
Yes, Wubi is installing Ubuntu as a Windows application. 

There is some advice for installing in the link in my signature.

---

### Post by getagrip on 2011-10-22
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade


I ran those three codes and re-started and it worked!!

Just curious....I had to have run all three codes in teh sequence written right?

I only asked because when I ran the "clean" first code I wasn't sure it did anything.

Thanks!

---

### Post by mörgæs on 2011-10-23
Good, then please mark the thread 'solved'.

'Clean' removes old packages, saving space. It will not give you any confirmation on screen.

Yes, the commands should be run in this order. If everything works, you can still run 'clean' once in a while to be sure that you are not wasting space.

---

