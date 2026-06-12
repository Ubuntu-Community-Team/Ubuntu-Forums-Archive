---
title: "&quot;deb command not found&quot;"
date: 2009-12-26
forum: General Help
---

### Post by demonlordbrad on 2009-12-26
Hi all,

I've been trying to run a program called moblock on Ubuntu. For those of us who are not familiar with it it's a program that prevents many different kinds of computers from seeing what you are doing. Unfortunately in order to install this program I need to use Deb, and Deb-src commands. When I type one of these commands it responds 
"No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found"

does anyone have any idea how I can fix this error?

If it helps anyone I am running Ubuntu 9.10 desktop, a fresh boot  at  that.

---

### Post by spiderbatdad on 2009-12-26
looks like usage is:
blockcontrol option
after the package is installed.
Are you talking about [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

---

### Post by diesch on 2009-12-26
This Deb and Deb-src commands aren't for being run at the command line but written to */etc/apt/sources.list*

---

### Post by demonlordbrad on 2009-12-26
sorry, I'm pretty bad at this, you guys are both right but how do I install it then?

---

### Post by gsmanners on 2009-12-26
This is explained here:

[https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html)

I don't know how well it relates to what you're running, but it should be close.

---

### Post by diesch on 2009-12-26
Create as root a file named */etc/apt/sources.list.d/moblock* and write the two lines into this file. Then run the command listed under "Add my gpg key" and reload the package information (e.g."Reload" in Synaptic or *apt-get update* at the command line) and install the package <i>moblock</i>

---

### Post by Rbacon on 2012-11-23
> **gsmanners said:**
> This is explained here:

[https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html)

I don't know how well it relates to what you're running, but it should be close.

I am having the same problem with another install but I am very new to servers and working on command lines at all... I get a 404 page not found when I try that link. Is there a new link to help me with getting into a folder?

---

### Post by oldos2er on 2012-11-23
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

