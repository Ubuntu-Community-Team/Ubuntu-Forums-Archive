---
title: "networking with windows 7"
date: 2010-11-09
forum: General Help
---

### Post by sapoleon on 2010-11-09
Hi, 
I have a problem, from some time on. I have in my network, office, that I am migrating to ubuntu. But, there is one machine, that is functioning like a server, that has windows 7 home premium.

i have 1 ubuntu 10.04, one vista, and 2 xp machines appart of the w7 one. 

I can see with samba in ubuntu, all the machines, except the one with w7, which is the only one that have to stay with windows.

I can see it when i go to net in nautilus, but, when I try to connect, and see the shared disks and directories, it pops up a dialog asking for authentication, with usr, password and domain, and no matter what i write in it, I can not get into that machine. In the same way, I can not enter the shared directories in the Ubuntu box from the w7 machine.

And there is no problem connecting all the other machines between them, and all the others with the w7 machine. Is just something to do with Ubuntu, or with the connection between Ubuntu and W7.

Can someone point me in the write direction?

I have search the web, and found some cases with the same problem, but no answer.. or at least, no working answer...

---

### Post by CharlesA on 2010-11-09
Do you happen to have Windows Live installed on the Win7 box?

It screws with the authentication token or something.

[http://ubuntuforums.org/showthread.php?t=1584199](http://ubuntuforums.org/showthread.php?t=1584199)

---

### Post by sapoleon on 2010-11-11
Hi CharlesA, first of all, thanks for your answer

Yes, I have read those post too, I have it installed, but I already put the service in manual mode and not running, without any help.
I also added in the registry the LSA value level 1 (don´t remember exactly the DWord name now, but it´s done, and still not working.

One good thing thou, I can now enter my Ubuntu from W7, but not the other way around. I still get a user, domain and password request in Ubuntu, that no matter what I write there, I can not get access to W7.

---

### Post by sapoleon on 2010-11-11
OK
I unistalled windows live (I just used messenger) and that solved the problem.

Changing the service to manual and not running, does not help, it must be uninstalled.

---

### Post by CharlesA on 2010-11-11
If I am accessing a Windows box from Ubuntu, it always prompts me for the username and password. Does it let you connect if you put the correct info in?

---

### Post by sapoleon on 2010-11-24
Hi CharlesA, 

Sorry for taking long in answering you.

No, I could not manage to connect to Win7 with the windows live installed. I had to remove all the options of windows live, including messenger. (using pidgin in windows now).

Even if entering the correct data, and all those, and changing the configuration in the registry, or trying to set the windows live servers to manual and not running. No Way Jose. The only thing that helped, was remove the windows live.

---

### Post by CharlesA on 2010-11-24
Glad you got it working. That Windows Live thing is a pain in the butt, for sure.

---

