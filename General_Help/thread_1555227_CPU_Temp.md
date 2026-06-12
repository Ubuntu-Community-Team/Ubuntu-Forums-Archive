---
title: "CPU Temp"
date: 2010-08-17
forum: General Help
---

### Post by jc4orr on 2010-08-17
I am going to be overclocking my cpu, but I want to make sure I dont push it too far. I was looking around here for a program that will read the temp. so I ran
```
sudo apt-get install libsensors4
```
then
```
sudo apt-get install lm-sensors
```
I answered yes to everything, and it found a couple of sensors, but at the end I get this message:
```
Monitoring programs won't work untill the needed module are loaded. 
You may want to run '/ect/init.d/module-init-tools start' to load them.
```
when I type in
```
/ect/init.d/module-init-tools start
```
I get this error
```
bash: /ect/init.d/module-init-tools: No such file or directory
```

can anyone help or point me in the direction of a program.

---

### Post by ibuclaw on 2010-08-17
A quick wizardry search reveals you may want to install the package module-init-tools

Also, my spidey senses tell me you aren't using the correct path name. It should be:
```
sudo /etc/init.d/module-init-tools start
```

Regards

---

### Post by uRock on 2010-08-17
> **ibuclaw said:**
> A quick wizardry search reveals you may want to install the package module-init-tools

Also, my spidey senses tell me you aren't using the correct path name. It should be:
```
sudo /etc/init.d/module-init-tools start
```Regards
Did you roll a D100 or 2D10 to get that?:lolflag:

---

### Post by NewDisciple on 2010-08-17
Copied this from someplace quite some time ago. I use it and it works.

Enabling Hardware Sensors in Linux
1. Installing the sensor libraries
First thing’s first – you need to install the libraries that allow Linux to read your sensors. To do this, install the lm-sensors library, by running the command:
sudo apt-get install lm-sensors

This will install the libraries for your motherboard’s sensors. For your hard-disk sensors, you’ll want to install hddtemp:
sudo apt-get install hddtemp

n Ubuntu, the install will ask you several questions. First it will ask if it should run SUID root, select “yes.” It will then ask you for an interval for logging the temperature to a file; since we are going to have an applet display our system temperatures for us, this isn’t necessary, so most users will be fine leaving the default of ‘0&#8242; and pressing enter; if you wish to log this data, however, I’d recommend a value between 2 and 10 seconds. Next, it will ask if it should run as a deamon; select yes, and leave the default values for hostname and port. Finally, it will ask if you wish for it to run on startup – select “yes.”

2. Running sensors-detect
Now that your sensor libraries are installed, you need to detect your sensors! Run the command:
sudo sensors-detect

Which will probe your system for sensors. Answer “YES” to all questions! Don’t just hit enter, type “YES”, because at the end there will be a question for which the default answer is “no”, and we’ll want to answer in the affirmative.
The sensors-detect program will scan yur system, and then give you a summary, stating which sensors it has found. It will then say: I will now generate the commands needed to load the required modules. After you hit ENTER to continue, it will ask, Do you want to add these lines to /etc/modules automatically? (yes/NO) This is the question we want to make sure we answer YES to.

3. Loading the modules
Since we answered YES to the previous question, our sensor modules will be loaded by default the next time we start up. But since we don’t want to have to reboot, we’re going to use the information we got from the sensors-detect script to load the modules ourselves, this time only. Right above the last question will appear a list of modules that you should load, in the form of:
#----cut here----
# Chip drivers
smsc47m1
#----cut here----
You may have more, or different, items listed – that’s fine! What we want to do now, to load these modules, is use the modprobe command, as follows:
sudo modprobe (module name)

So, in my case, I would type
sudo modprobe xxxxx

If all goes well, you should be returned to the command-line, without any output.

4. Monitoring the sensors!
Wow, that was a lot of work! Now, let’s see the rewards. On the command line, you can simply run the
sensors

to install the applet.
Sudo apt-get install sensors-applet

 Now, add the applet by right-clicking on your desktop panel, selecting “Add to Panel,” and you will now see a “Hardware Sensors Monitor” applet in the System & Hardware section. Click and drag this to your panel to add it.

---

