---
title: "Slow Boot / Shutdown - Oneiric"
date: 2011-10-15
forum: General Help
---

### Post by crjackson on 2011-10-15
Man it takes this version a month of Sundays to boot, reboot or shutdown (2D or not).

Is everyone having this problem?  Is there anything that can be done to improve this?

Thanks

---

### Post by crjackson on 2011-10-16
Okay, so no one seems to have clue. Well can some one tell me how to make Unity2D the default?

My slow lappies auto login, in order to get the 2D option, I have to log out, then select the 2D session and login again.

I would be nice if it remembered my last choice but I guess that's not an option any more.

So, now the question is, how do I set my preferred session (Unity2D for now) as the default selection? This way it would boot to the 2D session and make my experience better...

Thanks

---

### Post by crjackson on 2011-10-16
Well, I figured out how to make 2D the default session, that's progress I suppose.

Thanks to those who chimed in with a suggestion...

The answer is:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s ubuntu-2d
```

---

### Post by MidnightFirepaw on 2011-10-16
I noticed a 5 second startup time increase and a ten second shutdown time increase, however it could be startup programs too. I find the wait worth it however *gnome 3 FTW*

---

### Post by crjackson on 2011-10-16
> **MidnightFirepaw said:**
> I noticed a 5 second startup time increase and a ten second shutdown time increase, however it could be startup programs too. I find the wait worth it however *gnome 3 FTW*

Mine takes about 3 minutes to boot, and 5 minutes to shutdown. It's ridicules for me.

---

### Post by oldgeekster on 2011-10-16
> **crjackson said:**
> Mine takes about 3 minutes to boot, and 5 minutes to shutdown. It's ridicules for me.Just out of curiosity, what do you get when you open a terminal and run ```
*[I]/usr/lib/nux/unity_support_test -p*[/I]
```

And yeah, my system responds with "yes" to all items - now on 11.10, seems to take about 5-10 seconds longer to boot up/shut down than it did on 11.04.....

---

### Post by crjackson on 2011-10-16
> **oldgeekster said:**
> Just out of curiosity, what do you get when you open a terminal and run ```
*[I]/usr/lib/nux/unity_support_test -p*[/I]
```

And yeah, my system responds with "yes" to all items - now on 11.10, seems to take about 5-10 seconds longer to boot up/shut down than it did on 11.04.....

```
charles@charles-MS-7100:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 8800 GT/PCI/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 280.13

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
charles@charles-MS-7100:~$ 

```

---

### Post by oldgeekster on 2011-10-16
> **crjackson said:**
> ```
charles@charles-MS-7100:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 8800 GT/PCI/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 280.13

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
charles@charles-MS-7100:~$ 

```Looks pretty darned close to my own, so that certainly didn't give us anything to base an explanation on.  What do you have in "Startup Applications"?

---

### Post by Call Me Ishmael on 2011-10-17
Me too. Probably an NVIDIA driver glitch?
```
andrea@andrea-laptop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 8400M GS/PCI/SSE2
OpenGL version string:  3.3.0 NVIDIA 280.13

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

---

### Post by mjuhasz on 2011-10-17
In order to bring back shutdown speed to what you got used to in Natty just insert this line into /etc/init/network-manager.conf:
```
stop on runlevel [6]
```

Mine looks like this:

```

# network-manager - network connection manager
#
# The Network Manager daemon manages the system's network connections,
# automatically switching between the best available.

description	"network connection manager"

start on (local-filesystems
	  and started dbus)
stop on stopping dbus
stop on runlevel [6]

expect fork
respawn

exec NetworkManager

```

---

### Post by crjackson on 2011-10-20
> **mjuhasz said:**
> In order to bring back shutdown speed to what you got used to in Natty just insert this line into /etc/init/network-manager.conf:
```
stop on runlevel [6]
```

Mine looks like this:

```

# network-manager - network connection manager
#
# The Network Manager daemon manages the system's network connections,
# automatically switching between the best available.

description	"network connection manager"

start on (local-filesystems
	  and started dbus)
stop on stopping dbus
stop on runlevel [6]

expect fork
respawn

exec NetworkManager

```

Thanks for the reply. I made the modification and it didn't help for the most part.

I've found that the only way to shut down normally and quick is:

sudo shutdown -P now

---

### Post by vauge on 2011-10-21
Watching this thread closely. I have the same issue - very slow boot/shutdown. I have an 8600 nvidia. 

It also takes forever again to get to Gnome Shell after login.

---

### Post by rattskjelke on 2011-10-21
Xubuntu does the same thing, I think. On shutdown it hangs on the splash screen/activity indicator for about 10 seconds and during that whole time the DSL modem is constantly sending or receiving data. I haven't had this happen with any other distro that I have tried. Does Ubuntu phone home whenever it is shut down now? Is it spying on me?

---

### Post by ubupirate on 2011-10-21
> **rattskjelke said:**
> Xubuntu does the same thing, I think. On shutdown it hangs on the splash screen/activity indicator for about 10 seconds and during that time the DSL modem is sending or receiveing or receivingf data. Does Ubuntu phone home whenever it is shut down? Is it spying on me?

It seems to be affecting all editions of *ubuntu with 11.10. Slow shutdown/bootup times in Ubuntu, Kubuntu, Xubuntu and Lubuntu.

---

### Post by Diskdoc on 2011-10-25
I'm having slowness trouble with Oneiric as well. Getting to the login-screen (booting X) is ok but after logging in it takes _several minutes_ of harddrive trashing before I arrive at a usable desktop! :-O

I'm wondering if this has something to do with system databases maybe? Or upstart? Or that I moved a lot of mails to Evolution (although it doesn't autostart).

(edit)

I attached the latest bootcharts from Natty and Oneiric, in case anyone can make sense of them :-p

---

### Post by Flywaver on 2011-10-25
> **mjuhasz said:**
> In order to bring back shutdown speed to what you got used to in Natty just insert this line into /etc/init/network-manager.conf:
```
stop on runlevel [6]
```

Thanks mjuhasz for the tip...although I have no idea what it means! :-k

I am also having startup/shutdown slowliness...is it just me or it has gotten worst in the last 2 versions? :???:

---

### Post by Flywaver on 2011-10-25
why does my test shows this?

```
OpenGL renderer string: GeForce 6800 GS/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 280.13
``` :confused:

Is it because I have a 6800 card?

---

### Post by crjackson on 2011-10-25
> **Flywaver said:**
> why does my test shows this?

```
OpenGL renderer string: GeForce 6800 GS/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 280.13
``` :confused:

Is it because I have a 6800 card?

No it's not your video card. I have 12 computers all with the same slowness issues and with video cards from nVidia, ATI, and Intel. It seems Ubuntu has no favourites time time around.

---

### Post by rattskjelke on 2011-11-03
> **rattskjelke said:**
> Xubuntu does the same thing, I think. On shutdown it hangs on the splash screen/activity indicator for about 10 seconds and during that whole time the DSL modem is constantly sending or receiving data. I haven't had this happen with any other distro that I have tried. Does Ubuntu phone home whenever it is shut down now? Is it spying on me?

Today I found out you can disable the splash screen and see plain text stuff (terminal?) during boot and shutdown.
When it hangs on shutdown I see this:
```
* Asking all remaining processes to terminate...        [ fail ]
```With *fail* in red text.
How do I know what failed? Is there some log I can check?

---

