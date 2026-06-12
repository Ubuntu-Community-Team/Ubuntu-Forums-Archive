---
title: "Gnome App Launcher &amp; WINEPREFIX"
date: 2010-07-31
forum: General Help
---

### Post by Peter7K on 2010-07-31
Hello.  After a recent update of my Ubuntu 10.04, my launcher for this app no longer works:

```
WINEPREFIX=$HOME/.wine-1.2-rc7 wine-1.2-rc7 "C:/Program Files/League of Legends/lol.launcher.exe"
```

It runs fine in the terminal, but if I create a launcher with that exact line, I get this error: 

Could not launch application
Failed to execute child process "WINEPREFIX=$HOME/.wine-1.2-rc7" (No such file or directory)


If I try to run it as "Application in Terminal" from a launcher it yields the error:

There was an error creating the child process for this terminal 


Any way to resolve this?  It gets rather tedious copying the line every time I want to run it.  Thank you for your time.

---

### Post by Peter7K on 2010-08-02
Really? No one else has this issue? :(

---

### Post by Peter7K on 2010-11-02
Bump, now on 10.10, still no fix?

---

### Post by dtfinch on 2010-11-02
I write .sh scripts for launching programs in wine, since many require other fixes like changing the current directory, changing the screen resolution before and after, or turning off the screen saver.

So it'd be something like:```
#!/bin/sh
WINEPREFIX=$HOME/.wine-1.2-rc7 wine-1.2-rc7 "C:/Program Files/League of Legends/lol.launcher.exe"
```
Then you'd use chmod 755 to make the script executable, and point the launcher to that script.

---

### Post by Peter7K on 2010-11-03
Thanks!  Works wonderfully.

---

### Post by Karl1982 on 2010-12-13
> **Peter7K said:**
> Hello.  After a recent update of my Ubuntu 10.04, my launcher for this app no longer works:

```
WINEPREFIX=$HOME/.wine-1.2-rc7 wine-1.2-rc7 "C:/Program Files/League of Legends/lol.launcher.exe"
```It runs fine in the terminal, but if I create a launcher with that exact line, I get this error: 

Could not launch application
Failed to execute child process "WINEPREFIX=$HOME/.wine-1.2-rc7" (No such file or directory)

The reason your launcher isn't working is because WINEPREFIX isn't a command, so the line makes no sense to Linux.  As for why it worked before, I couldn't say.  You need the "env" command at the beginning of the launcher command line.  I would also put the variable's value in quotes if possible, but that may not work with a variable in it:

```
env WINEPREFIX="$HOME/.wine-1.2-rc7" wine-1.2-rc7 "C:/Program Files/League of Legends/lol.launcher.exe"
```On the rare occasion WINE makes these launchers for you, it writes them like that.

---

### Post by EpicFai1 on 2011-02-12
I still can't get my LoL to run. I tried these commands, looked up my LoL location (env WINEPREFIX="/home/log/.wine" wine C:\\windows\\comm" and\\start.exe /Unix /home/log/.wine/dosdevices/c:/users/Public/Desktop/Play\ League\ of\ Legends.lnk), and still I get no positive response. I repaired my LoL and is still says that there's an error in lol.launcher.exe. Also, every time I try the repair, it says that "A previous instance of the launcher is running but is not responsive. Would you like to terminate this instance?" I click yes (or no, once) and then it gives me the "the program lol.launcher.exe has encountered a serious problem and needs to close. We're sorry for the inconvenience" and then goes on to talk about the wine site, which hasn't been much help, either, because it states that wine runs as 'silver' on Ubuntu 10.10. And yes, I have tried restarting the pc, updating wine (newest version is already installed), etc. I'm too tenacious to give up. Any suggestions?

---

### Post by SpawnHappyJake on 2011-06-30
I replaced $HOME with the actual path and that fixed it for me.
Working example:

```
env WINEPREFIX=/home/spawnhappyjake/oblivion wine "C:\\Program Files\\Bethesda Softworks\\Oblivion\\OblivionLauncher.exe"
```

Cheers,
Jake

---

