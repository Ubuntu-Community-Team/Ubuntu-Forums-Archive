---
title: "Bluetooth headset pairing succesful, but can't use it"
date: 2011-01-18
forum: General Help
---

### Post by Dave M G on 2011-01-18
Ubuntu Forums,

I have a bluetooth headset that I hope I can get to work with Ubuntu 10.10 so that I can use it with Skype.

I am using [these instructions]("https://help.ubuntu.com/community/BluetoothHeadset") to get it to work. However, there are some differences between my experience and what I expect from the instructions, ultimately leading to some errors.

First, I should mention that according to Blueman device manager, it would seem I have successfully paired my device. It has a MAC address. I have attached a screen shot of the interface:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181406&stc=1&d=1295358503[/IMG]

It sure looks like the device is recognized by my system. 

However, when I get to step 5, the MAC address of the one device I see is not the same as the one in the interface above:
```
$ hcitool scan
Scanning ...
	00:1B:DC:0F:C1:CB	RAISUKEUCHI-PC
```

I assume that means that the device found by hcitool is not my headset.

I tried to press on anyway, using the MAC address from the Blueman interface (knowing this probably wouldn't work). When I got to step 11, I got this error:
```
$ pactl load-module module-alsa-sink device=btheadset
Failure: Module initalization failed
```

I looked up that error on Google, but came up with almost nothing that offered any explanations or solutions.

How can I resolve any of the above errors, or, alternatively, is there another set of instructions I can use that will get my Bluetooth headset working with Skype?

Thank you for any advice.

---

### Post by gradinaruvasile on 2011-01-18
You dont need all that terminal stuff.

Just connect the device as [COLOR="Red"]headset[/COLOR], go into the volume controls settings, and select the bluetooth headset as the default sound out device.

---

### Post by Dave M G on 2011-01-18
gradinaruvasile,

Thank you for responding.

Wow, that was easy. I guess the instructions I was looking at is out of date.

It works just as you describe.

Thanks for setting me straight.

-- 
Dave M G

---

### Post by LouisBlank on 2011-03-02
Hi all, 

I have a similar problem.  My device is recognized by hcitool, but will not connect as 'headset' and doesn't show up in the sound devices, so I cannot select it.  

```

louis@louis-desktop:~$ hcitool scan
Scanning ...
	00:25:DB:50:12:81	SH34

```

Here is an idea of the response from the bluetooth manager...

[IMG]http://dl.dropbox.com/u/9159375/bluetooth.png[/IMG]


BTW - blue tooth file transfers and all works with other devices, just nothing on the headset.

Any ideas?

---

### Post by epitaph123 on 2011-07-15
my bluetooth headset connects fine, so i go to pulse audio to the hardware tab but my headset is not listed.

how do i get pulse audio to detect my connected headset?

---

