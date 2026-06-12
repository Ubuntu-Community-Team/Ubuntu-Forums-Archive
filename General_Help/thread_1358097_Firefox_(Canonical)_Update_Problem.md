---
title: "Firefox (Canonical) Update Problem"
date: 2009-12-18
forum: General Help
---

### Post by snorkytheweasel on 2009-12-18
Karmic on eeepc

Update Manager ran & installed various updates. All seems OK except FireFox 3.5.5 (Canonical 1.0).

FireFox now displays a ribbon across the window:
"Your browser has been updated and needs to restart" and has a restart button.

Restarting FireFox does not make the ribbon go away. Neither does rebooting Ubuntu.

I'd use one of the package managers, but they won't run an update on FireFox because they think the latest version is installed.

I'd like to have the latest appropriate version of FireFox. More importantly, I'd like to have that pesky ribbon go away.

How do I fix or update (if needed) FireFox 3.5.5 on Karmic Koala?

---

### Post by scouser73 on 2009-12-18
[[COLOR="Red"]**Download Firefox 3.5.6**[/COLOR]]("http://www.mozilla-europe.org/en/firefox/")

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

Enter these commands in Terminal

> sudo -i
Enter your password if asked
> cd /opt
> chown -R username firefox
[COLOR="Red"]**The username is your name**[/COLOR]

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have Firefox installed.

---

