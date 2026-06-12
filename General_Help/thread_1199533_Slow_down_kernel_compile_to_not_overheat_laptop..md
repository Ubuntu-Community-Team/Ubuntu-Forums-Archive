---
title: "Slow down kernel compile to not overheat laptop."
date: 2009-06-29
forum: General Help
---

### Post by jargoman on 2009-06-29
I'm trying to compile a custom patched kernel using this guide. 

[http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")

All is good except compiling over heats my laptop and it shuts down. I've done countless things to get power usage to minimum. ie frequency scaling ect ect. Still the laptop will over heat and shut down. 

The heat is fine so long as I don't do anything resource intensive and I can live with that.

All I really want to accomplish is to be able to compile my kernel slowly. Go figure eh?

I've tried hacking my makefile using this guide  
[http://pc.autons.net/stuff/kernel-compile-slowdown.phtml]("http://pc.autons.net/stuff/kernel-compile-slowdown.phtml") 
but that only results in errors. All I really want to do is either change the nice level of the compile and / or preferably slip in a "sleep 5" between each object that gets built. 

I thought it would be easy but I have been searching for days looking for a solution. 

I already tried...
```
nice -n 19 fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers 
```
and...
```
fakeroot nice -n 19 make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers 
```

It runs but seems to have no effect.

Is there a way to change the nice level of every shell that is spawned from the command?

---

### Post by t4thfavor on 2009-06-30
Just put a big house fan on it while its compiling. OR if its winter where you are you could out it in the garage or outside (protected of course)

Take out some ram as that will cause it to slow down it may even alleviate your heat issues. Though it will cause more paging, which may make more heat.

EDIT:
I forgot to mention not to close the lid, that makes them head up big time.

---

### Post by lavinog on 2009-06-30
Can you use an intrepid live cd?
Jaunty seems to have issues with causing laptops to overheat.

---

### Post by jargoman on 2009-07-01
Ya I read the gazillion pages of complains about laptop heat in jaunty. It's odd there doesn't seem to be an obvious cause. I was thinking perhaps there are two cpu frequency scalers competing with each other and instead of the cpu's actual frequency being the problem it may be the rate the frequencies were being switched as each cpu-scaler fought for control. 

I'll try the fan, I'm using an ice pack right now. 

I'm not blaming linux, my fan isn't detected in vista. It works but I guess it's completely controlled by the bios which I tried updating but still nada.

What are cooling devices? Thermal detectors? fans?
```

jargoman@ubuntu-laptop:~$ dmesg | grep cool
[    1.375875] processor ACPI_CPU:00: registered as cooling_device0
[    1.375911] processor ACPI_CPU:01: registered as cooling_device1
[   12.404168] acpi device:13: registered as cooling_device2

```

edit:
k cooling_device2 is oddly enough my screen brightness control. I guess the other "cpu" cooling_devices only change processor states. They seem to have a min of 0 and a max of 3. Good ol HP will allow me control over each core of my processor individually, who knows the damage that could wreak, but god forbid they give me control over my FAN. 

I found the locations with. 
```

sudo find /sys | grep cool

```

The odd thing is that I switched my bios settings to "fan always on" but it seems like once ACPI is detected it goes back to the way it was previously.

---

### Post by XCan on 2009-07-01
Can you perhaps use the frequency scaling app. to limit your CPU to run at its lowest multiplier?

---

### Post by lavinog on 2009-07-01
> **jargoman said:**
> 

I'm not blaming linux, my fan isn't detected in vista. It works but I guess it's completely controlled by the bios which I tried updating but still nada.
...
edit:
k cooling_device2 is oddly enough my screen brightness control. I guess the other "cpu" cooling_devices only change processor states. They seem to have a min of 0 and a max of 3. Good ol HP will allow me control over each core of my processor individually, who knows the damage that could wreak, but god forbid they give me control over my FAN. 
...
The odd thing is that I switched my bios settings to "fan always on" but it seems like once ACPI is detected it goes back to the way it was previously.

Interesting find about the cooling_device2=brightness.
I don't have a fan setting in my bios, nor do I have fan control or readings in ubuntu.
My compaq laptop is 3 years old now and never got hot until now.

---

### Post by t4thfavor on 2009-07-01
Are you having any luck with that overheating issue? Did you disable compiz? If that is enabled it could be causing the video mem to get hotter than normal, and that may be your issue.

---

### Post by jargoman on 2009-07-02
I switched to gnome. disabled many startup programs. disabled effects :(  installed powernowd. installed rcconf to disable unneeded startup scripts. removed any module I didn't use and I'm talking usb, ethernet, pcmia. changed swappiness to zero. installed nvidia drivers and got gpu scaling working. changed my fstab settings to noatime. set my display brightness to 21%. 

Now it stays around 60c~70c unless I watch a flash video or compile something then it sky rockets. A degree a second past 100c

The reason I'm so paranoid is that it doesn't shut off until it hits 120c. Then is hard dies. 

It sucks because I want to compile a custom patched kernel so I can make an ubuntu or arch based backtrack like distro that's slim enough to fit on a usb . I would like to be able to compile a kernel each night when I sleep and not risk my hardware. 

If I could somehow get the compile process to sleep every so often and let the computer go idle. Preferably 10 seconds on, then 15 seconds sleep. Then I would just leave it in front of a fan.

---

