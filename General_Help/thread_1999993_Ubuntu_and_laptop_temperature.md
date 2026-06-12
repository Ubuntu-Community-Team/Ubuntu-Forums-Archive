---
title: "Ubuntu and laptop temperature"
date: 2012-06-08
forum: General Help
---

### Post by Scozzar on 2012-06-08
I have noticed that running Ubuntu causes my laptop to heat up a lot more than Windows 7.  It's an i7 processor clocked @ 2ghz.  I'm not sure if this is normal, but I just wanted to know.  

My laptop runs at usually 39% when I am using Windows 7, but after about 2 hours of Ubuntu use, I found it to be at 47% when I had restarted to Windows.  I don't know specific temperature as I don't have any program to read that, but I do have percentages, provided by the Toshiba Laptop Checkup bloatware...It's not the most helpful, but it gets the point across, you know?

---

### Post by patrickceg on 2012-06-08
Linux installs sometimes take up more power (so more heat and less battery life), although things are MUCH improved from a few years ago. If you have an AMD or nVidia graphics card, you can probably lower temperatures a little by installing the proprietary drivers for the card. (See the "Additional Drivers" app

)

It's a little hit or miss, but Ubuntu and other Linux have lm-sensors if you want to read temperatures:
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by Scozzar on 2012-06-08
Do the different versions of Linux offer different power consumption and heat? As in, if I were to use Kubuntu instead of Ubuntu, would it run less hot or more hot? (Kubuntu was the only one I can think of off the top of my head :P).  I like Ubuntu, but my laptop needs to last at least another five years or so, so I don't want to fry anything

---

### Post by 3rdalbum on 2012-06-09
> **Scozzar said:**
> I like Ubuntu, but my laptop needs to last at least another five years or so, so I don't want to fry anything

You won't fry anything. There are hardware temperature sensors that turn off the computer straight away if it gets too hot. Linux itself has code that will safely shut down the computer if things get toward the dangerous point. An extra 8% of temperature (I hate this entirely unhelpful measurement) doesn't sound like too much of a difference.

You'd have to remember that, the way you are measuring it, you're running the computer for a while and then rebooting it and measuring the temperature. Essentially, you're giving it time to heat up, then putting the computer through one of the most stressful things you can do to a computer (booting), then measuring the temperature. This may be elevating the temperature and throwing off your perception of Ubuntu's running temperature.

If you install the 'lm-sensors' package on Ubuntu, then run the 'sudo sensors-detect' command, then run the 'sensors' command you will be able to read the temperatures that have been observed by the computer's built-in temperature sensors.

During the 'sensors-detect' phase, just answer 'y' to everything.

---

