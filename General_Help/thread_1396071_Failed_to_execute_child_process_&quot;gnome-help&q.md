---
title: "Failed to execute child process &quot;gnome-help&quot; (No such file or directory)"
date: 2010-02-01
forum: General Help
---

### Post by WildcatRay on 2010-02-01
Failed to execute child process "gnome-help" (No such file or directory)

I get this error when clicking on the Help button in, for example, the preferences dialog box like for the Time and Date panel.

I cannot find anything in the Synaptic Pkg. Mgr. or Ubuntu Software Center that indicates "gnome-help". What do I need to do to fix/install whatever is needed so that I will have the related help information/pages? Thanks.

Ubuntu 9.10 Karmic Koala

---

### Post by gadolinio on 2010-02-01
I've found no package called gnome-help. And as the prompt says that a file or directory is missing, i searched for some file called that way, and only found a link called "gnome-help" in /usr/bin. It links yo an execulable called "yelp", in that same folder, i think (at least there's a "yelp" there, and both files open the help window). Maybe if you create such a link in /usr/bin, it will work again...
Hope you find this useful

---

### Post by WildcatRay on 2010-02-02
I did some more searching and then went to the Gnome Library. I find that I do not have "Help" in my System menu. Shouldn't I have that there? Should it have been installed when I first installed Ubuntu? How could I have unintentionally uninstalled or deleted it? Besides redoing my installation, is there a way to reinstall it? If so, where do I find the instructions to do this?

---

### Post by WildcatRay on 2010-02-08
I just went ahead and reinstalled Karmic since no one else posted their thoughts and ideas on why "gnome-help" was missing.

---

### Post by tekCowboy on 2012-04-16
I had removed the firefox web browser, and other browsers and re-installed them.  Then I started receiving this error message.

I checked in the software update, searching for "gnome-help," found that "Help" was not installed, and re-installed the Help application.

Fixed it for me.

---

