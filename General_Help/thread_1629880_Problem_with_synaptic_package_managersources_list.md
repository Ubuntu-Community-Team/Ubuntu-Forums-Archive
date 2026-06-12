---
title: "Problem with synaptic package manager/sources list"
date: 2010-11-24
forum: General Help
---

### Post by bradleysmith on 2010-11-24
First of all, hello, I'm brand new to this forum as well as Linux in general (I'm an apprentice at an IT solutions company, a technician converted me to Linux :P).
So far, my experience with Linux has been great! There have been some issues with it but I understand that there's a learning curve when moving to absolutely any OS.
Anyway, to my problem: I'm unable to use Synaptic Package Manager at the moment. This came about when I was trying to install the unsupported plugins for Compiz (It has been hell to get these and still no luck thus far :/). When I open up Synaptic, I get this error message:

E: Type ‘n’ is not known on line 3 in source list /etc/apt/sources.list.d/compiz-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

Apologies if I need some instructions beaten into my head, this is all quite new to me :S

P.S. If I'm on the wrong board for this, I'm sorry :S I think I got it right though.

---

### Post by surfer on 2010-11-24
could you post the output of
```

$ cat /etc/apt/sources.list.d/compiz-ppa-maverick.list

```
there seems to be a problem in there.

---

### Post by bradleysmith on 2010-11-24
deb [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) maverick main
n

---

### Post by surfer on 2010-11-24
just delete the 'n' at the bottom line.

---

### Post by drs305 on 2010-11-24
surfer,

Welcome to the Ubuntu forums!

You have to delete the line with "n":
```
gksu gedit /etc/apt/sources.list.d/compiz-ppa-maverick.list
```
Delete the "n" line, then save the file and update your sources:
```
sudo apt-get update
```
If you aren't familiar with 'sudo/gksu', you will be asked for a password. Enter your password and press ENTER. For "sudo" in a terminal with a non-graphical command, you won't see the password as you type it.

---

### Post by bradleysmith on 2010-11-24
Okay, that seems to have worked fine and that has got rid of the error, thank you (Y).

However, I now have a new error when I try to open up synaptic:

W: Duplicate sources.list entry [http://ppa.launchpad.net/compiz/ppa/ubuntu/](http://ppa.launchpad.net/compiz/ppa/ubuntu/) maverick/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_compiz_ppa_ubuntu_dists_maverick_main_binary-i386_Packages)

---

### Post by surfer on 2010-11-24
do you have a
```
deb http://ppa.launchpad.net/compiz/ppa/ubuntu/ maverick/main
```
line in your /etc/apt/sources.list file as well? if so, remove it and
```
$ sudo apt-get update
```

---

### Post by bradleysmith on 2010-11-24
Excellent, that has fixed the problem :D thanks for the help.

---

### Post by mkstallings1 on 2010-11-24
I also am having a problem with the synaptics package manager. It started after I tried to uninstall XBMC.  When I opened synaptics package manager I got the error:

E: Type 'main' is not known on line 3 in source list /etc/apt/sources.list.d/team-xbmc-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Newb would appreciate any help

---

### Post by drs305 on 2010-11-24
@ mkstallings1,

Investigate the same way as above:

```
cat /etc/apt/sources.list.d/team-xbmc-ppa-maverick.list
```
or open the file for editing:
```
gksu gedit /etc/apt/sources.list.d/team-xbmc-ppa-maverick.list
```
and compare the line with the others. There is something wrong. I just added it and in Maverick it would look like this:
> deb [http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu) maverick main


---

### Post by mkstallings1 on 2010-11-24
When I ran the commandI got the following response:

deb [http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu) maverick main
 main

---

### Post by mkstallings1 on 2010-11-24
Thanks got it fixed.  Had to delete a second instance of the word "main"

---

