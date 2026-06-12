---
title: "hulu plays choppy in full screen"
date: 2009-08-16
forum: General Help
---

### Post by rhythmiccycle on 2009-08-16
i have ubuntu 9 installed on my dell laptop

when i watch something from hulu in full screen (using firefox), the picture gets really choppy, regular size works fine.

is there a way to change the plugin and/or its settings.

---

### Post by 8thMP on 2009-08-16
I have also had this problem but it only happens to me when I'm watching animated shows on hulu and not regular shows.. I have just stopped watching in full screen when watching my shows..

---

### Post by gustavson12 on 2009-09-13
I had the same problem...

I have ubuntu 9.04 installed on a desktop with a nvidia 9800 graphics card.  I am using the NVIDIA accelerated graphics driver (version 180).

Found this page >> [http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/]("http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/")

Here's what I did:

Entered the following command in Terminal

```
sudo gedit /etc/init.d/ondemand
```

Pasted the following lines to the end of the document and saved the script

```
for CPU_THRESHOLD in /sys/devices/system/cpu/cpu*/cpufreq/ondemand/up_threshold
do
[ -f $CPU_THRESHOLD ] || continue
echo -n 40 > $CPU_THRESHOLD
done
```

Then I entered the following commands in Terminal

```
sudo mkdir /etc/adobe
```

```
echo “OverrideGPUValidation=true” > ~/mms.cfg
```

```
sudo mv ~/mms.cfg /etc/adobe/
```

Rebooted system and the choppy playback in full screen at hulu.com is gone.  Firefox seems to run better as well.

Please click on the link I provided for more info on what all this does.  This worked for me.  Hope this info helps...

---

### Post by rhythmiccycle on 2009-09-14
i did what gustavson12 said, and it seems to be working.

thanks alot.

---

### Post by Dan Again on 2009-11-08
This solution also worked perfectly for me. Thank you for helping me fix a chronic and annoying problem!

---

### Post by jwflammer on 2009-11-19
i use the hulu desktop that you can download and in stall its the pore mans HTPC its really smooth and kinda cool two thumbs up

---

