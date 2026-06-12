---
title: "GConf-Editor Entries"
date: 2010-06-01
forum: General Help
---

### Post by JustinR on 2010-06-01
Hey everybody, I installed Avant Window Navigator, since uninstalled it because I never used it. But now when ever I use GConf-Editor there are at least twenty unused entries by the application that I can't remove. I've searched on Google and found this thread: [http://ubuntuforums.org/showthread.php?t=538756](http://ubuntuforums.org/showthread.php?t=538756) but it method doesn't seem to work or I am not following it correctly. 

I'm sure these keys don't take up space but its un-aesthetically pleasing when I have to scroll down the window to get to the keys I want to get to!

Anybody have any ideas?

---

### Post by ankspo71 on 2010-06-01
Hi,
Look insided your /home/<user>/.gconf/apps/ folder for any sub folders called awn (or avant-window-navigator). You can delete them from there.

The .gconf folder is a hidden folder in your home directory. I believe you can unhide folders by pressing Ctrl + H in an open nautilus window. It has been a while since I have used nautilus though...

---

### Post by JustinR on 2010-06-02
> **ankspo71 said:**
> Hi,
Look insided your /home/<user>/.gconf/apps/ folder for any sub folders called awn (or avant-window-navigator). You can delete them from there.

The .gconf folder is a hidden folder in your home directory. I believe you can unhide folders by pressing Ctrl + H in an open nautilus window. It has been a while since I have used nautilus though...

Basically you just summarized the link I gave. :confused: It didn't work.

There are no folders called awn or avant-window-navigator, I looked in the %gconf.xml files to make sure an index of the keys weren't still there but most of the files are blank.

---

### Post by ankspo71 on 2010-06-02
Hi,
Check the entries in /usr/share/gconf/ too. Some applications will create system-wide configurations in there, and it might be why you see some entries for awn in the gconf-editor but not in your home folder.

---

### Post by JustinR on 2010-06-15
> **ankspo71 said:**
> Hi,
Check the entries in /usr/share/gconf/ too. Some applications will create system-wide configurations in there, and it might be why you see some entries for awn in the gconf-editor but not in your home folder.

Hi I know this thread was getting old but after doing a system wide search through the root directory "/" folders I found nothing related to AWN so i must be missing something.

I even used the Search for Files tool to search for avant and "awn" in files, folders, etc.

Any ideas?

---

### Post by dcstar on 2010-06-15
> **JustinR said:**
> Hi I know this thread was getting old but after doing a system wide search through the root directory "/" folders I found nothing related to AWN so i must be missing something.

I even used the Search for Files tool to search for avant and "awn" in files, folders, etc.

Any ideas?

The entries will be exactly in the same tree that you are supposedly seeing them in the editor.

---

### Post by JustinR on 2010-06-15
Yes I know, but there are no avant or awn files in /home/justin/.gconf or any other similar directories, I also checked system wide gconf entries like in /etc/gconf but nothing else is there either.

---

