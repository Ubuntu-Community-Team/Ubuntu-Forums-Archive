---
title: "Firefox (Shiretoko) doesn't remember any Passwords"
date: 2009-10-24
forum: General Help
---

### Post by t09 on 2009-10-24
since yesterday, my Firefox 3.5 (Shiretoko) does not remember any of my saved passwords anymore. I have to log in manually on every page, which is annoying. As I have entered the password, there's the usual "Do you want Shiretoko to remember the password" bar on top of the window, but when I click on "remember", nothing happens. the bar stays there. The only buttons that work and make the bar disappear, are "never for this site" and "not now".  BUT if I open the "Page Info", where it says "Have I saved any passwords for this web site", it says YES, but the login data is still not saved, obviously. If I click on "view saved passwords" , the box is empty.  - I just found out, if my Firefox says a website is "untrusted" and I want to make an exception, the window does not close as long as the "remember this exceprion" box is checked. I think this is the same problem.  ---  PS: I'm running ubuntu 9.04.

---

### Post by duanedesign on 2009-10-24
Close Firefox.

In the [terminal]("http://www.psychocats.net/ubuntu/terminal"), try the command: 

```
sudo chown -R username:username /home/username/.mozilla
```

Where username is your actual username

Start Firefox

NOTE: I have read that one cause of this problem can be running graphical apps with sudo instead of gksudo. (ex. sudo Nautilus, sudo firefox) If it opens a GUI/Window use gksudo. Text stuff that stays in the Terminal sudo. [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

If this does not work try a new Profile. A lot of FF problems are caused by corrupt profiles.

Close Firefox and open a terminal.

```
firefox -P
```

From here you can create a new profile. If this corrects your problem copy over your bookmarks and delete the old profile. Don't just copy all your folders/files over from the old account. You are likely to get the file that caused the problem in the first place. To copy over bookmarks:

Bookmarks > Organize Bookmarks > Import and Backup > Choose File

---

### Post by t09 on 2009-10-24
alright, the new profile solved the problem. [IMG]http://img41.imageshack.us/img41/8149/00000298.gif[/IMG]

big thanks! :-D

...and all of a sudden everything works fine, even in the old profile!! :P

---

### Post by vratnica on 2009-12-28
Hi there!

The same problem here, but when I type the firefox -P command in terminal, it says that firefox is not installed by me, and if I want to install it, ti type sudo apt-get install firefox-3-0

although I have already shiretoko installed, which is 3.5

If I try the same using the shiretoko name, the result is the same!

Please help!

---

### Post by t09 on 2010-04-26
> **vratnica said:**
> Hi there!

The same problem here, but when I type the firefox -P command in terminal, it says that firefox is not installed by me, and if I want to install it, ti type sudo apt-get install firefox-3-0

although I have already shiretoko installed, which is 3.5

If I try the same using the shiretoko name, the result is the same!

Please help!
if you installed shiretoko (3.5) you have to type "firefox-3.5" instead of "firefox".

---

