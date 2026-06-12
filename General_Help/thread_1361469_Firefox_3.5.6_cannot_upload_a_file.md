---
title: "Firefox 3.5.6 cannot upload a file"
date: 2009-12-22
forum: General Help
---

### Post by sazawal on 2009-12-22
Hi,

I am using firefox 3.5.6 in Ubuntu 9.10. I have this problem since few days that I cannot upload any photo or file on the internet, even attaching a file in the mail creates a problem. When I click "browse" for the file in the computer the window appearing does not load and it then hangs my firefox. I am forced to quit the application finally. Following are the list of my add ons installed.

Extensions:
Compact Menu 2 2.3.3
Cooliris 1.11.5
DownloadHelper 4.6.5
Download Statusbar 0.9.6.5
FoxyProxy Basic 1.3.1
StumbleUpon 3.52
Ubuntu Firefox Modifications 0.8

Themes:
iPox 2.20091115

Languages:
Firefox(en-GB) 3.5.2
Xulrunner(en-GB) 1.9.1.2

Plugins:
Adobe Reader 9.1
Cooliris
Divx Web Player
QuickTime Plug-in 7.2.0
Shockwave Flash
VLC Multimedia Plugin(compatible Totem 2.28.2)
Windows Media Player Plug-in 10(compatible; Totem)

Please someone help me out

---

### Post by lovinglinux on 2009-12-22
Cooliris is known to cause serious problems, sometimes preventing Firefox to start. Nevertheless, it doesn't seem to be it.

There are some things you can do to determine the culprit. Close Firefox and then:

1) Start Firefox in safe mode from a terminal

```
firefox -safe-mode
```

If the problem disappears, then it's probably an extension or plugin. I would think about java in particular.

2) Start Firefox using a clean profile

```
firefox -P
```

This will launch the profile manager, from where you can create and start a new profile. if the problem disappears then it's probably a corrupted file on your profile folder or a particular option in Firefox settings.

3) Open **about:config** in the address bar, then type **ui.allow_platform_file_picker** in the filter form and set this option to false.

If the problem disappears, then it could be a problem with Nautilus, although I'm not sure how this would behave on Gnome (I use KDE).

Post your results.

Also see [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by sazawal on 2009-12-22
Thanks for the reply ......

My firefox is okay now

---

### Post by lovinglinux on 2009-12-22
> **sazawal said:**
> Thanks for the reply ......

My firefox is okay now

Do you mind sharing the solution?

---

### Post by sazawal on 2009-12-22
I am sorry. I dont know it went fine automatically. I removed few addons earlier including

1.Prism for google talk
2.Tiny Menu

I also cleared the cache and removed all History.
I dont understand, it was not working earlier when I checked after cleaning up the firefox but today it started working fine.

---

