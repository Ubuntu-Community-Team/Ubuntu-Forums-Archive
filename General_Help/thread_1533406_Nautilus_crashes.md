---
title: "Nautilus crashes"
date: 2010-07-17
forum: General Help
---

### Post by darkmaxa on 2010-07-17
Nautilus works pretty well, except when moving files (or directories) with drag and drop.

If moving files on the same physical disk, everything is OK.

If moving files from Home to mounted partition (or reverse), Nautilus always crashes! :|

Scenario is:
- Open nautilus
- F3 for two panes
- in one pane Home folder, in other pane mounted partition
- select dirs to move
- middle click, drag & drop selected files on the other pane
- from context menu -> Move here
- nautilus crashes without any error message

Any help?

---

### Post by lidex on 2010-07-18
Run nautilus from a terminal and try that again. Post back here your terminal output.
```
nautilus
```

---

### Post by darkmaxa on 2010-07-18
Thank you for the response.

Terminal output:
```
darkmaxa@TOWER:~$ sudo nautilus
[sudo] password for darkmaxa: 
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


[COLOR=Blue](nautilus:3139): Gdk-CRITICAL **: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed[/COLOR]

[COLOR=SandyBrown]** (nautilus:3139): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files[/COLOR]

[COLOR=Red]** (nautilus:3139): CRITICAL **: nautilus_file_get_uri: assertion `NAUTILUS_IS_FILE (file)' failed
Segmentation fault[/COLOR]
darkmaxa@TOWER:~$ 
```blue line - after drag & drop (context menu still opened)
orange line - just after click on "Move here"
red line - after Nautilus window is gone

More info:
If I use two separate Nautilus windows, then **everything is OK**. If I use one window with extra pane (F3) Nautilus **always** crashes. (In both cases I'm moving same dirs on the same locations)


The same thing happens when I  use the Live CD, not every time, but 1 of 5 (approximately).

---

### Post by lidex on 2010-07-18
Why did you run that with sudo? Try it as written:
```
nautilus
```

If you need to run nautilus as root - not now - use graphical sudo:
```
gksudo nautilus
```

---

### Post by darkmaxa on 2010-07-18
> Why did you run that with sudo? Try it as written:
```

darkmaxa@TOWER:~$ nautilus
darkmaxa@TOWER:~$ I still can use console, Nautilus not print anything here...
I: command not found
darkmaxa@TOWER:~$
```

So...? :)

---

### Post by lidex on 2010-07-18
It won't show anything at that time. A nautilus window should open. Use that to induce the error conditions and then check terminal for error output.

---

### Post by darkmaxa on 2010-07-18
Scenario:
- Open terminal and type just "nautilus" and hit enter
- Nautilus opened
- F3 (for extra pane), in one pane ~/Download in other /mnt/Storage
- do drag&drop of two dirs from Storage to ~/Download
- Nautilus crashes without any error message, window just disappear

After that Terminal output is:
```
darkmaxa@TOWER:~$ nautilus
darkmaxa@TOWER:~$ 

```I don't why, but if I run Nautilus with just "nautilus", there is no output in console. If I run Nautilus with "sudo nautilus", output is as I quoted above.

---

### Post by lidex on 2010-07-18
Check your logs:
```
cat ~/.xsession-errors
cat /var/log/messages
cat /var/log/syslog
```

---

### Post by darkmaxa on 2010-07-18
I've deleted these three logs, restart the system, then start nautilus from console and reproduce the Nautilus crash.

Logs are in the attachment.

---

### Post by lidex on 2010-07-18
Try uninstalling ubuntuone. If it takes any other packages out with it that are needed, reinstall only those before quitting.

---

### Post by darkmaxa on 2010-07-18
I'm not sure what exactly to uninstall, so better to ask ...
```
sudo apt-get remove ubuntuone-client
```
or
```
sudo apt-get remove ubuntuone-client-gnome
```
or something else?

---

### Post by lidex on 2010-07-18
Try synaptic. Search ubuntuone. See my screen below - you can uninstall any of those. As you can see I don't have them.

---

### Post by darkmaxa on 2010-07-18
I've uninstalled all ubuntuone packages, but Nautilus still crashes when moving files. :(

---

### Post by AlphaLexman on 2010-07-18
I have been watching this thread for a few hours now.

Even though I am on 9.10 and you are on 10.04, my nautilus does not have the F3 feature you describe.

I have noticed on many threads, as nautilus controls the desktop wallpaper, icons, etc.

The error messages posted in the 3rd post indicates a window management issue. It maybe moot, but please try:
```
nautilus --no-desktop
```
from a terminal, do your 'F3' drag and drop stuff and let me know what happens.

---

### Post by darkmaxa on 2010-07-18
> **AlphaLexman said:**
> 
```
nautilus --no-desktop
```

No effect, same thing happens. But anyway, thanks for idea!

---

### Post by lkjoel on 2010-07-18
First of all, its
```
nautilus --no-desktop --browser
```
And second, try installing LinuxEssentials from my sig.
Then type:
```
chmod +x FASTGNOME.sh
./FASTGNOME.sh
```
Or if you have Terminal Enhancements installed, type:
```
chmod +x FASTGNOME.sh
FASTGNOME.sh
```

---

### Post by darkmaxa on 2010-07-19
> **lkjoel said:**
> First of all, its
```
nautilus --no-desktop --browser
```

No effect, but thx anyway! :)

> **lkjoel said:**
> 
And second, try installing LinuxEssentials from my sig.


I don't like to install things for which I'm not sure what exactly do. How Linux Essentials can help me with Nautilus?

---

### Post by lkjoel on 2010-07-19
> **darkmaxa said:**
> No effect, but thx anyway! :)



I don't like to install things for which I'm not sure what exactly do. How Linux Essentials can help me with Nautilus?
It restarts Nautilus.
Nautilus is the default desktop for GNOME.
Usually restarting Nautilus, and removing useless components fixes a lot.
And it makes your computer much faster.

---

### Post by darkmaxa on 2010-07-20
Does anyone can reproduce this problem? :-k

---

### Post by lkjoel on 2010-07-20
I know that you will probably not agree with me, but would you like to switch DE's?

---

### Post by lidex on 2010-07-20
Try this for me. Delete this folder:
```
rm -r  ~/.local/share/gvfs-metadata
```
**It's only metadata.**
Now restart and give us a new syslog.

---

### Post by darkmaxa on 2010-07-20
> **lidex said:**
> Try this for me. Delete this folder:
```
rm -r  ~/.local/share/gvfs-metadata
```**It's only metadata.**
Now restart and give us a new syslog.

Done.

---

### Post by lidex on 2010-07-20
OK. Now give us the output of this command:
```
dpkg -l | grep "nautilus"
```

---

### Post by darkmaxa on 2010-07-21
> **lidex said:**
> OK. Now give us the output of this command:
```
dpkg -l | grep "nautilus"
```

Here it is:

> ii  libnautilus-extension1                         1:2.30.1-0ubuntu1.1                             libraries for nautilus components - runtime 
ii  nautilus                                       1:2.30.1-0ubuntu1.1                             file manager and graphical shell for GNOME
ii  nautilus-data                                  1:2.30.1-0ubuntu1.1                             data files for nautilus
ii  nautilus-sendto                                2.28.4-0ubuntu1                                 integrates Evolution and Pidgin into the Nau
ii  nautilus-share                                 0.7.2-12build1                                  Nautilus extension to share folder using Sam

---

### Post by darkmaxa on 2010-07-23
[]("http://ubuntuforums.org/member.php?u=577099")lidex, what next? :)

---

### Post by AlphaLexman on 2010-07-23
Install Thunar or pcmanfm.

---

### Post by lidex on 2010-07-23
I see a couple of gdm entries that are suspect. Try re-installing:
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```

No help? Try logging in as a different user.

---

### Post by darkmaxa on 2010-07-24
> **lidex said:**
> I see a couple of gdm entries that are suspect. Try re-installing:
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```No help? Try logging in as a different user.

Reinstall of gdm didn't help.

I've created new user account and move two dirs 3 times from left to right panel (and reverse) without any problems, but the fourth attempt has caused Nautilus crash, that is similar situation like with Live CD. If I use my primary user account, Nautilus crashes every time I try to move files

---

### Post by lidex on 2010-07-24
OK. Boot into your normal user account. Move all the files/folders from your desktop. To make sure you moved them all do this:
```
cd ~/Desktop
ls
```
Now this:
```
rm -r  ~/.local/share/gvfs-metadata
rm -r  ~/.gconf/apps/nautilus/desktop-metadata
```
Now this:
```
sudo apt-get install --reinstall nautilus && sudo dpkg-reconfigure nautilus
```
Reboot.

---

### Post by AlphaLexman on 2010-07-25
Maybe, JUST maybe, related to this problem...
[http://ubuntuforums.org/showthread.php?t=1380964](http://ubuntuforums.org/showthread.php?t=1380964)

---

### Post by darkmaxa on 2010-07-29
> **lidex said:**
> OK. Boot into your normal user account. Move all the files/folders from your desktop. To make sure you moved them all do this:
```
cd ~/Desktop
ls
```Now this:
```
rm -r  ~/.local/share/gvfs-metadata
rm -r  ~/.gconf/apps/nautilus/desktop-metadata
```Now this:
```
sudo apt-get install --reinstall nautilus && sudo dpkg-reconfigure nautilus
```Reboot.

Thank you very much, but it didn't help. :(

@AlphaLexman
No, my Nautilus issue isn't caused by svg/jpeg pictures.

---

### Post by lidex on 2010-07-30
I am at a loss. Did you check out the link in post #30?

---

### Post by darkmaxa on 2010-07-30
> **lidex said:**
> I am at a loss. Did you check out the link in post #30?

Yes, I am...

---

### Post by iceman on 2010-12-01
I have the same problem with a SunBlade2000 with Ubuntu 10.4 (and with Debian Squeeze too!!)
I don't know if the problem is related to my LVM partition (i have 2 fibrechannel 73gb disks), but i didn't find a solution.
Did you find one?

---

