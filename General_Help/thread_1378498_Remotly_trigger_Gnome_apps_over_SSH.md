---
title: "Remotly trigger Gnome apps over SSH?"
date: 2010-01-11
forum: General Help
---

### Post by CCKrause on 2010-01-11
I have a keyboard&monitor damaged laptop which I've converted into a media server/HTPC with a large external monitor. I've installed Ubuntu 9.10, and attached an external 1TB HDD with my video collection. As a media player it works perfectly fine. I can connect to it through my home network, both with VNC and with SSH.

I can use VNC on my current laptop to access the player's desktop and play video files. However, this is awkward as the screen resolution of the playback monitor is 1920x1080 - much bigger than the laptop's screen - which means I either end up scrolling the viewpoint around, or scaling the virtual screen down to make reading text very difficult.

What I'd like to be able to do is to trigger Gnome applications - specifically the Totem video player - via a SSH session, on the current Gnome desktop.

The idea is that I'd like to be able to browse the directories which house my video collection in SSH, launch the player in the session, and have it appear on the monitor.

Ultimately, I'd like to be able to invoke this from a PHP script - thus allowing me to create a (simple) web application on a LAMP installation which would allow me to browse & play my video collection.

Currently, when I try and invoke totem, it seems to want to connect the invocation of the software to the SSH session, which - of course - it can't do.

Any suggestions about where I might start in trying to set this up?

---

### Post by conehead77 on 2010-01-11
So you want to start applications on the remote server and have the GUI on your desktop? I think ssh -x will do what you want.

**edit:** I just checked and it is ssh -X (capital X)

---

### Post by junapp on 2010-01-11
the way I understood it is you want to export your DISPLAY.

I can't test your exact setup right now, but if I go to TTY1 (alt+ctrl+f1), log in, then 
export DISPLAY=:0.0

then run something like "gedit" from that tty1 command line, it appears on the gui in tty7.

I think "who" should give you the list of which displays are in use.

---

### Post by junapp on 2010-01-11
as an aside, I believe vlc has a html backend, as does xbmc. You might be just in it for the exercise, but in the meantime those tools could remove your awkwardness until you get your php script on the go.

edit
[http://xbmc.org/](http://xbmc.org/)
[http://xbmc.org/wiki/?title=The_Web_Interface](http://xbmc.org/wiki/?title=The_Web_Interface)

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)
[http://www.videolan.org/doc/play-howto/en/ch04.html#id310608](http://www.videolan.org/doc/play-howto/en/ch04.html#id310608)

---

### Post by CCKrause on 2010-01-11
> **conehead77 said:**
> So you want to start applications on the remote server and have the GUI on your desktop? I think ssh -x will do what you want.

**edit:** I just checked and it is ssh -X (capital X)

Thanks for the suggestion :)

That would work - I looked into that - but that isn't what I want to do.

I want to use Computer A (my laptop) to trigger applications on Computer B (the media server/HTPC), and have the application appear on the desktop of Computer B (the media server/HTPC large external monitor).

---

### Post by CCKrause on 2010-01-11
> **junapp said:**
> as an aside, I believe vlc has a html backend, as does xbmc. You might be just in it for the exercise, but in the meantime those tools could remove your awkwardness until you get your php script on the go.

edit
[http://xbmc.org/](http://xbmc.org/)
[http://xbmc.org/wiki/?title=The_Web_Interface](http://xbmc.org/wiki/?title=The_Web_Interface)

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)
[http://www.videolan.org/doc/play-howto/en/ch04.html#id310608](http://www.videolan.org/doc/play-howto/en/ch04.html#id310608)

Cool, thanks! :D

I hadn't noticed that VLC and XBMC had web interfaces! I'll have to try this out when I get back from work tonight. This might do the trick.

I **had **tried invoking totem from the command line using the 'DISPLAY=0.0' parameter - to no avail - but I hadn't checked through who to list the displays - I was only guessing that the default display would have been 0.0

---

### Post by junapp on 2010-01-11
> **CCKrause said:**
>  I was only guessing that the default display would have been 0.0
if you are doing it remotely, maybe you need the local ip address in addition to :0.0 - probably not - its just a guess. Good luck with xbmc - I'm loving it.

---

### Post by CCKrause on 2010-01-11
> **junapp said:**
> the way I understood it is you want to export your DISPLAY.

I can't test your exact setup right now, but if I go to TTY1 (alt+ctrl+f1), log in, then 
export DISPLAY=:0.0

then run something like "gedit" from that tty1 command line, it appears on the gui in tty7.

I think "who" should give you the list of which displays are in use.

No luck with this approach

```
totem <video file>
```results in:

```
Cannot open display: 
```and

```
sudo totem <video file> --display=:0.0
```results in

```
(totem:4293): Unique-DBus-WARNING **: Unable to open a connection to the session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.


(totem:4293): Unique-DBus-WARNING **: Unable to connect to the running instance, aborting.

```

---

