---
title: "Wine??"
date: 2011-02-21
forum: General Help
---

### Post by Syed75 on 2011-02-21
I can't get any software in wine to work??

---

### Post by Vaphell on 2011-02-21
it would be nice if you provided some additional details.

---

### Post by Syed75 on 2011-02-21
That's all I have.

Ubuntu 10.04 installed WINE and any software in it won't work. Other than Notepad.

---

### Post by 3Miro on 2011-02-21
A lot of softwre doesn't run with wine and a lot more needs special installation/settings. Your best bet is to go to winehq database 

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Then look for information about the specific program that you want to run.

---

### Post by keithpeter on 2011-02-21
Hello

I recently installed wine under 10.10 from the software centre. I ran the wine config program and set it to mirror a Windows XP computer. 

I then popped the installation CD for Inspiration into the CD drive. Attempting to run the setup from the cd generated an error about the executable bit not being set, so I copied the contents of the CD to a folder on the desktop. Then I right clicked on the installer programme and went to Properties | Permissions and set the 'Allow executing file as programme' box. 

Then Inspiration installed fine, and I deleted the folder with the installer.

What error messages do you get when trying to run an exe?

---

### Post by Syed75 on 2011-02-21
> **keithpeter said:**
> Hello

I recently installed wine under 10.10 from the software centre. I ran the wine config program and set it to mirror a Windows XP computer. 

I then popped the installation CD for Inspiration into the CD drive. Attempting to run the setup from the cd generated an error about the executable bit not being set, so I copied the contents of the CD to a folder on the desktop. Then I right clicked on the installer programme and went to Properties | Permissions and set the 'Allow executing file as programme' box. 

Then Inspiration installed fine, and I deleted the folder with the installer.

What error messages do you get when trying to run an exe?

It just doesn't load.

---

### Post by x1a4 on 2011-02-21
> **Syed75 said:**
> ... any software in it won't work. Other than Notepad.

What do you mean by that? 

Wine is a subsystem which allows you to run software for windows.  It is not the OS itself.  Aside from a text editor, web browser and file manager it doesn't really have any software.  If you have games, and other software made specifically for windows, you *might* be able to use them in Linux by way of Wine.

---

### Post by Syed75 on 2011-02-21
> **x1a4 said:**
> What do you mean by that? 

Wine is a subsystem which allows you to run software for windows.  It is not the OS itself.  Aside from a text editor, web browser and file manager it doesn't really have any software.  If you have games, and other software made specifically for windows, you *might* be able to use them in Linux by way of Wine.

I try to run Itunes but it won't work. Quick time nope. Skype nope.

AM I installing wrong???

Cause the default install works, which is Notepad.

---

### Post by x1a4 on 2011-02-21
> **Syed75 said:**
> It just doesn't load.

Try to run an exe like so: 
```
env WINEPREFIX="/home/*username*/.wine" wine start /unix "/home/*username*/.wine/drive_c/path/to/win-programme.exe"
```

Or like so: 
```
env WINEPREFIX="/home/*username*/.wine" wine "C:\\Path\\to\\win-programme.exe"
```

Where *username* is your user name. Do this from a terminal emulator then copy and post the messages here.  Not all windows software will work with Wine.

---

### Post by ajgreeny on 2011-02-21
Why would you use wine for Skype?  There is a skype package in the repos which works with no real fuss.

I can not help with Quicktime as a separate application, but again wonder why you want to install it.  There are other linux media players that can deal with the quicktime movies etc, so the windows quicktime application is not needed.

I have no idea about iTunes, as I have never used it, and never will either.

---

### Post by 3Miro on 2011-02-21
> **Syed75 said:**
> I try to run Itunes but it won't work. Quick time nope. Skype nope.

AM I installing wrong???

Cause the default install works, which is Notepad.

There is skype for Linux. This is the one that you should be using.

[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)

Check Move Player or VLC player and install extra codecs from Medibuntu. This should cover any needs fro quick time.

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

For iTunes, check winehq:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22647](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22647)

---

### Post by Syed75 on 2011-02-21
> **ajgreeny said:**
> Why would you use wine for Skype?  There is a skype package in the repos which works with no real fuss.

I can not help with Quicktime as a separate application, but again wonder why you want to install it.  There are other linux media players that can deal with the quicktime movies etc, so the windows quicktime application is not needed.

I have no idea about iTunes, as I have never used it, and never will either.

Just messin' around, so I could do group video call from Ubuntu.

Quick times came with iTunes..

And right now i'm trying to get the applications menu to respond..

Since it froze unexpectedly.

---

### Post by keithpeter on 2011-02-21
> **Syed75 said:**
> I try to run Itunes but it won't work. Quick time nope. Skype nope.

Nope, you are just trying to use programs that have known issues with wine.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17774](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17774)

[http://appdb.winehq.org/appview.php?appId=1029](http://appdb.winehq.org/appview.php?appId=1029)

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1592](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1592)

Others with more knowledge than me are trying to help. Is there a reason you can't use the skype client available in Ubuntu?

---

### Post by Syed75 on 2011-02-21
> **x1a4 said:**
> Try to run an exe like so: 
```
env WINEPREFIX="/home/*username*/.wine" wine start /unix "/home/*username*/.wine/drive_c/path/to/win-programme.exe"
```

Or like so: 
```
env WINEPREFIX="/home/*username*/.wine" wine "C:\\Path\\to\\win-programme.exe"
```

Where *username* is your user name. Do this from a terminal emulator then copy and post the messages here.  Not all windows software will work with Wine.

Error for both??

---

### Post by Syed75 on 2011-02-21
Dang my entire bottom panel froze... Reboot time.

---

### Post by 3Miro on 2011-02-21
> **Syed75 said:**
> Error for both??

Look Syed75, we cannot help you like that. If you are trying to do something, please provide details on what is it and why are you trying to do it. If something is not working properly, please put as many details on what is happening. If you get an error message, please copy/paste the error message (using code tags). Otherwise, we have absolutely no idea on what is happening.

For Skype, use the Linux version, I do video calls with it all the time. Many people that are new to Linux jump to wine to try and use the windows programs that they are familiar with, however, you should first look for a Linux program and use wine as a last resort. There are many media players for Linux, if you want to play .mp3 or videos, try those first. If you want to use some of the other features of iTunes, then look at the winehq link that I posted earlier.

---

### Post by Syed75 on 2011-02-21
I installed WINE and I tried to install stuff, and nothing worked.

And it wouldn't work at all. Nothing would uninstall or install after a few days? So I tried to re install and still nothing..

Now I'm basically doing that again.

---

### Post by x1a4 on 2011-02-21
> **Syed75 said:**
> Error for both??
What error is that? Please post it. 

Anyway, if you want to use Skype, use the Linux port.  iTunes will most likely not work.  Use VLC or Mplayer to view QuickTime videos; Rhythmbox or Exaile or Amarok for music.  Use Wine as a last resort if you can't find software to do the job of a given windows app.  And then, only after checking the App Database at [http://appdb.winehq.org/](http://appdb.winehq.org/). 

Don't think of software in terms of brand names, but functionality instead, then find Linux software which performs the same function.  If you used Outlook for email on windows, instead of trying to run it on Linux, access your email using Thunderbird, or Balsa, or Claws Mail, etc.  Instead of trying windows version of QuickTime to view QT movies, use a Linux movie player (in conjunction with the appropriate [Medibuntu]("http://medibuntu.org/") codecs).

---

### Post by x1a4 on 2011-02-21
> **Syed75 said:**
> Dang my entire bottom panel froze... Reboot time.

If your panel froze, don't reboot, restart the panel instead.  Worst case scenario, log out then log back in.  If your entire GUI freezes, press Ctrl+Alt+BackSpace and log back in.

---

### Post by ajgreeny on 2011-02-21
But you still have not told us why you are insisting on trying to install many applications using wine when there are perfectly good native linux alternatives which will work without all the hassle you are experiencing trying to use the windows applications instead.

It simply does not make sense continuing to beat your head against a brick-wall!

For your future reference, when you eventually try to use wine for something where there is no alternative, if you need to reinstall a windows app that is misbehaving with wine, you must at least uninstall it through wine and probably also delete the hidden ~/.wine folder in your home.  If you do not do so, you will still have all the errant configurations for the applications, and a re-install of those same apps will probably get you nowhere.

---

