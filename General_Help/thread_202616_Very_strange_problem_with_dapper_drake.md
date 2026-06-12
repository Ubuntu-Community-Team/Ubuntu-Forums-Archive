---
title: "Very strange problem with dapper drake"
date: 2006-06-23
forum: General Help
---

### Post by the_zoor on 2006-06-23
Hi! Installed dapper drake (6.06 DVD version) 2 days ago and a couple problem is making me totally confused. I've tried anything but I have no explanation on to why this is happening or what to do.

I actually have 2 problems... 

#1. I cannot boot with my network cable connected to my laptop. If I disconnect the cable from the laptop there is no problem. I can just connect it again once ubuntu is booted. However if I keep it connected in the laptop during reboot / boot it brings me to the login screen where I write my nickname and my password and then just freezes. Any ideas??

#2. This is even stranger. When I boot my "c" button does not work... thats right... one lousy button. I have to start the keyboard config tool in the system bar and then re-elect the same keyboard again and then it works as a charm... why? I've also tried to change the keyboard model since I use a laptop my specific keyboard is not in the list. How ever all the buttons are working. Its only the 'C' button that I cannot get working at boot.

Could some one please help me with these issues its driving me nuts ](*,) 

I'd be very happy for some support.

Best Regards!

---

### Post by nix4me on 2006-06-23
I have to say, i've helped alot of people with alot of problems but I have never heard of anyone having either one of those.

Have you searched the forums?

nix4me

---

### Post by the_zoor on 2006-06-24
[QUOTE=nix4me]I have to say, i've helped alot of people with alot of problems but I have never heard of anyone having either one of those.

Have you searched the forums?

nix4me[/QUOTE]

Yes I have but no success. I've never heard anyone having either one of these problems with any distro. Its a shame really 'cause I really like ubuntu in all ways. And dapper drake is working better than ever on my laptop if you exclude these two problems. At first I had an Idea that the C button issue was due to it being used as some sort of hotkey, but I have not configurated it as such. Nor can I see it being used as a hotkey... this problem is driving me nuts...

Thanks for your reply though, much appreciated :)

---

### Post by FuturePast on 2006-06-24
It would be useful to tell us which laptop you have.

---

### Post by PriceChild on 2006-06-24
If you've only got a fresh install on there, then a last resort may be to burn a new cd and fresh install it. - you never know.

---

### Post by the_zoor on 2006-06-25
[QUOTE=FuturePast]It would be useful to tell us which laptop you have.[/QUOTE]

Off course... my bad. My laptop is  "Fujitsu Siemens AMILO M 3438G"

Specs:

CPU: Intel® Pentium® M 760 (2.0GHz, 533MHz FSB, 2MB L2, XD, EIST, Dothan 90nm)

RAM: 1024MB (2x512MB, DDR2 - 533MHz)

HDD:  80GB SATA (1x80 GB HDD, 5400rpm)

GRAPHIC CARD: nVidia GeForce Go 6800 (256MB/0M, DVI-I)

SOUND: Azalia codec (7.1 SPDIF) 


Like this one: [http://www.laptopsdirect.co.uk/Fujitsu-Siemens_Amilo_M_3438G_LKN:GBR-177200-008/version.asp](http://www.laptopsdirect.co.uk/Fujitsu-Siemens_Amilo_M_3438G_LKN:GBR-177200-008/version.asp)

---

### Post by the_zoor on 2006-06-25
[QUOTE=PriceChild]If you've only got a fresh install on there, then a last resort may be to burn a new cd and fresh install it. - you never know.[/QUOTE]

I did... twice actually. Same strange problem. :)

---

### Post by JoWilly on 2006-06-25
Please report these 2 bugs on launchpad. It will help the whole community if the developers know about them.

---

### Post by incubus on 2006-06-25
zoor,

So you never had these problems with other versions of Ubuntu? Are you installing the English version?

About the network cable, one thing that comes to my mind is that maybe it's trying to boot from the network. I doubt it could cause that, but it may be worth checking the boot sequence in the BIOS.

Have you tried a different installation CD?

incubus

---

### Post by tonyr on 2006-06-25
[QUOTE=the_zoor]
#2. This is even stranger. When I boot my "c" button does not work... thats right... one lousy button. I have to start the keyboard config tool in the system bar and then re-elect the same keyboard again and then it works as a charm... why? I've also tried to change the keyboard model since I use a laptop my specific keyboard is not in the list. How ever all the buttons are working. Its only the 'C' button that I cannot get working at boot.
[/QUOTE]

Run **xev**, an event reporting tool, in a terminal.  You should get a window with a box in it.  
Put the focus in that window and hit the 'c' key.  The report shows up in the terminal where **xev** was called.  
See what it says about keycode value when the 'c' key is **working** and when it is **not working**.

---

### Post by the_zoor on 2006-06-25
[QUOTE=tonyr]Run **xev**, an event reporting tool, in a terminal.  You should get a window with a box in it.  
Put the focus in that window and hit the 'c' key.  The report shows up in the terminal where **xev** was called.  
See what it says about keycode value when the 'c' key is **working** and when it is **not working**.[/QUOTE]

Heres the results...

**when pressing the key "b"**:

[I]KeyPress event, serial 26, synthetic NO, window 0x3000001,
    root 0x63, subw 0x0, time 238461509, (596,694), root:(601,767),
    state 0x0, keycode 56 (keysym 0x62, b), same_screen YES,
    XLookupString gives 1 bytes: (62) "b"
    XmbLookupString gives 1 bytes: (62) "b"
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3000001,
    root 0x63, subw 0x0, time 238461618, (596,694), root:(601,767),
    state 0x0, keycode 56 (keysym 0x62, b), same_screen YES,
    XLookupString gives 1 bytes: (62) "b"[/I]

**When pressing the key "c" - directly after bootup when it doesn't work:**

[I]KeyPress event, serial 29, synthetic NO, window 0x3000001,
    root 0x63, subw 0x0, time 238463098, (596,694), root:(601,767),
    state 0x0, keycode 54 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3000001,
    root 0x63, subw 0x0, time 238463194, (596,694), root:(601,767),
    state 0x0, keycode 54 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes:[/I]

**When pressing the key "c" - directly after going in to keyboard settings:**

[I]KeyPress event, serial 29, synthetic NO, window 0x3200001,
    root 0x63, subw 0x0, time 238756676, (374,343), root:(379,392),
    state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (63) "c"
    XmbLookupString gives 1 bytes: (63) "c"
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3200001,
    root 0x63, subw 0x0, time 238756748, (374,343), root:(379,392),
    state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (63) "c"[/I]

---

### Post by the_zoor on 2006-06-25
[QUOTE=incubus]zoor,

So you never had these problems with other versions of Ubuntu? Are you installing the English version?

About the network cable, one thing that comes to my mind is that maybe it's trying to boot from the network. I doubt it could cause that, but it may be worth checking the boot sequence in the BIOS.

Have you tried a different installation CD?

incubus[/QUOTE]

No never ever had a problem as strange as this before. Not with ubuntu or any other linux distro. I checked the bios boot section. Nothing strange there. I even disabled everything else than cd/dvd rom and my harddrive. No change. I haven't tried with another installation cd though. But I doubt it being the problem. Seems unlikly, if I got this far in the installation it should be allright? I also did the media check prior to installing the OS.

---

### Post by tonyr on 2006-06-26
[QUOTE=the_zoor]Heres the results...
**When pressing the key "c" - directly after bootup when it doesn't work:**

[I]KeyPress event, serial 29, synthetic NO, window 0x3000001,
    root 0x63, subw 0x0, time 238463098, (596,694), root:(601,767),
    state 0x0, keycode 54 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3000001,
    root 0x63, subw 0x0, time 238463194, (596,694), root:(601,767),
    state 0x0, keycode 54 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes:[/I]

**When pressing the key "c" - directly after going in to keyboard settings:**

[I]KeyPress event, serial 29, synthetic NO, window 0x3200001,
    root 0x63, subw 0x0, time 238756676, (374,343), root:(379,392),
    state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (63) "c"
    XmbLookupString gives 1 bytes: (63) "c"
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3200001,
    root 0x63, subw 0x0, time 238756748, (374,343), root:(379,392),
    state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (63) "c"[/I][/QUOTE]

Something is corrupting your xmodmap, a table that maps keycodes (the code generated
by pressing a key) to their interpretations (letters, meta-characters, media keys, etc). The
particular corruption you are seeing has mapped your C key to the 'media key' shortcut
XF86AudioPlay, so in a way  your first guess about it being used as a hotkey was 
correct.  I assume that when you say you looked to see it if was being used as a hotkey
you looked in System->Preferences-Keyboard Shortcuts.

I don't know what the source of the corruption is.  Someone else might.  I can suggest
a workaround, which may or may not work for you depending on when/how the
corruption is occurring.

When you have the C key working after the config trick, install package **xkeycaps**. 
There is a description [here]("http://www.jwz.org/xkeycaps/").  In short, when you
run it, you can hover over a key to see what the current keycode mapping is, right
click to change the mapping, save an **xmodmap** file to your home directory, and
add an **xmodmap** command to your .login file (or whatever you are using
for local shell startup).  If this works, your keyboard should be well defined
the next time you log in.  If not, then the corruption is down th line somewhere.

---

### Post by the_zoor on 2006-06-27
[QUOTE=tonyr]Something is corrupting your xmodmap, a table that maps keycodes (the code generated
by pressing a key) to their interpretations (letters, meta-characters, media keys, etc). The
particular corruption you are seeing has mapped your C key to the 'media key' shortcut
XF86AudioPlay, so in a way  your first guess about it being used as a hotkey was 
correct.  I assume that when you say you looked to see it if was being used as a hotkey
you looked in System->Preferences-Keyboard Shortcuts.

I don't know what the source of the corruption is.  Someone else might.  I can suggest
a workaround, which may or may not work for you depending on when/how the
corruption is occurring.

When you have the C key working after the config trick, install package **xkeycaps**. 
There is a description [here]("http://www.jwz.org/xkeycaps/").  In short, when you
run it, you can hover over a key to see what the current keycode mapping is, right
click to change the mapping, save an **xmodmap** file to your home directory, and
add an **xmodmap** command to your .login file (or whatever you are using
for local shell startup).  If this works, your keyboard should be well defined
the next time you log in.  If not, then the corruption is down th line somewhere.[/QUOTE]

YES! It worked. No I have only have one problem to think about. Thanks a bunch! \\:D/

---

