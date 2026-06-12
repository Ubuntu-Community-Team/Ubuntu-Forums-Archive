---
title: "erm.. help please.."
date: 2010-08-21
forum: General Help
---

### Post by natholas on 2010-08-21
hey everyone.. i jsut got my new laptop (hp pavilion dv7 3105ea) and i tried setting up a duel boot with ubuntu 10.04   i made space on my hard drive by shrinking the windows partition and burned a cd with ubuntu.. booted from the cd and tried installing it.. when i got to the screen where u tell it the sizes and stuff for the partition and and swap it said that the 10gb of free space was unusable.. any ideas why? also i thought i would just do wubi and that installed.. but now i cant get it to boot into ubuntu with that.. the screen comes up where i can choose between windows and ubuntu and when i click on ubuntu it gives me an error.. i cant exactly remember what.. i might take a pic of it tomorrow.. any ideas? if its allot of hassle to fix it then i would just like to get rid of ubuntu.. but i have had experience in the past of trying to get rid of grub.. (ugly experiences..) so how can i do that safely? without being able to boot into ubuntu..

thanks :D

---

### Post by bcbc on 2010-08-21
You might have shrunk the windows partition, but make sure you don't already have 4 primary partitions (or 3 and 1 extended) - otherwise the space is unusable.

You need to try and see what the error is when you failed to boot wubi. You should have seen (after rebooting) a countdown that said press ESC to choose custom installation options 5.4.3.2.1.
Then you should have seen it perform the Ubuntu installation.

If it failed, it's wubi, so you can simply go to add/remove programs, look for the ubuntu entry and double click on it. It will remove it and that's all there is to it.

---

