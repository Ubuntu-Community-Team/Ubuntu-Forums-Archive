---
title: "Lirc, mce remote with mouse, control media player"
date: 2009-08-14
forum: General Help
---

### Post by smeck on 2009-08-14
Short version, I want to control play/pause with my remote like I can do with the media keys on my keyboard.

Long version, please bear with me, I'm stuck :(
I've recently bought one of these
[http://www.fractal-design.com/?view=product&category=5&prod=22](http://www.fractal-design.com/?view=product&category=5&prod=22)

I read a test saying it acts as a HID so I figured it would work nicely with Linux. And it kind of does. It's got a joypad thing to control the mouse, which works fine. But after using the joypad thing my Dinovo Edge stoped working (connected with bluetooth usb reciever, I guess both the Dinovo Edge and the remote use the module usbkbd). I had to reinsert the usb reciever for the Dinovo. This however I solved by following these steps.

> First, define this remote has which "event number"
cat /proc/bus/input/devices
Then, reconfigure lirc:
sudo dpkg-reconfigure lirc
Choose "Linux Input Layer (/dev/input/eventX)" as "IR Receiver" at the first screen, "None" as "IR Transmitter" at the second screen, et "/dev/input/eventX" at the last screen in which X is the "event number" above.
 from [http://ubuntuforums.org/showpost.php?p=6379336&postcount=7](http://ubuntuforums.org/showpost.php?p=6379336&postcount=7) There is also a link to get the mouse and keyboard on the remote to act as separate devices, but this requires there is two events, with cat /proc/bus/input/devices I get 
```
I: Bus=0003 Vendor=04b4 Product=0100 Version=0110
N: Name="Cypress Cypress USB Keyboard"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input4
U: Uniq=
H: Handlers=kbd mouse1 event4 
B: EV=100017
B: KEY=70000 2000000 3878d801c001 e08effdf01cfffff fffffffffffffffe
B: REL=103
B: MSC=10

``` so only one event. The mouse works until I run something like irw irexec or irxevent
[B]
So my how can I get the mouse functionality working?[/B]


Number keys work fine. But the Play and the other keys don't work. I assumed they would follow some sort of standard, but in irw the Play key generates this.
```
000000000001001d 00 LEFTCTRL linux-input-layer
000000000001002a 00 LEFTSHIFT linux-input-layer
0000000000010019 00 P linux-input-layer

```So the Play key on the remote generates three keycodes. After some googling I found that I need a lircrc file so I made this for testing
```
begin
    prog = irexec
    button = LEFTCTRL
    config = tvtime-command TOGGLE_MUTE
end
begin
    prog = irexec
    button = LEFTSHIFT
    config = tvtime-command TOGGLE_MUTE
end
begin
    prog = irexec
    button = P
    config = tvtime-command TOGGLE_MUTE
end
```And it works.

**But how do I get it to control media players the same way the Play/pause key on the keyboard does?**

I don't want to control Play on merely the music player, when watching a film I want to control that. With play/pause on my keyboard I can control whatever media program is runnig, if two or more is runnig it controls the one in focus.

I've tride this
```
#
begin
    prog = irexec
    button = LEFTCTRL
#    config = tvtime-command TOGGLE_MUTE
    config = sh '/etc/acpi/playbtn.sh'

end
begin
    prog = irexec
    button = LEFTSHIFT
#    config = tvtime-command TOGGLE_MUTE
    config = sh '/etc/acpi/playbtn.sh'
end
begin
    prog = irexec
    button = P
#    config = tvtime-command TOGGLE_MUTE
    config = sh '/etc/acpi/playbtn.sh'
end 
#

```Then ran irexec in terminal, pressing Play only gave me "Permission denied". Then tried sudo irexec but it didn't work. Thou ```
sudo sh '/etc/acpi/playbtn.sh'
```works in terminal.

Also tried
```
#
begin
    prog = irxevent
    button = LEFTCTRL
#    config = tvtime-command TOGGLE_MUTE
    config = Key PLAY CurrentWindow

end
begin
    prog = irxevent
    button = LEFTSHIFT
#    config = tvtime-command TOGGLE_MUTE
    config = Key PLAY CurrentWindow
end
begin
    prog = irxevent
    button = P
#    config = tvtime-command TOGGLE_MUTE
    config = Key PLAY CurrentWindow
end 
#
```

Sorry for the lengthy text, only wanted to get it all. Appreciate any help.

---

### Post by Dejavou42 on 2011-03-20
I know this post is kind of old, but I was searching for the solution to the exact same problem. In my search, I found this page.  [http://flavor8.com/index.php/2010/02/24/how-to-use-a-remote-control-to-control-banshee/](http://flavor8.com/index.php/2010/02/24/how-to-use-a-remote-control-to-control-banshee/) Although that page talks about controlling banshee. It explains exactly how to control the laptop with media key controls.

In short  you need to install a program called xautomation.

```
sudo apt-get install xautomation
```    

Then in your .lircrc config file you would have something like this:

```

begin
  prog=irexec
  remote=mceusb
  button=Play
  config=xte 'key XF86AudioPlay'
end

```

My particular problem was with the Volume up and down buttions, because calling /etc/acpi/volumeupbtn.sh resulted in permission  denied, so I used:    

```

begin
  prog=irexec
  remote=mceusb
  button=Play
  config=xte 'key XF86AudioLowerVolume'
end

```

Check here for a complete list of XF86 key symbols: [http://wiki.linuxquestions.org/wiki/XF86_keyboard_symbols](http://wiki.linuxquestions.org/wiki/XF86_keyboard_symbols).

Last after editing the .lircrc config file, you'll want to restart lirc and start irexec again:

```

sudo /etc/init.d/lirc restart

```

I hope this helps someone else who's trying to configure lirc                         . :)

---

