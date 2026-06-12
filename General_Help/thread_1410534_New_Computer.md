---
title: "New Computer"
date: 2010-02-18
forum: General Help
---

### Post by Potatochipz on 2010-02-18
Hey, so today I purchased a dell mini 9 off of someone, and so far am enjoying it but have some questions.  I created my own account so that i could delete off his main account, but when i created my account and log on it looks like one of those netbook ubuntu screens, while his looks more like a desktop.  I am trying to find out how to get it to be similar to that, also after doing some searching to try to factory reset i found that its not really an option so i am thinking about reinstalling, does anyone have an easy to follow install using a USB or SD card, i checked the one on the ubuntu home site and it gets a bit confusing, if not ill just suck it up and try to work through it.  Also any tips for using a ubuntu netbook?

Thanks in advance guys!

---

### Post by litemirrors on 2010-02-18
I have an eeebox b202 and initially tried the netbook remix of ubuntu, while it works fine the remix interface was annoying after awhile and I soon realized that the drivers for it seemed included in the main distro now. The only difference that I could see was the remix interface. Maybe someone can confirm that but.........

Install the main Ubuntu distro then get Gnome Art Manager and download the new themes. Try the Live CD first to make sure the system doesn't need any additional drivers downloaded which would be a pain in the ***.

Other than that you can also head to Gnome Look and download new icon packages or themes, it was confusing for me at first but I found out how to do it so post here if you need help.

There are actually 3 main accounts on a Ubuntu install from what I can tell. During install you make a user, but there is also root and one called gdm

gdm = the login theme

gksu -u gdm dbus-launch gnome-appearance-properties

root = anytime you access the root account through terminal the theme will be the ubuntu default unless you change the roots appearance

sudo gnome-appearance-properties

gnome-appearance-properties allows you to change the user theme you are logged in on.

Basically you'd just install 3 themes to each account if you wanted each account to be themed the same way, la la la

In a perfect world you would only need to run sudo nautilus then copy the themes to the root account, but it seems that unless you import the themes through appearance manager it can't detect them!

anyway bye

---

### Post by marshmallow1304 on 2010-02-18
Here's some documentation for installing from USB: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
I hope it's not the same one you thought was confusing.


It seems that you are running Ubuntu Netbook Remix (UNR) but you want to run regular Ubuntu.  If you want to keep the remix but use the regular desktop, there's a tool called Switch Desktop Mode in Preferences that allows you to switch back and forth between the UNR desktop and the regular one.

If you do not want to keep the UNR environment, you can install regular Ubuntu as per the link above.

---

