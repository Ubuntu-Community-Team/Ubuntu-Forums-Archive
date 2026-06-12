---
title: "No GUI"
date: 2012-03-08
forum: General Help
---

### Post by Parzi on 2012-03-08
Hello

What if I want Ubuntu completely without graphical user interface just command line/text based UI?. What should I do to modify my Ubuntu.  Or is there any Linux distro that comes only with textual UI?

---

### Post by kyphi on 2012-03-08
[http://inx.maincontent.net/](http://inx.maincontent.net/)

---

### Post by papibe on 2012-03-08
You have a couple of alternatives within the Ubuntu family:

- [Ubuntu server]("http://www.ubuntu.com/download/server/download").
- [Ubuntu minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") with command line option.

Hope that helps.
Regards.

---

### Post by Immolatus on 2012-03-08
you can remove GDM, Gnome, and Xorg. or just removing X would stop all gui. However all Ubuntu distro's (except server)come with a desktop so I would say.....do an install of the current Debian (if you prefer .deb)release and don't install the graphical or UI packages.
Even simpler solution just install Arch, it doesn't come with much of anything by default. the image is only about 340MB and it's very fast. Also the documentation wiki is the best I've seen.

---

### Post by Parzi on 2012-03-09
Thanks for advice. 

Is there any way to start ubuntu in command line only mode without removing my GUI?

---

### Post by papibe on 2012-03-09
For one time only, you can choose 'recovery mode' on the grub menu, and then select 'boot normaly' on the next menu options.

For a more permanent solution check post#2 on this [thread]("http://ubuntuforums.org/showthread.php?t=1812935&highlight=text+mode").

Regards.

---

### Post by Cheesemill on 2012-03-09
> **papibe said:**
> You have a couple of alternatives within the Ubuntu family:

- [Ubuntu server]("http://www.ubuntu.com/download/server/download").
- [Ubuntu minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") with command line option.

Hope that helps.
Regards.

Or use the alternate CD and select 'Install a CLI system'

---

### Post by Zill on 2012-03-09
> **Parzi said:**
> Thanks for advice. 

Is there any way to start ubuntu in command line only mode without removing my GUI?
How about Ctrl-Alt-F1 at the login screen to open a virtual terminal?
(Ctrl-Alt-F7 will get you back to the GUI)

---

