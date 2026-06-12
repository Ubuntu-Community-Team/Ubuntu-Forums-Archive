---
title: "thinkpad t42 black screen freeze - aptdaemon?"
date: 2010-06-06
forum: General Help
---

### Post by thefamousnomo on 2010-06-06
hello people

had 10.04lts running on a thinkpad t42 for the last month or so, and in the most part have been quite impressed. however, i have been suffereing from random lockups, where the screen goes black, mouse and keyboard are (seem) unresponsive and the magic sysreq key doesnt seem to work either.

can post lshw if requested, but having googled this seems to be an issue with video chipsets, mainly intel. this t42 has a 

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

and as with googled results the last entries in the syslog are

Jun 6 07:16:27 t42-laptop AptDaemon: INFO: Quiting due to inactivity
Jun 6 07:16:27 t42-laptop AptDaemon: INFO: Shutdown was requested

this seems to happen most often when using transmission (port 10009) and gotten much worse following a recent set of updates to kernel

2.6.32-22-generic

please help, this is really frustrating!

---

### Post by thefamousnomo on 2010-06-06
also, noticed that when the black screen freeze occurs the caps lock indicator below the screen flashes on-off-on-off...

would really appreciate any help people...

---

### Post by thefamousnomo on 2010-06-07
bump

this is very disappointing... :(

---

### Post by tgalati4 on 2010-06-07
The caps lock (and also the numlock) light flashing usually indicates a kernel panic.  It could be anything.  Since you have an ATI GPU in your T42, I would suspect a hardware fault.  The GPU's are known to get hot and delaminate causing hard lockups.

Try running an older distro (but something newer than Dapper) from the LiveCD.  If your machine locks up from an older live CD then I would suspect the hardware.  I've been running Jaunty on my T43p for the past year without problems.

Install lm-sensors and watch your GPU temperatures.  If they are running 60C then I would suspect a graphics chip delamination.

---

### Post by thefamousnomo on 2010-06-08
thanks for this man, at least ive got something to go on now... will check temps and maybe spin latest tinycore (other fav distro)

---

### Post by thefamousnomo on 2010-06-08
update

had some issues with lm-sensors initially as it reported that laptop thermal management is handled by acpi, and running sensors didnt seem to give me any descriptors for the readings... installed sensor-applet and was able to get the readings required.

gpu - 50 deg-c; vstable
cpu - 70 deg-c; vstable
hdd - 30 deg-c; vstable

no problems... but more bizarrely, i havent been able to reproduce the lockup! i had experienced maybe half a dozen randoms, then the day i first posted the laptop was virtually unusable and running transmission never failed to lock the machine up... i have been able to complete my download and get halfway through another... this is very strange...

the only variable i can think of is that during the 'bad day' the battery was charged to capacity but still plugged in during use... tonight the battery was fairly discharged, then plugged in before it ran out... it currently has 30mins until fully charged...

will post findings for info

btw. would kernel panic not get logged somewhere?

---

### Post by tgalati4 on 2010-06-08
```
dmesg | more
```

That will scroll through the messages.  Sometimes kernel panics only get written to a console.  Since your laptop is old, I would suspect a battery/power problem as well.  Running the laptop while simultaneously charging an old battery can cause an overcurrent condition which causes the laptop to shutdown or freeze.  How many minutes of runtime do you get on the battery?

Also, 70C is kind of toasty for your CPU.  Try installing tpfan and tweaking the parameters so your fan kicks up when you hit 60C.

```
apt-cache search tpfan
```

The T4x series have a lot of thermal issues.  That explains why the T43 has so many embedded sensors:

tgalati4@tpad-Gloria7 ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +51.0°C  (crit = +99.0°C)                  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       3249 RPM
temp1:       +51.0°C                                    
temp2:       +47.0°C                                    
temp3:       +36.0°C                                    
temp4:       +60.0°C                                    
temp5:       +33.0°C                                    
ERROR: Can't get value of subfeature temp6_input: Can't read
temp6:        +0.0°C                                    
temp7:       +27.0°C                                    
ERROR: Can't get value of subfeature temp8_input: Can't read
temp8:        +0.0°C                                    
temp9:       +46.0°C                                    
temp10:      +51.0°C                                    
temp11:      +46.0°C                                    
ERROR: Can't get value of subfeature temp12_input: Can't read
temp12:       +0.0°C                                    
ERROR: Can't get value of subfeature temp13_input: Can't read
temp13:       +0.0°C                                    
ERROR: Can't get value of subfeature temp14_input: Can't read
temp14:       +0.0°C                                    
ERROR: Can't get value of subfeature temp15_input: Can't read
temp15:       +0.0°C                                    
ERROR: Can't get value

---

### Post by gustavorahal on 2010-06-09
I have the same problem, same hardware, same 10.04. Could not find the cause as well. "sensors" tells me the various temperatures are sane.

---

### Post by biofuelfarmer on 2010-06-09
Same problem, T43 where a dual boot install of 10.04 was added.    Random freeze while in Firefox: black screen, cursor unmoveable, caps lock light flashing.  

Temps seem reasonable, had this machine open the other day and cleaned out all the dust before installing Lucid.   Updated it to the latest BIOS after seeing discussion this might be the culprit; this is the first freeze after that.

This freeze occurred just when I hit enter on a page of Consumer Reports auto reliability survey.   (My cars typically still run after the check engine light comes on.)

Based on a discussion about problems with 10.04 found elsewhere on this forum, I am thinking about downgrading.

Update:  I did in fact do a downgrade on the T43 machine, and also on a Dell D600 laptop.   Too early to tell if the problem is gone on the T43, but I can say for certain that the mouse problems I was having on the Dell are gone.  Unfortunately one of the benefits of 10.04 on the Dell was that Flash worked better, and now with 9.04 it's back to stuttering audio.   Oh well...   

My thanks to all those who repair these bugs!

---

### Post by gustavorahal on 2010-06-10
This problem might be related to bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765)

Will try kernel linux-rt 2.6.31 and see how it goes

---

### Post by gustavorahal on 2010-06-11
FYI, using 10.04 with kernel 2.6.31 solved the freeze problem. Did not experience freezes anymore. As I mentioned, just fire synaptic and install linux-rt kernel (with is based on 2.6.31). No regression was found up to now on using this kernel on 10.04.

---

### Post by thefamousnomo on 2010-06-12
hello people

thanks for all info, running some tests, will get back to you... strange thing is that temps can run fine for long periods of use, but sometimes after startup they seem to rocket up to limits very quickly...

cheers again, will report findings

---

### Post by thefamousnomo on 2010-06-15
just a wee update

i have had no freezes for over a week... have done little more than install sensors-applet...

still monitoring temp closely, it FEELs like a temp issue, and as i say i can use the laptop for hours and be fine, but can boot and be at limits almost instantly...

---

### Post by thefamousnomo on 2010-06-19
hiya

left a torrent on last night, got up a few hours later to a black-screen-freeze... hard rebooted and saw the temps sky hight! was convinced then this was a temps prob.

however, checking email, chatting and browsing web just now, temps were

hd 30
cpu 40
gpu 44

suffered another freeze... still intend to open up the machine and ensure its dust & lint free, but now feeling its something else. will try linux-rt and see how we do.

---

### Post by thefamousnomo on 2010-06-20
hello people

thanks for all the help thus far

can confirm that installing

linux-image-2.6.31-10-rt - Linux kernel image for version 2.6.31 on Ingo Molnar's full real time preemption patch

and

linux-rt - complete Realtime (RT) Linux kernel

i then changed the default kernel in /etc/default/grub by changing GRUB_DEFAULT=0 to GRUB_DEFAULT=4 (im not too up on this version of grub, is this the correct way to do this?)

i can confirm that the system no longer seems to freeze when booted with the linux-image-2.6.31-10-rt. however, do i need linux-rt installed, or is the above kernel enough?

also, im getting boot messages now before a very brief splash screen, and now having issues with the screen brightness (keeps dropping to just above minimum a few times after boot, have to adjust with function keys, sometimes drops back...)

can anyone help?

---

### Post by thefamousnomo on 2010-06-23
bumping

---

