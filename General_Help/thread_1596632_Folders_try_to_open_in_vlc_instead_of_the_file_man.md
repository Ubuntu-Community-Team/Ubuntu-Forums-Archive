---
title: "Folders try to open in vlc instead of the file manager"
date: 2010-10-14
forum: General Help
---

### Post by mr_cactus on 2010-10-14
I'm experiencing a fun issue with my install of the Maverick netbook remix.  Everything was working fine until last night.  

Now, when I click on the Files and Folders launcher, select any of the favorite folders at the bottom, and then click on the folder icon in the upper right, it tries to open that folder in vlc instead of the file manager, which is how it used to open.

If I uninstall vlc, it goes back to opening the folder in the file manager.  However, if I reinstall vlc, the issue reappears immediately.  

If anyone could help me with this frustration, it would be much appreciated.


If it's any help, I followed the oldish instructions [here]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html") for installing video codecs and believe they might be involved because the issue started around the same time.

---

### Post by mr_cactus on 2010-10-14
I hate to "bump" my own thread, but if anyone has any insight into what I could do to resolve this, I'd be really appreciative.  I don't want to have to fix this by reinstalling.

---

### Post by dantakeoff on 2010-10-14
try deleting the .vlc folder in your home folder after removing vlc, if its there, otherwise try completely removing every trace of vlc before reinstalling it:

sudo apt-get remove vlc --purge
rm -fr ~/.vlc
sudo apt-get install vlc

also, try right-clicking the folder/file, select "open with other application' and select the file manager...

---

### Post by mr_cactus on 2010-10-14
No dice.  Thanks for the suggestion though!

---

### Post by plucky on 2010-10-14
Did you try 

> also, try right-clicking the folder/file, select "open with other application' and select the file manager... 

From a terminal use ```
nautilus
``` and follow the above on any folder.

Good Luck

---

### Post by dantakeoff on 2010-10-14
theres got to be a solution...unfortunately i cant think of it... but with the medibuntu codecs, mplayer cant be beat...just a thought.

---

### Post by endotherm on 2010-10-14
i believe the answer you seek is here:
[http://ubuntuforums.org/showthread.php?t=1151325](http://ubuntuforums.org/showthread.php?t=1151325)

the thread is old, but the fixes on the last few pages are more appropriate for newer ubuntu releases

---

### Post by mr_cactus on 2010-10-14
Thanks everyone for all the help.  I believe I have it fixed now.  I found the solution [here]("http://www.ubuntugeek.com/how-to-change-back-nautilus-as-your-default-file-manager.html").

As expected, somehow vlc was set as my default file manager.  I needed to set it back to nautilus.  

To do that, I did this(verbose instructions in case others need them):
1.  Open a terminal
2.  *sudo apt-get install systemsettings*
3.  *systemsettings*
4.  That opens the System Settings window.
5.  Double click on *Default Applications*.
6.  Click on *File Manager*.
7.  Here it showed VLC was the default.  I clicked the button in front of *Other* and clicked the ... box at the end of the option.
8.  This brought up the *Edit File Type* window.  I clicked the *Add* button in the bottom half of the window.
9.  This brought up the *Choose Application* window.  I typed *nautilus* in the text box and clicked *OK*, closing the window.
10. In the *Edit File Type* window I removed vlc from the list and clicked *Apply* then *OK*
11. I then closed System Settings and everything seemed to work great from there on out.

---

### Post by dantakeoff on 2010-10-14
how did vlc become the default file manager to begin with?

---

### Post by mr_cactus on 2010-10-14
> **dantakeoff said:**
> how did vlc become the default file manager to begin with?

No clue

---

### Post by endotherm on 2010-10-14
usually this happens when the user right clicks a folder and selects "open with another application". the "Remember this application for Folder files" box is checked by default, so if the user is not careful, it sets the opening app as the primary in your 
~/.local/share/applications/mimeapps.list file. you can test if this is the case with this command:
```

cat ~/.local/share/applications/mimeapps.list | grep vlc

```
if you get any output, then VLC has been added as default handler for some mimetype.

---

