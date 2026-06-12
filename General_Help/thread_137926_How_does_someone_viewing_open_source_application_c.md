---
title: "How does someone viewing open source application code?"
date: 2006-02-28
forum: General Help
---

### Post by tinker312 on 2006-02-28
Hi Ubuntu community, 

Sometimes it seems that one of the most positive aspects of using a linux distribution is neglected.  This aspect is the ability to freely modify application code any way you want, with the result of some application providing you with more functionality than it did before. I realize there are different kinds of open source licenses. I can think of the GNU license off the top of my head. 

For the sake of knowledge, how would a guy see the code that makes up binary files? Is there a developer application that "loads" the program and allows us to read the application in a semi-friendly language?

How would someone look at the code that makes up the kernel? 

If anyone could turn me on to where I can read about this stuff I would greatly appreciate it. I'm fairly new to linux with my first box running Mandrake 8.0.  I've been hooked since and only have used Windows to play games. Now, Wine and and companies like Cedega are becoming so user-friendly that a nice Ubuntu box can play pretty much any MMORG, which is my favorite. The user-friendliness of Linux has come so far! My mother, with zero computer skills uses Ubuntu; I just providing support about every 2 months and it serves her great. I converted my neighbors to Ubuntu also, after a Windows virus fiasco which left them with no internet for a month, thanks to the cable company shutting down their port. 

I guess I'm ready to start exploring new ways to break my box and repair it, all for the sake of knowledge. 

Yours . . . 
John

---

### Post by Eleaf on 2006-02-28
Well, welcome!  :)

Usually to view a programs source, you need to go to the developers website, and they should have it readily available.  Many projects are listed on freshmeat or sourceforge which offer the source code.  You just have to do some looking around.  In the rare case the source code isn't readily available (very small projects), you can probably find the developers email address and request the source directly.  But you usually wouldn't ever have to do that.

As for the kernel.  I usually get it from [www.kernel.org](www.kernel.org) .  That site offers the newest linux kernel sources, and some older ones as well.  There are quite a few places to get these things.  Some distro's like gentoo have all (most) of the packages to be compiled from source.  Their package manager downloads the source and other dependencies and compiles it.

Have fun!  :)

---

### Post by tinker312 on 2006-02-28
Thanks Eleaf, 

What's the best way to view the code? Should I use Gedit, Vi, Emacs?

---

### Post by varunus on 2006-02-28
All three work; gedit is my favorite though.  Its easy, lightweight, and integrates well with GNOME.

If you'd prefer something like Visual Studio, install Anjuta.  Its a C/C++ IDE.

One way to get source code, is, if you know the name of the synaptic package, open a terminal and type:
```
apt-get source <packagename>
```

This will download all the source code, and if you do this, you can make a debian package easily from your modifications!  You can also type:
```
sudo apt-get build-dep <packagename>
```
to get everything needed to compile the package.

---

### Post by RAOF on 2006-02-28
The easiest way to get the source for an Ubuntu program is to download the source package - all of the packages are built from a source package.

To do this, you can "apt-get source *packagename*" from a terminal - this will download the source package, unpack the source into a directory (like *packagename*-*versionnumber*) and apply any Ubuntu patches to the source.

I like emacs for coding, but whatever you're comfortable with.  It only needs to be able to edit plain-text :)

---

### Post by tinker312 on 2006-02-28
Thanks all you,

This is what I was looking for. It's certainly less involved than what I was thinking :)

Yours . . . 
John

---

