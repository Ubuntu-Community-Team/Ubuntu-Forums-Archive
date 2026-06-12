---
title: "LIRC + SIIG Vista MCE remote?"
date: 2010-12-01
forum: General Help
---

### Post by mnelson100 on 2010-12-01
Greetings, I need a little help... thanks for your time.  I'm a brand new to LIRC, but I've used Ubuntu and a couple of other distros a little.

I have a SIIG Vista MCE remote I'm trying to get working with LIRC under Ubuntu 10.04... Ultimately with Boxee, but I haven't made it that far.

I ran apt-get install lirc, then picked "Windows Media Center Transceivers/Remotes (all)" for the remote and "none" for the IR transmitter.

When I run irw, I get code like "^[[A" when I push remote buttons... (keystrokes?) From what I've found searching, the output should look like the identifier codes listed in the config file, right?

Here's my /etc/lirc/lircd.conf:

```

#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:

include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

```... and /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:

```
#
# brand:                        HP
# model no. of remote control:  TSGH-IR01
# devices being controlled by this remote: HP Slimline S3100y
#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects_remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#
#
# Updated with codes for MCE 2007 Remote additional buttons
# Visualization, Aspect, SlideShow, Eject
# Note:
# Renamed some buttons: DVD->DVDMenu, More->MoreInfo, Star->Asterisk, Hash->Pound
# Note:
# Blue, Yellow, Green, Red, and Teletext buttons do not exist on the HP remote

begin remote

  name        mceusb
  bits                 16
  flags  RC6|CONST_LENGTH
  eps                  30
  aeps                100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits        21
  pre_data        0x37FF0
  gap              105000
  toggle_bit           22
  rc6_mask    0x100000000


      begin codes

#unused by HP remote
        Blue          0x00007ba1
        Yellow        0x00007ba2
        Green         0x00007ba3
        Red           0x00007ba4
        Teletext      0x00007ba5

#ba6 - bae unused
        BA6           0x00007ba6
        BA7           0x00007ba7
        BA8           0x00007ba8
        BA9           0x00007ba9
        BAA           0x00007baa
        BAB           0x00007bab
        BAC           0x00007bac
        BAD           0x00007bad
        BAE           0x00007bae

        Radio         0x00007baf
        Print         0x00007bb1

#bb2 - bb4 unused
        BB2           0x00007bb2
        BB3           0x00007bb3
        BB4           0x00007bb4

        Videos        0x00007bb5
        Pictures      0x00007bb6
        RecTV         0x00007bb7
        Music         0x00007bb8
        TV            0x00007bb9

#bba - bbf unused
        BBA           0x00007bba
        BBB           0x00007bbb
        BBC           0x00007bbc
        BBD           0x00007bbd
        BBE           0x00007bbe
        BBF           0x00007bbf
#bc1 - bca unused
        BC1           0x00007bc1
        BC2           0x00007bc2
        BC3           0x00007bc3
        BC4           0x00007bc4
        BC5           0x00007bc5
        BC6           0x00007bc6
        BC7           0x00007bc7
        BC8           0x00007bc8
        BC9           0x00007bc9
        BCA           0x00007bca

        Eject         0x00007bcb
        SlideShow     0x00007bcc
        Visualization 0x00007bcd

#bce - bcf unused
        BCE           0x00007bce
        BCF           0x00007bcf
#bd1 - bd7 unused
        BD1           0x00007bd1
        BD2           0x00007bd2
        BD3           0x00007bd3
        BD4           0x00007bd4
        BD5           0x00007bd5
        BD6           0x00007bd6
        BD7           0x00007bd7

        Aspect        0x00007bd8
        Guide         0x00007bd9
        LiveTV        0x00007bda
        DVD           0x00007bdb
#NoGap
        Back          0x00007bdc
        OK            0x00007bdd
        Right         0x00007bde
        Left          0x00007bdf
        Down          0x00007be0
        Up            0x00007be1
#NoGap
        Star          0x00007be2
        Hash          0x00007be3
#NoGap
        Replay        0x00007be4
        Skip          0x00007be5
        Stop          0x00007be6
        Pause         0x00007be7
        Record        0x00007be8
        Play          0x00007be9
        Rewind        0x00007bea
        Forward       0x00007beb
#NoGap
        ChanDown      0x00007bec
        ChanUp        0x00007bed
        VolDown       0x00007bee
        VolUp         0x00007bef
#NoGap
        More          0x00007bf0
        Mute          0x00007bf1
        Home          0x00007bf2
        Power         0x00007bf3
#NoGap
        Enter         0x00007bf4
        Clear         0x00007bf5
#NoGap
        Nine          0x00007bf6
        Eight         0x00007bf7
        Seven         0x00007bf8
        Six           0x00007bf9
        Five          0x00007bfa
        Four          0x00007bfb
        Three         0x00007bfc
        Two           0x00007bfd
        One           0x00007bfe
        Zero          0x00007bff
      end codes

end remote
#
# this config file was automatically generated
# using lirc-0.8.4a(default) on Mon Feb 23 23:55:04 2009
#
# contributed by
#
# brand:                       Hauppauge
# model no. of remote control:
# devices being controlled by this remote: PVR-150 Remote (MCE kit)
# SMK dongle 0609:031d
#

begin remote

  name  mceusb_hauppauge
  bits           13
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2674   870
  one           455   427
  zero          455   427
  pre_data_bits   24
  pre_data       0x1BFF82
  gap          106288
  min_repeat      1
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          TV                       0x1BB9
          Music                    0x1BB8
          Pictures                 0x1BB6
          Videos                   0x1BB5
          Power                    0x1BF3
          Stop                     0x1BE6
          Record                   0x1BE8
          Pause                    0x1BE7
          Play                     0x1BE9
          Rewind                   0x1BEA
          Foward                   0x1BEB
          Replay                   0x1BE4
          Skip                     0x1BE5
          Back                     0x1BDC
          More                     0x1BF0
          Up                       0x1BE1
          Left                     0x1BDF
          Right                    0x1BDE
          OK                       0x1BDD
          Down                     0x1BE0
          VolUp                    0x1BEF
          VolDown                  0x1BEE
          Home                     0x1BF2
          ChanDown                 0x1BED
          ChanUp                   0x1BEC
          Mute                     0x1BF1
          RecTV                    0x1BB7
          Guide                    0x1BD9
          LiveTV                   0x1BDA
          DVD                      0x1BDB
          One                      0x1BFE
          Two                      0x1BFD
          Three                    0x1BFC
          Four                     0x1BFB
          Five                     0x1BFA
          Six                      0x1BF9
          Seven                    0x1BF8
          Eight                    0x1BF7
          Nine                     0x1BF6
          Star                     0x1BE2
          Zero                     0x1BFF
          Hash                     0x1BE3
          Clear                    0x1BF5
          Enter                    0x1BF4
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.8.4a(default) on Tue Mar 10 19:27:09 2009
#
# contributed by
#
# brand:  SIIG Vista MCE remote
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name  vista_mce
  bits           16
  flags RC6
  eps            30
  aeps          100

  header       2654   889
  one           427   427
  zero          427   427
  pre_data_bits   21
  pre_data       0x37FF0
  gap          69850
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          Power                    0xEBF3
          Pictures                 0x6BB6
          Radio                    0xEBAF
          Videos                   0x6BB5
          Music                    0xEBB8
          Rec                      0x6BE8
          Pause                    0xEBE7
          Stop                     0x6BE6
          Skipback                 0xEBE4
          Play                     0x6BE9
          Skipfwd                  0xEBE5
          Rwd                      0x6BEA
          Fwd                      0xEBEB
          Start                    0x6BF2
          Back                     0xEBDC
          More                     0x6BF0
          Volup                    0xEBEF
          Voldown                  0x6BEE
          Chup                     0xEBED
          Chdown                   0x6BEC
          Up                       0xEBE1
          Down                     0x6BE0
          Left                     0xEBDF
          Right                    0x6BDE
          Mute                     0xEBF1
          Rectv                    0x6BB7
          Guide                    0xEBD9
          Livetv                   0x6BDA
          Dvdmenu                  0xEBDB
          1                        0x6BFE
          2                        0xEBFD
          3                        0x6BFC
          4                        0xEBFB
          5                        0x6BFA
          6                        0xEBF9
          7                        0x6BF8
          8                        0xEBF7
          9                        0x6BF6
          *                        0xEBE2
          0                        0x6BFF
          #                        0xEBE3
          Clear                    0x6BF5
          Enter                    0xEBF4
      end codes

end remote



```... which is interesting, because my exact remote is defined towards the bottom (vista_mce).  How do I tell LIRC to use that particular remote from the several defined in the file...?  :???:

Thanks!

Michael

---

### Post by mnelson100 on 2010-12-01
I forgot to add that many of the buttons on the remote don't seem to get any kind of response from irw... the "Pictures" and "Videos" buttons, for example.

Thanks

Michael

---

### Post by mnelson100 on 2010-12-01
***Bump

Any ideas?  Is there a better forum to post this?

Thanks!

---

### Post by mnelson100 on 2010-12-08
One more bump...

Thanks

---

### Post by undesigned on 2010-12-21
Having the same problem with my SIIG remote.  It used to work with 9.x (mceusb).

---

### Post by rogerbinns on 2010-12-25
Good news.  You can get it working.  Bad news - not all the buttons work.

First unplug and then replug the USB dongle. Run dmesg|tail in a terminal and you should see something like this:


```
$ dmesg | tail
[10493.508918] usb 1-1.1.3: new low speed USB device using ehci_hcd and address 8
[10493.629435] input: Formosa21 IR603 HID MCE as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.3/1-1.1.3:1.0/input/input7
[10493.629654] generic-usb 0003:147A:E031.0005: input,hiddev96,hidraw3: USB HID v1.11 Keyboard [Formosa21 IR603 HID MCE] on usb-0000:00:1a.0-1.1.3/input0
```

What this is saying is that the dongle is showing up as a USB human interface device, specifically a keyboard.  If you run irw in a terminal and press the number keys on the remote you'll see just the numbers being printed.

```
$ irw
12345

```

If you are seeing anything different then this post doesn't apply to you.

So now we know that this remote control isn't showing up as a remote control, but as a keyboard we can continue.  lirc knows how to deal with this.  View the file /proc/bus/input/devices and look for the Formosa21 IR603 HID MCE section.  Mine looks like this, but your numbers will differ depending on how many USB devices you have plugged in and the order you plugged them in:

```
I: Bus=0003 Vendor=147a Product=e031 Version=0111
N: Name="Formosa21 IR603 HID MCE"
P: Phys=usb-0000:00:1a.0-1.1.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.3/1-1.1.3:1.0/input/input7
U: Uniq=
H: Handlers=sysrq kbd event6 
B: EV=10001f
B: KEY=837fff002c3027 bf00444400000000 1 f848b27c000 667bfad9415fed e08effdf01cfffff fffffffffffffffe
B: REL=40
B: ABS=100000000
B: MSC=10

```

In particular note the H: Handlers row and look for the event part - in my case **event6**.  Yours will be a different number.  From a terminal run:

```
sudo dpkg-reconfigure lirc
```

Instead of selecting your actual remote, choose "Linux input layer (/dev/input/eventX)".  Select your event number from earlier, /dev/input/event6 in my case.  Lirc should be restarted.  Now run irw again and press keys.  You should get output like below:

```
$ irw
0000000080010002 00 KEY_1 devinput
00000000800100d0 00 KEY_FASTFORWARD devinput
00000000800100a6 00 KEY_STOPCD devinput
00000000800100a7 00 KEY_RECORD devinput
0000000080010073 00 KEY_VOLUMEUP devinput

```

Unfortunately several keys will not work such as DVD menu and the top row ones (Pictures, Radio etc).

Now that we know everything works, we don't want to be at the whim of random USB numbers.  In your terminal do this:

```

$ cd /dev/input/by-id
$ ls -l
lrwxrwxrwx 1 root root 9 2010-12-25 11:47 usb-Formosa21_IR603_HID_MCE-event-kbd -> ../event6
lrwxrwxrwx 1 root root 9 2010-12-25 00:52 usb-Microsoft_Microsoft®_Digital_Media_Keyboard_3000-event-kbd -> ../event3
lrwxrwxrwx 1 root root 6 2010-12-25 00:52 usb-Microsoft_Microsoft®_Digital_Media_Keyboard_3000-kbd -> ../js0
lrwxrwxrwx 1 root root 9 2010-12-25 00:52 usb-Microsoft_Microsoft®_LifeCam_Cinema_TM_-event-if00 -> ../event5
lrwxrwxrwx 1 root root 9 2010-12-25 00:52 usb-Microsoft_Microsoft_Wireless_Optical_Mouse®_1.00-event-mouse -> ../event4
lrwxrwxrwx 1 root root 9 2010-12-25 00:52 usb-Microsoft_Microsoft_Wireless_Optical_Mouse®_1.00-mouse -> ../mouse0

```

This shows a list of names we can use instead of numbers.  You can see that the first entry points to event6 and has the "Formosa21 IR603 HID MCE" text in it.  As root/sudo/gksu edit the file /etc/lirc/hardware.conf and change the REMOTE_DEVICE line.  Mine now looks like this:

```
REMOTE_DEVICE="/dev/input/by-id/usb-Formosa21_IR603_HID_MCE-event-kbd"
```

From the terminal restart the lirc service:

```
sudo service lirc restart
```

Use irw as earlier to confirm everything is working.

---

### Post by Fisslefink on 2011-01-05
I just wanted to share my success story with a different Vista MCE receiver from the Formosa discussed in this thread.

I recently added a Vista MCE remote transceiver (HP P/N 5070-2584, Model # OVU422000/06) to my Ubuntu 10.10 box and was quite surprised that it was recognized as a /dev/input device.  Everyone seems to be scrambling with the way Ubuntu 10.10 recognizes LIRC MCE devices.

I achieved my desired setup by doing the following:

[LIST=1]
[*] Ran "sudo dpkg-reconfigure lirc" and chose "Linux input layer (/dev/input/eventX)" as suggested by Rogerbinns, above.

[*] Unfortunately my device doesn't show up in /dev/input/by-id like the Formosa device does.  So instead, I used "udevadm info" to chase down a unique device attribute to use in a udev rule (see other articles on writing udev rules for more info on this ... note that the "udevinfo" tool is now "udevadm info").

[*] I then created a udev rule in /etc/udev/rules.d which detects my IR transceiver and creates a symlink at /dev/input/hpremote.  See the attached file 10-HPremote.rules.

[*] I also created a HAL daemon rule which ignores my remote as an input device, as suggested [here]("http://www.lirc.org/html/devinput.html") ...not sure if this is necessary.  See the attached file lirc.fdi.

[*] After running "sudo udevadm control --reload-rules" and "sudo udevadm trigger", I can now see a device at /dev/input/hpremote

[*] I modified /etc/lirc/hardware/conf to point to "REMOTE_DEVICE=/dev/input/hpremote".  Verified that everything works with "sudo service lirc restart" followed by "irw".  See the attached hardware.conf.

[*] I customized /etc/lirc/lircrc to send keypresses from different buttons with irxevent  This is because the "repeat" argument allows me to customize the delay between button presses, avoiding unwanted repeats.  See the attached lircrc.

[*] I also wanted the fancy on-screen display of the volume using "notify-send", so I used a small script called "vol.sh" which is executed by irexec.  It works nicely.  See the attached vol.sh and the relevant entries in lircrc.  Note that my username is "mythtv" on this machine.

[*] To get irxevent to be started by init.d, I had to modify /etc/init.d/lirc.  This is attached as "lirc".

[*] In some applications, I was getting duplicate button presses because Xorg recognized the remote as a keyboard (first keypress), and irxevent was sending a customized keypress (second keypress).  This was resolved by adding a new file to /usr/share/X11/xorg.conf.d called "00-ignorehpremote.conf"

The file contains the following:
```
Section "InputClass"
  Identifier "Ignore HP Vista Remote as Keyboard"
  MatchProduct "Media Center Ed. eHome Infrared Remote Transceiver"
  Option "Ignore" "true"
EndSection
```

Simply log out and log back in to restart X.  At this point, the remote will no longer be recognized as a keyboard, but it will still by recognized by LIRC.
[/LIST]

With this configuration and kernel 2.6.37-020637rc2-generic, three buttons still do not work:
[LIST]
[*]Visualization
[*]Slide Show
[*]Eject
[/LIST]

I hope that helps, or at least provides some ideas.

PS:  For what it's worth, this post may be worth a read...  [http://ubuntuforums.org/showthread.php?p=9984844#post9984844](http://ubuntuforums.org/showthread.php?p=9984844#post9984844)

---

