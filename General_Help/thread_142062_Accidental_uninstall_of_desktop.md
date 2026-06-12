---
title: "Accidental uninstall of desktop"
date: 2006-03-09
forum: General Help
---

### Post by 4deck on 2006-03-09
I had been having some problems with playing video from DVD and as such attempted to unstall any and all multimedia apps I had (using Adept to uninstall).  Everything was going fine until Adept hung up--I did a hard reboot and now cant seem to get back to the desktop.  I can get to the command prompt and I know my hard disk is in order but I don't know how to repair the desktop from there.  What can I do?

Before the reboot--but after the adept unstall was finished everything worked normally, then I rebooted and now nothing.  Please help!!!!

---

### Post by Aine on 2006-03-09
Welcome to the forums ;).

What error are you getting?

Does it go to a black screen and say something about tmp lock or does it go to a blue screen with garbled text telling you an error and making you press enter?

---

### Post by 4deck on 2006-03-09
I dont actually get an error, the pc just logs prompts for my UBUNTU username and password, and logs me into an ubuntu prompt.  I used to boot directly to the KDE desktop.  I can't actually find the desktop now, but my file structure seems to be OK.

Thanks for the quick response.

:)

---

### Post by bascha on 2006-03-09
After you logon, try and type startx.

---

### Post by 4deck on 2006-03-09
It runs through a couple screens very quickly and then gives me

cannot start xsession.  ...no .xsession files found, no terminal emulators found.

---

### Post by Aine on 2006-03-10
I'm still new, but sounds like your X is missing or corrupted?

What happens when you're in terminal and you type

```
sudo apt-get install xserver-xorg
```

?

---

### Post by 4deck on 2006-03-10
It says it already has the most recent version.

---

### Post by Aine on 2006-03-10
Ok, try to do this

```
sudo dpkg reconfigure xserver-xorg
```

If you can, try to paste your xorg.conf file .. you can FTP it to a server through terminal if you have a server to put it to.

When you recofigure it, it'll ask about GLcore..if you have an nvidia card, GLcore = bad so make sure to disable it.

---

### Post by 4deck on 2006-03-10
It won't allow me to do that without other options.  I can't seem to get it to reinstall or configure it using apt-get, either--the system tells me it has the most updated version of xserver-xorg.

---

### Post by Aine on 2006-03-11
what happens if you try 

sudo /etc/init.d/gdm start 

?

---

### Post by feathers on 2006-03-11
If an install process is interrupted, you can usually restart it by typing dpkg --configure -a. If this does nothing, Try to install kubuntu-desktop with apt-get install kubuntu-desktop. If this does nothing, do apt-get remove kubuntu-desktop and then install it. You can safely uninstall kubuntu-desktop as it does not remove anything else. 
If all this does not help you need to post error messages you get.

---

### Post by Lexicon on 2006-03-11
feathers and Aine, thanks.  I'm not the one you were trying to help (my thread is in the "Desktop Support" forum), but your suggestions worked to get me back from the same problem 4deck is having.  I *think* I did:

```

sudo apt-get install xserver-xorg
sudo apt-get install kubuntu-desktop

```

And was back in business.  I also had to fix my xorg.conf file back to change what I did that seemed to have caused the problem in the first place (although fixing the file without those reinstalls didn't do it on its own).  Again, thanks!  And to 4deck: really hope you get back on your feet.

---

### Post by 4deck on 2006-03-12
Thank you everyone! I was able to get back to normal--without a hitch or re-installing (ie the typical XP fix) by apt-get installing kubuntu-desktop. This worked fantastically. Thanks for everyones help.

---

