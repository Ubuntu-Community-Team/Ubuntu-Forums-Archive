---
title: "Update last night has caused many problems"
date: 2009-09-14
forum: General Help
---

### Post by scratman on 2009-09-14
OK, so I am running the Alpha for 9.10, and everything was pretty much peachy for me up until now.  I got back from a weekend holiday last night, checked my mails, and then did a system update.  Gotta restart my PC, so I let it do its' thing, and get that sick feeling in the pit of my stomach.

First of all, my PC wouldn't restart properly.  Shutdown was fine, but when it boots up it just hangs at the hardware initialisation screen before Ubuntu actually begins to load.  Was like this for about 15 minutes while I made coffee and milled around waiting.  So I turned the machine off for a few minutes and then booted it from cold.  This time goes better, but the machine hangs just before I get to the login screen.

I managed to get some help from the forums, which involved editing Xorg.conf using sudo touch and changing nvidia to nv from my Kubuntu partition!

So now I have managed to get back into my Ubuntu system, but there are still problems.  Nautilus doesn't work.  No desktop icons, cannot access anything in the Places menu, Deleted Items folder will not open.  I've installed Thunar, and that seems to be working OK at the moment, but I'd prefer to have Nautilus back.  Additionally, I cannot use VLC, Totem, or Xine to play media.

Does anybody have any advice or require further information?

Thanks in advance.

---

### Post by lovinglinux on 2009-09-14
> **scratman said:**
> Does anybody have any advice or require further information

Don't use Alpha versions on a production environment. They break, as it did.

---

### Post by sdowney717 on 2009-09-14
try making a new user and log into it.

---

### Post by earthpigg on 2009-09-14
> **scratman said:**
> 
So now I have managed to get back into my Ubuntu system, but there are still problems.  Nautilus doesn't work.  No desktop icons, cannot access anything in the Places menu, Deleted Items folder will not open.  I've installed Thunar, and that seems to be working OK at the moment, but I'd prefer to have Nautilus back.  Additionally, I cannot use VLC, Totem, or Xine to play media.

Does anybody have any advice or require further information?

start deleting dotfiles in your home folder for specific apps that are giving you trouble so they default to the default settings. log out/back in or quit/start the program in question for changes to take effect.

sdowney717's solution is very similar: a new user will come with blank/default dotfiles.


(any file/folder in your home folder starting with a dot is a dotfile. it contains configuration and setting information for some program or another, usually hinted at by the file name.)

---

