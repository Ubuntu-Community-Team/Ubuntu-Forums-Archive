---
title: "Hardware control &amp; general security questions"
date: 2011-03-07
forum: General Help
---

### Post by Davo_80 on 2011-03-07
Hi to all,

I am new to Ubuntuforums. First post here. 

I am new to Ubuntu as well, but not new to Linux in general. Since about 1996-7, I have been using MandrakeLinux, later Mandriva. For a while, I've been quite active at MandrivaClub.nl (MCNL) as I am Dutch speaking (though Belgian).

The past quarrels at MDV drove me away from it, in combination with unsatisfactory updates of certain packages. Mageia, the rogue offspring of MDV was to hostile in the beginning towards MDV itself for me to eat it. 

I am very fond of Gnome. So, Ubuntu was in the picture. 

I installed it from a USB key I wrote in Windows XP. No problems.

I could easily enable my US Robotics PCI Wireless card using the "additional drivers". New experience for me, but greatness!

I have three other questions of a more fundamental nature (the third question is rather cosmetic though) and they are a consequence of over 10 years of Mandriva usage; since MDV users are spoiled with some great control features.

1. WHY does Ubuntu ask for MY password as a user instead of a general Root password (which was never asked during installation). Is the first user = root ? If so, ok. In my linux understanding, if I do "updatedb" the console should ask for a root password, not my user password. Equal for installing software etc. I guess there must be some help page explaining this? Any pointers here? Thanks. 

2. Hardware control. Mandriva has really great hardware control UI's. Here in Ubuntu, I'm missing this a little bit. I find all standard Gnome UI's about hardware, but so far, I didn't find a clear page with all hardware listed, where I could alter and play with settings. An other example: firewalls. No UI's to set this? I guess I'm overlooking it, or that there are great add-ons in the depositories. Any help or insight would be appreciated. 

3. Categories in software library. +3000 packages in one list, technical stuff left out. Seriously? Why aren't there thematic lists?

Thanks for any help.

Looking forward to a long period of fun with Ubuntu!

Kind regards,

Dave

---

### Post by mikewhatever on 2011-03-07
> **Davo_80 said:**
> Hi to all,

...

1. WHY does Ubuntu ask for MY password as a user instead of a general Root password (which was never asked during installation). Is the first user = root ? If so, ok. In my linux understanding, if I do "updatedb" the console should ask for a root password, not my user password. Equal for installing software etc. I guess there must be some help page explaining this? Any pointers here? Thanks. 

Ubuntu uses 'sudo' instead of root (see the link).
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> 2. Hardware control. Mandriva has really great hardware control UI's. Here in Ubuntu, I'm missing this a little bit. I find all standard Gnome UI's about hardware, but so far, I didn't find a clear page with all hardware listed, where I could alter and play with settings. An other example: firewalls. No UI's to set this? I guess I'm overlooking it, or that there are great add-ons in the depositories. Any help or insight would be appreciated. 

I think the 'hardware control UI' was a Mandriva thing, as for firewalls, you can install and use gufw. It's not included because the default Ubuntu installation has no open ports, and subsequently, nothing to firewall.

> 3. Categories in software library. +3000 packages in one list, technical stuff left out. Seriously? Why aren't there thematic lists?

Software is nicely categorized in the Software Center. What version of Ubuntu do you use?

---

### Post by grahammechanical on 2011-03-07
Ubuntu is for human beings. This I understand to mean that the developers are trying to make things fool-proof for those who just want to use their computer and are not interested in commands and all that stuff.

I would guess that those with the skills to use the command line can still do so but I do not think that the command line is the approach that Ubuntu is taking.

Have you looked in the Synaptic Package Manager? You might find that more to your liking than the Software Centre. These two utilities demonstrate the move away from letting educated users do things to not needing to be very educated to do it.

I also think that Universal Firewall is installed by default and activated at boot up.

I think that you can do anything you want any way that you want in Ubuntu. And if you can become part of the Ubuntu team then I think that people like me will reap the benefits.

Welcome to the Ubuntu Community.

Regards.

P.S. The first user is root but not in the way you understand. When we try to do something that would usually require root privileges we are asked to authenticate. As we are the root user our log in password will work but the root privileges will only last for that one purpose. This is so that we are protected from ourselves. We do not need to log in as root and then log out only to log back in as an ordinary user.

---

### Post by JKyleOKC on 2011-03-07
Dave,

I also was a Mandrake user, since version 8.1 -- but when my original box blew up (almost literally -- the power switch shorted out) I tried to install the latest version of Mandriva on its replacement and found it (a) too bloated to use and (b) absent most of the features I had come to depend on.

After some shopping around, I came across Xubuntu in 2007 (Fiesty Fawn) and found it rather easy to comprehend, although not at all like the RedHat-based Mandrake/Mandriva systems.

Ubuntu and its offspring are based on Debian rather than on Red Hat, and consequently have some major differences in internal organization. I find the "deb" packages far superior to the "rpm" packages I used to deal with, but at first their simplicity was a bit unsettling.

Additionally, the runlevels here are drastically different from those based on Red Hat, so system configuration is something one must re-learn. The worst thing I've found about this is that none of my reference books talk about such differences, though.

Welcome to the world of Ubuntu; one the strangeness wears off I think you'll like it.

Incidentally, it's possible to make the use of "root" mimic that with which you're familiar, but I've not yet found it necessary (after doing it once, on an earlier test installation). Using "sudo" quickly becomes second nature, and certainly beats having to log in as a different user when I need to adjust a system setting! Of course, in my Mandrake days I just used "su" in much the same way as I use "sudo" today...

---

### Post by Davo_80 on 2011-03-10
> **mikewhatever said:**
> Ubuntu uses 'sudo' instead of root (see the link).
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

 

I think the 'hardware control UI' was a Mandriva thing, as for firewalls, you can install and use gufw. It's not included because the default Ubuntu installation has no open ports, and subsequently, nothing to firewall.



Software is nicely categorized in the Software Center. What version of Ubuntu do you use?

Thank you for your reaction.

1. Sudo -> I found out in the meanwhile. Ok with that. 

2. System control UI's would have been a better term instead of hardware control. I guess it's about getting used to a different way.

3. I am using ubuntu 10.10. When I click Applications > Ubuntu Software Center, it's all in one big list... What am I missing?

Thanks for your help!

---

### Post by Davo_80 on 2011-03-10
> **grahammechanical said:**
> Ubuntu is for human beings. This I understand to mean that the developers are trying to make things fool-proof for those who just want to use their computer and are not interested in commands and all that stuff.

I would guess that those with the skills to use the command line can still do so but I do not think that the command line is the approach that Ubuntu is taking.

Have you looked in the Synaptic Package Manager? You might find that more to your liking than the Software Centre. These two utilities demonstrate the move away from letting educated users do things to not needing to be very educated to do it.
[...].

I think that you can do anything you want any way that you want in Ubuntu. And if you can become part of the Ubuntu team then I think that people like me will reap the benefits.


Also thank you for pointing some things out to me.

The approach to a system is indeed very different between Ubuntu and Mandriva. By using Ubuntu, I feel I have somewhat less control (like in MS Windows - don't kill me please) but on the other hand, in the past 10+ years, I also killed my Mandriva system a couple of times. So, it is a trade-off I guess. For daily use, Ubuntu is indeed great I guess. And the real die-hards will indeed refer to the CLI when needed. I can live with it.

The synaptic Package manager is more to my likes than the standard software center. I just installed it and like it. Thanks for telling me.

---

### Post by Davo_80 on 2011-03-10
> **JKyleOKC said:**
> Dave,

I also was a Mandrake user, since version 8.1 

[...]

Ubuntu and its offspring are based on Debian rather than on Red Hat, and consequently have some major differences in internal organization. I find the "deb" packages far superior to the "rpm" packages I used to deal with, but at first their simplicity was a bit unsettling.

Additionally, the runlevels here are drastically different from those based on Red Hat, so system configuration is something one must re-learn. The worst thing I've found about this is that none of my reference books talk about such differences, though.

Welcome to the world of Ubuntu; one the strangeness wears off I think you'll like it.

Incidentally, it's possible to make the use of "root" mimic that with which you're familiar, but I've not yet found it necessary (after doing it once, on an earlier test installation). Using "sudo" quickly becomes second nature, and certainly beats having to log in as a different user when I need to adjust a system setting! Of course, in my Mandrake days I just used "su" in much the same way as I use "sudo" today...

Well it is very interesting to read your comment as you are also an ex-Mandrake user.

If it's about re-learning some things, i'm in because learning is what life is about.

Ubuntu indeed looks a bit more accessible; for the first time since long, my wife is surfing the internet in a linux environment. Interesting! (all i had to do was import her bookmarks into firefox) :)

Your 'su' and 'sudo' comparison is also what I made of it. I'm a frequent CLI user... I'll get going in no-time.

Cheers for Ubuntuforums!

---

### Post by JKyleOKC on 2011-03-12
The first thing I learned about runlevels was that the Debian approach makes 2, 3, 4, and 5 all identical to each other, unlike the RedHat way of having 5 for GUI and 3 for CLI. The second was that there's no default file that defines them; instead they are more or less hardwired into the boot sequence.

Ubuntu is moving away from the SysV original /etc/rc.d way of handling the boot sequence to a new event-driven approach called upstart. Since it IS event-driven rather than purely sequential, it's a bit difficult to wrap one's mind around -- almost exactly like the difference between programming for DOS and for Windows, some 20 years ago! This move began around 2008 and each new release has taken it a bit farther along the path. I stay with the LTS (Long Term Support) releases so don't know what in this area changed with 10.10, but as of 10.04 not all of the scripts usually found in /etc/rc2 and relatives are what you might expect to see. If this gives you any problems just yell and folks here will be quick to come up with answers. Quite a few of us old-timers know the way things used to be and can help with the transition.

---

