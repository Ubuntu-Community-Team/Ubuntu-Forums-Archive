---
title: "A few configuration questions from RH user"
date: 2009-09-22
forum: General Help
---

### Post by FunkyRes on 2009-09-22
For the desktop, Ubuntu has won me over.
I have been using CentOS for quite some time and Fedora before that.

The main thing I like is the ease of getting both kino and cinelerra going, I've never done multimedia production before, the only pre-packaged kino I could find for CentOS worked for everything BUT dv import over FireWire, it would crash every time. Ubuntu it works just peachy.

However there are a couple things that I haven't figured out:

A) Is it possible to have switch user applet *and* shutdown in the System menu? It seems the only way to get Shutdown in the System menu is to delete the switch user applet. I'm wondering if there's a configuration somewhere that lets me do both.

B) With the nautilus-open-terminal package in Jaunty, right clicking on the Desktop opens a terminal in the Desktop. In CentOS - it opens in the home directory, unless you right click in a nautilus window. I prefer the CentOS behavior, as usually when I open a terminal I want to be in my home directory. Is there a configuration to give me the CentOS behavior?

C) Since my various user accounts both at home and on my remote server are RH/CentOS in origin, the UID/GID starts at 500. That was an easy change, but I already found that I needed to change the gdm greeter preference for minimum UID to allow automatic login. Are there any other configurations in particular I need to look at? I'm not running dovecot or an ssh server, I'm only running Ubuntu on a strictly desktop machine, so minimum UID/GID for servers isn't an issue. I'm just wondering if there are any issues with other pieces.

D) RH uses a PAM module for the console user. The power of this is I can set up rules to make the serial port my GPS device cable is plugged into and the FireWire port owned by the console user. What is the Ubuntu way of doing that? I really do not want to add various users I and family/friends use to the groups that ordinarily own those device nodes.

Thanks for suggestions.

---

### Post by P4man on 2009-09-22
> **FunkyRes said:**
> 

B) With the nautilus-open-terminal package in Jaunty, right clicking on the Desktop opens a terminal in the Desktop. In CentOS - it opens in the home directory, unless you right click in a nautilus window. I prefer the CentOS behavior, as usually when I open a terminal I want to be in my home directory. Is there a configuration to give me the CentOS behavior?


Open gconf-editor. Browse to apps>nautilus-open-terminal, enable 'desktop_opens_home_dir". Thanks for that question, I never knew it was possible :)

Not sure about the other questions.

---

### Post by FunkyRes on 2009-09-22
Thanks! That solved the terminal issue :)

---

### Post by wojox on 2009-09-22
On my Jaunty I go into System and my bottom two option are Log Out and Shut Down. When I choose Log Out if gives me the option to Switch User.

---

### Post by FunkyRes on 2009-09-22
> **wojox said:**
> On my Jaunty I go into System and my bottom two option are Log Out and Shut Down. When I choose Log Out if gives me the option to Switch User.

OK - so apparently I'm not very observant.
I removed switch user and looked and indeed, it is in the menu option.

---

