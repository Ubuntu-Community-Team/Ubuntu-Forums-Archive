---
title: "Adobe Flash problems after upgrade to Precise Pangolin"
date: 2012-09-07
forum: General Help
---

### Post by fiklein on 2012-09-07
I am running Xubuntu 12.04 and Flash will work in YouTube but not Hulu or other sites. I have a 32 bit system with 128MB Nvidia video card and plenty of RAM.
I have tried a previous version (pinned flash in 11.10), but unlocked it and upgraded and had the same problem. I have uninstalled and installed Flash and Restricted Extras and have purged these using Terminal, and have done a "Complete Removal" using Synaptic, then reinstalled with the same problems.
Again, Youtube works, but not much else that depends on Flash.:mad:

---

### Post by coffeecat on 2012-09-07
Not a Forum Feedback & Help thread.

*Thread moved to **General Help**.*

---

### Post by Epodx64 on 2012-09-07
My guess would be it's probably your video card causing the problems try using jockey to update to the post-release updates or add the x-swat/x-updates ppa and grab the 304.x driver should fix the problem.

---

### Post by fiklein on 2012-09-07
I read somewhere that Nvidia is not well supported and that disabling hardware acceleration may help. I do not know if Chrome has the same problem as Firefox, so may try that if Nvidia fix does not work. I am not familiar with "jockey." Is that a program? Is that just slang for fiddling around with the settings? I appreciate the help with trying to get this old computer back on track.

---

### Post by critin on 2012-09-07
> **fiklein said:**
> I am not familiar with "jockey." Is that a program? Is that just slang for fiddling around with the settings? I appreciate the help with trying to get this old computer back on track.

Jocky is the name of the "Additional Drivers" app.  in all versions.  If you open it and find that a noveau driver is recommended, you could try it.  I have better luck with the linux noveau drivers than with my nVidia. (but it's old)

---

### Post by alex2399 on 2012-09-07
Is your processor SSE2 capable?

Check via the command
```
cat /proc/cpu
```
in the terminal. If you see SSE2 is supported by your CPU, then disregard the rest.

Otherwise, you may need to install a different flash version. 10.x has security updates AFAIK and 11.2.x has not, but is newer.
Google for the right version that does not require SSE2 support by searching for SSE2 and Flash.

Get a proper version that does not need SSE2 here:
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html]("http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html")


Note: that video works on some sites may be due to them using HTML5. Also see:
[http://askubuntu.com/questions/159379/have-to-run-chrome-from-google-chrome-disable-bundled-ppapi-flash-command-t]("http://askubuntu.com/questions/159379/have-to-run-chrome-from-google-chrome-disable-bundled-ppapi-flash-command-t")

---

### Post by fiklein on 2012-09-07
I have tried to install this update via the GUI, but it does not activate after repeated attempts and reboots. It reverts to the old driver. Is there a command line that might be more successful? I have tried the rest of the suggestions and now Youtube does not even play.

---

### Post by Epodx64 on 2012-09-08
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
add this repository 
**ppa:ubuntu-x-swat/x-updates**

Then run sudo apt-get update then try letting Jockey install the 304.x drivers if it fails to do so open a terminal and try 
sudo apt-get update
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings

---

### Post by fiklein on 2012-09-08
I have the newest Nvidia drivers and settings manager installed. No luck running anything. My computer does not seem to have SSE2 support. I tried a previous Flash version in the past (I had an old one pinned and it did not work, so I went to the new one).
I use Firefox, but have read that Chrome has a different Flash driver if I am correct. Is that a possible solution? If not, I will chase after old Flash versions for Firefox again.
Also, is there any simple solution available by playing with the Nvidia settings.
Thank you so much for the help up to now.

---

### Post by fiklein on 2012-09-09
How exactly do I install an earlier version of FLASH? I have tried changing the *.so file, but could not get it to write. I can download the targz package from an earlier version, but have not gotten it to install. Can somebody help me install that package? I am using Xubuntu. I used to use Ubuntu, but Unity took up too many resources. Does using Nautilus seem reasonable. Help!
Thanks.

---

### Post by fiklein on 2012-09-09
I am able to watch Youtube with Gnash, but not Hulu. Is Lightspark or an alternative worth a try?

---

### Post by alex2399 on 2012-09-10
Using the newest Google Chrome with built-in flash will not work. It also needs SSE2.

What does it mean you can not replace the *.so file with an older version? If it is a permission problem use root rights for copying in the terminal.

For example:
```
sudo cp /home/username/libflashplayer.so /destination
```

sudo = get root/admin rights (i.e.: do almost anything, but think before you press enter)

cp = copy command

/home/username/libflashplayer.so = where the older flash version is(example)

/destination = where it should go


If you want to know where the currently used libflashplayer.so file is use the command "locate" with part of the filename you want to find. For example"

```
locate libflash
```
or
```
locate libflashplayer.so
```

The tar.gz file is an archive like "zip" or "rar". Just unpack it using nautilus to a convenient location in your home folder. Find where libflashplayer.so in that unpacked archive is located and use it to replace your flash version.

Alternatively if you are more used to Windows style copying and pasting you may use nautilus with root rights.

From a terminal for example:
```
sudo nautilus
```

But be wary, if you give a command as root in the terminal or nautilus, the machine will do it whatever the outcome may be. Doesn't matter if the system is a calculator or a life-support machine in a hospital.

P.S.: I can't give you the exact commands and file locations, I had the same problem on a different machine with a different system. Therefore it would be unwise to just assume everything is the same on your end.

Also, it may be a good idea to remove Gnash and other Flash replacements.

---

### Post by fiklein on 2012-09-10
I appreciate the help. I am aware of the dangers of root privileges, but do not know Linux/Debian/Unix commands and syntax well. For some reason, the Home folder in Xubuntu installs with only "read" privileges, so I will have to use sudo to be able to make the changes. If nothing else, the problem has been narrowed down to "SSE" issues, as the rest has been fixed.
This is not my only computer, so even if I cannot get Flash to work in Hulu, I have multiple other versions of Xubuntu or Ubuntu available that are working well. I just love to see the problems solved as this teaches me more about how the operating system and hardware work.
Thank you!

---

### Post by fiklein on 2012-09-11
Thank you. EVERYTHING works now. 

I installed the current Flash player using the flashplugin-installer in Synaptic.

I downloaded the flashplayer11_1r102_63 from the archive:  [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

extracted it (right click "Extract here") to a folder on my desktop, then waded through all the various junk until I found the flashplayer11_1r102_63_linux.i386.targz file.

I then extracted that and found the flashplayer11_1r102_63_linux.i386.so file.

I had to install the "flashplayer11_1r102_63_linux.i386.so" file in two places to get it to work, as replacing it in the flashplugin installer directory did not solve the problem.
I opened a terminal (right click "Open terminal here") in the /usr/lib/flashplugin-installer directory, but I suppose you could open a terminal anywhere and accomplish the same. I saved the commands (mfaked is my user name, so anybody else should enter their own user name):
/usr/lib/flashplugin-installer$ sudo cp /home/mfaked/Desktop/flashplayer11_1r102_63_linux.i386/libflashplayer.so /usr/lib/
/usr/lib/flashplugin-installer$ sudo cp /home/mfaked/Desktop/flashplayer11_1r102_63_linux.i386/libflashplayer.so /usr/lib/firefox-addons/plugins

The Flash worked in Youtube, Hulu, and Project Free-TV websites.

Thank everybody for their help. I hope this will be useful to anybody else using Xubuntu 12.04 and Flash.

A final question, though, is how to prevent an upgrade to a newer *so file, thus causing the problem again. . I would think I should pin this in Synaptic, but there may be a better solution.

---

