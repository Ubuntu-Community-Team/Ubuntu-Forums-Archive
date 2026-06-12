---
title: "Unable to copy and paste files within Ubuntu 10.10"
date: 2010-11-27
forum: General Help
---

### Post by BCMerlin on 2010-11-27
I just installed Ubuntu 10.10 on my laptop. Now I am organising the structure of maps and folders, etc. My struggle is that I seem to have no permission to copy, paste and move files to another place then the home folder and the desktop.

I am a total newby in Ubuntu and coming from a Windows operating system, so please give me some assist. I guess it must be very simple, but I don't have a clue at the moment.

Thanx, Barbara

---

### Post by leviathan8 on 2010-11-27
Open up a terminal, and type:
> sudo nautilusYou will get a root fm, but take care not to mess anything up in your filesystem.

---

### Post by CoolJohnB on 2010-11-27
A safer alternative would be to make the folders you require in your home folder, that way you can be sure not to mess up any of the system files.

---

### Post by Joe of loath on 2010-11-27
Basically, leave everything alone outside of your home folder and any mounted drives. There's no need to store stuff outside of those, and there's a chance you could muck something up.

RE Leviathan, you'd actually need to use gksu instead of sudo ;)

---

### Post by BCMerlin on 2010-11-28
Thank you all guys, for the responses!  I happily found the "prob". The prob was my little knowledge of Ubuntu and my short nose I guess... :mrgreen:

The place I wanted to drag en drop my folders to was within the home folder. Didn't know this folder was divided into many others, like "my documents" in Windows. But anyway, thanx for the helping hands.

You can help me with some other problems also if you like. I will make different posts for that. It's about the wireless internet connection that doesn't work anymore. And my keyboard that's standardised in the wrong language even while I added the correct one in the layout. So please take a look in my other posts.

---

