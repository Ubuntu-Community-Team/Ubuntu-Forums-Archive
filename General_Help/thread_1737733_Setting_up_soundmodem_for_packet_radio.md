---
title: "Setting up soundmodem for packet radio"
date: 2011-04-23
forum: General Help
---

### Post by doctordruidphd on 2011-04-23
I am trying to set up a signalink-USB interface with the soundmodem program, to work as a software TNC. So far, no luck. Has anyone actually got this working? 

The essential problem seems to be that soundmodem is an OSS program, and won't work directly with pulseaudio. The soundmodem program must be run as sudo, and padsp does not work. Thus:

greenman@Wolfenstein:~$ sudo soundmodem
sm[26967]: unknown node "text"
sm[26967]: unknown node "text"
sm[26967]: unknown node "text"
sm[26967]: unknown node "text"
sm[26967]: unknown node "text"
sm[26967]: unknown node "text"
sm[26967]: unknown node "text"
sm[26967]: unknown node "text"
sm[26967]: unknown node "text"
sm[26967]: audio: Error, cannot open "/dev/dsp"
sm[26967]: cannot start audio

Anyone got this working?

I should mention that I have tried this on both 10.10 and 11.04, same results.

---

### Post by extemporaneous cromulence on 2011-05-24
By some sick twist of fate, /dev/dsp has finally been removed, right when I finally got my TNCs delivered, too.

I don't have it working, yet, but when you run soundmodemconfig, create your configuration and set the Mode to alsa on the IO tab.  Change the alsa audio driver to your soundcard.  If, like me, you have no clue what goes there, just start with the first non-/dev/dsp entry and then try to create a channel under that configuration and the menu will change. A Diagnostics menu will pop up between File and Help.  Try to launch the Scope or the Modem, or any of those.  You will get a popup message if you have an invalid soundcard entered.  Keep going back to the configuration and cycling through the ALSA Audio Driver entries and trying to launch the scope.  

Eventually you'll get a scope to pop up.  If you have are using a multiple soundcard setup, you'll want to make sure the one hooked up to the TNC is actually the one you have selected.  Just crank your squelch down with the radio on and you'll see all kinds of activity popup in the scope.

If I get things working, I'll come back and post more details.  Please, please, please post more details if you get it working.  If anyone who sees this thread has a working setup and can offer any pointers, I'd certainly appreciate some details from you, too.

---

### Post by 5149.5 on 2011-05-24
```
aplay -l
```

Might help.

---

### Post by doctordruidphd on 2011-05-25
I have this working. I must say it was a real fight.

Probably the most useful link is this:
[http://www.qbjnet.com/packet.html](http://www.qbjnet.com/packet.html)

But you don't need most of the info here - you don't need (or want) to compile the kernel, or do all of the networking stuff in the shell scripts, unless you plan on setting up a network or bbs system.

To set up soundmodem, you mostly need to follow the instructions in the link -- set it up for a network device (sm0), not serial, unless you are using software that works with KISS (Airmail does not).  If you are using paclink-unix (which I am) you will want sm0.
You can figure out the device number from the /proc/asound/modules file -- that lists your sound cards, and their numbers. Be aware that, unless you play around with the alsa configuration files, it can assign the cards in any order. The best plan is to boot your system without the Signalink plugged in; plug it in and turn it on after the system is up, and it will assign the same number to the card every time.

Running soundmodemconfig (which will need gksudo or kdesudo), Choose File > New > Configuration, call it sm0 (this is what most ax25 software is looking for). Highlight sm0, in the IO tab, choose alsa, in the audio driver choose plughw:2,0 substituting for the "2" whatever the /proc/asound/modules file shows for your soundcard. I also checked Half Duples, Capture channel "mono", and ptt driver "none" (the signalink has an internal vox). In the channel access tab, I set TxDelay to 300, slot time 100, PPersistence 64 no check full duplex, and txtail 30. You may need to play with those values, the defaults resulted in packet errors.

Addendum: yes, this means pulseaudio gets involved, and you will have to play with pavucontrol to get the levels right. But you have to do this, since the signalink can't handle 1200 baud sampling rate directly.

Once that is done, choose File > New >Channel. For modulator, mode-afsk, bits-1200, freq0-1200. freq2-2200, check diff encoding. Same values for demodulator (this is for 1200 baud packet, didn't test 9600). for packet io (this is tricky) choose MKISS, interface-sm0 callsign-yourcallsign, IP address-44.128.1.0 mask-255.255.255.254 broadcast-44.128.1.255 . These ip values are evidently defaults that ax25 software expects, don't get creative until you get it working.

Then choose File > Quit, and it will save what you have done.

IMPORTANT: see the next post, and particularly the part about avahi, or this still won't work.

Now you should be able to run gk/kdesudo soundmodemconfig again, choose the channel0 tab, and the diagnostics tab should appear at the top. That is where the scopes are. You can set the receive level, and hit the PTT button at the top (preferably into a dummy load) to adjust the transmit parameters.

Once all this is alive, you can run sudo soundmodem, and that will give you and sm0 network device that ax25 software can access. Note that you cannot run soundmodemconfig with the soundmodem program acitve, it's one or the other at a time. I find the "ax25spy -tv" command useful for watching what is going on, and axcall useful for direct contacts. paclink-unix works great for connecting to winlink rms gateways. There is a yahoo paclink-unix group, and they were VERY helpful.

---

### Post by doctordruidphd on 2011-05-25
One additional thing, you will need an /etc/ax25/axports file. Mine looks like:

sm0     WA6NQW  ---     255     7       145.630

where WA6NQW is my callsign, substitute yours. You only need that line for basic functionality. You don't need the other junk unless you are setting up a node or bbs.

Another useful link:
[http://www.xastir.org/wiki/HowTo:SoundModem](http://www.xastir.org/wiki/HowTo:SoundModem)

And this one for setting the transmit audio level:
[http://www.febo.com/packet/layer-one/transmit.html](http://www.febo.com/packet/layer-one/transmit.html)

The "by ear" method is better than nothing.

IMPORTANT: you will need to edit the /etc/avahi/avahi-daemon.conf file to prevent avahi from probing the sm0 port, which causes all sorts of problems. In the [server] section, add the line:
deny-interfaces=sm0
and either restart avahi-daemon, or reboot. Otherwise your transmitter will key frequently and unexpectedly.

I also notice that if I plug in a scanner and start xsane, it probes the usb port with the signalink, and keys the transmitter. This might happen with other usb device/software combinations as well. Forewarned is forearmed.

---

### Post by extemporaneous cromulence on 2011-05-25
Thanks for the info!  

Looks like my setup is good and perhaps one of my TNCs or cable is bad, or the pinout is wrong for my particular HT (ICOM ICV82).  Even with avahi disabled I get the TX going when receiving data.  If I move the radio/tnc to a different computer, I get the same behavior.  My other radio behaves on either system... at least I tthink it is, hard to test without other packet traffic

---

### Post by doctordruidphd on 2011-05-25
Yep, incorrect pinout is a possibility.

You need to find a freq with some packet traffic on it -- ax25spy should start dumping the raw traffic to your screen as soon as it hears it.

You also need to check the vox level on the signalink (if that's what you are using).And make sure that full duplex is NOT checked in soundmodemconfig. And make sure your radio is not set to vox. Any of those could result in incoming traffic keying the transmitter.  It's also possible that by some freak means, pulseaudio could be patching incoming audio to the output -- check this in pavucontrol.

---

### Post by doctordruidphd on 2011-05-26
Furthermore:

It is possible that other daemons might be probing the sm0 virtual device.

See this link:
[http://www.zs6mrk.org/pakket_met_linux.htm](http://www.zs6mrk.org/pakket_met_linux.htm)

They mention that samba can be a problem. There could also be other things probing the sm0 device - depends on what you have running, but anything that looks for a usb device (webcam, scanner, printer) could be causing trouble.

> The other process that might try to transmit on our ax25 port is the samba server. You do not want to kill it because it may be useful. In the web browser type this address: [http://127.0.0.1:901/](http://127.0.0.1:901/)  Username will be “root” and password is whatever you set it to.

Click on the “Globals” button.

Then select “Advanced” on the next page and click the “Advanced” button.

In the “Base options” section type “eth0” in the “interface” field. If you have a wireless LAN type “wlan0” in this field. Without the quotes.

The next option is “bind interfaces only” - set that to “yes”.

Click on the “Commit Changes” button at the top.

Then click on the “Status” icon at the top. Click on the “Restart All” button on the next page.

After all of this your radio should not transmit when you start soundmodem.

---

