---
title: "Removing Evolution/Open Office"
date: 2010-01-07
forum: General Help
---

### Post by Thinkwritemute on 2010-01-07
> evolution-data-server-common
architecture independent files for Evolution Data Server

Why, when removing this package, does Synaptic want me to also remove:

> gnome-applet
gnome-panel
indicator-applet
ubuntu-netbook-remix

This seems pretty stupid. I just want to get rid of Evolution! Netbooks are cloud based machines, why was Evolution even included?! The same with OpenOffice.

---

### Post by Mahngiel on 2010-01-07
try 'sudo apt-get remove evolution openoffice --purge'

---

### Post by running_rabbit07 on 2010-01-07
> **Thinkwritemute said:**
> This seems pretty stupid. I just want to get rid of Evolution! Netbooks are cloud based machines, why was Evolution even included?! The same with OpenOffice.

Netbooks come with office productivity, because they are designed primarily for students to use at school without lugging around 10 pound 17inch laptop. It is also nice to have a mail client.

---

### Post by audiomick on 2010-01-07
> **Mahngiel said:**
> try 'sudo apt-get remove evolution openoffice --purge'

No, don't do that! Gnome and Evolution are closely interwoven, which probably why those gnome packages want to go west with the evo ones.

I have seen a lot of posts here from people who removed evo and then had a broken desktop. The common wisdom is to leave evolution alone.

---

### Post by running_rabbit07 on 2010-01-07
> **audiomick said:**
> No, don't do that! Gnome and Evolution are closely interwoven, which probably why those gnome packages want to go west with the evo ones.

I have seen a lot of posts here from people who removed evo and then had a broken desktop. The common wisdom is to leave evolution alone.

I've almost done the same thing. I go through Synaptic every time I install and remove every evo and open office program that doesn't show Ubuntu-Desktop as a dependency.

---

### Post by snowpine on 2010-01-07
> **Thinkwritemute said:**
> Why, when removing this package, does Synaptic want me to also remove:

gnome-applet
gnome-panel
indicator-applet
ubuntu-netbook-remix 

The four packages you list all depend on evolution (for example, the gnome panel needs evolution to display the calendar that drops down when you click the clock). The system will warn you when the application you're trying to remove is a depencency for another application; it's a good thing.

We had another thread about this recently (I don't have the link handy), and my recommendation is to simply remove the Evolution icon from your panel and pretend it isn't installed.

---

### Post by mkvnmtr on 2010-01-07
On the last three releases I have removed Evolution with no problems. I use the package manager. In the search box I type Evolution. Then I go through the installed packages that are Evolution related. I mark for complete removal. It will then tell you if it must remove anything else. If it is going to remove something I do not want removed I cancel. There is only one related server that tries to remove other packages. I leave it. It takes a little time but I have never messed up anything. It also works with pidgin and about 10 other things I do not want.

---

### Post by Mahngiel on 2010-01-07
> **audiomick said:**
> No, don't do that! Gnome and Evolution are closely interwoven, which probably why those gnome packages want to go west with the evo ones.
 
I have seen a lot of posts here from people who removed evo and then had a broken desktop. The common wisdom is to leave evolution alone.
 
I do this everytime I reinstall Ubuntu. NEVER had any problems

---

### Post by Thinkwritemute on 2010-01-08
Yes, pretend 300mb of useless data on a computer designed to browse the internet (email/collaborate on docs) doesn't exist. Along with the directories they make, the files they point to, and the ram they use up :P

Did the thread ever figure out why Ubuntu, a free open source software, tied it's GUI so heavily into a /single/ email client (of dubious use)?

---

### Post by snowpine on 2010-01-08
> **Thinkwritemute said:**
> Yes, pretend 300mb of useless data on a computer designed to browse the internet (email/collaborate on docs) doesn't exist. Along with the directories they make, the files they point to, and the ram they use up :P

Did the thread ever figure out why Ubuntu, a free open source software, tied it's GUI so heavily into a /single/ email client (of dubious use)?

Ubuntu provides a [Minimal Install CD]("https://help.ubuntu.com/community/Installation/MinimalCD") for users (such as yourself?) who want full control over exactly which applications are installed.

The "regular" install CD is meant to be full-featured and therefore includes a full "suite" of applications. And a lot of users (for example Windows refugees familiar with Outlook) want/need an application for their email, calendar, contacts, etc. Just because you do not personally use it does not mean the demand for it isn't strong. :)

It's also worth pointing out that Evolution is only found in the Gnome version of Ubuntu. You could also check out Xubuntu, Kubuntu, etc. which each have a completely different suite of applications. Gnome is a *very* full featured (some would say bloated?) desktop environment, no question about it. I personally use LXDE instead of Gnome on my Dell netbook (which only has an 8gb drive). On my Asus eee (which has a 160gb hard drive, plenty of room) I have a full Gnome install, and I simply pretend the Evolution icon isn't there. In other words, my point is, the default install of Ubuntu is not the only way to experience Ubuntu--because it is Linux, it can be infinitely customized to your needs.

---

### Post by llawwehttam on 2010-01-08
> **audiomick said:**
> No, don't do that! Gnome and Evolution are closely interwoven, which probably why those gnome packages want to go west with the evo ones.

I have seen a lot of posts here from people who removed evo and then had a broken desktop. The common wisdom is to leave evolution alone.
I removed evolution with ```
sudo apt-get purge evolution
``` in favor of thunderbird. I had no problems but that is not so say that you might.

---

### Post by scouser73 on 2010-01-08
Remove OpenOffice with this command > **sudo apt-get remove openoffice*.***

---

### Post by Thinkwritemute on 2010-01-08
> **snowpine said:**
> Ubuntu provides a [Minimal Install CD]("https://help.ubuntu.com/community/Installation/MinimalCD") for users (such as yourself?) who want full control over exactly which applications are installed.

The "regular" install CD is meant to be full-featured and therefore includes a full "suite" of applications. And a lot of users (for example Windows refugees familiar with Outlook) want/need an application for their email, calendar, contacts, etc. Just because you do not personally use it does not mean the demand for it isn't strong. :)

It's also worth pointing out that Evolution is only found in the Gnome version of Ubuntu. You could also check out Xubuntu, Kubuntu, etc. which each have a completely different suite of applications. Gnome is a *very* full featured (some would say bloated?) desktop environment, no question about it. I personally use LXDE instead of Gnome on my Dell netbook (which only has an 8gb drive). On my Asus eee (which has a 160gb hard drive, plenty of room) I have a full Gnome install, and I simply pretend the Evolution icon isn't there. In other words, my point is, the default install of Ubuntu is not the only way to experience Ubuntu--because it is Linux, it can be infinitely customized to your needs.

Except I didn't use the regular version of Ubuntu. I used the Netbook Remix.

It looks like I can just purge it off my system, as some of these guys suggest. It just seems like a major pain.

I can't wait for Ubuntu to actually be customizable when installing, instead of just "customizable if you feel like building your own from scratch".

---

### Post by snowpine on 2010-01-08
> **Thinkwritemute said:**
> Except I didn't use the regular version of Ubuntu. I used the Netbook Remix.

It looks like I can just purge it off my system, as some of these guys suggest. It just seems like a major pain.

I can't wait for Ubuntu to actually be customizable when installing, instead of just "customizable if you feel like building your own from scratch".

Ubuntu Netbook Remix is just Gnome with big icons. Evolution is installed by default because it is an integral part of the Gnome desktop environment.

You might also check out the [Kubuntu Netbook Remix]("http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Kubuntu-Netbook-Remix-Karmic-49499.shtml"). I haven't personally tried it, but since it uses KDE instead of Gnome, I imagine it doesn't include Evolution.

And don't forget the [Ubuntu Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") I mentioned in my previous post. It allows you to install *exactly* what **you** want (instead of what someone else thinks you want).

---

