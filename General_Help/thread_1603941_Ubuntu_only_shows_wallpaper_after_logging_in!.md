---
title: "Ubuntu only shows wallpaper after logging in!"
date: 2010-10-23
forum: General Help
---

### Post by Reokie on 2010-10-23
Hello, my first install was 10.04, and everything was working fine. Only last night, and this morning, when I tried logging into Ubuntu, I entered my username, password, but after it accepted it, it only showed my cursor and the login wallpaper. Sometimes it gets to my desktop wallpaper, but shows nothing else. I have a dual-boot with Vista, if that helps at all.

---

### Post by yetiman64 on 2010-10-23
When that happens here I use a tty terminal (CTRL + ALT + F2, can be any function key F1 to F6). Enter username then password, then type,
```
sudo service gdm restart
``` and press enter, you will be prompted for your password again.

The login screen comes back up after a few seconds, login as normal.

If you get a full desktop back, go back into the same tty terminal (you will still be logged into it) and type,
```
exit
```and press enter.

When the tty login comes back up use CTRL + ALT + F7 to return to your desktop.

Hope this helps if it happens again, you can practice it on a normal desktop but any programs running (eg. firefox) before using it will be shut down on your return.

Edit: I don't think it is related to dual booting or Vista as such, seems more related to gdm (the Graphical Display Manager)

---

### Post by Unknowndetective on 2011-07-19
I am having the same proble, I did the above mentioned but right after I put in "sudo service gdm restart" it puts me back to the login screen and I try signing in and all the comes up still in my mouse cursor and the main wallpaper. 

This happened after I finally updated my system on my Netbook Remix version of Ubuntu.

Any help would be great.

---

### Post by mikejonesey on 2011-07-19
you can enable and disable the background image in the gconf-editor
```
gconf-editor
```
/apps/gdm/simple-greeter/settings-manager-plugins/background

---

### Post by silvavlis on 2011-09-22
I have the same problem and mine is no upgrade, but a new installation of Natty :confused:

yetiman64's solution should work (will try it again next time this issue reappears), but a permanent solution should be found...

---

### Post by silvavlis on 2011-09-22
mikejonesey, I think that you didn't understand Reokie's problem...

But anyway thanks for trying to help! That's always welcomed :-)

---

