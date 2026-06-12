---
title: "How do I change the theme of superuser windows?"
date: 2010-04-26
forum: General Help
---

### Post by mjpatey on 2010-04-26
Hi, group-

I get tired of the ugly default GNOME theme that rears its head when I'm doing something as superuser.  I understand why it's desirable for these windows with elevated privileges to look different, but I'd like to choose a different theme.

So... what terminal command do I run to bring up the Appearance window?  My thought is if I simply run it with "sudo", any changes made would affect the appearance of future elevated-privilege windows.  Does that sound right, or am I out in left field?

Thanks for any insight you can provide!

-Mark

---

### Post by aysiu on 2010-04-26
It would be *gksudo*, not *sudo*

---

### Post by mjpatey on 2010-04-26
Ah, thanks, aysiu.  gksudo followed by what command to invoke the Appearance window?

edit:  sorry, I didn't really make it clear in my question that I have no idea what the command to invoke Appearance is!

---

### Post by Bachstelze on 2010-04-26
Just copy your GTK preferences file into root's home directory:

```
sudo cp ~/.gtk* /root
```

Then the apps you will run as root will use the same GTK theme as your user apps. Also, you can use [font=monospace]gtk-chtheme[/font] to easily change the GTK theme for a given user.

---

### Post by mjpatey on 2010-04-26
Bachstelze, thank you!  "gtk-chtheme" did the trick nicely.  :-)

---

### Post by aysiu on 2010-04-26
If you want to change the theme of root ```
gksudo gnome-appearance-properties
``` If you want the theme of root to match the theme of user ```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

### Post by thilina on 2011-01-22
Nowadays you don't even have to touch any configuration file. Just install Ubuntu tweak and you can easily do the task using a single click. For more information visit this link.

[http://alldtechstuff.blogspot.com/2011/01/change-theme-of-root-user-easily-in.html](http://alldtechstuff.blogspot.com/2011/01/change-theme-of-root-user-easily-in.html)

---

### Post by GreginSJ on 2011-05-05
You all seem to be able to work in Gnome with SuperUser status, how so?  I log in upon boot up as Administrator, but I still can't copy or move files between folders, or modify files because of lack of "permissions/privileges".  For example, let's say I have a file called host.conf which I double click to open in gedit.  Unfortunately, it opens as a Read-Only file.  So, I have to open a terminal window and issue a gksudo cmd:  $ gksudo gedit /etc/host.conf which allows me to modify the file and save it.  How can I modify that file without issuing a gksudo command from the terminal?  Thx.

---

### Post by jerome1232 on 2011-05-05
I don't personally use this but it looks valid enough, I recall hearing similar things in similar threads at least.

It was the first result on google btw

[http://maketecheasier.com/ubuntu-easy-and-quick-ways-to-open-any-files-as-root/2008/02/19](http://maketecheasier.com/ubuntu-easy-and-quick-ways-to-open-any-files-as-root/2008/02/19)

---

### Post by dinostabOMG on 2011-05-17
whoops

---

