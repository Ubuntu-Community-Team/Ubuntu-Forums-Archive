---
title: "Ubuntu 11.0.4 System crash &amp; shutdown every time I use Software Center"
date: 2011-08-01
forum: General Help
---

### Post by evaneus on 2011-08-01
Hi,
 I just installed Ubuntu 11.0.4 on an Asus 1005AH Eepc for a friend. The only changes I made after default install were to add French as primary language.
 Whenever I attempt to install a downloaded .deb or a package found through the Software Center, after asking for the password and a little delay the OS crashes and the system shuts down. There is no visual indication of what might be going wrong.
 Can someone let me know how I might track down what the problem is?

Thx,
e

---

### Post by bez654 on 2011-08-02
I have no idea, but I would try a couple of other things.
Can you install debs through a terminal? 
sudo apt-get install thing_you_want_to_install
or add .deb if you want to install a local file you've downloaded.

is your system upto date? 
I had problems with an old kernel on my eee 1000H. In a terminal...
sudo apt-get update
sudo apt-get upgrade
then say Y to update your system.

Does the system crash everytime you get a prompt for a super user password? try changing something that needs to prompt you for a password. i.e. changing the system time, installing a printer etc...

---

### Post by evaneus on 2011-08-02
Actually, after looking through syslog I found that it is shutting down due to critical temperature being reached - 88 degrees. It must have been heating up more when running installs.
 That said, I think there is a problem with the sensor or something, because the system is not hot at all when it shuts down due to 'overheating'
 I'm playing with pwmconfig and fan control, but so far am still having the problem. The system did not have this problem when it was running Win XP, which confuses me because if the sensors are reading incorrectly I would assume that to be a hardware problem. 
 The fan is working, and does speed up when CPU is being utilised. But as I said before, the system really is not getting that hot so I am not sure the fan is the problem.

---

### Post by dino99 on 2011-08-02
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

a bit old but:
[http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors](http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors)

[http://askubuntu.com/questions/33976/is-there-a-hardware-temperature-sensor-indicator](http://askubuntu.com/questions/33976/is-there-a-hardware-temperature-sensor-indicator)

---

### Post by evaneus on 2011-08-02
Thanks,
 I installed lm_sensors and it detected a new temperature sensor that pwmconfig was not showing before.

Now I have 2 sensors, the original (acpitz-virtual-0) showing a hotter 53 degrees, and the newer coretemp-isa-0000 showing a more reasonable 32 degrees.

I ran pwmconfig and configured it again. However the system still shuts down when the acpitz-virtual-0 sensor gets to 88 degrees. I really don't believe this is an genuine overheating situation, as the PC is not hot at all.

Perhaps this acpitz sensor is innacurate and I need to somehow tell the system to ignore it and use the core-temp one instead?

---

### Post by glene77is on 2011-08-02
> **evaneus said:**
> Actually, after looking through syslog I found that it is shutting down due to critical temperature being reached - 88 degrees. It must have been heating up more when running installs.
 That said, I think there is a problem with the sensor or something, because the system is not hot at all when it shuts down due to 'overheating'


Evaneus,
Have you tried making an "air space" under your laptop?
I use several screw-drivers under my laptop, just to make a space for Air to flow.  
Keeps it cooler.

---

### Post by evaneus on 2011-08-02
Thanks for the suggestion, I did try giving it some space. But when I tried downloading and installing chromium through the software center, the temperature climbed and climbed on acpitz-virtual-0 until it hit 88 degrees and the system crashed. 
 This whole time the fan was running at 4,025 rpm, I'm not positive that is the max RPM - but according to pwmconfig it is. If indeed it is, it would appear the sensor may be getting an incorrect reading in Linux. Because the system doesn't seem to overheat in Windows. 

Sadly, this is a friend's laptop and I have run out of time, and have to revert to plan A an put Windows XP back on there with the Asus restore disk :(
 I tried Ubuntu for him because (apart from XP sucking) his version of XP is in Spanish and he couldn't get a French language pack for it. Natty looked gorgeous, and I had managed to install the French translations so he would have been happy with that.

Oh well. I tried.

---

