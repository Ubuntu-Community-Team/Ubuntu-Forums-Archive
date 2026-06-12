---
title: "Who can crack this..."
date: 2009-11-03
forum: General Help
---

### Post by emigrant on 2009-11-03
hi all,
any body know how to enable 'extra visual effects' work simultaniously in multiple user accounts?

i mean at a time it works only for one user. to make it work to the other i have to log out from one account :(

specs:

core2duo E8400
2GB RAM
vga 256mb

restricted hardware drivers not listed.

thank you very much for your help.

---

### Post by dbyjazz on 2009-11-03
could you please give more info on what your problem is?

---

### Post by emigrant on 2009-11-03
thanks for your input :)
my problem is,
i have 4 user accounts my my system.
and you know visual effects right? which have 3 setups (none, normal, extra).
i can enable 'extra' only in one account (if two accounts are logged in at the same time). to enable 'extra' on the other account, i have to log off from the one in which 'extra' is alreay working.

hope this is clear ??? :(

---

### Post by dbyjazz on 2009-11-03
try downloading this

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by P4man on 2009-11-03
It works just fine here, compiz on multiple logged in accounts. It does not work with the guest account though, im not sure why.

---

### Post by emigrant on 2009-11-03
> **dbyjazz said:**
> try downloading this

```
sudo apt-get install compizconfig-settings-manager
```

man its already installed :o

---

### Post by dbyjazz on 2009-11-03
that's really weird. I'm sorry but I don't have any other ideas. please report a bug [here]("https://launchpad.net/ubuntu")

---

### Post by newboymak on 2009-11-03
code:
#!bin/sh
SECS=5
INTERVAL=5
OS=$(uname)

case $OS in 
AIX|HP-UX|SunOS)
F1=2
F2=3
F3=4
F4=5
echo "\nthe operating system is ...$OS"
;;

Linux)
F1=3
F2=4
F3=5
F4=6
echo "\nthe operating system is ...$OS"
;;

*) echo "error:$OS is not a supportes os"
echo "\n\t...exiting..\n"
exit 1
;;
esac


echo "\ngathering cpu stats using sar ...\n"
echo "there are $INTERVAL sampling periods with\n"
echo "each inter lasting $SECS sec\n"
echo "...pls wait while gathering stats...\n"

sar $SECS $INTERVAL | grep Average \
| awk '{print $'$F1', $'$F2', $'$F3', $'$F4'}' \
| while read FIRST SECOND THIRD FOURTH

do
case $OS in
AIX|HP-UX|SunOS)
echo "\n user part is ${FIRST}%"
echo "\n system part is ${SECOND}%"
echo "\n I/O wait  is ${THIRD}%"
echo "\n Idle time is ${FOURTH}%"
;;
LINUX)
echo "\n user part is ${FIRST}%"
echo "\n nice part is ${SECOND}%"
echo "\n system part is ${THIRD}%"
echo "\n Idle time is ${FOURTH}%"
;;
esac 
done
echo



i have a strange problem, the while loop taking FIRST SECOND THIRD FOURTH as arguments is not working , i tried commands individually , they work to produce to give system performance data.

wheni try running it as a whole it wil exit without giving any output systemperformance data :( can anyone figure out wat is wrong . plz help.
i am trying it from a day :(

---

### Post by newboymak on 2009-11-03
the operating system is ...Linux

gathering cpu stats using sar ...

there are 5 sampling periods with

each inter lasting 5 sec

...pls wait while gathering stats...

[The output ends here!]
i am using ubuntu 8.1

---

### Post by P4man on 2009-11-03
newboymak, I have no idea at all what you asking or saying, but its clearly not related to this thread, so please dont hijack it, start your own thread and make som effort clarifying what you are doing or trying to achieve.

---

### Post by P4man on 2009-11-03
edit: wrong thread sorry

---

### Post by emigrant on 2009-11-04
> **P4man said:**
> It works just fine here, compiz on multiple logged in accounts. It does not work with the guest account though, im not sure why.

will this give a clue for why doesn't it run on multiple logged in accounts.
this is what i got when i tried to run compiz from the second account while account one is logged in.

```
$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000027 (awn_elemen)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

```

---

### Post by P4man on 2009-11-04
Nor really. But do you have onboard intel GPU? It seems to have a limitation relating to using compiz when the desktop size is > 2048 in either direction. Now im wondering if you start a new session if the old one is still counted. Perhaps you could try something silly: set your screen resolution to 800x600 and see if you can then enable compiz on more than one user account?

---

### Post by m4tic on 2009-11-04
Is this a quiz or you really do have a problem?

---

### Post by emigrant on 2009-11-04
first let me thank you for being helpful for everybody here :)

> **P4man said:**
> Nor really. But do you have onboard intel GPU? It seems to have a limitation relating to using compiz when the desktop size is > 2048 in either direction. 

yeah i have and i think its disabled since the seperate one is now woking.

> **P4man said:**
>  Now im wondering if you start a new session if the old one is still counted. Perhaps you could try something silly: set your screen resolution to 800x600 and see if you can then enable compiz on more than one user account?

i tried giving 800x600 in the second account but still no avail :(

---

### Post by emigrant on 2009-11-04
> **m4tic said:**
> Is this a quiz or you really do have a problem?
i really do have this problem. perhaps the most irritating one ever ;)

---

### Post by P4man on 2009-11-04
are the other accounts administrator accounts? Does that change anything?
I guess not but Im running out of ideas.. perhaps head to launchpad and file a bug..

---

### Post by emigrant on 2009-11-04
@ P4man,
thank you iv already reported bug.
one last quiz:
do you think i should install some graphic card drivers although 'hardware drivers' won't list any.?

---

### Post by Giblet5 on 2009-11-04
Seems obvious, but...

Are you trying to log in to the second account from another workstation (XDMCP) ..... or are you trying both from the same Monitor/Keyboard/Mouse/VideoCard?

The second one works here.

[COLOR="DarkRed"]**Make sure the second user (eg, "user2") owns everything in their home directory, including /home/user2/.config and /home/user2/.gconf*...**[/COLOR]

---

### Post by HiImTye on 2009-11-04
are you using the default drivers? more to the point do you have DRI and are you able to set resolutions on your primary login?

---

### Post by emigrant on 2009-11-04
> **HiImTye said:**
> are you using the default drivers? more to the point do you have DRI and are you able to set resolutions on your primary login?
since i installed jaunty from live cd, i didnt install any additional drivers nor did i update the system.
also the 'system>admin>hardware drivers' doesnt show any.

yes, im able to set resolution in the primary account as well as other non privilege accoutns.

i don't know whether i have DRI or not :(

---

### Post by Giblet5 on 2009-11-04
The issue of what driver is being used seems moot.

OP says he can use Extra Effects on at least one account.

If the Extra effects can be enabled by any user of a given hardware, then drivers are not going to cause the reported behavior.

---

### Post by HiImTye on 2009-11-04
```
glxinfo | grep rendering
```

---

### Post by emigrant on 2009-11-04
direct rendering yes
:)

---

### Post by Giblet5 on 2009-11-04
Please open a terminal window, execute the following command, and select/copy the output.

Then click New Reply below, and click the "#" at the top of the reply editor and paste that output. Then click "Submit Reply".

```
xdpyinfo
```

---

### Post by emigrant on 2009-11-04
@ Giblet5, im laughing at how you asked me to do that :lolflag:
```

name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10600000
X.Org version: 1.6.0
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x4400005, revert to Parent
number of extensions:    28
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    DRI2
    GLX
    Generic Event Extension
    MIT-SCREEN-SAVER
    MIT-SHM
    RANDR
    RECORD
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    X-Resource
    XC-MISC
    XFIXES
    XFree86-DGA
    XFree86-DRI
    XFree86-VidModeExtension
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1024x768 pixels (271x203 millimeters)
  resolution:    96x96 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x7c
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0x7a803f
    KeyPressMask             KeyReleaseMask           ButtonPressMask          
    ButtonReleaseMask        EnterWindowMask          LeaveWindowMask          
    ExposureMask             StructureNotifyMask      SubstructureNotifyMask   
    SubstructureRedirectMask FocusChangeMask          PropertyChangeMask       
  number of visuals:    16
  default visual id:  0x21
  visual:
    visual id:    0x21
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x22
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6e
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x6f
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x70
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x71
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x72
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x73
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x74
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x75
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x76
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x77
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x78
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x79
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x7a
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5d
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits

```

---

### Post by Giblet5 on 2009-11-04
How did you create the second user account?

I can duplicate the behavior you describe by creating a duplicate entry in /etc/passwd (same uid/gid), changing the username and the home directory, creating that home directory, then switching users to that account.

The system thinks that one user is trying to start compiz twice.


PS: Could you perform the user switch that doesn't work, attempt to enable Extra effects, then post the last 100 lines (approx) of ~/.xsession-errors please?

---

### Post by emigrant on 2009-11-04
i created all the non-primary accounts by going to 'create user'


```
second_user@emigrant-desktop:~$ less /home/second_user/.xsession-errors | tail -100
``````

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-kagWm0/socket
SSH_AUTH_SOCK=/tmp/keyring-kagWm0/socket.ssh
Window manager warning: Failed to read saved session file /home/second_user/.config/metacity/sessions/10c07026fefdda0cfa125735275119908900000155770019.ms: Failed to open file '/home/ilhar/.config/metacity/sessions/10c07026fefdda0cfa125735275119908900000155770019.ms': No such file or directory
** (gnome-panel:15789): DEBUG: Adding applet 0.
** (gnome-panel:15789): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:15789): DEBUG: Adding applet 1.
** (gnome-panel:15789): DEBUG: Adding applet 2.

** (nm-applet:15799): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

** (gnome-panel:15789): DEBUG: Adding applet 3.
** (gnome-panel:15789): DEBUG: Adding applet 4.
** (gnome-panel:15789): DEBUG: Adding applet 5.
** (gnome-panel:15789): DEBUG: Adding applet 6.
** (gnome-panel:15789): DEBUG: Adding applet 7.
** (gnome-panel:15789): DEBUG: Adding applet 8.
** (gnome-panel:15789): DEBUG: Adding applet 9.

(gnome-panel:15789): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:15789): DEBUG: Adding applet 10.
** (gnome-panel:15789): DEBUG: Adding applet 11.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (gnome-panel:15789): DEBUG: Adding applet 12.
** (gnome-panel:15789): DEBUG: Adding applet 13.

** (nautilus:15790): WARNING **: Unable to add monitor: Not supported

(gnome-appearance-properties:15855): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:15855): appearance-properties-WARNING **: Unknown Tag: _name

There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
evolution-alarm-notify-Message: Setting timeout for 26419 1257379200 1257352781
evolution-alarm-notify-Message:  Thu Nov  5 05:30:00 2009

evolution-alarm-notify-Message:  Wed Nov  4 22:09:41 2009

** (update-notifier:15822): DEBUG: crashreport_check

```

---

### Post by Giblet5 on 2009-11-04
I was wrong. It is driver related.

Screen 1 has no Xgl capabilities and I suspect that the intel driver will only allow accelerated extensions on one screen at a time.

I guess it's easy to get spoiled by an expensive video card. That works here with the 185 nvidia driver.

---

