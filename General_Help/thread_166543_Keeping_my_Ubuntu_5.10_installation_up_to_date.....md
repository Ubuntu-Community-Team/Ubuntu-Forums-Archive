---
title: "Keeping my Ubuntu 5.10 installation up to date....?"
date: 2006-04-26
forum: General Help
---

### Post by mbobak on 2006-04-26
Hi,

I'm a long time Linux user, long enough to remember 1.0.x kernels.....

But, I'm very new to Ubuntu and the "Ubuntu" way of doing things.  Seems like every distro has a different approach to package managment and keeping things up to date.

So, I guess my first question is, what's the difference between doing 'sudo synaptic' and clicking 'Add Applications' from the 'Applications' menu?

The programs are clearly different.  Why two GUI programs that do the same thing?

Finally, there's an automatic update tool?  How does that fit into the picture?

Just trying to learn the ropes....

-Mark

---

### Post by cosmoshell on 2006-04-26
ine is for finding and installing programs and another is for updateing them

---

### Post by nanotube on 2006-04-26
the add applications one is for total newbies, and presents the most commonly used apps.
synaptic is for more experienced users, and lets you search the repositories of thousands of packages. (and of course for fans of commandline, there is apt-get).

the automatic update tool does what it sounds like it does - checks if any of the packages that you have already installed need updates (mostly these will be security updates).

---

### Post by mbobak on 2006-04-26
[QUOTE=cosmoshell]ine is for finding and installing programs and another is for updateing them[/QUOTE]

So, you're saying 'Add Applications' is  to add software, but synaptic is to update it?  I'm not sure it's as simple as that....It seems to me that either tool can be used for installation.

Hmm....ok, it looks like Synaptic has the more advanced functionality.  The 'Add Applications' utility is a nice piece of eyecandy for newbies?

-Mark

---

### Post by 5-HT on 2006-04-26
Hi, synaptic, 'add applications', and 'automatic updates' are all frontends to apt.

Synaptic is the more 'fully-featured' GUI package management tool, whereas 'add applications' is more of a limited tool in the sense that it lists only a few of the available packages. The automatic update tool is more of a convenience feature really, just to let you know that there are updates available for the packages that you have installed.

There's no need to use any or all of them (you could stick with apt-get or aptitude for package management, or even venture into using lower-level tools), they are simply nice tools that are geared towards similar, but slightly different purposes (though synaptic can do everything that 'add applications' and 'automatic updates' can).

Choice is great!

Hope that helps.

---

### Post by mbobak on 2006-04-26
Whoops nanotube slipped in.  Thanks for the explanation, nanotube.  I came to the same conclusion, so I guess that's a good thing...;-)

---

### Post by mbobak on 2006-04-26
Hehe....and now 5-HT slipped in!  Thanks for your help...I think I've got it now.  I'll concentrate on getting comfortable with Synaptic.

-Mark

---

### Post by nanotube on 2006-04-26
heh yea, that's what's great about these forums - you can count on a few people to slip in :)

yes, synaptic is a great choice - in my personal opinion, it presents the best balance between ease of use (gui), and power. though eventually you will find apt-get and friends of the commandline persuasion come in handy once in a while as well. :)

---

### Post by 5-HT on 2006-04-26
[quote=mbobak]Hehe....and now 5-HT slipped in!  Thanks for your help...I think I've got it now.  I'll concentrate on getting comfortable with Synaptic.

-Mark[/quote] 
NP. Also, there's even another package manager availalbe for Ubuntu, aptitude.
I think aptitude may even be the preferred package manager for Debian Sarge.
It has some nice dependency handling capabilities that are not present in apt and synaptic. 

Here's a link on the matter if you want to take a gander: 

[HOWTO: use aptitude instead of synaptic and why]("http://ubuntuforums.org/showthread.php?t=37736")

---

