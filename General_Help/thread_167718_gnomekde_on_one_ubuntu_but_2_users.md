---
title: "gnome/kde on one ubuntu but 2 users???"
date: 2006-04-29
forum: General Help
---

### Post by tamarku on 2006-04-29
Is it possible to run gnome AND KDE on the same Ubuntu installation but under 2 different users?  I've worked with PCLINUXOS, Linspire, Xandros and I believe they were all KDE, and Ubuntu is the only Gnome Desktop I've played with.  I'm not really sure which I like.  I use my PC mainly for listening to music, Web Surfing, maybe some online banking, I like to pretend to play with HTML and maybe some other teach myself programming(just to play).  So anyway I don't think it will really matter to me which one but I'd like a side by side comparison.  Anyway, would it be possible if I made and additional user on my current gnome ubuntu and then made that second user my KDE user.  I must say I really like Ubuntu and I really like the way I don't feel pressured to 'donate'.  I realize it would help to keep the FREE linux project alive but I am starting to feel a bit pressured by some distro's that I need to donate or my OS may not be around.  Sidetracked again.  (chaos).  If someone could help me out with this question I would greatly appreciate it. 
THANKS.

---

### Post by Gannin on 2006-04-29
After installing the KDE packages, create your second user as you normally would, then logout of your current user.  From the login window, choose that you wish to login to KDE next, and then login with your new user.

---

### Post by aysiu on 2006-04-29
One user can use both KDE and Gnome, actually. I don't see why you need two users, as both users' menus will be cluttered up with extra applications, anyway.

If you want to try out KDE, go to Applications > Accessories > Terminal and copy and paste these commands: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` Log out > Session > KDE > Log back in.

---

### Post by tamarku on 2006-04-29
Will this leave gnome intact on my first user?  Plus, is there a thread I can read about getting the KDE packages downloaded and installed?

---

### Post by tamarku on 2006-04-29
Sorry aysiu, I'm giving your instructions a shot right now. Thanks for the quick responses.

---

### Post by aysiu on 2006-04-29
My instructions will get KDE fully downloaded and installed.
I'm not sure what you mean about the first user being affected.

As I said before, *all* users will be "affected" by KDE. Kubuntu comes with its own set of packages, and Gnome comes with its own set of packages, when you add one to the other, you get a bunch of cluttered menus in **both** environments. Each will have a combination of KDE *and* Gnome applications. Of course, you can manually delete the extraneous entries from the menus, but they will appear (at least at first) for **all users**.

So... there's no point in creating a second user.

---

### Post by tamarku on 2006-04-29
Yep, I see what you mean about the cluttered mess.  My response was to Gannin's reply.  You had beat me to it.  I'm running KDE right now.  Looks pretty sharp.  I like that Evolution maintained everything also.  This is a cool trick.  I will have to play and see which one I like best.  Does one call for more system resources then the other?

---

### Post by aysiu on 2006-04-29
[QUOTE=tamarku]Yep, I see what you mean about the cluttered mess.  My response was to Gannin's reply.  You had beat me to it.  I'm running KDE right now.  Looks pretty sharp.  I like that Evolution maintained everything also.  This is a cool trick.  I will have to play and see which one I like best.  Does one call for more system resources then the other?[/QUOTE] People say KDE is more resource intensive, but if you have 512 MB of RAM or above, you may not notice a difference.

Also, you can minimize the resources in KDE if you want by doing ```
sudo apt-get update
sudo apt-get install kpersonalizer
kpersonalizer
``` and then choosing "fewer effects" in the wizard.

---

### Post by tamarku on 2006-04-29
Well I am hoping to upgrade to a Gig of RAM so it shouldn't be to bad.  I will definately keep that in mind.  I must say the graphics look much crisper in KDE.  Well, Jeez, now I think I found something else to play with.  THANKS !!

---

