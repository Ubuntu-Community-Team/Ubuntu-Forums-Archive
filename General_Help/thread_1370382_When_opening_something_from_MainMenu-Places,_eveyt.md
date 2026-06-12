---
title: "When opening something from MainMenu-Places, eveything opens with PCMAN. Why??"
date: 2010-01-02
forum: General Help
---

### Post by Svens on 2010-01-02
[SIZE="2"]Hi everybody!
My problem is a little bit strange. My default file manager is Nautilus. As example - if I open any folder that is on my desktop, it is opened with Nautilus. I like that. But, when I go to Main Menu - Places, then every folder, that is there, is opened with PCMAN FM. I don't like PCMAN. It does'nt even know which program to use for opening audio or picture files by default (I know it is fixable, but I still don't like PCMAN).
So - How can I change the file manager, that is working in Main Menu - Places?
This problem occurred suddenly, don't know if it was my fault.[/SIZE]

[SIZE="1"]BTW - I have not got ANY updates from Update Manager for like a week or more now. Is it OK? Is it because of Christmas and New Year, and developers are getting some rest? :) If I choose karmic-proposed updates, then Update manager shows me some possible updates, but I want only stable updates, and I have not got them for like 10 days. I just want to know, if it is OK, or there is something messed up with my Ubuntu.[/SIZE]

I am using Ubuntu 9.10.

Happy New Year for You all!!!

---

### Post by Svens on 2010-01-02
I found a thread in this forum, where someone has a similiar problem, and someone recomended to do the reverse thing of getting PCMAN to do all this stuff. The link for making PCMAN be default file manager is: [http://www.ubuntugeek.com/how-to-replace-nautilus-with-pcman-file-manager-in-ubuntu.html](http://www.ubuntugeek.com/how-to-replace-nautilus-with-pcman-file-manager-in-ubuntu.html)
And it is said there, that to make it default, you need to edit two files from /usr/share/applications, and the files are:
nautilus-folder-handler.desktop
and
nautilus-computed.desktop.

And in these files you need to edit lines which start with "exec", and make those lines continue with a word "pcman". So in my case, I would have to edit those lines FROM "pcman" TO "nautilus", BUT they allready look like that!
Exec line in nautilus-computer.desktop is:
**Exec=nautilus --no-desktop computer:**
Exec line in nautilus-folder-handler.desktop is:
**Exec=nautilus --no-desktop %U**

And there is no appearance of a word "pcman" in those files at all!

The problem still exists. :(

---

### Post by prshah on 2010-01-02
> **Svens said:**
> But, when I go to Main Menu - Places, then every folder, that is there, is opened with PCMAN FM.

Please see [Re: Top Panel folders opens with VLC]("http://ubuntuforums.org/showpost.php?p=6082327&postcount=2") for a possible solution.

---

### Post by Svens on 2010-01-02
Thank You for Your answer!
Unfortunately it did not solve my problem. Everything in there is set to open with "File manager" (nautilus) allready. And still - when I try to open any folder in places (except "Computer" or "Network"), it is opened with PCMAN.

---

### Post by Svens on 2010-01-02
Yes! I think I found a sollution!
I went to "Computer", then right-clicked "File-System", choosed "Properties", and in section "Open With" choosed "File Manager" (Yes, there was "PCMAN" there instead!)
Thank you, prshah! You helped a lot! :KS

---

### Post by michael.conner on 2010-02-11
Thanks -- I tried out LXDE last night and it was using PCMan instead of Nautilus in Gnome sessions, too. Very annoying.

---

