---
title: "Nvidia-drivers stopped working, and X aswell, just like that."
date: 2010-12-18
forum: General Help
---

### Post by DarkAmbient on 2010-12-18
Everything worked fine yesterday when i shutdown the computer.

This morning: My X-server couldn't find my screen. Searched alot and tried alot to solve this.

Found this other thread:
[http://ubuntuforums.org/showthread.php?t=1625877](http://ubuntuforums.org/showthread.php?t=1625877)

But what worked for him/her didn't solve my problem.

I've tried to purge everything I could find installed using 'aptitude search nvidia', didn't work. However, removing the /etc/X11/xorg.conf file manually as root, got X to find my screen. But without any active driver. Then I tried to (re) install the (Nvidia) 173 or current -driver again, but it got me back right where i started. That is, On start-up, no screen found and the console starts.

After the process of getting x running again (but without any active nvidia drivers) I tried the nvidia drivers from nvidia.com. Downloaded them, rebooted into a root-console. Entered some needed command, something like 'initlev 3'. Then I ran the nvidias-173 install script. After that the only thing I get on my monitor is a message saying "out of range".

So I tried using 'nvidia-xconfig' (which i think (if needed it) writes a new xorg.conf, right?) Then 'nano xorg.conf' and adding Option "UseEdit" "FALSE" in the Device section of the conf file. Read that somewhere that it could help x to find the monitor. Then Save and reboot. But didn't help anything. I can still enter cli-shell using ctrl+alt+F* though.

Think that should cover the most of my day so far...


Some output from commands is:
(typing this from another computer whilst reading on the messed-up computer, so pardon any typos)

lspci | grep VGA gives me:
```
01:00.0 VGA compitable controller: nVidia Corporation NV34 [GeForce FX 5200] (rev 1) 
```

And yes it's an old computer. ;-)


Not sure of any other commands that could be of use for the output, regarding this.

Oh almost forgot, I tried starting jockey-gtk from the console. Just for the sake of the output. And it says that x-server is allready active for display 0. But as said, all I get is a msg saying "out of range".

Any ideas?

---

### Post by clrg on 2010-12-18
Your X server is up and running but using a resolution your screen doesn't support. Try setting the resolution and refresh rate manually in xorg.conf.

---

### Post by DarkAmbient on 2010-12-18
> **clrg said:**
> Your X server is up and running but using a resolution your screen doesn't support. Try setting the resolution and refresh rate manually in xorg.conf.

Thanks for answering. Searched on it and found this: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Didn't get it to work though, even though he in that post had the same nvidia card/model as me. 

Tried both various resolutions & refresh-rates. Then tried both restarting computer or just the x server with 'service gdm start'

I'll just re-install Ubuntu from scratch. Got all my projects i work on backed-up remotely, and no personal stuff on it.

Still curious on what went wrong from the start though. Must be related to some update through the update-manager i went through yesterday?

---

### Post by DarkAmbient on 2010-12-18
Well, here I am again. Re-installed Ubuntu from scratch. Sadly it didn't solve the problem... my guess is that it has something to do with the (my) newest kernel update. (2.6.35.23-generic) Just guessing.

Got a 640x480 resolution after installing the nvidia 173 drivers. But actually got the x-server to behave alot better after some tweaking in xorg.conf. Now im running 1680x1050 as I did before the problem occured. I suspect I need to fine-tweak it further though, as right now my eyes hurt a bit looking at the screen. But not too much ;)


Figuring out how to tweak is thanks to this page: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973) that I mentioned earlier. Thanks to "clrg" who enlightened me earlier, and gave me a good lead.


So, if it's of worth to anyone, what I did was.

In the no-gui console:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
to backup the xorg config file.

To edit xorg.conf using nano:

```
sudo nano /etc/X11/xorg.conf
```

In nano, ctrl+o saves the file. You exit with ctrl+x.


and this was how the file "looked" before i changed anything. (after a fresh install of Ubuntu)

> Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


After I altered it some and got x-server to run (And no more messages saying "Out of Range"), it looks like this:

> Section "Monitor"
    Identifier    "monitor0"
    HorizSync     31-75
    VertRefresh    60-61
EndSection


Section "Screen"
	Identifier	"Screen0"
	Device		"device0"
	Monitor		"monitor0"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"device0"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection



After your happy with the altering of xorg.conf:

```
sudo service gdm start
```

to start the x-server.

if it still wont work, press ctrl+alt+F1.

in case the x-server runs but isn't working, type:

```
sudo service gdm stop
```

to stop it.

Then try edit xorg.conf in nano again. Then try to start x, again.


I got it to work with first adding the Monitor section. In the link further up, the values were:

> HorizSync     31-101
VertRefresh    60-160

I lowering them to this it worked for me:

> HorizSync     31-75
VertRefresh    60-61

Then I renamed some other stuff... the link further up explains more on tweaking your xorg.conf file correcly. Not sure whats the best settings (if any). But I'm happy aslong as its working.

However I'm glad for any input on this one... advice or anything. As I mentioned earlier, it feels like its a bit "annoying" for my eyes to watch my flat-screen" now. It wasnt like that before.

Anyway, hope someone finds this useful. cheers


**Edit: after this I opened the 'nVidia X server settings' under system->administration. And clicked 'X Server Display Configuration' then picked resolution and 'save to X Configuration File'. Thought everything would mess up again after a reboot.. but instead everything worked like a charm. :-)**

---

