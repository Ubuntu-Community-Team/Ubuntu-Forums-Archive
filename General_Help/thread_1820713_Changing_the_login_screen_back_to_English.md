---
title: "Changing the login screen back to English"
date: 2011-08-08
forum: General Help
---

### Post by ilantal on 2011-08-08
This should be an easy question but I can't seem to find the answer. I am using Unity in 11.04 and while playing around to make the menus display in Hebrew, I somehow changed the login screen to display Hebrew as well.
It is very convenient that at login time I can determine whether the menus will be in Hebrew or English, but I would like to transfer back to the login screen itself being in English.

This I can't seem to be able to do. If I got it to switch from English to Hebrew I should be able to get it to switch back, but how?

Thanks,
Ilan

---

### Post by blueridgedog on 2011-08-08
You could try and reinstall the gnome log in package:

```
sudo aptitude reinstall --purge gdm
```

Or reconfigure your language:

```
sudo dpkg-reconfigure locales
```

---

### Post by grahammechanical on 2011-08-08
At the login screen when you click your user name you get three menus in the bottom panel. The middle menu lets you set the language. Are you saying that this does not work for you?

Regards.

---

### Post by ilantal on 2011-08-09
Thanks for the replies. I didn't have aptitude installed, so I installed it and did the sudo. No change. Likewise, no change for the reconfigure locales.

There are 3 boxes on the bottom of the login screen. One for keyboard which is set at USA. The second for the menu language which I can conveniently set as either English or Hebrew. Hebrew is written with Hebrew characters. The third is the system to be used. It can be Recovery, Unity-2D, Ubuntu (written in Hebrew), Ubuntu Classic (again written in Hebrew). All this works like a charm and I can have everything in either Hebrew or English.

The problem is what I think I remember: I think I remember that I somehow changed the login screen so that it would appear in Hebrew. If I go to the Login Screen on the Control Center, it doesn't give me any option to change it back, so apparently I changed something else, but I can't remember what.

It is no big deal that the login screen is in Hebrew, but I remember it used to be in English and in Linux I have control over everything. So why can't I get the control back and have the login in English? It should be possible.

Ilan

---

### Post by ilantal on 2011-08-24
I finally got the login screen back to English. I will document it in case it helps someone else. I did a couple of things and I'm not sure which of them did the trick.
First I went into Language Support, highlighted English and pressed Apply System-Wide. Then I went into Keyboard Preferences, Layout, again highlighted English and hit Apply System-Wide.
After a reboot my login screen was back in English.

Presumably I could change it back to Hebrew by doing the same thing and choosing Hebrew in place of English.

Thanks for the help I received,
Ilan

---

