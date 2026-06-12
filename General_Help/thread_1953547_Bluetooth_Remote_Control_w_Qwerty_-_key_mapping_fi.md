---
title: "Bluetooth Remote Control w/ Qwerty - key mapping file?"
date: 2012-04-06
forum: General Help
---

### Post by jschimmoeller on 2012-04-06
I have a tivo slide bluetooth remote that has a qwerty keyboard.  I have paired this device via bluetooth manager and it does work. However, i need to remap some the keys for the remote and here is where I am having difficulty. Additionally, I am running ubuntu 11.10 64bit 

1.  I want to remap the power button to not shut off the power to the box.
      a.  using evtest /dev/input/event6 I see the power button keycode is below: 
Event: time 1333734515.868039, type 4 (Misc), code 4 (ScanCode), value c0030
Event: time 1333734515.868048, type 1 (Key), code 116 (Power), value 1
Event: time 1333734515.868050, -------------- Report Sync ------------
Event: time 1333734515.999247, type 4 (Misc), code 4 (ScanCode), value c0030
Event: time 1333734515.999256, type 1 (Key), code 116 (Power), value 0
Event: time 1333734515.999261, -------------- Report Sync ------------

      b.  based on what I know I have downloaded and recompiled evdev and have modified file (i have validated in the log files the new library is loaded): 
               /usr/share/X11/xorg.conf.d/10-evdev.conf 

            code in file is:
Section "InputClass"
    Identifier "TiVo Keyboard Remote"        
    MatchProduct "TiVo Keyboard Remote"   
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
    Option "event_key_remap"   "116=9 " # remap 116 to escape
EndSection

  Additionally, I have tried to add the code below /etc/X11/xorg.conf but that makes all input devices not work:

Section "InputClass"
    Identifier "TiVo Keyboard Remote"        
    Driver "evdev"
    Option "Device" "/dev/input/event6"
    Option "event_key_remap" "116=9" 
  EndSection

The problem is this is not work!  any ideas? 

Thanks in advance
James

---

### Post by teaguecl on 2012-05-10
James, I have been working with this remote under XBMCBuntu.  Collectively, the XBMC users have been documenting our finds here:
[http://wiki.xbmc.org/index.php?title=TiVo_Slide](http://wiki.xbmc.org/index.php?title=TiVo_Slide)

It doesn't directly answer your question - but maybe our method of using udev to remap the keys will be helpful to you.

---

