---
title: "Mercury TV Tuner Card"
date: 2006-05-05
forum: General Help
---

### Post by hellmet on 2006-05-05
Hi Guys,
I have a Mercury LP 7130 Tv Tuner Card.
I have no idea how to install it or even detect it
in Ubuntu.
Any help on the same will be very grateful.
Thanks a ton in advance...

-hellmet

---

### Post by dlai on 2006-05-05
first of all try and find out what kind of chip your card has... you check that by looking in ivtvdriver.org or sites for the bttv8448(I'm not sure about the name of that one) if you have a ivtv card go [here]("http://hyams.webhop.net/mythtv/myth_ubuntu.html") and go through the ivtv-section... piece by piece, if you have dapper you'll have to copy(it is important that you copy) the files into the directory of /lib/firmware/<kernel ver>/

---

### Post by hellmet on 2006-05-05
Philips 7130 Chip is the one this mercury Tuner card has.
I am presenlty on Breezy.
So please give instructions for this version.

---

### Post by Jose Catre-Vandis on 2006-05-05
can you give us a dmesg output please, I think you want the saa7134 module

---

### Post by hellmet on 2006-05-05
Hello Jose..
Cud u be more specific??
Wats the dmesg..
I am a complete noob.
Thanks.

---

### Post by hellmet on 2006-05-06
OKAY GOTCHA...


i have attached the file containing the output of
LSPCI and DMESG.

---

### Post by Jose Catre-Vandis on 2006-05-06
OK

This is the useful bit:

```
[4294718.687000] Linux video capture interface: v1.00
[4294718.714000] saa7130/34: v4l2 driver version 0.2.12 loaded
[4294718.717000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294718.717000] saa7130[0]: found at 0000:06:00.0, rev: 1, irq: 21, latency: 32, mmio: 0xff7ffc00
[4294718.717000] saa7130[0]: subsystem: 18d0:2100, board: UNKNOWN/GENERIC [card=0,autodetected]
[4294718.717000] saa7130[0]: board init: gpio is 38500
[4294718.828000] saa7130[0]: i2c eeprom 00: d0 18 00 21 10 28 ff ff ff ff ff ff ff ff ff ff
[4294718.828000] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294718.828000] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294718.828000] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294718.853000] saa7130[0]: registered device video0 [v4l2]
[4294718.854000] saa7130[0]: registered device vbi0
```

The saa7130 module is loading but is not autodetecting your card. According to the Gentoo Tv hardware wiki, your card =2 and tuner =3. You will have to load these manually, and then set up to always load if it works.

In terminal:

```
sudo rmmod saa7130
```

```
sudo modprobe saa7130 card=2 tuner =3
```

(you may need to try this again with just the card=2, leaving out the tuner=3 part)

Then check dmesg again and see if your card is recognised. if it is then try out tvtime to see if you get channels and tv. Check the tvtime site for additional setup issues which might relate to your graphics setup.

If this all works then you can set ubuntu to always load your card on boot:

```
sudo gedit /etc/modprobe.conf
```

add the line:

options     saa7130 card=2 tuner=3

And save. Reboot. Test. Enjoy :-)

---

### Post by hellmet on 2006-05-06
wow that was quick dude..thanks a lot..
I need to reboot into Ubuntu to check that out.
(Dual Booting from Winxp..my eth0 (8139D) is unrecognised in Ubuntu)
is this TVtime integrated in Ubuntu?
Or do i need to download and integrate it seperately??

---

### Post by hellmet on 2006-05-06
modprobe saa7134 ....
returns..module not found.
Shud I modprobe 7134??

---

### Post by Jose Catre-Vandis on 2006-05-06
Sorry, I have assumed that saa7130 is a separate module to saa7134 (help please someone!) so it may be you need to run saa7134. I don't know this bit.

You need to be "root" to run these commands

sudo rmmod saa7134
sudo modprobe saa7134 card=2

You can find tvtime in the repositories (you may need to broaden your sources list for this, see the ubuntu wiki, or check forum)

---

### Post by hellmet on 2006-05-06
when I modprobe..what do I get??
does it return to prompt??
It happened to me..

---

### Post by GeneralZod on 2006-05-06
[QUOTE=hellemt]when I modprobe..what do I get??
does it return to prompt??
It happened to me..[/QUOTE]

A successful "modprobe" should indeed return you straight to the prompt with no errors or warnings (or output of any kind).  To double-check that it worked, do

```

lsmod | grep saa

```

---

### Post by hellmet on 2006-05-06
am able to return to prompt with any x y z values for 
card and tuner.

---

### Post by Jose Catre-Vandis on 2006-05-06
does it take longer with card=2 ? Any change to dmesg output?

Take a trip to [http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134) for a full run down on what to do. You will find reference to a Mercury TV Tuner at the bottom of the page

---

### Post by hellmet on 2006-05-09
The card is getting identified...
Installed TVTIME.
But when I start TVTIME all I get is a Black Blank Screen.
The menu is in no way helpful to do a channel scan..
Am I missing somthing??
How do I scan for channels..
BTW..
[B]
tvtime-scanner --device=/dev/video0[/B]
gives
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/sanjay/.tvtime/tvtime.xml
Scanning using TV standard PAL-M.
/home/sanjay/.tvtime/stationlist.xml: No existing PAL-M station list "Custom".

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.

But my 
lspci 
gives
[B]0000:06:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
[/B]

Am I doing sumthing wrong..

Any help will be grateful.

---

### Post by azure_look on 2006-12-31
helmet,
have the same tuner card as yours...and am now able to watch tv..but bit of a problem, do not get all the channels as in windows...
If I edit the stationlist.xml from tvtime, with frequencies from winxp, I get only static at that frequencies..please help

---

### Post by hellmet on 2007-01-21
did u try out
'tvtime-scanner' at the command prompt?
That way, all channels are scanned.
I guess you did not select the right Region.
In Tvtime, also select the proper region. and see

---

### Post by hellmet on 2007-06-15
When I look back at this thread, it tells me as to how far I came about learning Linux.
Something that I struggled with is, as easy as typing one line of command now :D.
It took me ages to know what that was though.

---

