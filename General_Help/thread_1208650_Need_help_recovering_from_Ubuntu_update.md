---
title: "Need help recovering from Ubuntu update"
date: 2009-07-09
forum: General Help
---

### Post by oldsch00l on 2009-07-09
Here's the scoop.  I have a laptop that I use windows server on. I installed Ubuntu from within Windows using the Wubi install.

Worked fine for a year and I have gotten used to using it at work more than Windows lately.  

I decided up upgrade from 8.04 to 8.10. That went great.  I then went to 9.04.  That's when the trouble started.  Now, when I boot, I get a jumbled up mess instead of a logon screen.  Sometimes it looks like part of the logon screen and sometimes it's just lines. I searched the forums as I thought it was probably a problem with the graphics.  Someone suggested booting the live cd. If it works, replace your xorg.conf with the one on the live cd. It works from the cd but I can't for the life of me, figure out how to copy the file over the one on the original install.  

Can anyone tell me how to do that? I am no command line guru so specifics would be appreciated.

Also, if anyone feels I'm on the wrong path, please let me know. I have some important docs I can't get to and minutes from a board meeting.
Thanks!

---

### Post by geirha on 2009-07-09
I'd try the following. Boot Ubuntu as regular, then when the garbled login screen shows up, hit Ctrl+Alt+F1 to get to a console. Log in there, then run 
```
sudo dpkg-reconfigure xserver-xorg
```

You'll get some question about what keyboard you have and such, then it will generate a new xorg.conf. once done, run ```
sudo /etc/init.d/gdm restart
``` And your login screen should hopefully show up non-garbled.

---

### Post by oldsch00l on 2009-07-09
I was told to edit /etc/x11/xorg.conf but when I do, I get GTK warning **: cannot open display:

I don't appear to have /etc/x11 directory as when I try to change to it I get no such file or directory.

---

### Post by geirha on 2009-07-09
> **oldsch00l said:**
> I was told to edit /etc/x11/xorg.conf but when I do, I get GTK warning **: cannot open display:

I don't appear to have /etc/x11 directory as when I try to change to it I get no such file or directory.

Well, it's /etc/X11/xorg.conf, with a capital X in X11. Linux is case-sensitive. Go in one step at the time, and use ls to get your bearings.

```
cd /
ls  # will show you all files and directories in /
cd etc
ls
cd X11
ls

```

---

### Post by oldsch00l on 2009-07-09
Ctrl-alt-f1 doesn't do anything.  Still have the garbled graphics. Can I do it from recovery console at command prompt?

---

### Post by oldsch00l on 2009-07-09
I'm in the X11 dir and I see different files with dates in the name. I think the 20090628... would work.  That would have been the upgrade to 8.10 I did. It worked after that one.

You think that file would work?  If so, can I just use cp command to name it to the xorg.conf or is there something else I should do?

Thanks a ton for your help. I already feel like I'm closer in 15 minutes than I have gotten in a week on my own.

---

### Post by oldsch00l on 2009-07-09
I tried copying one of the older files and restarting gnome but that didn't work.  Tried using the .failsafe file as well but didn't work.  Think it might be something other than the xorg.conf file causing the problem?

---

### Post by geirha on 2009-07-09
You can also run it from recovery mode, yes. Try the ```
sudo dpkg-reconfigure xserver-xorg
``` approach

---

### Post by nacho32 on 2009-07-09
you should do a clean install updates from one version to another seem to be more of a pain then what it is worth ,,problem city, get the latest and have fun:guitar:

---

### Post by oldsch00l on 2009-07-09
sudo dpkg-reconfigure xserver-xorg Didn't work.  Same results.  I would do a clean install but I don't know how with Wubi/dual boot.  I also have some files that are priceless (I know, should have them backed up).  I can't lose them by doing a reinstall.

If I could figure out how to copy the files to something I could get off the computer, I would be fine.  I could reinstall then. I can't seem to get a usb drive mounted to copy to and can't figure out any other way.  I found a command in the forums to mount a usb drive but a directory of the /mnt/usbflash directory afterward didn't appear to contain the files of the drive.  Also, after copying from my documents folder to that directory didn't result in me having the files on the flash drive when I was done.

---

### Post by geirha on 2009-07-09
Well, ok, from the liveCD, you can mount your wubi drive(s) by first mounting the windows drive where Ubuntu is installed. You can do that from nautilus. Once you've found the one that contains the ubuntu dir, go into it and find the root.disk file (or maybe it is ubuntu.disk?). Open a terminal and type in ```
sudo mount -o loop */path/to/root.disk* /mnt
```

To get the correct path to root.disk to the terminal, first type in "sudo mount -o loop ", then drag and drop the root.disk file to the terminal, and the full path to the file will be filled in. Then complete with " /mnt".

You may need to be root to get access to all your files. You do that by running ```
gksudo nautilus
``` but be careful you don't delete anything.

I recommend you first backup your files (which you should do regularly anyway), then attempt to replace the xorg.conf with the one on the liveCD.

---

### Post by nacho32 on 2009-07-09
you said you had files but can't back them up not sure on the file size but you can try to upload to a host. Then do a clean install

---

### Post by oldsch00l on 2009-07-10
Thank you very much! That allowed me to get the files I needed.  Unfortunately, the xorg.conf file from the cd didn't fix the problem. It must be something else.  Not a big deal anymore as I have my files.  I will just uninstall Ubuntu from Windows and reinstall 9.04 from cd.  I think I will do dual boot instead of Wubi this time.  I'm more familiar with that.
Thanks again,

---

