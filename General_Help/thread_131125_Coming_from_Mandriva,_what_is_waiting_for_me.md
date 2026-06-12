---
title: "Coming from Mandriva, what is waiting for me?"
date: 2006-02-15
forum: General Help
---

### Post by mexlinux on 2006-02-15
OK, once I got an ubuntu 5.04 live cd, my first impression was (and is still being), this is Ugly! (GNOME and GTK apps are in general, **from my point of view**: ugly, dull, confusing and lacking of options)... well....
Now I know about Kubuntu, that's more like what I want.

I have benn using only Mandrake since the begining of my switch to Linux 4 year ago. I am comfortable, but I have hear too much noice about Kubuntu lately, so I'm considering to switch.

But I have some questions:
-what abut all the plf aplications, are there corresponding packages avilabe for Kubuntu? How to get them?
-I currently have a Dell Insipiron 630m Laptop, has anyone tried on it? (the mentioned live cd does not work on thi laptop it just shows a black screen...knoppix works)
-What are (for the final user) the differences between using DEB instead of RPM?
-Is easy to get packages, is there an equivalent to easyurpmi site?
-Mandriva has a Control Center very usefull to configure many opions of the system in a very easy way, is there an equivalent?
-Are the configuration files, in general the same that in Mandriva? Or what are the differences between a debian and a mandriva distro?
...more too come for sure.

Thanks in advance

---

### Post by aysiu on 2006-02-15
[QUOTE=mexlinux]OK, once I got an ubuntu 5.04 live cd, my first impression was (and is still being), this is Ugly! (GNOME and GTK apps are in general, **from my point of view**: ugly, dull, confusing and lacking of options)... well....[/quote] That's what everybody thinks... well, not *everybody*, but *most* people. Thankfully, that's not Gnome's fault--it's Ubuntu's. Gnome can be tweaked to be quite beautiful, actually. Install a few themes, change the icons, change the wallpaper...

> 
Now I know about Kubuntu, that's more like what I want. To each her own.

> 
I have benn using only Mandrake since the begining of my switch to Linux 4 year ago. I am comfortable, but I have hear too much noice about Kubuntu lately, so I'm considering to switch. If you like Mandrake, I see no reason to switch besides curiosity. Have you considered PCLinuxOS? It's a pretty cool distro, and it's based on Mandriva.

> 
But I have some questions:
-what abut all the plf aplications, are there corresponding packages avilabe for Kubuntu? How to get them? Ubuntu and Kubuntu share repositories. They're actually the same distro. They just have different default desktop environments.

> 
-I currently have a Dell Insipiron 630m Laptop, has anyone tried on it? (the mentioned live cd does not work on thi laptop it just shows a black screen...knoppix works) That's not a good sign. The live CD is a pretty good indicator of how well the installation will work. If Knoppix works, you may consider using Mepis. It's another cool distro, but it's Knoppix-based.

> 
-What are (for the final user) the differences between using DEB instead of RPM? As far as I know... none. They both have dependencies, and they both can be packaged and managed so as to fulfill those dependencies.

> 
-Is easy to get packages, is there an equivalent to easyurpmi site? There's [http://packages.ubuntu.com](http://packages.ubuntu.com) and [http://www.apt-get.org](http://www.apt-get.org)
Mixing Debian and Ubuntu repositories isn't a generally good idea. If you add a Debian repository, add it, install the package, then get rid of the repository afterward.

> 
-Mandriva has a Control Center very usefull to configure many opions of the system in a very easy way, is there an equivalent? Try Alt-F2 and ```
kcontrol
``` That's about as good as it gets in Kubuntu.

> 
-Are the configuration files, in general the same that in Mandriva? Or what are the differences between a debian and a mandriva distro? Can you mention a couple of examples? /etc/fstab and /boot/grub/menu.lst are pretty standard for distros.

---

### Post by tsmiller on 2006-02-15
I have also been using Mandrake (Mandriva) for a long time.  I have been looking at Kubuntu for about two days now.  It is obvious that Kubuntu is not as mature as Mandriva in some things  (things like the install process and most configurations), but briefly I will tell you what I see.

I like Kubuntu's philosophy.  I worry that down the road Mandriva, Redhat, Suse, etc will continue to become more commerialized and less open and free. And I do not mean money wise.  I have contributed to them financially which is fine.

I do Not like the RPM package management system.  Because of dependency hell, I pretty much download the source and do the configure, make, install thing.  I do not have alot to base it on, but the Kubuntu install process seems to be more comprehensive, stable, well designed, user friendly, and better organized.  I like the way that they distinguish between the main and the universe.  

I think that over the next few releases kubuntu's distribution will settle down and mature.  I know there are irritating things about both Kubuntu and Mandriva.  Things that you just learn to live with.  I have been using linux exclusively for about five or six years now and I really respect the people that put it together.  It is a big complex endeavor.  In the long run, if community support continues, I think that Kubuntu is going to be in the better position.  

This is just my personal opinion. But after looking at Kubuntu that first day, I knew that I was going to change to it.  

Good luck whichever direction you go.  

Tom

---

### Post by gingermark on 2006-02-16
[QUOTE=mexlinux]
-what abut all the plf aplications, are there corresponding packages avilabe for Kubuntu? How to get them?[/QUOTE]
in debian-based distros like (K)ubuntu there is a file called sources.list located in /etc/apt - you can edit this file to add repositories. And yes, a (K)ubuntu PLF repository exists.
[QUOTE=mexlinux]
-I currently have a Dell Insipiron 630m Laptop, has anyone tried on it? (the mentioned live cd does not work on thi laptop it just shows a black screen...knoppix works)[/QUOTE]
It might well be worth grabbing a Breezy Live CD if you can to check this. Also, Dapper will be out in a couple of months, and I'm sure it will have improved hardware support (although currently it's pretty good)
[QUOTE=mexlinux]
-Mandriva has a Control Center very usefull to configure many opions of the system in a very easy way, is there an equivalent?[/QUOTE]
Kubuntu defaults to it's own version of kcontrol (called System settings) but it pretty much just includes the same modules as kcontrol (which is also installed). I don't know if Mandriva's control centre has been customised for the distribution, I get the feeling Kubuntu's is similar to the default KDE one, although I'm not certain.

---

### Post by mexlinux on 2006-02-16
[QUOTE=aysiu]
 If you like Mandrake, I see no reason to switch besides curiosity. Have you considered PCLinuxOS? It's a pretty cool distro, and it's based on Mandriva.
[/QUOTE]

Welll yes, curiosity is a reason as said befor, I have heard soo much noice abiut kubuntu....

BUT what is really annoying is the suspend in my laptop.
Currenly I can suspend to memory, but some times it wakes up, some times it does not, and I can not suspend to disk.....

I remember I read (but I can not find where) some guy telling that my laptop model suspends very well in ubuntu. So Thats the main reason.

---

### Post by bulldogzerofive on 2006-02-17
I made that same switch.

And boy was I happy that I did.

Now, I only used MDK 10.0 and 10.1, but the greatest thing was that the bugs pretty much went away for me.  I no longer have apps breaking after an update, is the big thing.

True, the look and feel is not as polished as mandriva, but I find the rest of the system works better, and is still pretty cutting-edge.  Besides, if look and feel matters you can always tweak it to your liking.

---

### Post by sarah_b on 2006-02-17
[QUOTE=bulldogzerofive]I no longer have apps breaking after an update, is the big thing.[/QUOTE]

I tried running Kubuntu 5.04, I liked what I seen but my experiences were the same as above. I just put Kubuntu Dapper flight 3 on a different computer and am giving that a try. So far, so good. A couple of months until the final release ? 

I am so comfortable with ubuntu Beeze, Kubuntu will have to be awfully good for me to switch.

---

### Post by Joey French on 2006-02-17
I came to ubuntu when Mandrake became Mandriva. I have been so much happier. True, Mandriva is more polished, but rpm sucks bad. Apt-get is one of the best things about ubuntu. If you want to, just install ubuntu, then install kubuntu-desktop, and have the best of both worlds (Since you seem to like KDE more than Gnome). I fell in love with this distro the minute I found I could do this- with almost no effort at all. 

Good luck!
Joey French

---

