---
title: "Change default keyboard layout"
date: 2010-06-21
forum: General Help
---

### Post by Janeleaper on 2010-06-21
This was a fresh install of 10.04.

I set the keyboard for UK Intl for use with a cordless keyboard.  The keyboard turns out to be incompatible with 10.04, because it does not type the ' and " signs correctly.  I tried another cordless keyboard with the same result.

I gave up and attached a plug in usb keyboard which has a USA layout.  I added USA International layout and set to apply system wide.  

The problem is that whenever the computer is shut down and restarted it reverts to the UK setting, and even though I'm using a USA keyboard it still does not type the ' and " signs correctly.  

Can I fix this without doing a full re-install?

---

### Post by jesuisbenjamin on 2010-06-22
Hi there,

The physical layout of the keyboard you use should not matter (the model is what matters as far as hardware is concerned).

Did you select the USA layout as default? Did you remove the UK layout?
Also are you sure the actual layout should correspond to your expectations? What i mean is: if you print-preview the USA keyboard, does the layout correspond to what you want? There are variants for the USA keyboard, perhaps you need to select another one?

It would be better to be sure of what the issue is before re-installing :)

---

### Post by fducloux on 2010-09-11
hi, i'm having the exact same problem.
I've set my ubuntu keyboard to USA intl - dead keys, and removed the GB keyboard
and every single time i reboot, or just log out and back in, i get the GB keyboard as default.

it's rather annoying!
i think this started after the last software updates..
any ideas where to look for?

---

### Post by j4ck455 on 2010-09-12
Exact same problem here, also started off with a UK layout cordless keyboard (Logitech) that I ditched and switch for a corded US Intl. keyboard (also Logitech), and despite removing the "GBr" layout and making "USA" the default system wide, when I reboot "GBr" reappears as the default again.

It is extremely annoying.

I'm also using:> NVIDIA accelerated graphics driver (version current) [Recommended]and I'm wondering if that is somehow overriding the keyboard settings?

I have tried to find relevant settings in /etc; /etc/kdb; /etc/X11, but so far I have not found out where the keyboard layout setting is actually saved or read from.

<added>
[LIST]
[*]In my PC's /etc/X11/xorg.conf, the following comment exists in several places:> # commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
[*]My PC's /etc/default/console-setup:> # The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="logicd"
XKBLAYOUT="**[COLOR="Red"]gb[/COLOR]**"
XKBVARIANT=""
XKBOPTIONS="grp:alts_toggle"
[/LIST]
</added>

---

### Post by jskala on 2011-05-13
Thanks j4ck455, it helped me a lot. I just want to add, that you can find the settings in /etc/default/keyboard on Ubuntu 11.04 Natty.

Update:
Too bad. I just restarted my computer and the Czech keyboard (in my case) is still the default. I even tried removing it completely, leaving only the US keyboard, but after a reboot the Czech one is back.

---

### Post by bachor on 2011-08-10
Did you guys figured out?

 I'm in need to be able to switch default US keyboard to the Czech layout without having Czech when booting up. As I have my whole system encrypted and need to type password to be able boot in UBUNTU 10 with LXDE desktop. [going Ubu 11 soon,or Lubuntu or alike]

 Any luck or idea? I couldn't even find layouts on this LXDE desktop :confused:

 Thanx :)

---

### Post by isthisthat on 2011-09-21
Hi guys,
Loggin out, changing the keyboard at login screen and logging in again solved it for me once and for all (thanks to a suggestion in this thread [http://ubuntuforums.org/showthread.php?t=951881](http://ubuntuforums.org/showthread.php?t=951881)). It may take 2 tries so be patient!

Cheers
:guitar:

---

