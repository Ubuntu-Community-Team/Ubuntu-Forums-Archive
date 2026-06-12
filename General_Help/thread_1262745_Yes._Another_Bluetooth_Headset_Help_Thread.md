---
title: "Yes. Another Bluetooth Headset Help Thread"
date: 2009-09-10
forum: General Help
---

### Post by Man-O-Leisure on 2009-09-10
Sorry if not posting this in the correct place.. i have read through so many threads on the net already about trying to get a bluetooth headset to work for use with skype, but none have worked for me.  I am a complete Ubuntu/Linux novice, and would appreciate someone that can help me through getting this to work.

I have a Plantronics 320 BT Headset, Dlink DBT-122 BT Dongle. Currently running Ubuntu 9.04 with Gnome.

Dongle seems to work, i get a bluetooth icon up the top of screen, can pair my headset with teh dongle, add the passkey and that goes through ok, but after that, i have no idea how i can get this to work in Skype, cause i go to the Audio setup in Skype like i do in windows, and the BT Headset just isnt there to choose.. 

Can someone please let me know what i can try next to get this working? I really dont understand too much about Linux, so some simple instructions are highly appreciated.  I also cant get my webcam to work but i will get to worrying about that after i can sort this out. Thanks in advance everyone

---

### Post by P4man on 2009-09-10
Did you download the latest skype from skype website? There is just a new beta that (finally) supports pulseaudio. If you got that version, then go in to system > preferences > sound and select your bluetooth set as default capture device.

If you dont have skype 2.1.0.47, I suggest you get that first:
[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

---

### Post by Man-O-Leisure on 2009-09-10
Thanks for the reply..

I have already got the latest Beta release of Skype installed yes.

When i go to the sound preferences as you suggested, i dont see any reference there at all for a bluetooth device at all to select

---

### Post by P4man on 2009-09-10
I dont have bluetooth audio here to test with, but I would make from that BT audio is not working.

Try this howto:
[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

Note the comments at the end state this will not work with Skype, but I'm pretty sure that doesn't take the latest skype into account, where they fixed pulseaudio and BT.

---

### Post by Man-O-Leisure on 2009-09-10
Thanks again, i will give that a shot tonight when i get home from work and report back

---

### Post by Man-O-Leisure on 2009-09-11
> **P4man said:**
> I dont have bluetooth audio here to test with, but I would make from that BT audio is not working.

Try this howto:
[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

Note the comments at the end state this will not work with Skype, but I'm pretty sure that doesn't take the latest skype into account, where they fixed pulseaudio and BT.


I got to step 11 of that guide, where i had to run: 
pactl load-module module-alsa-sink device=btheadset

And i got the following error: 

Failure: Module initalization failed

---

### Post by P4man on 2009-09-11
Hmm..  Im wondering if those commands shouldn't be run with root privileges. Try putting "sudo" in front.

If that doesnt help, try running this first:

```
sudo /etc/init.d/bluetooth stop
sudo /etc/init.d/bluetooth start
```

and try again.

---

### Post by MalibuJack on 2009-11-07
Thanks, p4man - I was having the same problem as Man-O-Leisure with step 11 of the howto at [https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset). Your suggestion of stopping and restarting Bluetooth fixed the problem on my Eee 1000 running the 9.04 (Jaunty) netbook remix - I have an inexpensive Insignia bluetooth headset. I haven't tried it with Skype, but it works with rhythmbox.

---

### Post by ebaccia on 2009-12-28
Hello all, 

I recently installed ubuntu 9.1 nbr on a eee 701 sd did the updates, loaded new skype 2.1.0.47 beta, and I tested it with 3 different BT usb dongles.  They were all found, I paired with a jabra headset, and it works with skype out of the box.  I did unccheck the skyoe audio control, because it was a little to loud for me.
the only thing that I have not got to work yet is the bluetooth answer button.  I have read hundreds of posts, but they all seem to refer to older bluez systems.  According to the bluez info for the latest  releases, they use dbus to manage trusts, pairing, data, ect.  so it appears that file referenced in old threads are of no use.  All the records stored under the BT mac address are in hex.

Is there an easy way to activate the headset answer button?


Complimets to all involved in 9.1 nbr much easier than eeebuntu!!

:P

---

