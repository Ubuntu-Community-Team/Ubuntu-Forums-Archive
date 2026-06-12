---
title: "I need to instal &quot;KnowIt&quot; on Precise Pengolin"
date: 2012-06-30
forum: General Help
---

### Post by Cotopaxi on 2012-06-30
In Kubuntu 11.04 I was working with a program called KnowIt, which is not in the repositories anymore in Precise Pengolin!

I did download the tarball, but I am totally unable to install it.

The link of the page at sourceforge is:

[http://knowit.sourceforge.net/]("http://knowit.sourceforge.net/")

I gave the program "BasKet" a try and the program did open the KnowIt file, but I am totally unable to work with this program and I would really love to have KnowIt installed. Can anyone give me a helping hand?

Thanks very much indeed!

---

### Post by dgharmon on 2012-06-30
> **Cotopaxi said:**
> In Kubuntu 11.04 I was working with a program called KnowIt .. I did download the tarball, but I am totally unable to install 

It says here there is a deb file, so all you have to do to install it is download it and type at the console:

$sudo dpkg –i filename.deb

If it complains about missing libary files then fire up synaptic and install them ...

[http://knowit.sourceforge.net/files/knowit_0.10-1_i386.deb](http://knowit.sourceforge.net/files/knowit_0.10-1_i386.deb)

---

### Post by Cotopaxi on 2012-07-01
dgharmon,

thanks for your reply, I will post the output of the installation instruction. I added to your installation instruction the force-all command.

> sudo dpkg -i --force-all knowit_0.10-0ubuntu3_amd64.deb
Selecting previously unselected package knowit.
(Reading database ... 214946 files and directories currently installed.)
Unpacking knowit (from knowit_0.10-0ubuntu3_amd64.deb) ...
dpkg: knowit: dependency problems, but configuring anyway as you requested:
 knowit depends on kdelibs4c2a (>= 4:3.5.9); however:
  Package kdelibs4c2a is not installed.
Setting up knowit (0.10-0ubuntu3) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...


Thanks very much indeed again for your help!

---

