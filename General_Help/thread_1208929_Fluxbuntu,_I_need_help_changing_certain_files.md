---
title: "Fluxbuntu, I need help changing certain files"
date: 2009-07-09
forum: General Help
---

### Post by jiffypop on 2009-07-09
Hey I'm brand new to fluxbuntu, and linux in general, so I'm having a little bit of difficulty. Right now I'm trying to change a few scripts. 

-The theme script that controls the styles etc.
-the boot/grub/menu.lst script

I open them up with leafpad, change them and try to save them, but it tells me that "can't open file to write" what does this mean, and what is the right way to edit scripts?

---

### Post by kerry_s on 2009-07-09
you use sudo for the cli & gksudo for graphical programs, for files that are not in your home.

press-> alt+f2
type-> gksudo leafpad /boot/grub/menu.lst

what file manager does fluxbuntu have ? you might be able to make a right click "open as root" for ease of use.

---

### Post by jiffypop on 2009-07-09
hey that totally worked, unfortunately I don't know the answer to your question, and I don't know how to find out the answer, but ty :) it worked. Now I just need to figure out how to unzip a tar.gz.

---

### Post by kerry_s on 2009-07-09
when you open the file manager don't it have a name ?

i think it uses pcmanfm, which is a little complicated to add a right click program, so just deal with it how you want. ;)

for the tar.gz. " sudo apt-get install xarchiver " that should give you the right click> extract here, if it is pcmanfm like i think it is.

---

### Post by jiffypop on 2009-07-09
It says that it uses ROX, so that last bit didn't help. I was able to open it using the X-terminal though.

---

### Post by kerry_s on 2009-07-09
> **jiffypop said:**
> It says that it uses ROX, so that last bit didn't help. I was able to open it using the X-terminal though.

rox huh, what are you specs?
rox takes learning, that new user friendly. you should try pcmanfm instead. still light but easier.

**sudo apt-get install pcmanfm**

---

### Post by jiffypop on 2009-07-09
it gave me this error. "couldn't find package pcmanfm"

---

### Post by kerry_s on 2009-07-09
> **jiffypop said:**
> it gave me this error. "couldn't find package pcmanfm"

are you connected to the internet?
there should be 2 versions in there. the first 1 automounts drives when you plug then in, the second doesn't.

---

### Post by jiffypop on 2009-07-10
yes I'm connected to the internet, but now I'm confused... I don't understand your last tip.

---

### Post by kerry_s on 2009-07-10
> **jiffypop said:**
> yes I'm connected to the internet, but now I'm confused... I don't understand your last tip.

did you update first then? is all your repo's on?

try:
**sudo apt-get update**
then
**sudo apt-get install pcmanfm  **

---

### Post by jiffypop on 2009-07-10
so I typed in the first command and it replied

Reading package lists.... Done

then I typed in the second command and it replied

Building dependancy tree
Reading state information... Done
E: Couldn't find package pcmanfm

Am I supposed to download pcmanfm from somewhere and put it in a directory or something first? And sorry but I don't know what a repo is....

---

### Post by kerry_s on 2009-07-10
alright don't worry about it then.

the repo's is where you get the software to install and use on your system. does fluxbuntu have synaptic anywhere in the menus?
if so that is the gui front end to apt-get.
like for example you should not need to use tar.gz packages, you would just apt-get what you want or use the gui to select and install what you want.

give this a read: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
check this out to: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by jiffypop on 2009-07-10
Yes, I do have synaptic... and I'll give those a read, tyvm for the help so far. I would be doomed without you. :) This linux stuff is fun, hopefully some day I won't be such a noob.

---

### Post by jiffypop on 2009-07-10
Turns out that I can't use most repositories because apparently Fluxbuntu uses gutsy gibbon... how to I upgrade it to Feisty?

---

### Post by jiffypop on 2009-07-10
or, am i wrong and I just need to use a different repository? What I do understand is that all of the currently enablable repositories are outdated or no longer exist, and I don't know what repositories I should add.

---

### Post by kerry_s on 2009-07-10
ooh, thats a oldie. i recommend you grab something more updated.
you didn't say what your specs are, be nice to know what you got to work with.

---

### Post by jiffypop on 2009-07-10
Pentium III, 128Mb ram, 27Gb hardrive... I think I'll install antiX

---

### Post by kerry_s on 2009-07-10
> **jiffypop said:**
> Pentium III, 128Mb ram, 27Gb hardrive... I think I'll install antiX

ouch, antix is sweet and it's based on debian so it will be faster then the *ubuntu's.

no chance of upgrading the ram? if you can get 256mb, thats the sweet spot, you can run most things comfortably.
main thing is you get some practice in right now, then later you can do a base install buildup, so you have only what you need.

i'm on p3 450mhz 256mb ram myself. ;)

---

### Post by jiffypop on 2009-07-10
Nope, but oh well fluxbuntu was fast enough, and antiX is supposed to be just as fast, plus there's more people using it, and it's up to date. Ty for your help.

---

### Post by snowpine on 2009-07-11
Good choice, AntiX is very fast. :)

---

### Post by jiffypop on 2009-07-13
I'm loving it, and I'm finding myself addicted to fluxbox. :D

---

