---
title: "udev rule for headset"
date: 2010-05-23
forum: General Help
---

### Post by Jenkins1 on 2010-05-23
Hi,

I am trying to write a udev rule for my headset but i don't understand where i get the information to make the rule. I know i need to add ```
RUN+="bash /home/luke-jennings/headset"
``` at the end of it so the script i wrote runs. I don't know how to get any of the identifying info for the headset and which bits to use where. How do I get the information?

Thanks in advanced

---

### Post by BoneKracker on 2010-05-23
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

(Tutorial by Gentoo developer and OLPC contributor Daniel Drake.)  Read the whole thing, but the answer to your question is in the section entitled, "Finding suitable information from sysfs".

---

### Post by Jenkins1 on 2010-05-23
> **BoneKracker said:**
> [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

(Tutorial by Gentoo developer and OLPC contributor Daniel Drake.)  Read the whole thing, but the answer to your question is in the section entitled, "Finding suitable information from sysfs".

Thanks for the link. I now have a rule ```
SUBSYSTEMS=="pci", ATTRS{vendor}=="0x8086", RUN+="/usr/bin/headset"
```
but the rule does not appear to run the script. Running ```
headset
```
and the script works so some how the rule doesn't not work. 

The information I used to make the rule came from.

```
udevadm info -a all -p /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.3/input/input20

```

the output is attached. If anyone can spot my error it would be appreciated.

---

### Post by Jenkins1 on 2010-05-23
by adding echo lines to the script that the rule runs, I have determined the rule works but the script is running multiple times the script now reads ```
#!/bin/bash

speakers=$(pacmd list-cards | grep "alsa_card.usb-Logitech_Logitech_USB_Headset$
mic=$(pacmd list-sources | grep "alsa_input.usb-Logitech_Logitech_USB_Headset-0$
echo hello > /home/luke-jennings/Desktop/headst 
echo $speakers
echo $mic
echo hello1 >> /home/luke-jennings/Desktop/headst 
amixer -c 1 sset Speaker,0 80%
echo hello2 >> /home/luke-jennings/Desktop/headst 
pacmd set-default-sink $speakers
echo hello3 >> /home/luke-jennings/Desktop/headst 
pacmd set-default-source $mic
echo hello4 >> /home/luke-jennings/Desktop/headst 

``` and the file that the echo goes to reads

```

hello
hello1
hello2
hello3
hello4
hello
hello1
hello
hello1
hello
hello1
hello
hello1
hello
hello1
hello
hello1
hello
hello1
hello
hello1
hello2
hello3
hello2
hello2
hello2
hello2
hello2
hello2
hello2
hello4
hello3
hello3
hello3
hello3
hello3
hello3
hello4
hello3
hello4
hello4
hello4
hello4
hello4
hello4
```

Any suggestions on how to make it run once? I have tried a sleep line at the start of the script but then the headphones don't work at all.

---

### Post by Jenkins1 on 2010-05-25
bump

---

### Post by Jenkins1 on 2010-05-27
bump,

It would be great if someone could suggest why the script is running in a funny order that would be great.

---

### Post by Jenkins1 on 2010-05-30
Well I found out that part of the problem is that the pacmd commands have to run as the user that is logged in. They don't work as root so now my udev rule is:

```
SYSFS{idVendor}=="046d", SYSFS{idProduct}=="0a0b", MODE="660", RUN+="/usr/bin/callheadset"
```

callheadset is:
```
#!/bin/bash
echo "running headset" >> /home/luke-jennings/Desktop/headset
sudo chmod +w /home/luke-jennings/Desktop/headset
su luke-jennings -c /usr/local/bin/headset
```

and /usr/local/bin/headset is:
```
#!/bin/bash
echo "turning up alsamixer" >> /home/luke-jennings/Desktop/headset
amixer -c 1 sset Speaker,0 80%
echo "setting mic" >> /home/luke-jennings/Desktop/headset
pacmd set-default-source $(pacmd list-sources | grep "alsa_input.usb-Logitech_Logitech_USB_Headset-00-Headset.analog-mono" -B1 | grep index | awk '{ print $2;}')
echo "setting earphones" >> /home/luke-jennings/Desktop/headset
pacmd set-default-sink $(pacmd list-sinks | grep "alsa_output.usb-Logitech_Logitech_USB_Headset-00-Headset.analog-stereo" -B1 | grep index | awk '{ print $2; }')
```

But the echo file still reads rather randomly and the scripts don't do what they were meant to. the echo file is:
```
running headset
turning up alsamixer
setting mic
setting earphones
running headset
running headset
running headset
running headset
running headset
running headset
running headset
running headset
turning up alsamixer
setting mic
setting earphones
turning up alsamixer
setting mic
turning up alsamixer
turning up alsamixer
turning up alsamixer
turning up alsamixer
turning up alsamixer
turning up alsamixer
setting mic
setting mic
setting mic
setting mic
setting mic
setting mic
setting earphones
setting earphones
setting earphones
setting earphones
setting earphones
setting earphones
setting earphones
```

but as a root user running ```
callheadset
``` gives the expected ```
running headset
turning up alsamixer
setting mic
setting earphones
```

in the echo file.

Any one have any idea why the udev rule is doing this I am very stuck on this part. Any suggestions welcome.

---

