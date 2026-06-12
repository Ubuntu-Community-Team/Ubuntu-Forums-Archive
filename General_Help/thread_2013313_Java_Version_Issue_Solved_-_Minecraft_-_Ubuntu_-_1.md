---
title: "Java Version Issue Solved - Minecraft - Ubuntu - 10.04 LTS"
date: 2012-06-30
forum: General Help
---

### Post by Olyander on 2012-06-30
If you have experienced this issue, here is the fix.

Upgrading to new Oracle Java JRE 1.7.X breaks Minecraft on a 64 bit arch system - In my case a laptop.

This is a simple fix.

Simply do not upgrade to 1.7.X any of them, it doesn't work.

If you already did, here is how to make Minecraft work again with JRE

Howto:

1. If using Firefox 10 or better on 64 bit arch, download JRE 1.6 jre1.6.0_27 where you can find it. this site here only allows current version 1.7.X:  [http://www.java.com/en/download/linux_manual.jsp?locale=en](http://www.java.com/en/download/linux_manual.jsp?locale=en)
You DO NOT WANT that version. I usually keep a copy of my java versions, so I reinstalled it like this.

2. reinstall older JRE 1.6.X:

a. remove links:
sudo rm -rf /usr/bin/java*

b. remove mozilla plugin links:
rm -rf /home/usernamehere/.mozilla/plugins/libnpjp2.so

c. copy older JRE 1.6.X to new location or in same place 1.7.X lives. my system I made dir in /usr/lib/jre
sudo mkdir /usr/lib/jre
sudo cp -Rp /home/usernamehere/Downloads/jre1.6.0_27 /usr/lib/jre/

d. make new links:
cd /home/usernamehere/.mozilla/plugins
ln -s /usr/lib/jre/jre1.6.0_27/lib/amd64/libnpjp2.so ./

e. make new links to java*
cd /usr/bin
sudo ln -s /usr/lib/jre/jre1.6.0_27/bin/java* ./

3. restart browser:
type in url: 
about:plugins
do a search - cntrl-f 
type in java, you will see java Java(TM) Plug-in 1.6.X is loaded

4. goto [http://javatester.org/version.html](http://javatester.org/version.html)
if you see pink rectangle and version you are a GO!

5. goto minecraft.net, bottom right, select, single player.
Enjoy your game. It should work! unless of course you had java disabled all this time in Firefox settings, in that case, enable.

Moral of the story?
Sites that offer games should have in big bold links, what it requires, for this example, Java Versions that work! or that they have upgraded too, and definetly "Howtos" like this one to make life simple again for all intended audience/perspective users.

Njoy, Oly
6-30-2012
9:50am PacTime

---

### Post by efflandt on 2012-06-30
No need to use real Java that you have to jump through hoops to install.

You can simply use **openjdk-6-jre** (Openjdk 6 Runtime) using software center or synaptic.  That definitely works for minecraft in 64-bit Ubuntu 10.10 through 12.04.  It should work in 10.04 too, but I have no way to test that.

Note: I am using **lwjgl 2.6** because the 2.4.2 that came with minecraft occasionally resulted in stuck movement keys.  Updating lwjgl requires replacing files in .minecraft/bin/ and .minecraft/bin/natives/ with similarly named files from a zip file.  Haven't tried newer lwjgl versions.

---

### Post by Olyander on 2012-07-09
the reason for this post is, it is NOT common knowledge that upgrading your java-whatever will still work. most if not all n00bs simply press update when the update window pops up. i usually don't do it, but i did, thus the ultimate reason for the post. those of us who have run into this, know now, but my other point was, sites that sport games, should also make us aware NOT to update/upgrade as certainly, as in this case, and many other progams based on java that run off the web are going to break.

simply pressing update is NOT the way to go. most of us know this already, after using linux/unix for sometime, those that don't are going to spend a lot of wasted time.

anyfoo, hope this post helps someone, and remember, do NOT update/upgrade just becuz the popup says too. actually turn that auto update OFF and read through stuff, and pin out those things you know/think will break what you installed from source or other ./configure means. fair warning...

---

