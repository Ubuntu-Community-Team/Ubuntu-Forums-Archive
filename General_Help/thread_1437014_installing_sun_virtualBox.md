---
title: "installing sun virtualBox"
date: 2010-03-23
forum: General Help
---

### Post by mIXpRo on 2010-03-23
hiii,
does anyone knows how to install sun virtualBox , cause i've downloaded the .deb package from there site and installed it but i don't know how to start it .

---

### Post by ahayzen on 2010-03-23
Sun virtual Box appears under Applications > system tools.

If that doesn't appear right hand click on Applications
click edit menus
a new window should open
Now make sure Application is selected in the left pane and tick system tools in the main pane in the centre.
Now click close.

Virtual box will now be under Applications > System Tools > SunVritualBox

Andy

---

### Post by howefield on 2010-03-23
It may just need you to log out and back in from your session to refresh your menu.

---

### Post by linden940 on 2010-03-23
[http://www.youtube.com/watch?v=A3k3Vtdr8Vg](http://www.youtube.com/watch?v=A3k3Vtdr8Vg)


watch that...u only need to watch the ending part..as u got the right vbox lol

---

### Post by mIXpRo on 2010-03-23
is there an addition to virtual box like so for the windows virtual : which you can select a window in the vitual machine and the hosting machine without having to capture the mouse ?

---

### Post by norseman-has-a-laptop on 2010-03-23
how do you install it is there a site i can get it from i would like to have it again i just forgot how i got it on there once before

---

### Post by howefield on 2010-03-23
You need guest additions.

What are the host and guest operating system ?

---

### Post by norseman-has-a-laptop on 2010-03-23
ubuntu host  xp guest

---

### Post by ahayzen on 2010-03-23
Guest operating system runs inside Virtual Box
Host is the one 'running' virtual box

---

### Post by howefield on 2010-03-23
> **norseman-has-a-laptop said:**
> how do you install it is there a site i can get it from i would like to have it again i just forgot how i got it on there once before

Install the OSE version from the Ubuntu repository  or the PUEL version from..

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by linden940 on 2010-03-23
open vbox...start the system then on the top click 

devices  > install guest additions

---

### Post by mIXpRo on 2010-03-23
> **howefield said:**
> You need guest additions.

What are the host and guest operating system ?

the hosting os is ubuntu 9.04 and the guest is windows 7

---

### Post by ahayzen on 2010-03-23
Beware that the OSE version doesn't have USB support

---

### Post by howefield on 2010-03-23
> **mIXpRo said:**
> the hosting os is ubuntu 9.04 and the guest is windows 7

As per linden940 response, do that and the guest additions wizard should pop up.

---

### Post by linden940 on 2010-03-23
i dont think it really matters whats the guest computer is...the guest addon should work with all or....most os *all windows os 4 sure*

---

### Post by howefield on 2010-03-23
> **linden940 said:**
> i dont think it really matters whats the guest computer is...the guest addon should work with all or....most os *all windows os 4 sure*

Installing guest additions is different for linux guests than it is for Windows guests..

---

### Post by linden940 on 2010-03-23
yea..but anit it installed the same way? or theres other steps u have to make?

---

### Post by howefield on 2010-03-23
> **linden940 said:**
> or theres other steps u have to make?

Yes, do some research, you'll find it.

But these extraneous posts make it harder for the OP to find the reponses to his questions. Keep on topic ;)

---

### Post by mIXpRo on 2010-03-23
when trying to install guestadditions.iso i get what in the picture attached , what to do ?

---

### Post by mIXpRo on 2010-03-23
and when trying to force unmount i get :-

---

### Post by linden940 on 2010-03-23
on the bottom u will see a cd thing...right click on it and click mount...find where the iso is saved on your desktop...should be in the vbox folder where it was installed...go to that folder you will find a iso called *something like this* guest addons.iso click on it and then it will work...


sometimes it just wont work so you have 2 do that...hope this helps u

---

### Post by howefield on 2010-03-23
Have you checked that the guest additions iso is mounted, and not the cd-rom. (From the Devices menu)

---

