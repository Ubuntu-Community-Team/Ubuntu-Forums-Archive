---
title: "Unity not working"
date: 2012-02-19
forum: General Help
---

### Post by cebosound on 2012-02-19
Hello.

I a few days ago I intalled Ubuntu through Wubi on my PC.  THis pc is older (dell dimension 9150), so maybe the issue is the graphics card.

but when I click on the ubuntu button (or press the windows key) it acts like its going to load the dash, but it doesnt.  nothing comes up.   .....  

I have been researching , but have not found a solution.  I am a bit of a newbie at linux.   My thought was maybe my graphics card isnt suffiecient for 3d, so i want to try 2d unity, but i can't get the terminal up since i can't get into the dash.

Please help.

---

### Post by cebosound on 2012-02-19
Update:

I restarted ubuntu.  and noticed in the login screen there was an option to choose ubuntu2d.   ... but when I got into ubuntu desktop.  still can't get the dash to open. so i have no idea to access any apps or get terminal open.   

I guess I will have to get to the old Gnome format and not use the Dash. (which i do think is a nice function).

Or maybe its because this wasn't a full install on my pc, but a dual boot install using Wubi.  ??????

---

### Post by grahammechanical on 2012-02-19
It would help if you said what version of Ubuntu you are using.

Can you launch programs from the Launcher? Did you run Additional Drivers to activate a proprietary video driver? Usually an Additonal Driver icon appears on the top panel after the first log in. It looks like a computer adapter/expansion card.

You need that to get Ubuntu (3D). Otherwise you only get Ubuntu 2D as a log in option.

Regards.

---

### Post by cebosound on 2012-02-19
> **grahammechanical said:**
> It would help if you said what version of Ubuntu you are using.

Can you launch programs from the Launcher? Did you run Additional Drivers to activate a proprietary video driver? Usually an Additonal Driver icon appears on the top panel after the first log in. It looks like a computer adapter/expansion card.

You need that to get Ubuntu (3D). Otherwise you only get Ubuntu 2D as a log in option.

Regards.
thanks for the reply.

I thought by saying i installed ubuntu a few days ago would be enough for people to realize i had the latest version.  ... but i have the latest version of this time.

i can't get any program launcher to open up.   ... i had used ubuntu a couple years ago.  but haven't used it in a while.  i like the unity stuff, but it doesnt seem to be working.  ... maybe i need to get the additional software drivers like you meantioned.  i will check that out and get back .  thanks

---

### Post by cebosound on 2012-02-20
Ubuntu 11.04

Unable to get the dash to work.  (won't open up).

I have done software update, and downloaded pack of proprietary software.   but still not working........  Does anyone know what software I can try to download to get my 3d working. 

A couple years ago I ran ubuntu on this computer and did alot of the compiz tweaks , including the 3d cube , etc.   So i would think my graphics card could handle it.  ....  so maybe i just need the correct drivers???

thanks

---

### Post by wildmanne39 on 2012-02-20
Hi, old an older computer with unity it probably can not.

Please post the output of:
```
sudo lshw
```
```
/usr/lib/nux/unity_support_test -p
```
Thanks

---

### Post by cebosound on 2012-02-20
> **wildmanne39 said:**
> Hi, old an older computer with unity it probably can not.

Please post the output of:
```
sudo lshw
```
```
/usr/lib/nux/unity_support_test -p
```
Thanks

thanks for the reply.  well part of the problem was, i didn't know how to get to the terminal to do any fo the sudo stuff.  

Good news, i solved it!!!  through the software center i found some proprieter driver software.  installed it,  restarted. now everything is working.   ....

I have 2 new laptops that are both core2duo, but this is an older pc ive had that i set up for a desktop experience; mainly just for some browsing, etc.  THis Dell PC is pentium 4 i believe, but a couple years back i installed an addition 2 rams of rom.  so running about 2.5 ram and pc has 160 hard drive.   ... should run all the basic funtions of Ubuntu.

Thanks again !!!!   glad i got it solved. :)

---

### Post by mörgæs on 2012-02-20
Good, please mark the thread 'solved' using 'thread tools'.

---

### Post by wildmanne39 on 2012-02-20
Hi, I am glad it is working.
Enjoy

---

### Post by cebosound on 2012-02-20
Thank you everyone that posted on this thread!

I am loving ubuntu so far.  Who needs windows anymore. lol. 

the doc/ dash with unity is much better than the old interface, imo.   


SOLVED!!  :)

---

