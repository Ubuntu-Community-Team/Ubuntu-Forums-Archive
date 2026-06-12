---
title: "What can I use in place of CPU-Z and for monitoring temps with Ubuntu?"
date: 2010-06-28
forum: General Help
---

### Post by sastusbulbas on 2010-06-28
Hi all,

Wondering what I can use in Ubuntu for monitoring CPU core temps, CPU and memory speed and such, used CPU-Z, prime, HD tune up and and the like when OC'ing and UC'ing my Windows PC's but what Ubuntu equivalents are there?

---

### Post by justleen on 2010-06-28
You can use IPMI if your system supports it, or lm_sensors, for temperature monitoring.
speeds and such can be found trough hwmgr or lshw, or get the info from /proc
```

cat /proc/cpuinfo

```

---

### Post by Kevbert on 2010-06-28
Please take a look at [[COLOR="Red"]conky[/COLOR]]("http://conky.sourceforge.net/"). It's fully customizable and available in the repos. Once installed just enter conky from Applications-Accessories-Terminal for a default demo.

---

### Post by gamblor01 on 2010-06-28
Yeah lm-sensors is probably a good start.  Try:

```

sudo apt-get install lm-sensons

```

Unfortunately there has to be info in that package specific to each motherboard so yours may or may not be supported.  It doesn't offer much on my motherboard so I'm stuck with just monitoring other temps such as hard drives and GPU.

If you want to monitor your disks then check out the hddtemp package.  Make sure to install it as a service (it will ask you this and default to port 7634).

If you have an nvidia card there is also temperature information inside of the nvidia-config package.  This package is generally installed along with the driver but if not, you can always install it separately though apt.



Once the packages are installed that's all well and good but you'll need a way to display the information.  The way I pull the information is all via scripts that get invoked from conky.  I attached a screenshot so you can see it.

If you have any problems getting the info then let us know and we can help.  Here is some info to get you started:

To get hdd temps after installing hddtemp:

```

nc localhost 7634

```


To get the temp of your nvidia GPU you can either view it directly from the nvidia-config GUI or extract it on the command line:

```

nvidia-settings -q gpucoretemp |grep '):' | cut -d ' ' -f 6,6 | sed -e 's/.\{1\}$//'

```

---

### Post by nss0000 on 2010-06-28
> **justleen said:**
> You can use IPMI if your system supports it, or lm_sensors, for temperature monitoring.
speeds and such can be found trough hwmgr or lshw, or get the info from /proc
```

cat /proc/cpuinfo

```

Running x64-LL_10.04 on quad AMD_965:

Actually different mobos allow different info-sets. My MSI_790_gd70 does NOT permit any cpu temp info to be released outside the BIOS. GPU_temp yes, CPU_temp no! Basically it's none-of-your-business. Snotty lil' bastard! Conky, LM_sensors & <*/cpuinfo>  having nothing to say about cpu temps. You are *ucked batman. Period. 

I hardwired temp probes to various kit-points including a cpu-cooler heatpipe. I know lots about relative temps.

---

### Post by sastusbulbas on 2010-06-28
Well I am a complete newbie with Ubuntu, none of the above makes any sense and I need to monitor CPU temps as I am running a passive cooler.

It would be nice to be able to monitor CPU and memory settings after OC'ing too so is there no package I can just click on and install? The above Conky doesn't seem to do anything IE download and install and cannot find it in repo? wherever that is?

---

### Post by sastusbulbas on 2010-06-28
Well according to installed software I have managed to install Conky-all, but when I look in Applications I cannot find it anywhere?

---

### Post by Kevbert on 2010-06-28
You won't find a shortcut for conky as it's run from the terminal by default. If you want a shortcut, right click on Applications (top rhd corner of desktop) and a menu will appear, select 'Edit Menus'. Select 'Applications/Accessories' so that its highlighted and then click on 'New Item'. Enter the following: Type - Application, Name - Conky (or whatever you want to see in the menu list), Command - conky (note lower case), Comment - Resource monitor (example). Now click on Close and Close again and you should be able to launch conky.
To get rid of conky from the desktop the terminal command is
```
killall conky
```

---

### Post by sastusbulbas on 2010-06-29
Thankyou,

Got Conky running.

BUT, didn't see anything to do with CPU temps, and considering how important monitoring CPU temps are when building a PC and overclocking or running passive CPU cooling I cannot understand why no application has been put together to monitor such within Ubuntu?

So again is there a CPU-Z equivalent for Ubuntu?

Is there a Prime equivalent for Ubuntu?

Is there a HDD monitor for Ubuntu?

Is there a CPU Temp monitor for Ubuntu?

Is there any applications with which to monitor and assist with overclocking, underclocking and passive cooling?

---

### Post by KonfuseKitty on 2010-06-29
I'm a newbie myself so this might be a silly question, but have you tried running the <sensors> command in terminal?  It displays CPU and motherboard temperatures among other things.

---

### Post by Mark Phelps on 2010-06-29
You have to do more than install lm-sensors, after install, you have to run "sudo sensors-detect" and reply Yes to all the questions.  This will install sensor modules to be used by the kernel.

Then, reboot, and once back into Ubuntu, run "sensors".  You should see a long list of temp and fan readings.

If you don't, there are either no modules for your sensors, or the installed modules aren't working with your kernel version.

Either way, in that case, conky will not be seeing any information to report.

---

### Post by nerdy_kid on 2010-06-29
i would probably experiment more with ubuntu in general before trying to overclock anything

---

### Post by clhsharky on 2010-06-29
> What can I use in place of CPU-Z

CPU-G

[http://www.gtk-apps.org/content/show.php/CPU-G?content=113796&PHPSESSID=d5059fc0f6c754ba6ae0865da95e0cf5](http://www.gtk-apps.org/content/show.php/CPU-G?content=113796&PHPSESSID=d5059fc0f6c754ba6ae0865da95e0cf5)

Sharky

---

### Post by sastusbulbas on 2010-06-29
If I try that I get this.

steve@steve-desktop:~$ <sensors>
bash: syntax error near unexpected token `newline'
steve@steve-desktop:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
steve@steve-desktop:~$ sensors-detect
You need to be root to run this script.
steve@steve-desktop:~$

---

### Post by sastusbulbas on 2010-06-29
> **nerdy_kid said:**
> i would probably experiment more with ubuntu in general before trying to overclock anything

Well thats all and well but I have installed it within a machine which was overclocked and is now underclocked, which has a passive CPU heatsink hence me wanting to monitor temps and adjust bios as necessary.

---

### Post by KonfuseKitty on 2010-06-29
Yup, I fogot you have to install it, use the Ubuntu Sofware Center to search for lm-sensors.  After installing you can run the "sensors" command.

---

### Post by sastusbulbas on 2010-06-29
> **clhsharky said:**
> CPU-G

[http://www.gtk-apps.org/content/show.php/CPU-G?content=113796&PHPSESSID=d5059fc0f6c754ba6ae0865da95e0cf5](http://www.gtk-apps.org/content/show.php/CPU-G?content=113796&PHPSESSID=d5059fc0f6c754ba6ae0865da95e0cf5)

Sharky

OK I can download this, but what do I do to install it?

---

### Post by Spr0k3t on 2010-06-29
I checked out GPU-G, but there seems to be missing a major function you are looking for: motherboard and cpu temp output.  You will be able to get more out of lm-sensors and conky... so let me help you with that.

1. Install lm-sensors if you have not already.  (Run 'sudo apt-get install lm-sensors' from a terminal to install)
2. From a terminal run 'sudo sensors-detect'
3. Enter your password and answer yes to every question except this one:
```
Do you want to add these lines automatically to /etc/modules? (yes/NO)
```
4. Once complete, run 'sensors'.  This will give you the heat output and any possible fans connected as well as current voltages (given the information is supported in the kernal for your motherboard).

Now, copy and paste the output of sensors surrounded by "code" tags so we can take a look at the configuration.  Next we'll create a custom conky configuration file specifically for your hardward and the information you are looking for.

---

### Post by Mark Phelps on 2010-06-29
> **sastusbulbas said:**
> If I try that I get this.

steve@steve-desktop:~$ <sensors>
bash: syntax error near unexpected token `newline'

You enter the command "sensors" without the quote marks or other special characters.
> 
steve@steve-desktop:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
steve@steve-desktop:~$ sensors-detect
You need to be root to run this script.
steve@steve-desktop:~$
I told you to do "sudo sensors-detect".  The "sudo" is needed in order to run the command.

You need to pay closer attention and enter what people tell you.

---

### Post by moonport on 2010-06-29
Thanks for the tip.

---

### Post by sastusbulbas on 2010-06-29
Well I would input that, but terminal will not let me enter my password giving me nothing but an unresponsive blinking cursor!

The bloody useless terminal has the cheek to tell me, "Sorry, try again. then
sudo: 3 incorrect password attempts" after not allowing me to enter the password?

Oh wait, now it lets me in, but wait I have already done all that previously? As I remember typing yes at each point.

---

### Post by sastusbulbas on 2010-06-29
OK so another idiot question, how do I run or access LM sensors to see anything?

---

### Post by Joe-ubunt on 2010-06-29
> **sastusbulbas said:**
> OK so another idiot question, how do I run or access LM sensors to see anything?

just type _sensors_ into the terminal. If that pulls up your cpu temps and voltages than all you need to do is right click on a panel and Add to Panel the Hardware Sensors monitor or use another gui to monitor your temps. 

If that doesn't work make sure lm-sensors is properly installed and try the sudo sensors-detect again, answer Y to all and restart.

If it still doesn't work then you may need to add **acpi_enforce_resources=lax** in between the  quotes in GRUB_CMDLINE_LINUX=""  in your etc/default/grub file. That's what I had to do in order to get my sensors to work properly. It might not work for you though. If you want to try that then type gksudo gedit /etc/default/grub in a terminal, enter password at the prompt, add   acpi_enforce_resources=lax in between the  quotes in  GRUB_CMDLINE_LINUX= , save, type sudo update-grub into a terminal, restart computer.

Still though, the sensors command should at least pull up something for   you. Lm-sensors is an excellent Ubuntu tool for monitoring temps and   voltages.

---

### Post by Spr0k3t on 2010-06-29
To see what temps are able to be scanned by lm-sensors, just type "sensors" at the terminal.  You should see something like this:

```
spr0k3t@farnsworth:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.23 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:      +3.23 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +5.02 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +11.97 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     1278 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed: 730 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:8035 RPM  (min =  600 RPM)
CHASSIS3 FAN Speed: 743 RPM  (min =  600 RPM)
POWER FAN Speed:    753 RPM  (min =    0 RPM)
CPU Temperature:    +44.5°C  (high = +60.0°C, crit = +75.0°C)
MB Temperature:     +46.0°C  (high = +45.0°C, crit = +75.0°C)
```

Keep in mind, sensors is dependant on having the modules for your motherboard built into the kernel.  So if someone has not reverse-engineered the motherboard, or the manufacturer has not released the machine code for the bios level queries, it's possible you will not see any of this information.  The good part, many of the newer motherboards are coming out with very minor changes to already known working modules.  The motherboard I use was not accessible when 9.04 was initially released, but a month later and everything was listed.

---

### Post by sastusbulbas on 2010-06-29
Many thanks everyone :D

Adapter: ISA adapter
Core 0:      +42.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +40.0°C  (high = +80.0°C, crit = +100.0°C)  

w83697hf-isa-0290
Adapter: ISA adapter
in0:         +1.01 V  (min =  +0.67 V, max =  +0.06 V)   ALARM
in2:         +3.30 V  (min =  +2.30 V, max =  +3.41 V)   
in3:         +2.94 V  (min =  +2.19 V, max =  +2.50 V)   ALARM
in4:         +2.98 V  (min =  +2.30 V, max =  +0.26 V)   ALARM
in5:         +3.12 V  (min =  +2.38 V, max =  +3.34 V)   
in6:         +3.23 V  (min =  +3.23 V, max =  +0.38 V)   ALARM
in7:         +3.20 V  (min =  +2.59 V, max =  +0.22 V)   ALARM
in8:         +3.36 V  (min =  +0.77 V, max =  +2.08 V)   ALARM
fan1:          0 RPM  (min = 9926 RPM, div = 8)  ALARM
fan2:          0 RPM  (min = 2280 RPM, div = 8)  ALARM
temp1:       +34.0°C  (high = +103.0°C, hyst = +95.0°C)  sensor = thermistor
temp2:       +36.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
beep_enable:enabled

---

### Post by Spr0k3t on 2010-06-29
Awesome... now let's make use of that output.  Take the attachment to this post (.conkyrc-cpu.txt) and save it to /home/USERNAME/.conkyrc-cpu

From here, let's create a new menu item.
1. Go to System -> Preferences -> Main Menu
2. Left pane, go to System Tools under Applications
3. Click New Item
4. Give it the name CPU-Conky
5. The command will be: conky --config=/home/USERNAME/.conkyrc-cpu

Close it up and you should be able to launch the app from the applications menu.  The window will update once a second with the current data.

Just remember that Conky is extremely configurable with tons of options.

---

### Post by sastusbulbas on 2010-06-30
OK when I click that I get no option to choose where is is saved and I have no /home/USERNAME/.conkyrc-cpu location (IE home user name contains no folder named conkyrc-cpu?

I already have Conky-all within my application tray but it does not have the above added?

---

### Post by Spr0k3t on 2010-06-30
The file /home/USERNAME/.conkyrc-cpu is the name of the file, not the folder.  Instead of just clicking on the link, right-click and choose "Save location as" which will give you a filesave dialog box.  More often than not, the dialog will default to your home directory (this is where you want to save the file).  At the top of the dialog box, the first textfield will be Name:, edit the filename and remove the ".txt" from it.  Click save.

Now then... once you are this far, we can then open the configuration with conky from the terminal.

```
conky --config=/{path to file}/.conky-cpu
```

Just be sure to change the {path to file} to be the path to your home directory.  On my system my home directory is /home/spr0k3t/.  Change yours accordingly.  This conky configuration file is one that I have personally modified to give you the current temps of your CPU and Motherboard.  Once everything is set up correctly, you will be able to use it like an application instead of having to check "sensors" from the terminal all the time.  Conky-all is just the application... the .conkyrc-cpu is a configuration to use with conky.

---

### Post by sastusbulbas on 2010-06-30
I am too much of a noobie and the above is making no sense?

Save the file in downloads then edit?

Left click or right click? Before after? what exact command line in terminal?

---

### Post by Spr0k3t on 2010-06-30
Actually, I think I'm too much into Linux that I'm not drawing it out enough.  You know how that gets when you are too close to something that you can't acurately describe what steps you need to take to achieve something simple.  Try describing the pictures on a dollar bill to someone who is blind... you'll understand the feeling.  Let's break this down to some raw elements and if I go over your head, don't hesitate to ask for clarification.  It's how many people learn, both the teacher and the student.

Reading a few of your other posts, I got that your home directory is "/home/steve/" so let's see how well I can convey this for you.

In my posting #26, there's an attached file.  Right click on the link for the attached file and click "Save Link As" (at least for firefox).  In the name field, remove the ".txt" from the filename.

[img]http://ubuntuforums.org/attachment.php?attachmentid=161997&stc=1&d=1277935401[/img]

Now, from the terminal type this:

```
conky --config=/home/steve/.conkyrc-cpu
```

If you did this correctly, you will see a window with details similar to this:

[img]http://ubuntuforums.org/attachment.php?attachmentid=162000&stc=1&d=1277936908[/img]

The window works just like an application.  If you get this far, we can then set it up so that you can open the "app" from an icon in the applications menu or even from the desktop.

---

### Post by nmaster on 2010-06-30
i use acpi in the terminal.  you can apt-get it.

---

