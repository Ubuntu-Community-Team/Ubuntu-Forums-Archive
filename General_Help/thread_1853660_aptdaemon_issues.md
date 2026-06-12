---
title: "aptdaemon issues"
date: 2011-10-02
forum: General Help
---

### Post by dragonzuela on 2011-10-02
Hi, I'm fairly new to Linux in general and have been loving Ubuntu so far, but ran into some software installation issues today.  I managed to install some applications from the Terminal a couple weeks ago with no problems, but today I tried to get WINE and it seems that I broke something.

I naively tried to install WINE with:

```
sudo apt-get install wine
```and it seemed to be working until terms and conditions for ttf-mscore-fonts installer popped up in the terminal (I can't manage to reproduce the screen at this point, sorry) and seemed to want me to click <Ok> to continue, except that neither clicking nor hitting the enter key did anything, so I exited the Terminal.

I'm not sure I remember everything that I tried after that since I was so frantically looking for a fix, but basically since that point I have not been able to install or remove any applications.  When I try anything with apt-get from the terminal, I get:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```(even if I have all other applications closed).

When I try to install or remove anything from the Ubuntu Sofware Center, I get the even more unsettling pop-up message:
[INDENT]An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

[/INDENT]Any advice is greatly appreciated!  Thanks in advance!

---

### Post by dniMretsaM on 2011-10-02
Two things to try: 
[LIST]
[*](1) Reboot your computer.
[*](2) Run this in terminal:```
sudo dpkg -configure-a
```
[/LIST]

---

### Post by dragonzuela on 2011-10-02
Ok, after a reboot and running ```
sudo dpkg --configure -a
``` I'm not getting the message from the terminal any more regarding /var/lib/dpkg/lock.  However, if I try to install or upgrade anything from the terminal, I see the ttf-mscorefonts-installer message from before:

```
Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; TrueType core fonts for the Web EULA                                        
 &#9474;                                                                             
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                           
 &#9474;                                                                             
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement         
 &#9474; ("EULA") is a legal agreement between you (either an individual or a        
 &#9474; single entity) and Microsoft Corporation for the Microsoft software         
 &#9474; accompanying this EULA, which includes computer software and may include    
 &#9474; associated media, printed materials, and "on-line" or electronic            
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your        
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be      
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of        
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                            
 &#9474;                                                                             
 &#9474;                                  <Ok>
```And trying to do anything from the Ubuntu Software Center gives the same error message that I saw previously.

Thanks for the speedy response!

Edit: Ah, there's more of that license agreement if I scroll down with the mouse wheel, but nowhere to click to accept it.

---

### Post by dragonzuela on 2011-10-02
```
me@me-Inspiron-1318:~$ sudo dpkg --configure -a
[sudo] password for me: 
me@me-Inspiron-1318:~$ sudo apt-get remove ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ttf-mscorefonts-installer
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing ttf-mscorefonts-installer (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
me@me-Inspiron-1318:~$ sudo apt-get install --reinstall ttf-mscorefonts-installer
```

And then we're back at the End User License Agreement of Doom.

---

### Post by dniMretsaM on 2011-10-02
Try running the command again (maybe reboot first) and the open up the Software Center and then try to re-install [FONT=Courier New]ttf-mscorefonts-installer[/FONT] from there. This will allow you to view the EULA in a GUI and be able to click OK. What happens if you scroll all the way to the end of the EULA and press enter? In things like this I've used before, the option do accept or becomes available after that. In case you were wondering, the reason this is happening is because the dpkg is being interrupted in the middle of trying to install something (your closing the terminal emulator while the EULA is up is what's causing the interruption). So (being a computer) it complains about this and forces you to manually fix it. But when you do it brings up the EULA again. Since you can't get out of it, you have to interrupt the process again. Basically it's a never ending cycle until you accept/decline the EULA.

---

### Post by dragonzuela on 2011-10-02
[I]In case you were wondering, the reason this is happening is because the  dpkg is being interrupted in the middle of trying to install something

[/I]Yup, I figured as much at this point!  Good learning experience I guess.

Ok, rebooted again (luckily it only takes a few seconds), did sudo dpkg --configure -a, and went into the Ubuntu Software Center.  There is a button to remove ttf-mscorefonts-installer, but (and maybe this is a dumb question) I don't see any option to reinstall it from there.  If I click the remove button it fails.

Scrolling to the end of the EULA from the terminal and hitting enter doesn't do anything, unfortunately.

---

### Post by oldos2er on 2011-10-02
To accept the terms of the EULA, use Tab to highlight 'Ok', then Enter.

---

### Post by dniMretsaM on 2011-10-02
Hmm, OK. Repeat and try Synaptic. It may have an option to reinstall from there. I know there is one in Muon (a package manager for KDE) but I'm not exactly sure about how to do it in GNOME. You also might try Ctrl+Z at the end of the EULA. Might just start the dpkg error going again.

EDIT: Or follow oldos2er's advice. Having someone with experience help you can make things a lot easier...

---

### Post by dragonzuela on 2011-10-02
Got it to work by using the tab key to accept the EULA from the terminal.  Thank you both!!

---

### Post by dniMretsaM on 2011-10-03
Congratz! Mark as solved please.

---

