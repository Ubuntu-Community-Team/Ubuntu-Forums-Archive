---
title: "autofs, fstab+cifs or 3rd option for Klaptop"
date: 2011-04-22
forum: General Help
---

### Post by deckoff on 2011-04-22
Hi.
I use my laptop mainly at home, but not always. I own a NAS drive, which I use all the time when at home
My question is - what is the best way to read and write to my NAS drive, considering my usage?
1. cifs in fstab - The way I use it at the moment  - downsides:slow shutdown (read some cures, have not tried them), SLOW suspend and hibernate when not at home.
2.autofs -  Have not tried it. Sound like I doubl click and mount my drive when I need it, and dont get stupid errors and slow shutdowns and suspends.
3. Link to network location - seems harmless, but I am not quite sure if I can write, and wheather all apps will access the NAS.
So, I would like an opinion from you what is the best way to connect your laptop to your NAS drive, considering the way I  use it, and why. :);)

---

### Post by Ghost_Mazal on 2011-04-22
I always use nr 1 and I must say I have never experienced the problems you describe.

You might consider a simple mount script for your share. Execute it when you are home and when you not there you just don't use it.

In my experience mounting the share into a local folder is best as not all applications have the ability to browse to the network.

---

### Post by deckoff on 2011-04-22
Thanx for the answer. I use the option nr one and just commented the line that mounts the NAS at the moment:) I'd rather love a solution that even does not involve running a script :) I look for someone who has implemented solution two - just to let us know if this solution works without scripts and all. :)

---

