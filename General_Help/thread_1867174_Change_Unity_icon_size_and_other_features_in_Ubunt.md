---
title: "Change Unity icon size and other features in Ubuntu 2D?"
date: 2011-10-22
forum: General Help
---

### Post by NickUhlig on 2011-10-22
I'm not going to mince words here, I absolutely hate the newest release, but I've decided to stick with it and get used to the new system (I had 11.04 running under Gnome Classic but it looks like they have hamstrung that by making it ugly and almost unusable in the new release).

My biggest problems are the complete lack of theming/colour change options (I used the Gnome tweaker but I should **not** have to install extra software to get functionality that was present in a previous release), the ruining of the Gnome Classic layout with an ugly, thick task bar, different/stupid menu layout, and the clock somehow centred in the bar, and finally, the complete lack of customization abilities for Unity under Ubuntu 2D.

I have 11.10 installed on an older machine, and it simply cannot handle the full set of animations and graphics features with the Ubuntu 3D.  So I run it in 2D, but now I have this enormous ugly Unity taskbar on the side, and CCSM does absolutely **NOTHING** to change that.  I can't change icon size, or backlight options, or opacity, or even where the dock appears.

If anyone has solutions to the final problem I would be grateful to hear them.

If you know how to get Gnome CLassic to work with the original menus (Applications, System, Places), and without having the clock in the centre of the taskbar, I would also be interested in hearing that.

---

### Post by haqking on 2011-10-22
> **NickUhlig said:**
> I'm not going to mince words here, I absolutely hate the newest release, but I've decided to stick with it and get used to the new system (I had 11.04 running under Gnome Classic but it looks like they have hamstrung that by making it ugly and almost unusable in the new release).

My biggest problems are the complete lack of theming/colour change options (I used the Gnome tweaker but I should **not** have to install extra software to get functionality that was present in a previous release), the ruining of the Gnome Classic layout with an ugly, thick task bar, different/stupid menu layout, and the clock somehow centred in the bar, and finally, the complete lack of customization abilities for Unity under Ubuntu 2D.

I have 11.10 installed on an older machine, and it simply cannot handle the full set of animations and graphics features with the Ubuntu 3D.  So I run it in 2D, but now I have this enormous ugly Unity taskbar on the side, and CCSM does absolutely **NOTHING** to change that.  I can't change icon size, or backlight options, or opacity, or even where the dock appears.

If anyone has solutions to the final problem I would be grateful to hear them.

If you know how to get Gnome CLassic to work with the original menus (Applications, System, Places), and without having the clock in the centre of the taskbar, I would also be interested in hearing that.

themes will be put on hold really as they are in gtk2 and we need gtk 3 so you will have to wait, if you upgraded then that might be an issue over a fresh install which wont have to deal with your currenty theme setup.

As for ccsm then in the unity plugin you should be able to change the backlight and resize the icons

---

### Post by beew on 2011-10-22
> **haqking said:**
> 

As for ccsm then in the unity plugin you should be able to change the backlight and resize the icons

ccsm and compiz doesn't work on Unity2d, I think.

---

### Post by NickUhlig on 2011-10-22
> **beew said:**
> ccsm and compiz doesn't work on Unity2d, I think.


Correct.  This is what I was asking about.  It works fine in Ubuntu 3d, but not when I run the session in 2D.

---

### Post by haqking on 2011-10-22
> **NickUhlig said:**
> Correct.  This is what I was asking about.  It works fine in Ubuntu 3d, but not when I run the session in 2D.

ahh gotcha missed that bit ;-)

---

### Post by NickUhlig on 2011-10-22
bump

---

### Post by Frogs Hair on 2011-10-22
This will give you some options for Unity 2D [http://www.omgubuntu.co.uk/2011/10/unity-2d-tweak-app-updated-for-11-10/](http://www.omgubuntu.co.uk/2011/10/unity-2d-tweak-app-updated-for-11-10/)

---

### Post by StevenD on 2011-10-22
I have tried to get somewhere with my 11.10 woes on two other topics and after working on this mess for 8 hours I still don't have it working. When I upgraded to this latest version last night it worked for a short while and I was able to get the icon size down in the Launcher to as small as it would go. Much better than the big doofy default size. That only last a short time then when I rebooted now all I got was some menu items in the top left corner and nothing else I tried several suggested methods for fixing this but none of them worked. I finally found out I could choose Unity 2D when logging on only to discover as others have pointed out that CCSM doesn't work. :mad:

So then at another suggestion I decided to scrap the update and do a clean install. Is that working? No. A big part of my problem I'm sure is that I have Ubuntu installed on an external hard drive and I can the USB stick to work.

It's a :cry:ing shame because I like this new upgrade and was really and was hoping it would work. All I really wanted was to get smaller icons in the launcher.

---

### Post by kherring7383 on 2011-10-22
Something that I have found to help with the Launcher Icon size is install the beta version of Ubuntu Tweak that can be used to resize the icons. 

Another option is the Unity plugin in Compiz. However, Compiz is known to have some bugs with the new release that will crash the desktop and force you to reset it. Over the last few days, I've installed 11.10 about 4 times and with each I have managed to crash it until I found settings that seem to be stable. 

As for the ugly Dash icon size there's really no fix for that yet so I avoid using it and instead use Docky to run my favorite apps and use the Launcher as a way to run system configuration apps I commonly use which for me seems to work. 

Lastly, I've used Ubuntu for several years now and with each release there's always some resistance to the change and like many I too really didn't like Unity but after cleaning it up with smaller icons some transparency effects and auto hide it's Ok so I'll stick with it and install the updates as they are released.

---

### Post by deserthowler on 2011-10-22
I'm using Unity 2D in Ubuntu 11.10.  From what I understand Unity 2D has nothing to do with compiz but runs directly on the gtk3 tool kit.  I found information that worked in 11.04.  When I applied it to 11.10, I got a blank white menu bar.  My understanding is resizing launch bar icons in Unity 2D is not doable right now.  Hopefully this will happen by the time 12.04 is released.  There might be a hack coming soon from somewhere but I don't have one yet.

In the mean time I use my custom fvwm window manager and stick to Ubuntu 10.04 as my main screen on my working machine.

Earl

---

### Post by bonzini on 2012-03-25
See [http://ubuntuforums.org/showthread.php?t=1943423](http://ubuntuforums.org/showthread.php?t=1943423)

---

