---
title: "Switching from Ubuntu to KDE version of Ubuntu (Kubuntu)"
date: 2006-03-10
forum: General Help
---

### Post by zainka on 2006-03-10
Hi

I once before christmess installed Ubuntu as my first Linux experience on a P3 550MHz deskflop. Now, while beeing an windows experiencede user i found the Linux (Ubuntu) to be tremendeous slow (Very slow response to user activity, say several seconds++ and then add some more +)  and thus I wonder if there is any better performance to expect if switching to Kubuntu using the KDE version since I have heard from someone tha KDE is so mucho faster. But is this the thruth? Is KDE better, more stable or wath or is there no differences expect to the GUI? And finaly, if switching to Kubuntu, Should I do a full installation of Kubuntu or only change GUI, (And which actions must be taken to the grub installer if switching).
And then, Finaly indeed! What can possible make the Linux so slow according to Win2k in my system (P3 550MHz 133MHz Bus, 256MB Ram)?:-k 

Thanks

---

### Post by dermotti on 2006-03-10
You could always try to download kdebase with synaptic and try it out....

My personal opinion is KDE is less stables, but faster and easier to use for a novice.

---

### Post by Sef on 2006-03-10
> What can possible make the Linux so slow according to Win2k in my system (P3 550MHz 133MHz Bus, 256MB Ram)?

Well your system is not going to be too fast. You could try upgrading the Ram to 512, but otherwise i would try a lightweight distro, like DSL or featherlinux.  They would run faster on your system.

---

### Post by Jucato on 2006-03-10
You could also try to use Xubuntu/Xfce. I heard it's good and fast for lower spec systems, or for those who really want speed. From what I've heard, KDE is slower than GNOME. I really can't tell because I haven't used GNOME except on a Live CD. All I can tell is that KDE offers more options upfront, whereas you have to go searching for some features in GNOME. KDE is also known for offering more eye candy, from applets to window decorations, to composite managers, and so on.

Kubuntu, I've heard, is less stable than Ubuntu. That doesn't mean the KDE itself is less stable than GNOME. Remember that Kubuntu is KDE mixed with Ubuntu flavors. So it isn't pure KDE. (in this sense, I don't know if there really is a pure KDE out there).

You have 2 options on how to go about installing Kubuntu. You could install it over Ubuntu, preserving your apps (which will still work in KDE) or starting fresh with a new install. If you install it over Ubuntu (by installing the kubuntu-desktop metapackage) all you need to do to switch from GNOME to KDE is to log out to the login screen (GDM or KDM, whichever you prefer to use) and choose KDE from the Sessions option. If you are doing a fresh install, the installer will install a new GRUB for you.

---

### Post by ComplexNumber on 2006-03-10
normally, gnome is a lot faster than KDE because it has much less overhead. apparently though, there is something about the cairo/pango in ubuntu which makes it a lot slower than typical gnome.

---

### Post by Adrian on 2006-03-10
[QUOTE=zainka]And then, Finaly indeed! What can possible make the Linux so slow according to Win2k in my system (P3 550MHz 133MHz Bus, 256MB Ram)?
[/QUOTE]

People will always tell you to upgrade. However, most of the time that isn't necessary (if you're not a heavy gamer). 256MB is enough for running desktop Linux, really. Many new computers still come with 256MB, so don't worry. Last year I successfully ran KDE on a 128MB machine.

I think your CPU speed is ok too. I'm running a 700MHz Celeron and it feels very fast. At least as fast as Windows 2000, which you already are running. Keep in mind that KDE 3.0 was launched in 2002 (the first betas came in 2001), and KDE 3.5 is not THAT much slower really. Of course it is a good idea to disable all effects (animations and such) if you want a really quick system.

When I switched to Linux, I tested both Gnome and KDE, and KDE was actually faster on my machine.

At least you should give it a try :)

---

### Post by Adrian on 2006-03-10
[QUOTE=ComplexNumber]normally, gnome is a lot faster than KDE because it has much less overhead. apparently though, there is something about the cairo/pango in ubuntu which makes it a lot slower than typical gnome.[/QUOTE]

My experience is completely different. I've compared them both on Debian and Freebsd too. I always thought KDE felt snappier.

However, that was on **MY** machine :)

---

### Post by newbie2 on 2006-03-10
Fine-Tuning Kubuntu
> As nice as Kubuntu is, the default installation doesn't fit every user. This article shows how to get help, get access to more software packages, set up a firewall, and review and get rid of unnecessary services. This article covers Kubuntu 5.10, Breezy Badger.
[http://www.linuxdevcenter.com/pub/a/linux/2006/03/09/tuning-kubuntu.html?CMP=OTC-0O724Z062301&ATT=Fine-Tuning+Kubuntu](http://www.linuxdevcenter.com/pub/a/linux/2006/03/09/tuning-kubuntu.html?CMP=OTC-0O724Z062301&ATT=Fine-Tuning+Kubuntu)

---

### Post by Jucato on 2006-03-10
Wow! thanks for that link! I've been using Kubuntu for almost 3 months, and it's the first time I've seen that. Adding it to my Bookmark library :D

---

### Post by zainka on 2006-05-25
Hi, and thank you all for your replay and second, sorry for brinnging this topic up and go again, it has been a while since there has been any activity, but then again, there has been a while since there has been any activity with me too, according to linux, But I never got finish with the problem I had.

What I really wanted to know, when doing a rethink, is that there must be an explination for why Ubuntu (Linux) is so much slover on the same machine where I run windows 2000?? I mean, isnt Linux youst as good as w2k or does it require more power to be able to gain same performance as windows at lower power?

However, I will continue to use Ubuntu to learn Linux, but I was cinda hoping for a better performance according to Windows.

Is there any benchmark tools I can download whic is compiled for both windows and linux so thath I can do a comparsion of the two?

Thanks in advance
Vidar (Z)

---

