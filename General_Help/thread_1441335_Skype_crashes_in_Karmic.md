---
title: "Skype crashes in Karmic"
date: 2010-03-28
forum: General Help
---

### Post by slowtrain on 2010-03-28
Ok, so my really old version of Skype started getting sound problems.  I went ahead and installed Skype from the company download site using the package: skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb .  I'm on an amd64 system.  Problem is that every time I tried to make a call w/ that, Skype dies suddenly (crashes).  The error I get is:

Desktop$ /usr/bin/skype: symbol lookup error: /usr/bin/skype: undefined symbol: _ZN10QBoxLayout13addSpacerItemEP11QSpacerItem

I've seen that discussed on one bboard as a problem due to Skype needing exactly Qt 4.4.0, but the latest version of Karmic has something more advanced.

I've also seen various solutions online, including going back to an earlier version of Skype (the company website no longer seems to have earlier versions), turning off automatic mixer level adjustments in Skype (doesn't work for me), etc.  The one thing that did work is downloading and running Static Skype form the company (it's on the download page for Linux), which I gather doesn't depend on Ubuntu libraries.  

This solution is a bit messy because it's not very integrated with Ubuntu and won't automatically upgrade.  Then again, it doesn't seem like the community documentation, which recommends putting Skype in your repositories is much of a solution--the Skype company website no longer seems to maintain a repository, so this doesn't work.  If anyone has a solution to the debian package install problem (software crashes) or the repository problem, I'm all ears.

I hope thie helps someone.

---

### Post by Kubunteando on 2010-03-29
I upgraded (using the Ubuntu repositories) Karmic to KDE 4.4.1 which uses libqt 4.6.x and skype works flawlessly. KDE works flawlessly even with the ATI proprietary drivers. Not a single crash in almost 1 month using the computer everyday.

That can be a solution to consider.

---

### Post by dr_psikick on 2010-04-02
Skype is crashing for me too.

I&#7743; using the last version of Skype and Karmic.

When starting skype from the console the only message that appears upon the crash is: Aborted

Some help would be appreciated. Thanks.

---

### Post by melcior on 2010-04-03
Skype and PulseAudio made my CPU to 200%. I need to kill yhe process using process manager . This is a transient situation, randomly I'm in a talk and the computer slows and slows. The only way to recover is killin skype and pulse audio and restart agai skype.
Some suggestions?

---

