---
title: "Auto detect usb headset and switch to it"
date: 2011-11-29
forum: General Help
---

### Post by Azdour on 2011-11-29
Hi,

On an Ubuntu 10.04 machine I've written the following udev rule:

```
SUBSYSTEMS=="usb", ATTR{product}=="Logitech USB Headset", ACTION=="add", GROUP=="audio", RUN+="<location of script>"
```

This runs a script on detecting a USB logitech headset connecting to a USB port. The script contains:

```
#!/bin/bash
echo "Switch to using USB headset..." > /var/tmp/switch.log
sleep 4s
pacmd set-default-sink alsa_output.usb-Logitech_Logitech_USB_Headset-00-Headset.analog-stereo >> /var/tmp/switch.log 2>&1
pacmd set-default-source alsa_input.usb-Logitech_Logitech_USB_Headset-00-Headset.analog-stereo  >> /var/tmp/switch.log 2>&1
```

Now I know it is running this script as I have various outputs that go to a log file.

I believe my problem I face is that the script runs as root, hence the following errors output to my log:

```
No PulseAudio daemon running, or not running as session daemon.
```

I tried to run pacmd as:

```
sudo -u <username> -H
```

But this resulted in the error that it could not find the logitech sink. So I decided to added the following to the script:

```
sudo -u system -H /usr/bin/pacmd list-sinks >> /var/tmp/switch.log 2>&1
```

In the logs I can see that this command only lists the internal soundcard and not the logitech headset. I even put in a pause of 4 seconds before running the command just in case it was running before the headset was fully detected, but it still did not work.

Does anyone have a generic solution that works? I've seen various attempts and even solutions here in the Ubuntu Forums but they do not work for me.

On this machine there are many different users who will want to use the USB headsets so I need a generic way to auto switch to the headset when they plug it in, thanks.

---

