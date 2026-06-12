---
title: "which wpa_supplicant release includes wpa_gui?"
date: 2006-04-26
forum: General Help
---

### Post by ASTRXen on 2006-04-26
Hi.
I'm kind of new to linux but have been able do get Ubuntu to work with my WPA encrypted network. I have been using wifi-radar so far. but then i read that wpa_gui exists, witch sound perfect. but when i installed wpa_supplicant it didn't install wpa_gui, just wpa_supplicant, wpa_passphrase and wpa_cli. I've got version 0.4.5 of wpa_supplicant. the latest seems to be 0.4.8?

shuld i download the 0.4.8 release to get wpa_gui or can i get it in any other way?

---

### Post by tobey on 2006-04-26
I have everything installed (wpa_gui, wpa_supplicant, ...) and still when I startup wpa_gui ( terminal ==> wpa_gui ==> enter) the gui opens, but it cant find my wireless card...
My wireless card is a AR5212 (ath0) and should be fully supported by wpa_gui but I get this in the terminal:
```
tobey@tobey-laptop:~$ wpa_gui
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Failed to open control connection to wpa_supplicant.
PING failed - trying to reconnect
PING failed - trying to reconnect

```
I can connect to my own ap (I've changed it from wpa to wep) but @ school I can't log-on with linux, that's the only reason I keep windows...

I'm sorry I post this here, but I'm really desperate and confused, I hope somebody can help me with a foolproof howto or something of that kind, I would thank you and put your image on a pedestal and worship you all day long...
(btw I'm running the Dapper Drake 6.06 release, beta, but others seem to get the wpa_gui to work, but nowhere a decent howto to find, and I've searched... Loads of searching. All this I did with my personal abilities, so I might have overlooked something, if so sorry... I'll stop wanking and ranting on about this, I just hope you understand my desperateness and so...)

Cheers!

<edit>
Maybe this could help too?
```
tobey@tobey-laptop:/etc$ wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
ioctl[SIOCSIWPMKSA]: Operation not permitted
ioctl[SIOCSIWMODE]: Operation not permitted
Could not configure driver to use managed mode
SIOCSIFFLAGS: Permission denied
Could not set interface 'ath0' UP
ioctl[IEEE80211_IOCTL_SETPARAM]: Operation not permitted
ioctl[SIOCSIWAP]: Operation not permitted
SIOCSIFFLAGS: Permission denied
Failed to initialize driver interface
tobey@tobey-laptop:/etc$

```
</edit>

---

### Post by testube_babies on 2006-04-26
Have you tried the network-manager package?  It works great for me with wireless + WPA. It might only support Dapper, though.  Here's an install script: [http://www.ubuntuforums.org/showthread.php?t=144820&highlight=network+manager+script](http://www.ubuntuforums.org/showthread.php?t=144820&highlight=network+manager+script)

---

### Post by tobey on 2006-04-27
I installed network-manager from the 'applications=>add/remove' window (so if it's the right thing it ought to work as the os did it for me and the os is considered über)
but when I run nm-applet there is an error:
"the networkmanager applet could not find some required resources. It cannot continue." as an x-window
```
tobey@tobey-laptop:~$ nm-applet

** (nm-applet:7298): WARNING **: Icon nm-vpn-lock missing: Icon 'nm-vpn-lock' not present in theme

(nm-applet:7298): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```in the terminal window

I'm really getting angry about not getting wpa to work decently :(...

---

### Post by Rinzwind on 2006-04-27
TOBEY: [https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/37128](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/37128)

It's allready solved ;)

Quote from there: 
> 
I've had the same problem and solved it by running gtk-update-icon-cache on all directories in /usr/share/icons.

The package should probably run it on the directory where it adds its icons.


---

### Post by tobey on 2006-04-27
Well...
That took care of the error messages allright :p but now the application just won't launch

---

### Post by enrivar on 2006-05-08
"X Error: baddevice" messages are probably due to uncommented devices in /etc/X11/xorg.conf.
When I upgraded to dapper from breezy I found a lot of Wacom input devices defined and uncommented in xorg.conf. Commenting out resolved the problem.

Hope this could help.

enrico
  
[QUOTE=tobey]I have everything installed (wpa_gui, wpa_supplicant, ...) and still when I startup wpa_gui ( terminal ==> wpa_gui ==> enter) the gui opens, but it cant find my wireless card...
My wireless card is a AR5212 (ath0) and should be fully supported by wpa_gui but I get this in the terminal:
```
tobey@tobey-laptop:~$ wpa_gui
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Failed to open control connection to wpa_supplicant.
PING failed - trying to reconnect
PING failed - trying to reconnect

```
</edit>[/QUOTE]

---

