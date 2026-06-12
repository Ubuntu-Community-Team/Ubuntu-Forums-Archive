---
title: "5 Minutes in and I've already Got Problems"
date: 2010-07-24
forum: General Help
---

### Post by jheddin on 2010-07-24
Hi!

As the thread title says (but not really), a friend got me to install ubuntu a while ago, and I thought it was a good idea, so I did it. I couldn't get my internet connection to go, so I asked him for help, he told me to do some update or other (I've forgotten by now, and he's since disappeared), and then I rebooted.

Ta-da, I got hit with the GNOME Power Management error that seems so common, and keeping me from logging in. I was busy so I just ignored it and booted back to windows 7 for a month, and now I've got some less busy time to try and fix it with.

I've looked through a bunch of threads, and nothing suggested in them seems to work.
I've tried:

sudo dpkg --configure -a
sudo apt-get clean
chmod 0777 /tmp
mkdir /var/lib/gconf/default
sudo apt-get --reinstall install ubuntu-desktop
sudo apt-get install --reinstall gnome-power-manager
and
sudo apt-get remove gnome-power-manager --purge followed by sudo apt-get install gnome-power-manager

So far, I either get a denial of access, which is weird, since my account is the only one and I've had to login to use the commands (with ctrl+alt+f1, in case there's some other way I don't know about yet and that's important to something), and I would assume being the only user would give me permissions, or the command seems to go through fine, but it doesn't DO anything, at least, not for my problem.

Help a newb out? :(:(

---

### Post by jynyl on 2010-07-24
Hi.  Welcome to Linux.  It's a little different to Windows.

It would help if you can be a little more specific with what is happening at your end.  For example, what version of Ubuntu are you using, what hardware is it running on (PC, laptop, netbook, ??), what did you do and precisely what error message did you get.

HTH

Peter

---

### Post by Excizted on 2010-07-24
You  should have permissions if you run a command through sudo.

I don't really understand whats happening, and since you've never really gotten to use your system, I suggest just reinstalling Ubuntu.

---

### Post by mikewhatever on 2010-07-24
Wow, what a mess of a post, all I got from it is that a month is, somehow, equals 5 minutes. Can you explain exactly what's the problem. If you see errors, post them (screenshot, copy/paste).

---

### Post by Rasa1111 on 2010-07-24
yeah, just (re)install the new version (10.04), and see if your probs dont vanish.

---

