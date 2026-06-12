---
title: "Transmission and Magnet links"
date: 2010-10-16
forum: General Help
---

### Post by devolute on 2010-10-16
I've just done a fresh install of the latest Ubuntu (10.10) and I'm having a problem with Magnet links.

I've done the following:

> * Type about:config into the address bar and press Enter.
* Right-click -> New -> Boolean -> Name: network.protocol-handler.external.magnet -> Value -> true
* Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /usr/bin/transmission
* Ensure network.protocol-handler.expose-all is set to true
as per these instructions: [http://ubuntuforums.org/showthread.php?t=811037](http://ubuntuforums.org/showthread.php?t=811037)

But Transmission will not start. It works fine with normal torrent links added either through Firefox or in Transmission itself, but when you click a Magnet link nothing happens.

This is a little annoying, because back in 10.4/9.10 everything worked fine.

I'm on 10.10 (64) and with the latest stable Transmission (2.10).

Any suggestions are appreciated.

---

### Post by t3s7a on 2011-02-01
Hey ;)

've just made the about:config configuration: 
 
> 
* Type about:config into the address bar and press Enter.
* Right-click -> New -> Boolean -> Name: network.protocol-handler.external.magnet -> Value -> true
* Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /usr/bin/transmission
* Ensure network.protocol-handler.expose-all is set to true



**but I'm still getting the same firefox msg of no magnet association has anyone found a solution for this?**

---

### Post by t3s7a on 2011-02-08
yup just found the solution... 

reboot it LOL

---

### Post by Martiini on 2011-09-27
this worked for me
/home/martin/.mozilla/firefox/5aewyn9t.default/prefs.js
```

user_pref("network.protocol-handler.app.bittorrent", "/usr/bin/ktorrent");
user_pref("network.protocol-handler.app.magnet", "/usr/bin/ktorrent");
user_pref("network.protocol-handler.expose.magnet", false);

```

---

### Post by pickarooney on 2012-02-07
I'm trying to us magnet links in ktorrent but I don't understand how they work exactly. Firefox throws the links to ktorrent OK but when I click on the magnet icon I see that the file is 'downloading' but there's no mention of where it's downloading to or what the progress is.

---

### Post by iris-n on 2012-02-28
Got it to work using transmission. Quite simple actually - /usr/bin/transmission does not exist, the name of the binary is /usr/bin/transmission-gtk

When I typed it, it began to work just fine. One thing is: I didn't follow the same instructions as OP, but the one at [https://trac.transmissionbt.com/wiki/MagnetLinks](https://trac.transmissionbt.com/wiki/MagnetLinks)

Interestingly, the transmission website also says the binary is /usr/bin/transmission rather than /usr/bin/transmission-gtk; maybe it is so in newer versions of ubuntu.

---

### Post by acorey on 2012-03-02
Ok, So I did all this stuff and added firefox plugins and nothing happened. Or so I thought. I was clicking on magnet links, the add to transmission box would come up, and there would be no files to choose. If I clicked add it would add an empty download. Or so I thought... Turns out that if I just waited a while, it all began to magically work. It wasn't exactly the same as it was before so naturally I freaked out... That's why I got into open-sourced stuff in the first place right?  So things would always be the same and consistent..</sarc> I am a dummy...

---

### Post by Salvia on 2012-03-04
Hey just in case anyone still needs to know, the GUI method might be a little easier.

Go to the menu bar click Edit->Preferences->Applications (tab)->scroll down to magnet and to the right select "Choose Other" in the drop down menu-> go to File System, then usr/bin/ and choose Transmission-GTK. 

After that you should be set.

---

### Post by AOB on 2012-04-17
I am using Google chrome on xubuntu 10.10 and would like to upgrade my Transmission so that I could use the magnet link. Looks like if you are using firefox there is already a solution. Anyone care to advise me on how to use the magnet link?

---

### Post by jwilson1484 on 2012-04-23
I had the same problem here is an easier way that worked for me. Check the path in file system/usr/bin/transmission to see if the application is transmission or transmission-gtk then open up a terminal and type 

gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/transmission '%s'"

gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/needs_terminal false

gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true

Three different commands and restart firefox and download magnet link and it will now prompt you if you would like to open with transmission. Worked for me

---

### Post by Bucky Ball on 2012-05-09
> **jwilson1484 said:**
> 
gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/transmission '%s'"

gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/needs_terminal false

gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true

... restart firefox and download magnet link and it will now prompt you if you would like to open with transmission. Worked for me

I tried this and when I click on the magnet link it asks if I'd like to open with Transmission, OK, the Transmission GUI (Torrent Options) opens but in 'Torrent File' it says '(None)'. That's generally where the torrent file appears. I can select where to download and all that fine. Hmm :(

---

