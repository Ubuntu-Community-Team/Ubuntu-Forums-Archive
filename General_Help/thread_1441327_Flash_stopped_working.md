---
title: "Flash stopped working"
date: 2010-03-28
forum: General Help
---

### Post by pcdave98 on 2010-03-28
Hello.

I've only had ubuntu installed for 5 or 6 days and everything was great. There were one or two niggles like the, apparently, standard DVD playback problem and I had to tinker to get my 3G dongle working. I was now an expert and getting quite cocky.

Now, however, I can no longer use Flash Player. When I try iPlayer or the little embedded Flash movies on the BBC website (or any site for that matter) I can see the movie - I can even see the large icon in the screen to start the movie and I can see the icons at the bottom for fast forward etc.

When I hover the cursor over them, the cursor arrow changes to a little hand, as expected, but when I click the mouse nothing happens. 

I must admit, I have been playing about trying to get familiar with this new OS so I've clearly changed something by mistake.

Thanks.

;)


Edit - ubuntu 9.10 with Flash 10

---

### Post by 2hot6ft2 on 2010-03-28
I don't know about iPlayer but to fix the rest.

Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc):
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
You will have to enter your password which wont be displayed just type it in and hit Enter
Then install gecko media player:
```
sudo apt-get install gecko-mediaplayer
```
Then restart firefox and try it out.

---

### Post by pcdave98 on 2010-03-28
Thanks for that but it's just the same.

/Dave

---

### Post by 2hot6ft2 on 2010-03-28
Ok, here's the page to re-install flash then.
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Use the drop down to select your ubuntu version. 9.04+ would be 9.10

---

### Post by pcdave98 on 2010-03-28
I get the little popout window telling me "downloading package 54 of 55" then, after maybe 2 minutes, I get "Could not find package 'adobe-flashplugin'."

---

### Post by 2hot6ft2 on 2010-03-28
That adds the PPA for adobe so you most likely timed out getting the apt updates. It may take a little while but since it apparently added the PPA before getting stuck you can do it manually like this:

Open a terminal
Applications > Accessories > Terminal
and run

```
sudo apt-get update
```
You will have to enter your password which wont be displayed just type it in and hit Enter
then once that finishes use
```
sudo apt-get install adobe-flashplugin
```
or
```
sudo apt-get reinstall adobe-flashplugin
```
since you say you already had it working
Sorry for the delay, I was eating.

---

### Post by pcdave98 on 2010-03-28
dave@dave-desktop:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin
dave@dave-desktop:~$

---

### Post by 2hot6ft2 on 2010-03-28
> **pcdave98 said:**
> dave@dave-desktop:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin
dave@dave-desktop:~$
What version of ubuntu are you using?
If it's 9.10 then go back to the adobe site and try again since it should make the package available.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Use the drop down to select your ubuntu version. 9.04+ would be for 9.10

---

### Post by lidex on 2010-03-28
Try these commands:
```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

Close your browser first and/or restart after. If more problems go here:
[http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1]("http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1")

---

### Post by 2hot6ft2 on 2010-03-28
> **lidex said:**
> If more problems go here:
[http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1]("http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1")
Glad you had that handy, haven't seen that before.;)

---

### Post by pcdave98 on 2010-03-28
> **2hot6ft2 said:**
> What version of ubuntu are you using?
If it's 9.10 then go back to the adobe site and try again since it should make the package available.



Yeah - 9.10 and latest adobe. Tried all that.

---

### Post by 2hot6ft2 on 2010-03-28
Did you try what lidex suggested?
> **lidex said:**
> Try these commands:
```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

Close your browser first and/or restart after. If more problems go here:
[http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1]("http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1")
If you tried that, and tried what I said, then I'm at a loss as to what the problem is, or what the solution is for it.

I'm sure someone here knows.

---

### Post by pcdave98 on 2010-03-28
OK:

The flash player will work once after a restart (maybe that was always the case) and it will also work once after this:

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
But only once. 

I can pause it - and I then I'm back to square one.

---

### Post by lidex on 2010-03-28
Close your browser (copy this info somewhere first). Run these commands:
```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get remove flashplugin-installer
```

Now these:
```
sudo updatedb
locate libflashplayer.so
```

Delete any instances that are still found.

---

### Post by lidex on 2010-03-28
To check they are gone, run the last two commands again. With no libflashplayer.so on your system run this:
```
sudo apt-get install flashplugin-installer
```

Open your browser and check "Tools>Add-ons>Plugins"

---

### Post by pcdave98 on 2010-03-29
How do I delete these:

dave@dave-desktop:~$ locate libflashplayer.so
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so


;)

---

### Post by 2hot6ft2 on 2010-03-29
> **pcdave98 said:**
> How do I delete these:

dave@dave-desktop:~$ locate libflashplayer.so
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so


;)
Since I'm sure you're used to browsing you can do it in in nautilus like this:
Open a terminal
Applications > Accessories > Terminal
and run
```
gksu nautilus
```
enter your password and hit Enter
then just browse to them and right click on each one and select Move to Trash.
Close nautilus. **DON'T** do anything else in nautilus before closing it, since you're running it as root.
Reboot before completing the instructions lidex gave.

---

### Post by pcdave98 on 2010-03-29
OK - I deleted:

/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so

Looked for:

/usr/share/ubufox/plugins/npwrapper.libflashplayer.so

but there was no file there. But I still get this:

dave@dave-desktop:~$ locate libflashplayer.so
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so

I've now established that it isn't a Flash problem. It's a problem just with Flash/ubuntu 64/BBC iPlayer. I've tried some of the suggestions that Google threw up but nothing has changed.

Thanks for all the help BTW.

---

### Post by pcdave98 on 2010-03-29
Since deleting that file everything is now working.

:D

Thanks again.

---

