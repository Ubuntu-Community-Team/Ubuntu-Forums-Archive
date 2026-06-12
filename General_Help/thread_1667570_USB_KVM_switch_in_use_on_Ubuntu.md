---
title: "USB KVM switch in use on Ubuntu"
date: 2011-01-15
forum: General Help
---

### Post by L a r r y on 2011-01-15
Hello,
Currently running a Windows XP computer and an Ubuntu computer through a new TRENDnet 2-computer USB KVM switch, a wireless laser mouse and a brand new GigaWare multimedia USB keyboard.  A 20-inch picture tube.

I can switch between computers using the buttons on the switch, and I can use the universal hot-key command on the Windows side to switch to Linux, but the universal command won't work on my Linux computer.  The universal command is two presses of the Scroll Lock key in succession.

In Windows, the Scroll Lock light comes on, on the first press and goes off on the second, as I switch computers.  In Ubuntu, the scroll lock light never lights.

The Windows computer is a 2002 model HP, 2.6 GHz Pentium 4, while this computer is similar to the K7S5A mainboard, different manufacturer, 1 GHz Athlon processor.

Any programs, commands or anything I might use on Ubuntu to determine the status of the keyboard's scroll lock, or would that more likely be a bios issue?

Thanks!

Edit:  TRENDnet TK-207K kvm model number.

---

### Post by dandnsmith on 2011-01-15
Possibly the Scroll Lock key is mapped to something 'different' in your installation.
I have a different KVM switch, which uses the same sequence, and that hasn't given me any trouble (and I'm currently running Windows on one, and UB 10.04 LTS on the other - as you seem to be from your sig.).

---

### Post by L a r r y on 2011-01-15
> **dandnsmith said:**
> Possibly the Scroll Lock key is mapped to something 'different' in your installation.
I have a different KVM switch, which uses the same sequence, and that hasn't given me any trouble (and I'm currently running Windows on one, and UB 10.04 LTS on the other - as you seem to be from your sig.).

Hi Derek, 
I ran across some other threads on this topic, and ran xev from the terminal to show that keypress and keyrelease events are being shown, but the scroll lock does not work the light. I ran xmodmap -pm to list a bunch of keys and there is no scroll lock in gnome listed, but after I added /etc/X11/xmodmap file containing ```
add mod3 = Scroll_Lock’
``` I was able to make the scroll lock light toggle on and off -- until I pulled the plug on the keyboard a couple of times to be able to read off the bottom of the kvm switch for the support ticket I submitted to TRENDnet.  Now the scroll lock doesn't exist anymore when I run xmodmap -pm and the light does not work.  Evidently one can program keyboard shortcuts and it works for that but it doesn't work this switch.

I bought this nice new GigaWare multimedia keyboard, and it has friction grips on the bottom that don't let the keyboard slide around like my old Walmart special did, and the multimedia buttons are neat too!  Only thing that doesn't work on those is the volume up and down, and mute, in any reliable way.  Works great on Windows, but my music is all over here!

I got the keyboard because I needed a USB keyboard to go with this USB switch.

I'll see what they say down at the tech support sometime next week.

---

### Post by erilidon on 2011-10-20
I had tried the xmodmap edit.. it didn't work. What worked for me on a similar Trendnet KVM was doubling tapping the Num Lock key instead of the scroll lock.

---

### Post by ben@kietzman.org on 2011-10-31
I ran into the same problem and could not find a workable solution for getting the scroll lock key to work.  I did end up figuring out an alternate solution.

[LIST=1]
[*]> sudo apt-get install xbindkeys-config xbindkeys
[*]> vim /path/to/kvm.sh
[INDENT]
#!/bin/bash
xset led on
sleep 1
xset led off
[/INDENT]
[*]Press CTRL-T to open a terminal.
[*]> chmod 755 /path/to/kvm.sh
[*]> xbindkeys-config
[LIST=1]
[*]Click the "New" button
[*]Input "KVM Switch" into the "Name" field.
[*]Click the "Get Key" button.
[*]Press CTRL-F12
[*]Input "/path/to/kvm.sh" into the "Action" field.
[*]Click the "Apply" button.
[*]Click the "Save & Apply & Exit" button.
[/LIST]
[*]Click the power icon in the upper-right.
[*]Select "Startup Applications..."
[*]Click the "Add" button.
[*]Input "X Bind Keys" into the "Name" field.
[*]Input "xbindkeys" into the Command field.
[*]Click the "Save" button.
[/LIST]

The CTRL-F12 key combination will now execute your kvm.sh script which will artificially press your Scroll Lock key twice which will trigger your KVM switch.

NOTE:  When in working in xbindkeys-config, you may want to remove the two rows that launch the xterm application.  One of them is bound to the CTRL-F combinations which Firefox uses when searching for text on a page.

---

