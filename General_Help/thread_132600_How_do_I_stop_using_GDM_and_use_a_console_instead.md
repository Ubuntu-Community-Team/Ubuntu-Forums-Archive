---
title: "How do I stop using GDM and use a console instead"
date: 2006-02-18
forum: General Help
---

### Post by ndhskp on 2006-02-18
**_Solved_**

Hello all.

How do I stop using GDM login and switch to a console startup.  I want to get rid of GDM entirely and have my computer boot or reboot directly to console.  At the console I know to start x I have to type startx.

I want to do this to cut down on GDM resource hogging and I also prefer a console on bootup anyway.  Any help would be great as I run a tor server and Folding@Home and not having GDM will allow more cpu time for my server and folding.

Thanks.

---

### Post by Protex on 2006-02-18
I have a question.

Will disabling GDM give more resources in general, or just at the time you login? It doesn't run all the time does it?

---

### Post by Vogateer on 2006-02-18
Have you tried to do this?

sudo update-rc.d gdm remove

That should remove gdm from being automatically started at boot, I believe.

---

### Post by ndhskp on 2006-02-18
[quote=Protex]I have a question.

Will disabling GDM give more resources in general, or just at the time you login? It doesn't run all the time does it?[/quote] 
Actually when you drop to a pure console GDM continues to run in the background.

For example Ctrl+Alt+F1 switches you to terminal 1 I think, now if I do ps fax I see xserver and gnome still running.  So this thread is about starting x manually.

Example after typing startx I go directly to gnome and then when I finish with gnome by using the System/Logout feature I drop back down to a console and that terminates xserver and gnome and frees cpu time for other stuff.  Cheers

---

### Post by ndhskp on 2006-02-18
**_Solved_**.

Okay here's what I did.

I decided to use Synaptic to remove GDM.  I clicked on the search button in Synaptic and entered GDM then the results came up and there was gdm.  I clicked on it and selected remove completely.  At this point it will want to remove ubuntu-desktop as well which I gave it permission to do.  I clicked apply and then rebooted the computer just to see if it really worked and it did.  I booted directly to tty1.  Then I entered startx which took me directly to gnome.  And now if I select System/Logout that will drop me back down to tty1 and terminate xserver and gnome there by freeing up cpu cycles and system memory for other stuff.  In my case my tor server and folding@home.

Mark this one solved.

---

### Post by bascha on 2006-02-18
I followed your instructions and it worked like a charm.  Been wanting to boot to console since I moved from Slackware to Ubuntu a while back.  Now to get fortune setup to give me my quote of the day.

thanks

---

### Post by ndhskp on 2006-02-18
[quote=bascha]I followed your instructions and it worked like a charm.  Been wanting to boot to console since I moved from Slackware to Ubuntu a while back.  Now to get fortune setup to give me my quote of the day.

thanks[/quote] 
Alright cool.  May fortune smile upon your attemps at setting up fortune. :)

---

