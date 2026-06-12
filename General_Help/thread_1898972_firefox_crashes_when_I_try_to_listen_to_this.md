---
title: "firefox crashes when I try to listen to this"
date: 2011-12-22
forum: General Help
---

### Post by flyingfisch on 2011-12-22
When I try to listen to [this](http://www.ricksteves.com/radio/streaming/program228a.asx) podcast, firefox crashes. It does not do this on windows. Do I need to get special codecs?

I can listen to most other asx files.

---

### Post by BC59 on 2011-12-22
I tried to open it in Firefox and Chrome and it's not working.

---

### Post by hakermania on 2011-12-22
Same here, I don't get crash, but I can't here anything.

---

### Post by jockyburns on 2011-12-22
I'm running 11.04  (natty) and using Chrome as my default browser and can link to that podcast effortlessly. You could try Chrome browser (not Chromium) and see how you get on.

---

### Post by hakermania on 2011-12-22
You can try downloading the file and using:
```

mplayer -playlist file_name.asx

```

---

### Post by flyingfisch on 2011-12-22
> **hakermania said:**
> You can try downloading the file and using:
```

mplayer -playlist file_name.asx

```

I did that :P

---

### Post by Frogs Hair on 2011-12-22
It says PC or Mac only on this page .  The Windows Media plug-in doesn't work for me .

 [http://www.ricksteves.com/radio/protected/descriptions.cfm?showID=371](http://www.ricksteves.com/radio/protected/descriptions.cfm?showID=371)

---

### Post by flyingfisch on 2011-12-22
> **Frogs Hair said:**
> It says PC or Mac only on this page .  The Windows Media plug-in doesn't work for me .

 [http://www.ricksteves.com/radio/protected/descriptions.cfm?showID=371](http://www.ricksteves.com/radio/protected/descriptions.cfm?showID=371)

I thought that linux would be able to listen to windows files. Oh well.

---

### Post by jockyburns on 2011-12-22
> **Frogs Hair said:**
> It says PC or Mac only on this page .  The Windows Media plug-in doesn't work for me .

 [http://www.ricksteves.com/radio/protected/descriptions.cfm?showID=371](http://www.ricksteves.com/radio/protected/descriptions.cfm?showID=371)


Still works fine on my computer. Clicking the top link on the page for windows media player, just opens the file in a new window which then plays perfectly. Maybe I have downloaded some sort of codec?? Been drunk many times since installing Ubuntu. ;);););)

---

### Post by flyingfisch on 2011-12-22
lol. I'm gonna try installing WMP in WINE and see if that works.

EDIT: I am not installing windows media player because it needs to verify that I have a genuine version of windows, which I obviously don't have.

---

### Post by Petrolea on 2011-12-22
It works on Chrome for me, didn't install anything special, only restricted-extras I think.

---

### Post by Frogs Hair on 2011-12-22
I got the site to work with Moonlight , but you may need the add-on to get it to work on a newer version of Firefox. I run FF Nightly 12.0 , so I don't know what versions Moonlight works with .
  
[https://addons.mozilla.org/en-us/thunderbird/addon/add-on-compatibility-reporter/](https://addons.mozilla.org/en-us/thunderbird/addon/add-on-compatibility-reporter/)

[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

---

### Post by ron999 on 2011-12-22
Hi
VLC will play it.
Like this:-
```
vlc http://www.ricksteves.com/radio/streaming/program228a.asx
```

---

### Post by BC59 on 2011-12-23
The mystery continue, it's not working in my VLC:

> vlc [http://www.ricksteves.com/radio/streaming/program228a.asx](http://www.ricksteves.com/radio/streaming/program228a.asx)
VLC media player 1.1.12 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0xcc5060] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setlocale(6, "")

(process:5698): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
[0xfbf420] ts demux error: cannot peek
[0xdb7e70] main playlist: stopping playback
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
TagLib: Could not open file [http://streaming.ricksteves.com/podcasts/pgm228a_pod.mp3](http://streaming.ricksteves.com/podcasts/pgm228a_pod.mp3)
[0xdb7e70] main playlist: stopping playback
[0xdd22d0] access_mms access error: cannot read data 2
TagLib: Could not open file streaming.ricksteves.com/podcasts/pgm228a_pod.mp3?MSWMExt=.asf


I think that without the installation of special codecs it's impossible to play.

---

### Post by BC59 on 2011-12-23
OK solution!

Install xine-plugin:
```
sudo apt-get install xine-plugin
```

If is not working continue to install the Medibuntu repository and packages:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```

It's only working in Chrome. In Firefox, VLC and Mplayer nothing

---

### Post by stinkeye on 2011-12-23
For me, opens in vlc and opera using the totem plugin but not firefox.
Not playing in firefox but playing in opera is strange because the 
path to the plugin in opera is **/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so** 
Opera and firefox both bring up the totem plugin but firefox never starts playing.

---

### Post by flyingfisch on 2011-12-26
I don't like chrome so I guess I'll try installing opera, which I loved on windows but didnt bother to install yet.

---

