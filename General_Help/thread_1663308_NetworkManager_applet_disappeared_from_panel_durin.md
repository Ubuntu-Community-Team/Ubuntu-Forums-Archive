---
title: "NetworkManager applet disappeared from panel during pppoeconf insatll"
date: 2011-01-09
forum: General Help
---

### Post by isee on 2011-01-09
Hi all!   I was installing pppoeconf according to this guide
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

when I rebooted, my NetworkManager applet had disappeared from my panel.  I'd really like to get it back as I am just supposed to be trying pppoeconf.  I do have wicd as a backup connection.

Ive seen commands like these
```
killall nm-system-settings
with
sudo service network-manager restart
```
or
```
killall gnome-panel
```
but I can't run code myself because I don't really know what it does, so any advice would be greatly appreciated.

I also noticed in System>Preferences>Network Connections, the DSL connections I set up through the NM applet are there, but under the "Wired" tab, there is nothing.  Isn't there supposed to be Auto eth1 or some such connection?

Seems right now if I want to use my router, my only option is a connection with wicd.

My reasons for and trials with pppoeconf are here
[http://ubuntuforums.org/showthread.php?t=1661568](http://ubuntuforums.org/showthread.php?t=1661568)

Cheers!

---

### Post by dino99 on 2011-01-09
into a terminal:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

metacity --replace &

---

### Post by isee on 2011-01-09
Sorry, that did nothing but cause a bit of problems.  First my computer flicked and then things stopped working and I got a "No Windows Manager" error of some kind.

I rebooted but then my keyboard wouldn't work, so rebooted again and it's ok it seems, but no NetworkManager applet in my panel.

---

### Post by isee on 2011-01-09
I can't find nm-applet in Synaptic.  Should I have that package in 10.04?

I have "Notification Area" on my panel already, so thats not the problem.

Uninstall and reinstall network-manager-gnome?:confused:

---

### Post by isee on 2011-01-09
Can anyone help me recover the nm-applet?

---

### Post by dineshs on 2011-01-10
Please try step-1 and step-2 in
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
and see if the icon is back

---

### Post by isee on 2011-01-10
Thanks dineshs, although I don't see that working as I have no nm-applet package in Synaptic.

Here's a couple tries in terminal to show
```
dpkg -s nm-applet
Package `nm-applet' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents
```

```
sudo apt-get install nm-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nm-applet

```

I will try your solution, although I rely on an ADSLpppoe (if thats correct) connection set up thruough pppoeconf.

---

### Post by dineshs on 2011-01-11
> I don't see that working as I have no nm-applet package in Synaptic.Dont you have *network-manager* and *network-manager-gnome*in synaptic?
> I will try your solution, although I rely on an ADSLpppoe (if thats correct) connection set up thruough pppoeconf. 
The connection (pon dsl-provider)will still work after editing /etc/network/interfaces

---

### Post by isee on 2011-01-13
> Dont you have *network-manager* and *network-manager-gnome *in synaptic?Yes  they are installed.  But is there also supposed to be an *nm-applet* (or possibly *network-manager-applet*) package installed?

Thank you for the info that the pon dsl-provider connection will be unaffected.  I will try your directions soon.

:)  Thanks!

---

### Post by isee on 2011-01-14
I checked my installation disk and there is no nm-applet package, that must be erroneous info I had.  Sorry.  The "apt-get install nm-applet" was recommended in #ubuntu IRC.

I am still removing invisible Notification Areas from my panel, I guess I added a lot of them trying to get my NetworkManager applet back that way lol.


update..... I JUST FOUND IT!  It is in my panel, its invisible though.  I was right clicking along the panel to find all the Notification Areas and the NM applet menu popped up!

I cant see it right now, but I did see enough to see it said > Network Not Managed

I can't find it again :(, but I know its there at least.

Any Ideas?

---

### Post by isee on 2011-01-14
dineshs - Thanks!  That did bring it back.  :KS

Any thoughts as to whether it was installing WICD or using pppoeconf that caused that?  I could post the lines I removed if that helps.

---

### Post by dineshs on 2011-01-14
> Any thoughts as to whether it was installing WICD or using pppoeconf that caused that?  I think it is pppoeconf.If you run pppoeconf command /etc/network/interfaces will get modified and NM will not manage your device (Ref section `d' [here]("https://help.ubuntu.com/community/NetworkManager0.7")) pon dsl-provider will still work because the details of your configuration are in /etc/ppp/peers/dsl-provider (This is my experience)

---

### Post by isee on 2011-01-15
:D

I would just like to mention that maybe the instructions on the pppoeconf page I refered to in my first post here could use a bit of editing.

First that it will affect NetworkManager like it did to me, and a link to your post to reslove the issue.

Second is the need to use the sudo prefix with pon and poff.  This stumped a noob like me for a bit.

Third is dealing with the "dip" group, and using the "adduser" command to make this smoother.

I think two and three are both covered in this link
[https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203](https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203)
and I also talked about them in my origional thread [http://ubuntuforums.org/showthread.php?t=1661568](http://ubuntuforums.org/showthread.php?t=1661568)

Also making a backup of /etc/network/interfaces as well as /etc/ppp/peers/dsl-provider would be useful information.

Again, thanks for your help!  Although a little frustrating, it was a good experience for me.

---

### Post by isee on 2011-01-15
:D

I would just like to mention that maybe the instructions on the pppoeconf page I refered to in my first post here could use a bit of editing.

First that it will affect NetworkManager like it did to me, and a link to your post to reslove the issue.

Second is the need to use the sudo prefix with pon and poff.  This stumped a noob like me for a bit.

Third is dealing with the "dip" group, and using the "adduser" command to make this smoother.

I think two and three are both covered in this link
[https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203](https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203), and I also talked about them in my origional thread [http://ubuntuforums.org/showthread.php?t=1661568](http://ubuntuforums.org/showthread.php?t=1661568)

Also making a backup of /etc/network/interfaces as well as /etc/ppp/peers/dsl-provider would be useful information.

Again, thanks for your help.  Although a little frustrating, it was a good experience for me.

---

### Post by isee on 2011-01-15
:D

I would just like to mention that maybe the instructions on the pppoeconf page I refered to in my first post here could use a bit of editing.

First that it will affect NetworkManager like it did to me, and a link to your post to reslove the issue.

Second is the need to use the sudo prefix with pon and poff.  This stumped a noob like me for a bit.

Third is dealing with the "dip" group, and using the "adduser" command to make this smoother.

I think two and three are both covered in this link
[https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203](https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203), and I also talked about them in my origional thread [http://ubuntuforums.org/showthread.php?t=1661568](http://ubuntuforums.org/showthread.php?t=1661568)

Also making a backup of /etc/network/interfaces as well as /etc/ppp/peers/dsl-provider would be useful information.

Again, thanks for your help.  Although a little frustrating, it was a good experience for me.

---

### Post by isee on 2011-01-15
:D

I would just like to mention that maybe the instructions on the pppoeconf page I refered to in my first post here could use a bit of editing.

First that it will affect NetworkManager like it did to me, and a link to your post to reslove the issue.

Second is the need to use the sudo prefix with pon and poff.  This stumped a noob like me for a bit.

Third is dealing with the "dip" group, and using the "adduser" command to make this smoother.

I think two and three are both covered in this link
[https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203](https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203), and I also talked about them in my origional thread [http://ubuntuforums.org/showthread.php?t=1661568](http://ubuntuforums.org/showthread.php?t=1661568)

Also making a backup of /etc/network/interfaces as well as /etc/ppp/peers/dsl-provider would be useful information.

Again, thanks for your help.  Although a little frustrating, it was a good experience for me.

---

### Post by isee on 2011-01-15
:D

I would just like to mention that maybe the instructions on the pppoeconf page I refered to in my first post here could use a bit of editing.

First that it will affect NetworkManager like it did to me, and a link to your post to reslove the issue.

Second is the need to use the sudo prefix with pon and poff.  This stumped a noob like me for a bit.

Third is dealing with the "dip" group and "pon", and using the "adduser" command to make this smoother.

I think two and three are both covered in this link
[https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203](https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203),
and I also talked about them in my original thread [http://ubuntuforums.org/showthread.php?t=1661568](http://ubuntuforums.org/showthread.php?t=1661568)

Also making a backup of /etc/network/interfaces as well as /etc/ppp/peers/dsl-provider would be useful information.

Again, thanks for your help.  Although a little frustrating, it was a good experience for me.

---

### Post by isee on 2011-01-15
How can I delete those multiple posts?   That was an accident.  The message wouldn't load and I kept hitting "Submit Reply", lol like my many "Notification Areas".

Sorry 'bout that.

PS Epiphany browser seems to be having a bit of an issue with these forums today.

---

### Post by dineshs on 2011-01-15
> How can I delete those multiple posts? That was an accident. The message wouldn't load and I kept hitting "Submit Reply", lol like my many "Notification Areas".You may click report post -the exclamation mark-below your avatar and proceed.There was some problem with ubuntuforums website

---

