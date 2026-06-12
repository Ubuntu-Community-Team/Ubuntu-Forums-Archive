---
title: "No Shutdown or Restart button in Kubuntu."
date: 2009-11-08
forum: General Help
---

### Post by TheNerdAL on 2009-11-08
There is no Shutdown or Restart Button in Kubuntu, Can someone help me?

---

### Post by H2SO_four on 2009-11-08
Thats because you no longer need to restart/shut down your system!

All joking aside, it should be in the menu in the lower left corner of your screen (like Windows)

---

### Post by TheNerdAL on 2009-11-08
> **H2SO_four said:**
> Thats because you no longer need to restart/shut down your system!

All joking aside, it should be in the menu in the lower left corner of your screen (like Windows)

No, there is only sleep and hibernate.

---

### Post by halj32 on 2009-11-08
Just right click on desktop for options, shutdown, logout etc

---

### Post by TheNerdAL on 2009-11-08
[quote=halj32;8269892]Just right click on desktop for options, shutdown, logout etc[/quote
Don't get no shutdown, just logout.

---

### Post by TheNerdAL on 2009-11-08
Anyone?

I have included a screen capture

---

### Post by SuperSonic4 on 2009-11-08
I've seen a few of these threads. Do you have kshutdown installed?

```
sudo apt-get install kshutdown
```

---

### Post by TheNerdAL on 2009-11-08
> **SuperSonic4 said:**
> I've seen a few of these threads. Do you have kshutdown installed?

```
sudo apt-get install kshutdown
```

I downloaded it, now what?

---

### Post by TheNerdAL on 2009-11-08
Anyone?

---

### Post by klemes on 2009-11-08
I had the same problem and the only way I found to remedy this was to erase my .kde(attention!!! better backup beforehand)in my home folder and start all over again.After that the power button reappeared but of course I had lost all my settings and had to set up KDE from the start.If nothing better comes up have in mind the above solution!!!

---

### Post by SuperSonic4 on 2009-11-08
I don't know if it'll work but you can try adding the lock/logout plasmoid to the desktop - but then I never had this problem

---

### Post by Jetro on 2010-11-11
Hi. I have the same issue.
I installed KDE in Ubuntu. 10.04.

It sounds both odd and depressive if I have to do kleme's solution. :(

---

### Post by Jetro on 2011-01-05
Super BUMP.
kleme's solution (deleting .kde folder) did not work.

---

### Post by arrrghhh on 2011-03-05
Damn, this isn't resolved?  I have this issue on 10.10, and I've seen it happen on my ubuntu live USB install.

I'd really like to know a solution for this.

Deleting the .kde folder is not a viable option, and why should I have to install something called kshutdown?  Shouldn't I be able to restart and shutdown my laptop?

---

### Post by wiggly81 on 2011-03-05
im not sure about KDE but in gnome you can pres ctrl+alt+delete and that brings up the shutdown/restart options.
im sometimes to lazy to use my mouse lol

---

### Post by Jetro on 2011-05-02
You can make the icons appear by changing the login manager. It may suck if you don't want the KDE one, but anyway:

Type
```
dpkg-reconfigure gdm
``` in a terminal. Use arrows and tab to cycle between alternatives. Select **kdm**. Log out, restart and the login manager should look entirely different.
This made the Restart and Shut Down button appear in Kubuntu/KDE to me. :)

[Link to another similar thread]("http://ubuntuforums.org/showthread.php?p=10756113"). Apparently you can add to the bug report by voting on it.

---

### Post by bergfly on 2011-05-03
Have you allowed shut down for your users in the system settings?

Open system settings, scroll down to system administration, then look for the start-up and shut-down icon. Click on that. Then go to session management and make sure offer shut-down options is checked. From your screen shot, that should help.

---

