---
title: "ubuntu 10.04 beta2 high temperature and Internet"
date: 2010-04-17
forum: General Help
---

### Post by c00lwaterz on 2010-04-17
Hi,

I have installed the ubuntu 10.04 beta 2. I have notice that it has high temperature. I have try the "top" in terminal. There are no high usage of CPU and Memory. but still get high temperature. same in karmic 9.1. I have been using this ubuntu 10.04 beta2 fresh install just today. I did not do anything or install anything. It gets hot easily after few minutes. It was installed properly and no problem.

2nd problem is I try to reboot then i see the wifi signal and it detects my wifi and also my accesspoint. so I try to connect. I was connected to my accesspoint. My accesspoint is near my side. then I click firefox to test the connection. but no luck. cannot display page. maybe the internet was block even i was connected to my accesspoint. I try to check the signal then I saw (88%).

If someboday can help me

thanks in advance

---

### Post by cariboo on 2010-04-17
Your network problem looks like a dns issue, or it may be the same issue as in [this]("http://ubuntuforums.org/showthread.php?t=1441818&highlight=slow") thread.

If things are running hot check the fan and surrounding area for dust build up.

---

### Post by moviemaniac on 2010-04-17
I noticed you use an ATI Radeon 4500 on a notebook. You're most likely using the opensource radeon-driver which currently (as in the versions in lucid) doesn't support power management. It is also most certain that your GPU and CPU share a heatsink and thus the GPU - which runs very hot because of the lack of power management - keeps the CPU temperature up.
The only fix* for this is to use the proprietary ATI fglrx driver which features power management and will keep your GPU (and thus the CPU) cool(er).

I noticed this on my brother's notebook too and the problem cost me quite a lot of hair (from the constant pulling :D ) before I nailed it - the CPU (C2D) would run on 75-80° Celsius in idle - with the fglrx driver it's down to more normal 45-50°.

*unless you want to compile the latest mainline-kernel and cutting-edge in-development drivers yourself

---

### Post by forcecore on 2010-04-17
what happens if someone installs final version of Lucid and do not know this and keeps open driver (person dont know about power managment problem) then burns down his laptop or desktop pc-s video card ?. This may become great issue around world especially on laptops after release and may damage Ubuntu popularity, imagine news: Ubuntu burns down GPU-s

---

### Post by eltonw on 2010-04-17
> **c00lwaterz said:**
> Hi,

I have installed the ubuntu 10.04 beta 2. I have notice that it has high temperature. I have try the "top" in terminal. There are no high usage of CPU and Memory. but still get high temperature. same in karmic 9.1. I have been using this ubuntu 10.04 beta2 fresh install just today. I did not do anything or install anything. It gets hot easily after few minutes. It was installed properly and no problem.

2nd problem is I try to reboot then i see the wifi signal and it detects my wifi and also my accesspoint. so I try to connect. I was connected to my accesspoint. My accesspoint is near my side. then I click firefox to test the connection. but no luck. cannot display page. maybe the internet was block even i was connected to my accesspoint. I try to check the signal then I saw (88%).

If someboday can help me

thanks in advance

The connection issue is discussed HERE: [http://ubuntuforums.org/showthread.php?p=9121252#post9121252]("http://ubuntuforums.org/showthread.php?p=9121252#post9121252")
also, it is actually a problem _[COLOR="DarkRed"]at the kernel level[/COLOR]_, since the problem is consistent across all distros using the current kernel ... not just debian, but even the rpr distros are affected.

see here also: [https://bugs.launchpad.net/bugs/496093]("https://bugs.launchpad.net/bugs/496093")

HTH,

---

### Post by noelvh on 2010-04-17
How dose one install the correct driver for ATI? I have the older x300 ATI card in my laptop, and the last thing I need is it over heating. I have tried to install the envyg driver under 9.04 and that failed. So If I go to the new 10.04 on this laptop can I get the correct driver, and if so can some one point me in the correct dierection. 

I have installed 10.04 on two machines at this point one with nivda 8800, and an intel video. No issues, and the intel was never run compiz till now under 10.04.

Noel

---

### Post by moviemaniac on 2010-04-18
> **forcecore said:**
> what happens if someone installs final version of Lucid and do not know this and keeps open driver (person dont know about power managment problem) then burns down his laptop or desktop pc-s video card ?. This may become great issue around world especially on laptops after release and may damage Ubuntu popularity, imagine news: Ubuntu burns down GPU-s
I don't know if you can really destroy GPUs that way or if they shut themselves off like the CPUs do when they run too hot. However I agree this is a serious problem for anyone running a fast radeon 3xxx/4xxx on a laptop where the GPU doesn't have it's own heatsink.

@noelvh: Your card (x300) is not supported by the ATI fglrx driver anymore so you can only use the open source one anyway. However I haven't seen this problem occur on pre-3xxx/4xxx series cards. I for myself am on an 2600XT and even though I'm using the open source driver without power management the card clocks so slowly that heat is not an issue (CPU when idle unter 30°, GPU below 50°).

---

### Post by c00lwaterz on 2010-04-18
thanks everyone for the help. my toshiba is 7 months old. just new. I will try all the suggestions and options you give. =)

I appreciate so much people here helping noob like me. Im really noob in linux but i like linux. I don't know why. I keep installing linux on my laptop.:guitar::guitar:

---

### Post by c00lwaterz on 2010-04-18
moviemaniac,

how do i install the correct driver for ati 4500? help pls. sorry for being noob. 

thanks for sharing and helping. I appreciate so much:guitar::guitar:

---

### Post by moviemaniac on 2010-04-18
Go to System -> (second menu from the top, don't remember how it's labeled exactly in the English version as I use the German translation) -> restricted drivers.

If you don't find it, press ALT+F2, enter "jockey-gtk" (without quotation marks) and press enter

Just enable the ATI driver there and let te program do its thing. After that reboot as instructed (don't faint when you see the ugly looking plymouth because the ATI fglrx driver doesn't support KMS).

---

### Post by c00lwaterz on 2010-04-18
hi moviemaniac,

I have installed the ati/amd proprietary fglrx graphics driver.
then i reboot.
After reboot. then activated. then I go to ati catalyst control. do i need to change any settings?

right now im using the lucid. I just use wired connection for a moment to fix overheat.

---

### Post by moviemaniac on 2010-04-18
You shouldn't have to change any of the settings but there is one setting where you can choose between maximum performance and maximum energy saving. You can set these options for the machine being on battery and on AC. The machine'll run even cooler (but with less graphics performance which shouldn't be an issue unless you play very demanding games) if you also set a/c slider to maximum battery life.

---

### Post by c00lwaterz on 2010-04-18
i tried to run lm sensors

the result is in attached image. is that normal?


thanks

---

### Post by c00lwaterz on 2010-04-18
Hi all,

after few minutes of waiting. I run again the sensor. I'm monitoring the temperature. I think it gets high after waiting. Not doing anything.

here is the latest update of temperature after few minutes of waiting.

---

### Post by c00lwaterz on 2010-04-18
now i have return to windows vista. after checking the temperature it goes to 75 deg C then it was freeze (so hot). I push the power button to get off.

Now I am running in windows system. any suggestion on how to fix?

thanks

---

### Post by tsger on 2010-04-18
I, too, have an ATI laptop video card.  Installed the proprietary drivers, noticed a MUCH improved temperature!  Current cpu temp is 47 c.

I am so thankful, now my hands don't feel like they are going to be burnt off!

---

### Post by antiram on 2010-04-19
the ati temp problem can solved with disable kms and use the old user mode setting with kernel bootparameter "radeon.modeset=0" or "nomodeset". Maybe the parameter must set before "splash" parameter. 

Then use a xorg.conf with following settings (all or any):
```

Section "Device"
        Driver          "radeon"
        ...
        Option          "ClockGating"           "on"
        Option          "DynamicPM"             "on"
        Option          "ForceLowPowerMode"     "on"
EndSection

```
The ForceLowPowerMode brings the lowest energy comsumption. eg. idle with a HD3450: 80Watt without powersaving, 74Watt with ClockGating+DynamicPM, 66Watt with all 3 options.

---

### Post by andrek on 2010-04-19
Looks like the Arch guys have the power management working on the open-source drivers (with KMS enabled). [http://bbs.archlinux.org/viewtopic.php?id=79509&p=48](http://bbs.archlinux.org/viewtopic.php?id=79509&p=48) Is there any PPA which would consist of the -git kernel & drm stuff packages, just to test it out?

---

### Post by c00lwaterz on 2010-04-19
hello,

so guys, what do you suggest me to do with my overheating laptop in lucid? I don't know much about coding.

thanks

---

### Post by c00lwaterz on 2010-04-20
up

---

### Post by cariboo on 2010-04-20
Please wait 24 hours before bumping your thread.

---

### Post by c00lwaterz on 2010-04-20
ok thanks

---

### Post by c00lwaterz on 2010-04-20
I have notice that the fan is not blowing.
then I update using update manager (wired connection).

The fan is so silent and no blowing. I have search google and other people have same experience.

Any suggestions?

---

### Post by forcecore on 2010-04-20
i am interested what developers do to add power control or remove open driver at all, belive me it may cause very catastrophic news on lot of sites and ruins Ubuntu popularity.

---

### Post by c00lwaterz on 2010-04-21
is there any solution? I tried but I cannot fix it. :confused:
the fan is not working in lucid beta2. :confused: also the wireless after i coonect then it will disconnect automatically after 4 seconds or few seconds. still not working internet on wifi. so for now i use wired to fix high temp but no luck

---

### Post by c00lwaterz on 2010-04-22
now. can I "up"?

---

### Post by screaminj3sus on 2010-04-22
Yeah, sadly you need to use fglrx if you want any power management. It sucks because the open source driver sunscompiz smoother, and without tearing! fglrx has nasty tearing all over, especially with video.

My laptop gets unbearably hot using the open source driver (mobility 2600) just idling it gets far hotter than windows does when gaming. fglrx runs hotter than the windows driver as well but its signifcantly better than the opensource driver, because the fan isnt full blast all the time and it stays reasonably cool.

---

### Post by c00lwaterz on 2010-04-23
in my case , even i have fglrx ati proprietary driver, my laptop still overheat (fan not working). How sad..:confused:

---

### Post by moviemaniac on 2010-04-23
In that case I cuess you're experiencing a different bug/problem.

Did you try executing sudo sensors-detect (and answer yes to all the questions) and see whether that helps (reboot afterwards or manually modprobe the modules listed at the end)?

---

### Post by c00lwaterz on 2010-04-23
not yet. so i will run the sudo sensors-detect then after that, what will i do?

I just did the intalls lm sensor then i type sensors to get the temp.

---

### Post by moviemaniac on 2010-04-23
sensors-detect does what it says: It detects _all_ supported sensors in your system and sees to it they get used (i.e. the appropriate module gets loaded on booting). You don't have to "do" anything afterwards.

---

### Post by c00lwaterz on 2010-04-23
after typing sudo sensors0detect . should i put the result here? so it can help me?

---

### Post by moviemaniac on 2010-04-23
correcting myself: Forget about sensors-detect! A bit of googling on your side would have brought you to this kernel bugreport stating this is a BIOS bug:

[https://bugzilla.kernel.org/show_bug.cgi?id=14529](https://bugzilla.kernel.org/show_bug.cgi?id=14529)

However there is also a way for you to workaround the problem:

open up a terminal and enter "sudo gedit /etc/default/grub"
look for the line saying GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
after splash (within the quotation marks) add acpi.power_nocheck
Close gedit, save and execute sudo update-grub
after that reboot and your fan should kick in much sooner.

---

### Post by c00lwaterz on 2010-04-23
so there is a report. would they fix it?

---

### Post by moviemaniac on 2010-04-23
Did you actually read the bugreport or what I wrote? I guess not because if you had then you wouldn't ask.

However yust to make sure here is a quote from the bugreport:

> **this is a BIOS problem** that the fan device reported uninitiated state.
we need to use acpi.power_nocheck to control ACPI fan devices.

Explanation: This is not for the kernel developers to fix - it needs to be addressed by Toshiba in the form of a BIOS upgrade. Yes, I know it works in Windows - most likely because there's a workaround in a Toshiba driver which makes it work on Windows. But just because it works on Windows it doesn't automatically mean it's the fault of the Linux kernel, it is still a problem Toshiba should work on.

---

### Post by c00lwaterz on 2010-04-23
i am reading while replying to thread. I don't know how. I am really noob here. :confused:
also they talk like professionals in linux :( not easy for me. I am willing to try but it will give me a hard time.

---

### Post by c00lwaterz on 2010-04-23
i saw this

Comment #27 From  Zhang Rui   2010-01-21 07:57:55  -------

what if you boot with boot option "acpi.power_nocheck"?

------- Comment #28 From brice rebsamen 2010-01-22 03:32:00 -------

booting with boot option "acpi.power_nocheck" solves the problem. The fan turns
faster when the temperature increases and slows down when the temperature
drops, thus effectively maintaining the temperature around 45C when the CPU is
moderately loaded, and around 60C when the CPU load gets high.

Thank you very much for that.

-------------------------------
so how to do this?

---

### Post by moviemaniac on 2010-04-23
> **c00lwaterz said:**
> i saw this

[...]

so how to do this?

Quoting myself from a few minutes ago...

> **moviemaniac said:**
> [...]
However there is also a way for you to workaround the problem:

open up a terminal and enter "sudo gedit /etc/default/grub"
look for the line saying GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
after splash (within the quotation marks) add acpi.power_nocheck
Close gedit, save and execute sudo update-grub
after that reboot and your fan should kick in much sooner.

---

### Post by c00lwaterz on 2010-04-23
this is the result

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found Windows Recovery Environment (loader) on /dev/sda2
Found Windows Vista (loader) on /dev/sda4
done


now i will restart :)

---

### Post by c00lwaterz on 2010-04-23
now i have restarted. still hot. not working( fan) how to check in terminal the fan if it is running?

---

### Post by c00lwaterz on 2010-04-23
RUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi.power_nocheck"

still hot going to 65 deg c.

---

### Post by moviemaniac on 2010-04-23
an you post the output of **cat /boot/grub/grub.cfg** just to make sure you modified the grub defaults correctly and they have been applied?

---

### Post by c00lwaterz on 2010-04-23
> **moviemaniac said:**
> an you post the output of **cat /boot/grub/grub.cfg** just to make sure you modified the grub defaults correctly and they have been applied?

how to do this?

thanks so much

---

### Post by moviemaniac on 2010-04-23
just type "cat /boot/grub/grub.cfg" and copy/paste what it says here.

---

### Post by c00lwaterz on 2010-04-23
here it is:

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
	insmod ntfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a8b22be6b22bb828
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash acpi.power_nocheck
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a8b22be6b22bb828
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-19-generic" {
	insmod ntfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a8b22be6b22bb828
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-19-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash acpi.power_nocheck
	initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, Linux 2.6.32-19-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a8b22be6b22bb828
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-19-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 02e0d61ee0d6182d
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
	insmod ntfs
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4e2efd202efd022f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by moviemaniac on 2010-04-23
Well, that looks okay - it's weirt it shouldn't work.

I've got two things for you to try:

1) Power down the notebook and switch it off again. Maybe the BIOS needs some kind of reset that doesn't work when rebooting. It might not help but you never know

2) If that doesn't work, edit the grub file as instructed before and add **acpi_osi=\"Linux\"** after **acpi.power_nocheck** Please do note that you need to copy the quotation marks too - everything I've typed here in bold needs to be added to this specific line. Save the file, run sudo update-grub, power down and reboot. See if that helps.

//edit:
Please also post the output of this command:
"grep . /sys/class/thermal/cooling_device*/*"

---

### Post by c00lwaterz on 2010-04-23
> **moviemaniac said:**
> Well, that looks okay - it's weirt it shouldn't work.

I've got two things for you to try:

1) Power down the notebook and switch it off again. Maybe the BIOS needs some kind of reset that doesn't work when rebooting. It might not help but you never know

2) If that doesn't work, edit the grub file as instructed before and add **acpi_osi=\"Linux\"** after **acpi.power_nocheck** Please do note that you need to copy the quotation marks too - everything I've typed here in bold needs to be added to this specific line. Save the file, run sudo update-grub, power down and reboot. See if that helps. If not then I also don't know what to do exactly anymore and it would be best for you to submit a bug against the kernel in launchpad.

so powerdown = shutdown?

---

### Post by moviemaniac on 2010-04-23
> **c00lwaterz said:**
> so powerdown = shutdown?
yes

---

### Post by c00lwaterz on 2010-04-23
the fan still don't work. using kernel 2.6.32

i have tried closing the lid then fan is on still hot

---

### Post by moviemaniac on 2010-04-23
Can you post the output of this command:
"grep . /sys/class/thermal/cooling_device*/*"

---

### Post by c00lwaterz on 2010-04-23
i tried closing the lid then the fan turns on and temp go down a bit

this is the result of "grep ./sys/class/thermal/cooling_device*/*" 



/sys/class/thermal/cooling_device0/cur_state:1
/sys/class/thermal/cooling_device0/max_state:1
/sys/class/thermal/cooling_device0/type:Fan
/sys/class/thermal/cooling_device1/cur_state:1
/sys/class/thermal/cooling_device1/max_state:1
/sys/class/thermal/cooling_device1/type:Fan
/sys/class/thermal/cooling_device2/cur_state:1
/sys/class/thermal/cooling_device2/max_state:1
/sys/class/thermal/cooling_device2/type:Fan
/sys/class/thermal/cooling_device3/cur_state:1
/sys/class/thermal/cooling_device3/max_state:1
/sys/class/thermal/cooling_device3/type:Fan
/sys/class/thermal/cooling_device4/cur_state:1
/sys/class/thermal/cooling_device4/max_state:1
/sys/class/thermal/cooling_device4/type:Fan
/sys/class/thermal/cooling_device5/cur_state:1
/sys/class/thermal/cooling_device5/max_state:1
/sys/class/thermal/cooling_device5/type:Fan
/sys/class/thermal/cooling_device6/cur_state:0
/sys/class/thermal/cooling_device6/max_state:0
/sys/class/thermal/cooling_device6/type:Processor
/sys/class/thermal/cooling_device7/cur_state:0
/sys/class/thermal/cooling_device7/max_state:0
/sys/class/thermal/cooling_device7/type:Processor
/sys/class/thermal/cooling_device8/cur_state:0
/sys/class/thermal/cooling_device8/max_state:7
/sys/class/thermal/cooling_device8/type:LCD

---

### Post by moviemaniac on 2010-04-23
oh-kay.

Let's try this - manually turning all the available fans on:
Do not reboot after these commands, they should take effect immediately

"sudo echo 0 > /sys/class/thermal/cooling_device0/cur_state"
"sudo echo 0 > /sys/class/thermal/cooling_device1/cur_state"
"sudo echo 0 > /sys/class/thermal/cooling_device2/cur_state"
"sudo echo 0 > /sys/class/thermal/cooling_device3/cur_state"
"sudo echo 0 > /sys/class/thermal/cooling_device4/cur_state"
"sudo echo 0 > /sys/class/thermal/cooling_device5/cur_state"

should that not work try these:
"sudo echo 0 > /sys/class/thermal/cooling_device0/state"
"sudo echo 0 > /sys/class/thermal/cooling_device1/state"
"sudo echo 0 > /sys/class/thermal/cooling_device2/state"
"sudo echo 0 > /sys/class/thermal/cooling_device3/state"
"sudo echo 0 > /sys/class/thermal/cooling_device4/state"
"sudo echo 0 > /sys/class/thermal/cooling_device5/state"

---

### Post by c00lwaterz on 2010-04-23
i have tried 

a@ubuntu:~$ sudo echo 0 > /sys/class/thermal/cooling_device0/cur_state
bash: /sys/class/thermal/cooling_device0/cur_state: Permission denied

---

### Post by c00lwaterz on 2010-04-23
this
@ubuntu:~$ sudo echo 0 > /sys/class/thermal/cooling_device0/state
bash: /sys/class/thermal/cooling_device0/state: No such file or directory

device0 to device5 no such file or directory

---

### Post by moviemaniac on 2010-04-23
I'm looking into it - I'll be back shortly

---

### Post by c00lwaterz on 2010-04-23
thanks and i am really thankful that people like you has patience helping people like me. 

thanks in advance

---

### Post by moviemaniac on 2010-04-23
okay, for some more information please post the output of these two separate commands

"grep . /sys/class/thermal/*/*" (slightly different than before

and:
"dmesg | grep fan"

as well as
"dmesg | grep FAN"

---

### Post by c00lwaterz on 2010-04-23
here

 grep . /sys/class/thermal/*/*
/sys/class/thermal/cooling_device0/cur_state:1
/sys/class/thermal/cooling_device0/max_state:1
/sys/class/thermal/cooling_device0/type:Fan
/sys/class/thermal/cooling_device1/cur_state:1
/sys/class/thermal/cooling_device1/max_state:1
/sys/class/thermal/cooling_device1/type:Fan
/sys/class/thermal/cooling_device2/cur_state:1
/sys/class/thermal/cooling_device2/max_state:1
/sys/class/thermal/cooling_device2/type:Fan
/sys/class/thermal/cooling_device3/cur_state:1
/sys/class/thermal/cooling_device3/max_state:1
/sys/class/thermal/cooling_device3/type:Fan
/sys/class/thermal/cooling_device4/cur_state:1
/sys/class/thermal/cooling_device4/max_state:1
/sys/class/thermal/cooling_device4/type:Fan
/sys/class/thermal/cooling_device5/cur_state:1
/sys/class/thermal/cooling_device5/max_state:1
/sys/class/thermal/cooling_device5/type:Fan
/sys/class/thermal/cooling_device6/cur_state:0
/sys/class/thermal/cooling_device6/max_state:0
/sys/class/thermal/cooling_device6/type:Processor
/sys/class/thermal/cooling_device7/cur_state:0
/sys/class/thermal/cooling_device7/max_state:0
/sys/class/thermal/cooling_device7/type:Processor
/sys/class/thermal/cooling_device8/cur_state:0
/sys/class/thermal/cooling_device8/max_state:7
/sys/class/thermal/cooling_device8/type:LCD
/sys/class/thermal/thermal_zone0/cdev0_trip_point:1
/sys/class/thermal/thermal_zone0/cdev1_trip_point:1
/sys/class/thermal/thermal_zone0/cdev2_trip_point:7
/sys/class/thermal/thermal_zone0/cdev3_trip_point:6
/sys/class/thermal/thermal_zone0/cdev4_trip_point:5
/sys/class/thermal/thermal_zone0/cdev5_trip_point:4
/sys/class/thermal/thermal_zone0/cdev6_trip_point:3
/sys/class/thermal/thermal_zone0/cdev7_trip_point:2
/sys/class/thermal/thermal_zone0/mode:enabled
/sys/class/thermal/thermal_zone0/temp:45000
/sys/class/thermal/thermal_zone0/trip_point_0_temp:108000
/sys/class/thermal/thermal_zone0/trip_point_0_type:critical
/sys/class/thermal/thermal_zone0/trip_point_1_temp:101000
/sys/class/thermal/thermal_zone0/trip_point_1_type:passive
/sys/class/thermal/thermal_zone0/trip_point_2_temp:98000
/sys/class/thermal/thermal_zone0/trip_point_2_type:active
/sys/class/thermal/thermal_zone0/trip_point_3_temp:90000
/sys/class/thermal/thermal_zone0/trip_point_3_type:active
/sys/class/thermal/thermal_zone0/trip_point_4_temp:80000
/sys/class/thermal/thermal_zone0/trip_point_4_type:active
/sys/class/thermal/thermal_zone0/trip_point_5_temp:70000
/sys/class/thermal/thermal_zone0/trip_point_5_type:active
/sys/class/thermal/thermal_zone0/trip_point_6_temp:60000
/sys/class/thermal/thermal_zone0/trip_point_6_type:active
/sys/class/thermal/thermal_zone0/trip_point_7_temp:42000
/sys/class/thermal/thermal_zone0/trip_point_7_type:active
/sys/class/thermal/thermal_zone0/type:acpitz

---

### Post by c00lwaterz on 2010-04-23
and another one

@ubuntu:~$ dmesg | grep FAN
[    0.336322] ACPI: Fan [FAN0] (on)
[    0.336422] ACPI: Fan [FAN1] (on)
[    0.336521] ACPI: Fan [FAN2] (on)
[    0.336620] ACPI: Fan [FAN3] (on)
[    0.336721] ACPI: Fan [FAN4] (on)
[    0.336819] ACPI: Fan [FAN5] (on)

---

### Post by moviemaniac on 2010-04-23
Okay, after reading some stuff and judging from your output I think your fan is running (but very slowly - if it were completely off the CPU would be much hotter) but due to the BIOS bug regarding the ACPI tables the fans don't spin up when the CPU gets hotter. There's nothing more I can do from here - that's where the programmers are needed.

I'd suggest you post about your issue on the kernel bugzilla and tell them that the workaround they posted doesn't work for you and you're affected by this bug.
Also you should take a look at this bugreport in Launchpad and post your details there so they know there are other users affected too: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500666](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500666)

I'm sorry I couldn't be of any more help. I know how frustrating this powermanagement stuff can be - I have a custom script running on my machine which manually adjusts the fan speeds after the sensors readings or otherwise mine would run too hot too but this script won't work in your case and neither can I adapt it to make it work for you...

However I'll keep looking for a bit, maybe I can come up with something but don't get your hopes up.

---

### Post by c00lwaterz on 2010-04-23
i notice this:

I restart then wait it for 5 minutes then the laptop is hot even the fan is working on the display terminal. then I try close lid again then the fan turn on in real(i can feel low running).

so if I don't close the lid, the fan is not working even it is on in the terminal

---

### Post by moviemaniac on 2010-04-23
Could you ry to suspend and resume the laptop? Someone mentioned the fans would work after doing that. It's at least worth a try.

---

### Post by c00lwaterz on 2010-04-23
thanks thanks I appreciate your effort. it's not the result is appreciated but the effort you've done to help me.


thanks again. I will try and try to fix this

---

### Post by c00lwaterz on 2010-04-23
yes when i close the lid it suspends. it works. fan run slow but i can feel the hot air going out and the temp is going down to 46 to 48 deg c.

it is better but i need to suspend it just once everytime i turn on the linux.

---

### Post by moviemaniac on 2010-04-23
I just reported you problem on the kernel bugzilla and also on launchpad (links have been posted here in this thread) and I'll stay on it for you!

Normally I would compile a custom mainline kernel for you now so you can try if the problem is gone in the latest version (2.6.34-rc5) but I can't as the ATI fglrx driver from Ubuntu only works with the 2.6.32 Ubuntu-kernel. Going back to the open source ATI driver - which is what you would need to do to use 2.6.34 - would only worsen the heat problems for you.

---

### Post by c00lwaterz on 2010-04-23
wow! thanks a lot! I don't know how to use bugzilla and launchpad. but you're great. you help me with all your effort and time. I appreciate so much:P:)

---

### Post by Jguy on 2010-04-23
I realize this issue has been somewhat resolved, but I cannot help but to add my 3 cents.

I had an old(ish) Acer laptop (actually, I still have it). I had a similar issue with it as you did, except whenever I put it into standby and resumed it, in Ubuntu or XP (it originally came with Vista), the laptop GPU/CPU temps would climb to 85C and the laptop would completly shut down. It turns out that power/thermal management was software based, not hardware based (and the only way the "software" would work is in Vista). So maybe this is part of your issue? The fans just don't respond to anything except what it was made to respond to? Stupid I know, but maybe an idea to mull around in your head for a while?

---

### Post by moviemaniac on 2010-04-23
Jguy,
I'm starting to thing that's the problem here too - what we would need here is a way to tell the fan to spin up to the RPMs requested by the thermal zone the CPU is in. Normally Linux' ACPI has such an ability but in this case a BIOS bug (according to upstream) prevents it from working. Pretty shitty situation if you ask me.

//edit: @coolwaterz: You could also try to update your bios to the latest version - instructions can be found here: [http://pc.toshiba-asia.com/portal/public/driverDlDetails.action?pgAction=driverDlDetails.action&a=driverDlDetails&itemId=30515&currentTab=service&type=Drivers](http://pc.toshiba-asia.com/portal/public/driverDlDetails.action?pgAction=driverDlDetails.action&a=driverDlDetails&itemId=30515&currentTab=service&type=Drivers)

---

### Post by c00lwaterz on 2010-04-23
hi moviemaniac,

for the mean time, I want to fix my wifi while I can use suspend for the fan. i can detect my wifi and access point. but when trying to connect, it doesn't connect. do you have any idea? i have search before but no luck. I will also try again today to search.

thanks

---

### Post by moviemaniac on 2010-04-24
Okay, first things first: Please post what lspci has to say about your wireless card, I need to know exactly which card you're using.

---

### Post by c00lwaterz on 2010-04-25
> **moviemaniac said:**
> Okay, first things first: Please post what lspci has to say about your wireless card, I need to know exactly which card you're using.

ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
02:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
02:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
02:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
08:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
08:00.1 Audio device: ATI Technologies Inc RV710/730

---

### Post by moviemaniac on 2010-04-25
Oh dear, the dreaded 8172 again... No wonder it's bumpy ride for you ;)

Download the latest driver from here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)

(It is the driver for the RTL8192SE)

- unpack the archive
- in the terminal cd to the extracted folder
- sudo make
- sudo make install
- reboot

You might have to repeat these steps after every kernel upgrade

---

### Post by moviemaniac on 2010-04-25
Update: forget about the instructions above, I found a better way:

Just install this package and you should be fine: [https://launchpad.net/~matt-price/+archive/mattprice/+files/rtl8192se-dkms_2.6.0015.0127.2010_all.deb](https://launchpad.net/~matt-price/+archive/mattprice/+files/rtl8192se-dkms_2.6.0015.0127.2010_all.deb)
And add this ppa here for updates: [https://launchpad.net/~matt-price/+archive/mattprice](https://launchpad.net/~matt-price/+archive/mattprice)

Also go to a terminal and enter:
gksu gedit /etc/pm/config.d/wireless
add this line to the file:
SUSPEND_MODULES="r8192se_pci"
save and exit
This should make the card work after suspend too

And one more thing about your CPU: You said it runs on 60-65° You don't have to worry about anything with these temperatures. Yes, they are high, but not too high. If you type sensors in your terminal the coretemp module tells you how hot the CPU can get. If the working temperature stays about 20° under this maximum temperature (which ranges from 90-110 or even more degrees) you're absolutely fine.

---

### Post by c00lwaterz on 2010-04-25
ok, i will try. I have fresh install again the ubuntu 10.04 beta2. because while i am reading forums then suddenly no internet. then i restart, still don't have internet in wired. so I reinstall. im now online using wired connection

---

### Post by c00lwaterz on 2010-04-25
hi moviemaniac,

the wireless is working perfectly. you're great! thanks so much
so now the temperature still gets high. i will monitor the temperature and i will post it here. now it is 75 deg c. I will post if it goes higher.


thanks so much moviemaniac..

---

### Post by c00lwaterz on 2010-04-25
update of temp

getting hotter

pls see attachment.

thanks so much :)

---

### Post by Untitled_No4 on 2010-04-25
moviemaniac has done a great job, but since you have a problem with the kernel and ATI open source drivers, you could try an alternative route by using the latest Kernel and open source drivers (which do have power management). It's actually not very difficult to achieve but don't do it unless you're willing to risk breaking.

Check out [http://ubuntuforums.org/showpost.php?p=7773102&postcount=1](http://ubuntuforums.org/showpost.php?p=7773102&postcount=1), scroll down to where it says **Ubuntu Stuff** and follow all instruction all the way to **Useful Wiki Info**

Where it says "pick the version of the kernel..." just pick the latest one, all the way at the end of the page "v2.6.34-rc5-lucid/"

If you follow the instructions then it should be a safe procedure, but I'll stress again the word should, so keep you installation disk ready.

---

### Post by moviemaniac on 2010-04-25
@Untitled_No4: So the Kernels un the Ubuntu mainline ppa support PM for KMS? Taht'd be good - the ones I build myself currently don't support it but I don't care either as my 2600XT doesn't run hot anyway.
I have thought about suggesting a kernel update to -34 but as the fan problem exists on the BIOS level and the open source drivers don't get the ATI card cooler than fglrx it's a long shot whether the fan problems are resolved in the newer kernels or not. But I guess it's worth a try since the notebook is virtually unusable with 85°+ CPU temp.

So, in short @c00lwaterz: Follow the instructions on this post here - scroll down a bit, it starts where it says "Ubuntu stuff": [http://ubuntuforums.org/showpost.php?p=7773102&postcount=1](http://ubuntuforums.org/showpost.php?p=7773102&postcount=1)
If you hit any problems following the instructions don' worry, we'll get you through this.

---

### Post by c00lwaterz on 2010-04-25
hi moviemaniac, 


thanks so much for the help in wireless..

I rest it awhile ago because of high temp and i let it cool. Now i will try the ubuntu stuff.

thanks for the support
I appreciate so much:)

---

### Post by c00lwaterz on 2010-04-25
what should I choose here:
- linux-headers...all.deb
- linux-headers..generic..i386.deb
- linux-image....i386.deb

so i need to choose i386 and rc5?
thanks


[ ]	BUILD.LOG	20-Apr-2010 12:06 	2.6M
[ ]	CHANGES	20-Apr-2010 10:03 	14K
[ ]	linux-headers-2.6.34-020634rc5-generic_2.6.34-020634rc5_amd64.deb	20-Apr-2010 11:06 	692K
[ ]	linux-headers-2.6.34-020634rc5-generic_2.6.34-020634rc5_i386.deb	20-Apr-2010 12:06 	673K
[ ]	linux-headers-2.6.34-020634rc5_2.6.34-020634rc5_all.deb	20-Apr-2010 10:07 	9.6M
[ ]	linux-image-2.6.34-020634rc5-generic_2.6.34-020634rc5_amd64.deb	20-Apr-2010 11:06 	30M
[ ]	linux-image-2.6.34-020634rc5-generic_2.6.34-020634rc5_i386.deb	20-Apr-2010 12:06 	30M
[ ]	linux-source-2.6.34_2.6.34-020634rc5_all.deb

---

### Post by moviemaniac on 2010-04-25
> **c00lwaterz said:**
> 

[ ]	BUILD.LOG	20-Apr-2010 12:06 	2.6M
[ ]	CHANGES	20-Apr-2010 10:03 	14K
[ ]	linux-headers-2.6.34-020634rc5-generic_2.6.34-020634rc5_amd64.deb	20-Apr-2010 11:06 	692K
[x ]	linux-headers-2.6.34-020634rc5-generic_2.6.34-020634rc5_i386.deb	20-Apr-2010 12:06 	673K
[x ]	linux-headers-2.6.34-020634rc5_2.6.34-020634rc5_all.deb	20-Apr-2010 10:07 	9.6M
[ ]	linux-image-2.6.34-020634rc5-generic_2.6.34-020634rc5_amd64.deb	20-Apr-2010 11:06 	30M
[ x]	linux-image-2.6.34-020634rc5-generic_2.6.34-020634rc5_i386.deb	20-Apr-2010 12:06 	30M
[ ]	linux-source-2.6.34_2.6.34-020634rc5_all.deb

I ticked the ones you need for i386 :)

---

### Post by Untitled_No4 on 2010-04-25
moviemaniac: the .34 mainline kernel does support PM. I had the same issue of an ATI GPU running hot (up to 100c) and with the mainline kernel, xorg-edger and adjust modprobe all is back to normal.

c00lwaterz:
You need to install three packages. The first is linux-headers-2.6.34-020634rc5_2.6.34-020634rc5_all.deb, whichever architecture you have.

The two other packages depend on the whether you installed 32 bit (i386) or 64 bit (amd64 or x86_64) Ubuntu. Each has a different iso file.
If you are not sure open terminal and run ```
uname -a
```
When I run that this is what I get:
> Linux ThinkPad-T500 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 **x86_64** GNU/Linux
Not the bold bit, which shows I'm running 64 bit. 
Once you've determined your architecture install the additional two packages
linux-headers....your architecture.deb
linux-image.....your architecture.deb
in that order. Once you've installed the new kernel reboot your system. You will have a new entry for it in your grub menu and you will have to chose it.

I see that moviemaniac beat me to it :)

---

### Post by c00lwaterz on 2010-04-25
hi moviemaniac and Untitled_No4,

I have downloaded the 2 headers. Now i need to use windows because it is really hot. I will download the 3rd file here in windows and put it in flashdisk so It will not take time. If i take time in linux, my laptop is getting hot. now i will download the linux-image-2.6.34-020634rc5-generic_2.6.34-020634rc5_i386.deb 20-Apr-2010 12:06 30M

thanks

---

### Post by moviemaniac on 2010-04-25
> **Untitled_No4 said:**
> moviemaniac: the .34 mainline kernel does support PM. I had the same issue of an ATI GPU running hot (up to 100c) and with the mainline kernel, xorg-edger and adjust modprobe all is back to normal.

That's good to know - now I have a better alternative to tell people when their GPU is getting too hot - previously if they didn't feel up to compiling their own kernel I had to tell them to use fglrx in order not to fry their GPUs :D

---

### Post by Untitled_No4 on 2010-04-25
moviemaniac, you're brave. I'd rather suggest fglrx just because it's a safer option for them. 
Also, I don't think the ATI heating issue is as severe as it looks, especially not for desktops. My office desktop has been running constantly (with only update required reboots) with the open source drivers since early Alpha 2. My home laptop was also running hot for a while without me realising because it's docked most of the time. Neither have shown any issues. Actually, the dynamic PM is automatically disabled when using dual screens so my laptop only uses PM when it's not docked, and this is where it matters due to the physical proximity to the hot parts. I think this might be the bigger issue here.

---

### Post by moviemaniac on 2010-04-25
@Untitled_No4: I guess it depends. If someone wants to use compiz or any other form of desktop effects fglrx is nearly unusable due to the lack of support for DRI2. Same goes for when you use your machine to watch movies/DVDs/BDs - the tearing is unbearable.

I fully agree the heating problem is mostly a non-issue for desktops. It is, however, a very serious issue for (some) notebook-users. Why? Because, as I already explained in several threads, many notebooks have one cooler/heatpipe for both the GPU and the CPU. I have two brothers, both were affected by this. One brother has a machine with a 4670 (methinks, might be a 4760 - I don't care, all I know is that it's a very fast model for notebooks) and the CPU would get hot up to 80° in idle! After switching to fglrx (he's a gamer too, so that's what he'd best use anyway) the idle CPU temperature sank by 30°(!). My other brother used the opensource driver too and his CPU (also a C2D) would only go up to 75° which is not that rare in notebooks but we were looking literally for months for a solution as after 15 minutes into Ubuntu his cpu governor (ondemand) would stick the CPU to run at 800MHz. No chance for it to run the CPU faster. Only after I fixed my other brothers notebook I thought the problems could be related. Sure enough, using fglrx his CPU temps went down by 20° and his CPU now scales up to 2,53GHz once again.
I on the other hand use an iMac 24" (just for the hardware... it IS a cool device if you have limited space on/under your desk) with an 2600XT which also shares the heatsink with the CPU but the GPU is so old/lame/whatever so it stays at 45-50° and doesn't noticeably affect the C2D CPU temps (30-35° when idling). Well, I have to admit, I'm using a custom fan-control-script which runs the fans much faster than Apples insane defaults (these would allow HDD temps of over 55° - 60 is the maximum for my WD HDD), without the custom-tailored fan-control I'm sure my GPU and CPU would run much hotter too with the open source drivers and my customized -34 kernels.
I'm sure these problems don't affect every ATI notebook user, but these two examples (and a few more here on the forums) show how bad an idea it is to ship KMS support withour proper PM. At least the release notes should mention these potential problems.

---

### Post by Untitled_No4 on 2010-04-25
I think we agree. Some people could definitely use the mainline kernel/xorg edgers method, hence why I mentioned it here. 
I'm not going into all those plymouth/kms discussions but thinking that all those issues just to get a flicker-free experience for some people and shaving a couple of seconds off boot time is a bit exaggerated but I like Kubuntu too much to consider that as a deal breaker.

---

### Post by c00lwaterz on 2010-04-25
hi moviemaniac,

here is what I have done:

Ubuntu stuff:
========================================
For Ubuntu users, I've modified info' from a post by Nerd King, & placed it below. This is a how-to for upgrading your kernel & the other packages required, to those that will always be newer than any supplied in the most current Ubuntu version. It is now followed by a quick how-to for getting Power Management working courtesy of a post in this thread by Untitled_No4:

The Procedure:

1. System -> Hardware Drivers -> Deactivate any ATI drivers and restart

2. Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
& pick the version of the kernel you want to use, be careful with your choice, having a read of this thread will help you with that choice. (I am on Arch & using the current kernel .34-git & the -git versions of the other required packages with no problems. So keeping an eye on the last parts of this thread should let you know just what should be safe to use.)

3. Download and execute the following (in this order, switch to 64 if need be)
- linux-headers...all.deb
- linux-headers..generic..i386.deb
- linux-image....i386.deb

4. Restart

then after restart, I don't have wifi again. Now I use windows to reply here in forum
--------------------------------------------------------------
i did not finish this one:

5. Add the xorg-edgers PPA ([https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)), update, upgrade.

6. Reboot.

7. Profit.

should I do that?

thanks

---

### Post by Untitled_No4 on 2010-04-25
Yes, you should do that, and also the bit underneath where you need to edit radeon-kms.conf.

---

### Post by moviemaniac on 2010-04-25
Yes, you should install the xorg-edgers ppa
And you might have to reinstall the wireless driver again (search for it in synaptic and select reinstall)

---

### Post by c00lwaterz on 2010-04-25
ok, thanks I will do it the xorg install using wired connection.

the ppa xorg is the fix for wifi isn't?

---

### Post by c00lwaterz on 2010-04-25
im lost. install is not successful with xorg, maybe im wrong in following. then I try to install wifi, no luck also. maybe i done wrong

---

### Post by Untitled_No4 on 2010-04-25
Do you get any errors?

---

### Post by c00lwaterz on 2010-04-25
yes in xorg. I did follow the instruction ppa but I don;t know how to make it correct.

---

### Post by Untitled_No4 on 2010-04-25
What errors do you get for xorg?

---

### Post by c00lwaterz on 2010-04-25
first I open terminal and type this:

sudo add-apt-repository ppa:user/ppa-name

then it says no such file.

then next try is I did it with this:

sudo add-apt-repository ppa:gwibber-daily/ppa

then after that I type:

sudo apt-get update

then after a few lines of code in buttom it has error.

I forgot the error name

---

### Post by Untitled_No4 on 2010-04-25
Run this:
```
sudo apt-add-repository ppa:gwibber-daily/ppa
sudo apt-get update
sudo apt-get upgrade
```
If you still get the error at the end of the output, copy/paste it here (hightlight text, right click and select copy, ctrl + c will not work in terminal)

Edit:
Sorry, you will also need to add the xorg repository:
```
sudo apt-add-repository ppa:xorg-edgers/ppa
```
As either the first or second command above. If you have already ran all three commands, then run this, and then second and third commands from above.

---

### Post by c00lwaterz on 2010-04-25
> **Untitled_No4 said:**
> Run this:
```
sudo apt-add-repository ppa:gwibber-daily/ppa
sudo apt-get update
sudo apt-get upgrade
```
If you still get the error at the end of the output, copy/paste it here (hightlight text, right click and select copy, ctrl + c will not work in terminal)

Edit:
Sorry, you will also need to add the xorg repository:
```
sudo apt-add-repository ppa:xorg-edgers/ppa
```
As either the first or second command above. If you have already ran all three commands, then run this, and then second and third commands from above.

after the sudo apt-get update

here is the last message :
[I]
Fetched 11.1MB in 1min 16s (147kB/s)                                           
W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
toshiba@ubuntu:~$ [/I]

---

### Post by Untitled_No4 on 2010-04-25
That's because you've added the ppa:user/ppa-name which doesn't exist. At the time being ignore this error and continue to 
```
sudo apt-get upgrade
``` and we'll remove it later.

---

### Post by c00lwaterz on 2010-04-25
> **Untitled_No4 said:**
> That's because you've added the ppa:user/ppa-name which doesn't exist. At the time being ignore this error and continue to 
```
sudo apt-get upgrade
``` and we'll remove it later.

yes im now in code sudo apt-get upgrade

it still in 27%.

can this help the high temp?

---

### Post by Untitled_No4 on 2010-04-25
> **c00lwaterz said:**
> can this help the high temp?

That's our goal...
Have you added the  ppa: xorg-edgers/ppa  as well? If yes, there is only one more step.

---

### Post by c00lwaterz on 2010-04-25
> **Untitled_No4 said:**
> That's our goal...
Have you added the  as well? If yes, there is only one more step.

yes that code is the first one I put in terminal

---

### Post by Untitled_No4 on 2010-04-25
Then the next step, after the upgrade is completed is to run the following
```
sudo gedit /etc/modprobe.d/radeon-kms.conf
```
The content of the file should look like that:
> options radeon modeset=1
and you will have to add " dynpm=1" so it looks like that:
> options radeon modeset=1 dynpm=1
Save, reboot, and your temperature should be normal.

---

### Post by c00lwaterz on 2010-04-25
> **Untitled_No4 said:**
> Then the next step, after the upgrade is completed is to run the following
```
sudo gedit /etc/modprobe.d/radeon-kms.conf
```
The content of the file should look like that:

and you will have to add " dynpm=1" so it looks like that:

Save, reboot, and your temperature should be normal.

should I do this if I have not yet installed the ati proprietary? because the last time I install it, I need to reinstall ubuntu so now I don't have. Do i need to reinstall ati proprietary?

I open the radeon kms

but no code inside. do i need to add the two codes?

---

### Post by Untitled_No4 on 2010-04-25
No, you don't need to install the proprietary ATI drivers, in fact you shouldn't install them.
Adding the xorg repository (called xorg-edgers) installs the latest xorg server which the proprietary ATI drivers do not work with.

---

### Post by c00lwaterz on 2010-04-25
while in sudo apt-get upgrade

while installing i have to choose yes or no in configuring grub pc. what to choose?

You chose not to install GRUB to any devices.  If you continue, the boot  &#9474; 
 &#9474; loader may not be properly configured, and when your computer next        &#9474; 
 &#9474; starts up it will use whatever was previously in the boot sector.  If     &#9474; 
 &#9474; there is an earlier version of GRUB 2 in the boot sector, it may be       &#9474; 
 &#9474; unable to load modules or handle the current configuration file.          &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; If you are already running a different boot loader and want to carry on   &#9474; 
 &#9474; doing so, or if this is a special environment where you do not need a     &#9474; 
 &#9474; boot loader, then you should continue anyway.  Otherwise, you should      &#9474; 
 &#9474; install GRUB somewhere.                                                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Continue without installing GRUB?

---

### Post by Untitled_No4 on 2010-04-25
Continue without installing Grub, but don't reboot yet!
When upgrade has finished run
```
sudo update-grub
```
and post output.

---

### Post by c00lwaterz on 2010-04-25
> **Untitled_No4 said:**
> Continue without installing Grub, but don't reboot yet!
When upgrade has finished run
```
sudo update-grub
```
and post output.

```
toshiba@ubuntu:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.34-020634rc5-generic
Found initrd image: /boot/initrd.img-2.6.34-020634rc5-generic
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found Windows Recovery Environment (loader) on /dev/sda2
Found Windows Vista (loader) on /dev/sda4
done
toshiba@ubuntu:~$ 
```

after installing xorg edgers then I restart because it is require then the wifi is now fix. I try it and currently using wifi now

---

### Post by c00lwaterz on 2010-04-25
here is the latest update of my temp. still hot :(

also in addition when I shutdown it goes to ubuntu splash and it never stops in that screen (it keeps the dot moving and moving, it is like waiting for something) but not turning off. so I will press the power button to turn off

---

### Post by Untitled_No4 on 2010-04-26
> after installing xorg edgers then I restart because it is require then the wifi is now fix. I try it and currently using wifi now

Did you edit radeon-kms.conf file before reboot?

Can you please run ```
dmesg | grep drm
``` and post the output here?

---

### Post by c00lwaterz on 2010-04-26
> **Untitled_No4 said:**
> Did you edit radeon-kms.conf file before reboot?

Can you please run ```
dmesg | grep drm
``` and post the output here?

yes I edit and copy the code you give.

```

toshiba@ubuntu:~$ dmesg | grep drm
[    7.755985] [drm] Initialized drm 1.1.0 20060810
[    8.322829] [drm] radeon kernel modesetting enabled.
[    8.324687] [drm] initializing kernel modesetting (RV710 0x1002:0x9553).
[    8.325398] [drm] register mmio base: 0xFEBF0000
[    8.325400] [drm] register mmio size: 65536
[    8.325541] [drm] Clocks initialized !
[    8.325545] [drm] 6 Power State(s)
[    8.325547] [drm] State 0 Default (default)
[    8.325549] [drm] 	16 PCIE Lanes
[    8.325550] [drm] 	3 Clock Mode(s)
[    8.325552] [drm] 		0 engine/memory: 680000/800000
[    8.325554] [drm] 		1 engine/memory: 680000/800000
[    8.325556] [drm] 		2 engine/memory: 680000/800000
[    8.325558] [drm] State 1 Performance 
[    8.325560] [drm] 	16 PCIE Lanes
[    8.325561] [drm] 	3 Clock Mode(s)
[    8.325563] [drm] 		0 engine/memory: 220000/250000
[    8.325565] [drm] 		1 engine/memory: 300000/500000
[    8.325567] [drm] 		2 engine/memory: 680000/800000
[    8.325569] [drm] State 2 Battery 
[    8.325570] [drm] 	16 PCIE Lanes
[    8.325572] [drm] 	3 Clock Mode(s)
[    8.325574] [drm] 		0 engine/memory: 220000/250000
[    8.325576] [drm] 		1 engine/memory: 220000/250000
[    8.325578] [drm] 		2 engine/memory: 300000/250000
[    8.325580] [drm] State 3 Default 
[    8.325581] [drm] 	16 PCIE Lanes
[    8.325582] [drm] 	3 Clock Mode(s)
[    8.325584] [drm] 		0 engine/memory: 600000/800000
[    8.325586] [drm] 		1 engine/memory: 600000/800000
[    8.325588] [drm] 		2 engine/memory: 600000/800000
[    8.325590] [drm] State 4 Performance 
[    8.325592] [drm] 	16 PCIE Lanes
[    8.325593] [drm] 	3 Clock Mode(s)
[    8.325595] [drm] 		0 engine/memory: 300000/800000
[    8.325597] [drm] 		1 engine/memory: 680000/800000
[    8.325599] [drm] 		2 engine/memory: 680000/800000
[    8.325601] [drm] State 5 Battery 
[    8.325602] [drm] 	16 PCIE Lanes
[    8.325604] [drm] 	3 Clock Mode(s)
[    8.325606] [drm] 		0 engine/memory: 300000/400000
[    8.325608] [drm] 		1 engine/memory: 300000/400000
[    8.325610] [drm] 		2 engine/memory: 300000/400000
[    8.325618] [drm] radeon: dynamic power management enabled
[    8.325619] [drm] radeon: power management initialized
[    8.326282] [drm] Detected VRAM RAM=256M, BAR=256M
[    8.326286] [drm] RAM width 64bits DDR
[    8.326959] [drm] radeon: 256M of VRAM memory ready
[    8.326961] [drm] radeon: 512M of GTT memory ready.
[    8.327040] [drm] radeon: using MSI.
[    8.327076] [drm] radeon: irq initialized.
[    8.327079] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    8.327523] [drm] Loading RV710 Microcode
[    8.648045] [drm] ring test succeeded in 1 usecs
[    8.648220] [drm] radeon: ib pool ready.
[    8.648304] [drm] ib test succeeded in 0 usecs
[    8.648307] [drm] Enabling audio support
[    8.648333] [drm] Unknown TV standard; defaulting to NTSC
[    8.649542] [drm] Radeon Display Connectors
[    8.649544] [drm] Connector 0:
[    8.649546] [drm]   VGA
[    8.649548] [drm]   DDC: 0x7fa0 0x7fa0 0x7fa4 0x7fa4 0x7fa8 0x7fa8 0x7fac 0x7fac
[    8.649550] [drm]   Encoders:
[    8.649551] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    8.649553] [drm] Connector 1:
[    8.649555] [drm]   LVDS
[    8.649557] [drm]   DDC: 0x7f68 0x7f68 0x7f6c 0x7f6c 0x7f70 0x7f70 0x7f74 0x7f74
[    8.649559] [drm]   Encoders:
[    8.649560] [drm]     LCD1: INTERNAL_UNIPHY2
[    8.649562] [drm] Connector 2:
[    8.649563] [drm]   DisplayPort
[    8.649565] [drm]   HPD3
[    8.649567] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[    8.649568] [drm]   Encoders:
[    8.649570] [drm]     DFP1: INTERNAL_UNIPHY
[    8.649571] [drm] Connector 3:
[    8.649573] [drm]   HDMI-A
[    8.649574] [drm]   HPD2
[    8.649576] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    8.649578] [drm]   Encoders:
[    8.649579] [drm]     DFP2: INTERNAL_UNIPHY
[    8.802252] [drm] Requested: e: 22000 m: 25000 p: 16
[    8.802256] [drm] Setting: e: 22000 m: 25000 p: 16
[    8.908795] [drm] fb mappable at 0xD0141000
[    8.908798] [drm] vram apper at 0xD0000000
[    8.908800] [drm] size 4096000
[    8.908801] [drm] fb depth is 24
[    8.908803] [drm]    pitch is 5120
[    8.908913] fb0: radeondrmfb frame buffer device
[    8.908920] [drm] Initialized radeon 2.3.0 20080528 for 0000:08:00.0 on minor 0
[    9.615400] [drm] Requested: e: 68000 m: 80000 p: 16
[    9.615404] [drm] Setting: e: 68000 m: 80000 p: 16
[   10.212537] [drm] Requested: e: 22000 m: 25000 p: 16
[   10.212543] [drm] Setting: e: 22000 m: 25000 p: 16
[   41.524053] [drm] Requested: e: 68000 m: 80000 p: 16
[   41.524069] [drm] Setting: e: 68000 m: 80000 p: 16
[   41.524104] [drm] not in vbl for pm change 00020002 00000000 at entry
[   41.524524] [drm] not in vbl for pm change 00020002 00000000 at exit
[   44.824040] [drm] Requested: e: 22000 m: 25000 p: 16
[   44.824046] [drm] Setting: e: 22000 m: 25000 p: 16
[   44.829871] [drm] not in vbl for pm change 00020002 00000000 at entry
[   50.928041] [drm] Requested: e: 68000 m: 80000 p: 16
[   50.928056] [drm] Setting: e: 68000 m: 80000 p: 16
[   50.928093] [drm] not in vbl for pm change 00020002 00000000 at entry
[   50.928500] [drm] not in vbl for pm change 00020002 00000000 at exit
[   52.428535] [drm] Requested: e: 22000 m: 25000 p: 16
[   52.428541] [drm] Setting: e: 22000 m: 25000 p: 16
[   52.434533] [drm] not in vbl for pm change 00020002 00000000 at exit
[   58.932543] [drm] Requested: e: 68000 m: 80000 p: 16
[   58.932559] [drm] Setting: e: 68000 m: 80000 p: 16
[   58.932591] [drm] not in vbl for pm change 00020002 00000000 at entry
[   58.932997] [drm] not in vbl for pm change 00020002 00000000 at exit
[   60.432562] [drm] Requested: e: 22000 m: 25000 p: 16
[   60.432568] [drm] Setting: e: 22000 m: 25000 p: 16
[   60.438437] [drm] not in vbl for pm change 00020002 00000000 at entry
[   64.736530] [drm] Requested: e: 68000 m: 80000 p: 16
[   64.736534] [drm] Setting: e: 68000 m: 80000 p: 16
[   64.740783] [drm] not in vbl for pm change 00020002 00000000 at entry
[   67.340677] [drm] Requested: e: 22000 m: 25000 p: 16
[   67.340683] [drm] Setting: e: 22000 m: 25000 p: 16
[   67.342222] [drm] not in vbl for pm change 00020002 00000000 at entry
[   71.140051] [drm] Requested: e: 68000 m: 80000 p: 16
[   71.140057] [drm] Setting: e: 68000 m: 80000 p: 16
[   74.044042] [drm] Requested: e: 22000 m: 25000 p: 16
[   74.044048] [drm] Setting: e: 22000 m: 25000 p: 16
[   94.044537] [drm] Requested: e: 68000 m: 80000 p: 16
[   94.044552] [drm] Setting: e: 68000 m: 80000 p: 16
[   94.044592] [drm] not in vbl for pm change 00020002 00000000 at entry
[   94.045000] [drm] not in vbl for pm change 00020002 00000000 at exit
[   95.644042] [drm] Requested: e: 22000 m: 25000 p: 16
[   95.644048] [drm] Setting: e: 22000 m: 25000 p: 16
[   95.657758] [drm] not in vbl for pm change 00020002 00000000 at entry
[  102.656064] [drm] Requested: e: 68000 m: 80000 p: 16
[  102.656079] [drm] Setting: e: 68000 m: 80000 p: 16
[  102.656129] [drm] not in vbl for pm change 00010002 00000000 at entry
[  102.656561] [drm] not in vbl for pm change 00020002 00000000 at exit
[  104.756040] [drm] Requested: e: 22000 m: 25000 p: 16
[  104.756046] [drm] Setting: e: 22000 m: 25000 p: 16
[  104.762753] [drm] not in vbl for pm change 00010002 00000000 at entry
[  117.988047] [drm] Requested: e: 68000 m: 80000 p: 16
[  117.988062] [drm] Setting: e: 68000 m: 80000 p: 16
[  117.988095] [drm] not in vbl for pm change 00020002 00000000 at entry
[  117.988523] [drm] not in vbl for pm change 00020002 00000000 at exit
[  118.488043] [drm] Requested: e: 22000 m: 25000 p: 16
[  118.488049] [drm] Setting: e: 22000 m: 25000 p: 16
[  118.503598] [drm] not in vbl for pm change 00020002 00000000 at entry
[  126.304537] [drm] Requested: e: 68000 m: 80000 p: 16
[  126.304552] [drm] Setting: e: 68000 m: 80000 p: 16
[  126.304586] [drm] not in vbl for pm change 00020002 00000000 at entry
[  126.304994] [drm] not in vbl for pm change 00020002 00000000 at exit
[  131.604540] [drm] Requested: e: 22000 m: 25000 p: 16
[  131.604553] [drm] Setting: e: 22000 m: 25000 p: 16
[  131.604586] [drm] not in vbl for pm change 00020002 00000000 at entry
[  131.604997] [drm] not in vbl for pm change 00010002 00000000 at exit
[  144.904525] [drm] Requested: e: 68000 m: 80000 p: 16
[  144.904537] [drm] Setting: e: 68000 m: 80000 p: 16
[  144.904552] [drm] not in vbl for pm change 00020002 00000000 at entry
[  144.904957] [drm] not in vbl for pm change 00020002 00000000 at exit
[  148.004544] [drm] Requested: e: 22000 m: 25000 p: 16
[  148.004551] [drm] Setting: e: 22000 m: 25000 p: 16
[  148.019809] [drm] not in vbl for pm change 00020002 00000000 at entry
[  156.816051] [drm] Requested: e: 68000 m: 80000 p: 16
[  156.816073] [drm] Setting: e: 68000 m: 80000 p: 16
[  156.816106] [drm] not in vbl for pm change 00020002 00000000 at entry
[  156.816601] [drm] not in vbl for pm change 00020002 00000000 at exit
[  161.216549] [drm] Requested: e: 22000 m: 25000 p: 16
[  161.216556] [drm] Setting: e: 22000 m: 25000 p: 16
[  168.228536] [drm] Requested: e: 68000 m: 80000 p: 16
[  168.228552] [drm] Setting: e: 68000 m: 80000 p: 16
[  168.228590] [drm] not in vbl for pm change 00020002 00000000 at entry
[  168.228997] [drm] not in vbl for pm change 00020002 00000000 at exit
[  168.828436] [drm] Requested: e: 22000 m: 25000 p: 16
[  168.828441] [drm] Setting: e: 22000 m: 25000 p: 16
[  174.136543] [drm] Requested: e: 68000 m: 80000 p: 16
[  174.136559] [drm] Setting: e: 68000 m: 80000 p: 16
[  174.136587] [drm] not in vbl for pm change 00020002 00000000 at entry
[  174.136994] [drm] not in vbl for pm change 00020002 00000000 at exit
[  182.036542] [drm] Requested: e: 22000 m: 25000 p: 16
[  182.036555] [drm] Setting: e: 22000 m: 25000 p: 16
[  182.036995] [drm] not in vbl for pm change 00020002 00000000 at exit
[  183.236540] [drm] Requested: e: 68000 m: 80000 p: 16
[  183.236548] [drm] Setting: e: 68000 m: 80000 p: 16
[  183.237696] [drm] not in vbl for pm change 00020002 00000000 at entry
[  183.736539] [drm] Requested: e: 22000 m: 25000 p: 16
[  183.736546] [drm] Setting: e: 22000 m: 25000 p: 16
[  183.738214] [drm] not in vbl for pm change 00020002 00000000 at entry
[  186.336047] [drm] Requested: e: 68000 m: 80000 p: 16
[  186.336054] [drm] Setting: e: 68000 m: 80000 p: 16
[  186.340945] [drm] not in vbl for pm change 00020002 00000000 at entry
[  200.640073] [drm] Requested: e: 22000 m: 25000 p: 16
[  200.640086] [drm] Setting: e: 22000 m: 25000 p: 16
[  200.640124] [drm] not in vbl for pm change 00020002 00000000 at entry
[  200.640798] [drm] not in vbl for pm change 00020002 00000000 at exit
[  204.640073] [drm] Requested: e: 68000 m: 80000 p: 16
[  204.640079] [drm] Setting: e: 68000 m: 80000 p: 16
[  211.540540] [drm] Requested: e: 22000 m: 25000 p: 16
[  211.540554] [drm] Setting: e: 22000 m: 25000 p: 16
[  211.540592] [drm] not in vbl for pm change 00020002 00000000 at entry
[  211.541003] [drm] not in vbl for pm change 00020002 00000000 at exit
[  212.040546] [drm] Requested: e: 68000 m: 80000 p: 16
[  212.040553] [drm] Setting: e: 68000 m: 80000 p: 16
[  213.148058] [drm] Requested: e: 22000 m: 25000 p: 16
[  213.148064] [drm] Setting: e: 22000 m: 25000 p: 16
[  213.152384] [drm] not in vbl for pm change 00020002 00000000 at entry
[  213.552551] [drm] Requested: e: 68000 m: 80000 p: 16
[  213.552558] [drm] Setting: e: 68000 m: 80000 p: 16
[  213.552793] [drm] not in vbl for pm change 00020002 00000000 at entry
[  215.252077] [drm] Requested: e: 22000 m: 25000 p: 16
[  215.252084] [drm] Setting: e: 22000 m: 25000 p: 16
[  215.254582] [drm] not in vbl for pm change 00020002 00000000 at entry
[  217.752055] [drm] Requested: e: 68000 m: 80000 p: 16
[  217.752062] [drm] Setting: e: 68000 m: 80000 p: 16
[  217.757206] [drm] not in vbl for pm change 00020002 00000000 at entry
[  218.256044] [drm] Requested: e: 22000 m: 25000 p: 16
[  218.256050] [drm] Setting: e: 22000 m: 25000 p: 16
toshiba@ubuntu:~$
```

---

### Post by Untitled_No4 on 2010-04-26
The output you have pasted include the following:
> [    8.325618] [drm] radeon: dynamic power management enabled
[    8.325619] [drm] radeon: power management initialized

this means that the power management for your ATI card is working, but why is your temperature still high is beyond me. I don't know what else to suggest.

---

### Post by moviemaniac on 2010-04-26
//edit: fuggettaboutit

@Untitled_No4: His problem is that due to a BIOS bug the fans don't spin up when the temperature rises...

---

### Post by Untitled_No4 on 2010-04-26
Hopefully this will help although I definitely didn't need to do that and I went through the process several times.

---

### Post by moviemaniac on 2010-04-26
Oops, my bad - it really seems to be working as the dmesg output shows the different clock speeds being set. In my case on a machine where I used the exact same kernel from Ubuntu's ppa it only wanted to work after updating the initramfs (and also on my self-compiled kernel). However PM on my laptop with an old ATI card (r100, mobility 7500) completely fails - once it's enabled the machine freezes completely upon entering GDM...
Ah well, different problems and it's still under heavy development... ;)

---

### Post by c00lwaterz on 2010-04-26
any idea how can i solve my prob with temp? the temperature is high even I put 2 deskfans.

---

### Post by jetsam on 2010-04-26
Air condition the room, and use a steel box for a case.

---

### Post by moviemaniac on 2010-04-26
> **c00lwaterz said:**
> any idea how can i solve my prob with temp? the temperature is high even I put 2 deskfans.
No, there's no more we can do on this point. I'm very sorry but you'll have to wait what the Ubuntu kernel devs and / or the guys from the upstream kernel team come up with. You could also write to Toshiba, tell them about your issues and send them a link to the kernel bug report. Seems like you're stuck with Vista for now :(

---

### Post by c00lwaterz on 2010-04-26
moviemaniac,

in lucid 10.04 when the final release is available, do i need to fix again the wifi or they included it in already?

I also notice that in debian, pcbsd, and other distro same problem with my laptop.

---

### Post by moviemaniac on 2010-04-26
You do not need to update/reinstall when the final version is available. When you update your machine using the update manager you'll have the final version on your hard drive on the 29th. And no, since it's a dkms module, you shouldn't have to reinstall the wifi driver.

---

### Post by c00lwaterz on 2010-04-26
for example I downloaded the final release 10.04 on april 29, 2010. Then I make it fresh install again to check if the high temp is fixed. Do i need to reinstall the wifi? or they include it in the final release?

---

### Post by moviemaniac on 2010-04-26
There's no need to download and reinstall on the 29th! Your system will be the same as the one you download if you use the update manager regularly!
And, yes, if you still want to reinstall, you will have to also install the wireless driver again because we are way beyond feature freeze and it will certainly not be included/updated and neither will be a fix for your temperature problem.

On another note: Did you do a BIOS upgrade on your laptop as I instructed a few pages ago?

---

### Post by Untitled_No4 on 2010-04-26
moviemaniac, 
Since we (I?) got c00lwaterz to install a mainline kernel and xorg drivers, wouldn't it be better if he reinstalls Ubuntu just in case the devs do patch up the stock kernel and/or xorg?
Don't think it's very likely that they'll do, but if the complaints keep coming they just might...

---

### Post by c00lwaterz on 2010-04-26
alright, many thanks to you moviemaniac and Untitled_No4. I appreciate the help and understanding my side. I am really noob at this but I really like linux because of it's simplicity. I will keep watching on linux and get news if the high temp is fixed. for now, I will just wait =)

thanks thanks again =)

---

### Post by moviemaniac on 2010-04-26
You're welcome!

Just keep watching this thread and as soon as something'll come up, I'll post some new info. I really hope it works out for you. 
Of course, you could always just sell the Toshiba and pick up another brand of laptop - the vast majority of all devices work just fine but Toshibas always tend to make problems :( Or you could just hotwire the cpu fan to the battery with a potentiometer on the side of the notebook to manually control the fan. I know that's what I'd do but you have to know what you're doing (and, of course, you'll lose any warranty you might still have).

@Untitled_No4: I'd say leave it as it is right now. If something should come along (I keep a close watch on the changes-list every day) we can always advise him of what to do when the day comes.

---

### Post by chaosz911 on 2010-04-26
I had a similar problem with the laptop heating up and going in thermal shutdown with 10.04. The solution was fairly simple (after searching the web for a few days haha).
Detect the internal sensors, since it only recognized one!

```
$ sudo apt-get install cpufrequtils lm-sensors
$ sudo sensors-detect
```
(answer yes to all questions with sensors-detect, this will add the proper modules to /etc/modules)

```
$ sudo cpufreq-set -g ondemand
```
(This will lower your cpu speed if you do not use it and thus make things even more cool)

And to test if it all went well

```
$ cpufreq-info
$ sensors
```

Hope this helps, it did for me!

---

### Post by c00lwaterz on 2010-04-26
thanks to all.. Maybe I don't have luck this time. I will keep watching, maybe some fix will come along.

I have added you guys, I will message you if I have some question regarding temperature some other time.

For now, I will just use windows and if I get a new unit, I will check fisrt if it is compatible with linux. I can't sell this toshiba because it is heavy duty. I mean, the quality of material is good. Not easily broken example (key buttons and others). My cousin bought a Compaq (forgot the model) after a few months the tab key is remove from its place (easily broken).

If I have extra money I will buy netbook and I will install ubuntu linux on it.

---

### Post by c00lwaterz on 2010-04-26
> **chaosz911 said:**
> I had a similar problem with the laptop heating up and going in thermal shutdown with 10.04. The solution was fairly simple (after searching the web for a few days haha).
Detect the internal sensors, since it only recognized one!

```
$ sudo apt-get install cpufrequtils lm-sensors
$ sudo sensors-detect
```
(answer yes to all questions with sensors-detect, this will add the proper modules to /etc/modules)

```
$ sudo cpufreq-set -g ondemand
```
(This will lower your cpu speed if you do not use it and thus make things even more cool)

And to test if it all went well

```
$ cpufreq-info
$ sensors
```

Hope this helps, it did for me!


If I lower the speed of my cpu, can this help lower my temperature?

---

### Post by chaosz911 on 2010-04-27
> If I lower the speed of my cpu, can this help lower my temperature?

Well if you have the same problem as I did it, sensors-detect will fix the problem.
On my laptop Ubuntu only saw 'core temp' instead of coretemp, cpu0 and cpu1. It just didn't see the cpu sensors! Which obviously caused the thermal shutdown. Lowering the cpu is just a workaround, it's not a fix, but yes it will lower the temperature.

---

### Post by c00lwaterz on 2010-04-27
do developers know about this issue? will they give solution? I think most new laptops have problem than the old unit. old unit is more supported in linux?

---

### Post by c00lwaterz on 2010-04-28
moviemaniac,

I have new idea but I don't know if this will help.

If I will use light weight linux? can this fix my overheat prob in linux?

thanks

---

### Post by moviemaniac on 2010-04-28
Sorry, but that won't hilp. "Light weight" refers mostly to memory usage (both RAM and hard drive), the kernel and the underlying problem of the fans not being accessed will stay the same - unfortunately.

---

### Post by c00lwaterz on 2010-04-28
okay, is there a way some other time to fix this issue? I mean, do developers will work on this prob to make fixes for future version of linux system with laptop overheat? I also notice that the temperature using windows is hot also but in linux, it is really hot hot. In windows my max temp I get is 67 deg celcius then it will blow a hot air out then going down to 60 then 57 then 55 deg celcius.


btw, I appreciate so much your effort and help. I also appreciate you reply with my thread. I am happy that someone is giving time to talk to me(response). :)

If this thread is inactive, can i private message you if I need help or if I have question?

I know that some people will be annoyed when I asked directly in private message. So I ask permission, if I could and I know you are considerate. I know you understand a person same as me (noob).

Thanks for the effort and time :)

---

### Post by moviemaniac on 2010-04-28
Nope, there's no other way (other than hotwiring the fan to the battery ;) ) right now. However, as I said, I'll keep watching this upstream and see to it it doesn't get forgotten. I cannot, however, promise anything, as this bug is mainly Toshibas fault - the kernel developers could find a workaround but you never now what's possible and what's not.

And yes, you can of course pm me with further questions, no problem at all.

---

### Post by BrokeMahPC on 2010-04-28
Urgent please help. I am stuck in the middle of a apt-get upgrade!

After adding the xorg.edgers.ppa I got this while upgrading - it relates to the
/etc/modprobe.d/radeon-kms.conf
which I manually edited as in some previous instructions.

Whilst upgrading the terminal gave me an option:.
1 install new config
2 keep existing config
I selected option "D" to display the differences between the two. I am  now stuck in that option and it has (END) before the cursor.

How do I return to and complete the original upgrade process? I would say it's best not to edit the radeon-kms.conf before you update and upgrate from xorg.edgers - their ppa wants to install this file with the modeset=1 option - let it. If you need to add dynpm=1, add it after.

---

### Post by moviemaniac on 2010-04-28
press "q" on your keyboard to get out of the screen and select to install the new file.

---

### Post by BrokeMahPC on 2010-04-28
Thanks - Q did it.

---

### Post by BrokeMahPC on 2010-04-28
started new thread about this.

---

### Post by c00lwaterz on 2010-04-28
> **moviemaniac said:**
> Nope, there's no other way (other than hotwiring the fan to the battery ;) ) right now. However, as I said, I'll keep watching this upstream and see to it it doesn't get forgotten. I cannot, however, promise anything, as this bug is mainly Toshibas fault - the kernel developers could find a workaround but you never now what's possible and what's not.

And yes, you can of course pm me with further questions, no problem at all.

i have join the toshiba forum and post my problem. I don't know if there forum is good as linux. I am confuse with the layout of their forum. I also try to email their support but I couldn't find. I just saw I need to put my number but it might cost me.

So I just join their forum and post my problem. I don't know if they will respond to my post. Is there a laptop that is heavy duty as toshiba? I mean the materials not easily broken. example is the keypad/keyboard in laptop it is good quality and not easily broken. Also hinges, is good and not easily broken. and last is the style/design of it.

Some laptops are easy to be broken such as in keyboard and hinges.

If time comes, If I will buy new one, I have new options. My previous options with laptop quality is dell, asus, and toshiba.

I heard so many times people saying toshiba is of good quality.

I don't know other laptops.

---

### Post by c00lwaterz on 2010-04-28
here is the link to my post in toshiba forum:
[http://laptopforums.toshiba.com/t5/General-Technology/Toshiba-m900-overheat-in-linux/m-p/102692]("http://laptopforums.toshiba.com/t5/General-Technology/Toshiba-m900-overheat-in-linux/m-p/102692")

I don't know if there is someone to respond to my thread.

---

### Post by moviemaniac on 2010-04-28
> **c00lwaterz said:**
> Is there a laptop that is heavy duty as toshiba? I mean the materials not easily broken. example is the keypad/keyboard in laptop it is good quality and not easily broken. Also hinges, is good and not easily broken. and last is the style/design of it.

Lenovo Thinkpad (especially the T-series). These machines are the old IBM Thinkpads, and these machines are built to last. My old T20 was over 8 years old when I gave it up, my current T40 is now over 4 years old and it's still going strong. No broken bits, very little signs of wear (modern glossy laptops look worse after a few months...). AND Lenovo offers a repair manual for every model with detailed explanation on how to fix/replace anything at home.
If (build)quality and Linux compatibility are a main concern I'd always recommend Lenovo Thinkpads.
Of course there are always the Dell notebooks. They're somewhere in the middle as far as build quality is concerned, but they're cheaper than the Lenovos (which are amongst the priciest) BUT you can get quite a few DELL laptops with Ubuntu preinstalled! See [http://www.ubuntu.com/dell](http://www.ubuntu.com/dell)

---

### Post by c00lwaterz on 2010-04-28
> **moviemaniac said:**
> Lenovo Thinkpad (especially the T-series). These machines are the old IBM Thinkpads, and these machines are built to last. My old T20 was over 8 years old when I gave it up, my current T40 is now over 4 years old and it's still going strong. No broken bits, very little signs of wear (modern glossy laptops look worse after a few months...). AND Lenovo offers a repair manual for every model with detailed explanation on how to fix/replace anything at home.
If (build)quality and Linux compatibility are a main concern I'd always recommend Lenovo Thinkpads.
Of course there are always the Dell notebooks. They're somewhere in the middle as far as build quality is concerned, but they're cheaper than the Lenovos (which are amongst the priciest) BUT you can get quite a few DELL laptops with Ubuntu preinstalled! See [http://www.ubuntu.com/dell](http://www.ubuntu.com/dell)

so dell and lenovo is more preferred for linux compatibility?
I wish I bought dell haha. Because dell and toshiba is the 2 brands I have been choosing last year before I came up with decision. before I came up with toshiba, I had this research about dell m1330 but when I check the store here, it was not available in our country. They say it is expensive so they don't have. They will only allow made-to-order for dell m1330. so I search again HP, sony and toshiba. then I came up with toshiba.

so now I know that dell and lenovo is more compatible with linux. If I need to buy laptop then I will choose dell and lenovo as option before I research and choose. 

thanks for the info

---

### Post by moviemaniac on 2010-04-28
> **c00lwaterz said:**
> so now I know that dell and lenovo is more compatible with linux. If I need to buy laptop then I will choose dell and lenovo as option before I research and choose. 

Well, usually most devices "just work" with linux so you are really unlucky to have bought one which has problems. I have run Linux on laptops from most vendors and have never before run into problems I couldn't fix.
That said, before buying your next laptop, just ask here in the ubuntuforums (or me via pm) about the model you intend to buy and whether someone has experiences with this or similar models.

---

### Post by c00lwaterz on 2010-04-28
what is the difference between idea pad and think pad. for me ideapad has more aesthetics in design but other than what is the difference?

thanks

---

### Post by jetsam on 2010-04-28
> **c00lwaterz said:**
> what is the difference between idea pad and think pad. for me ideapad has more aesthetics in design but other than what is the difference?

thanks

I'm pretty sure at the center of that tootsie pop lies the head of the marketing department, but it's opaque to me, too.  Maybe somebody better informed could enlighten the issue.

---

### Post by Untitled_No4 on 2010-04-28
I have had several ThinkPads laptop over the years and I don't think I'll ever buy any other laptop, they're just that good.
ThinkPads are known for their Linux compatibility since it's something that Lenovo inherited from IBM who are still big supported of Linux. 

The biggest advantage of ThinkPads for Linux users are the community resources available to them:
1. Thinkwiki.org - A site dedicated to Linux on ThinkPads. It's like the bible of Linux users on ThinkPads.
2. Thinkpads.com. The forum has a useful section for Linux users. They also have discount coupons for Americans, so it's worth checking them out before you buy.
3. forums.lenovo.com which are the official forums for Lenovo and where you can find official free support.

I also like to imagine that it helps that Red Hat devs use ThinkPads (as far as I was told by an RH employee).

---

### Post by Untitled_No4 on 2010-04-28
> **c00lwaterz said:**
> what is the difference between idea pad and think pad. for me ideapad has more aesthetics in design but other than what is the difference?

thanks

ThinkPads are the "professional" laptops while IdeaPads are targeted for home users.
In general a ThinkPad is more likely to have a good Linux support than an IdeaPad. It doesn't mean you have to avoid them, just that you need to research more. Thinkwiki and forums are your source of knowledge. 

I forgot to mention in my last post that the Cafe forum here has a thread about ThinkPad owners. It's a great place to get information about compatibility.

---

### Post by moviemaniac on 2010-04-28
Untitled_No4 beat me to it :D

The reason why Thinkpads are very good at supporting Linux is mainly because they closely follow Intel's specifications/design and use intel hardware as much as possible. Since Intel contributes a great deal to the kernel Intel hardware is always a safe bet. Note: With Intel hardware I do not only mean the CPU but also things like chipsets, wlan cards and stuff like that.

---

### Post by Untitled_No4 on 2010-04-28
Just one more thing about Dell...
Dell sell laptops preloaded with Ubuntu and they have a very good hardware support as well. My boyfriend has a Dell and has no issues, although I still do prefer my ThinkPad to his Inspiron.

---

### Post by c00lwaterz on 2010-04-28
How about price and specificiation of ideapad and thinkpad?

I also wonder why most desktop is more compatible than laptop when using linux? for issues they have less problem than laptops. I have installed it on my desktop and has no problem but I gave it to me brother for him to use it in his home work and study.

---

### Post by moviemaniac on 2010-04-28
Well, the ideapads are cheaper than the thinkpads.

I don't know, are desktops really more compatible than laptops? I'm not really sure about that. Sure, power management is sometimes a bit more problematic with notebooks but that's about the only difference.

//edit: I requested this trhead to be moved to the main support forums so it doesn't get locked along with the whole subforum.

---

### Post by c00lwaterz on 2010-04-28
hi moviemaniac, 

i saw this site Toshiba Linux Utilities [http://www.buzzard.me.uk/toshiba/index.html]("http://www.buzzard.me.uk/toshiba/index.html") I don't know if it can help.

Any idea?

Thanks

---

### Post by moviemaniac on 2010-04-28
I came across this page too. However since the page seems to have been updated last in 2003 I guess this wouldn't work anyway - nearly everything in the kernel has changed since then...

---

### Post by c00lwaterz on 2010-04-28
In my reading on that website, it says:

The internal fan on Toshiba laptops is designed to cool the machine down when it gets hot. The fan is linked to a thermocouple and will automatically turn on to prevent the laptop over heating.

However on older laptops this is overseen by the BIOS and does not work under a 32bit operating system such as Linux. While it does work on recent laptops what might be fine for the laptop is often too hot for the user. The ability to turn the fan on and keep the laptop that little bit cooler is a relief for many a user.

I have added a number of new options to the fan program. These are a toggle mode that will turn it on if it is off and vice versa, and automatic mode that will turn the fan on if the laptop is currently being powered by the mains.

The current version of the fan program will work on all Toshiba Pentium(tm) laptops that have a cooling fan. If you have previously used a version of the fan program that did not work on your laptop, please get the update to the latest version.
Source: [http://www.buzzard.me.uk/toshiba/fan.html]("http://www.buzzard.me.uk/toshiba/fan.html")

---

### Post by cariboo on 2010-04-28
Move to General Help before the Lucid sub-forum is closed.

---

### Post by moviemaniac on 2010-04-28
> **cariboo907 said:**
> Move to General Help before the Lucid sub-forum is closed.
Thanks, mate!

@c00lwaterz: Yes, I read that too, however the program was designed to run on very, very old Toshiba laptops with Pentium I processors and on Kernels 2.2.x or 2.4.x The code will NOT run under current 2.6.x kernels nor will it support your laptop model as that one is 5+ years into the "future" from the last update of the program ;)

---

### Post by c00lwaterz on 2010-04-28
thanks moviemaniac,

How we move this thread? I don't know how. or do we need to open new thread?

---

### Post by moviemaniac on 2010-04-28
The thread has already been moved ;)

---

### Post by c00lwaterz on 2010-04-28
oh cool haha

sorry for being know-nothing haha.

I saw this website [http://www.lesswatts.org/]("http://www.lesswatts.org/")

they have about acpi power management and cpu power management.

I don't know also if it can help

---

### Post by moviemaniac on 2010-04-28
It's just a hunch, but could you try this:

sudo apt-get install acpitool

when it is installed, run this:

acpitool -F x=1
(you may need to run it with sudo on front, but try it first without)

---

### Post by c00lwaterz on 2010-04-28
ok i will try now. I will go to ubuntu.

i saw this site also about linux and toshiba [http://linux.toshiba-dme.co.jp/linux/index.htm]("http://linux.toshiba-dme.co.jp/linux/index.htm")

---

### Post by c00lwaterz on 2010-04-28
the install was successful but when I run it


it says:

```
toshiba@ubuntu:~$ acpitool -F x=1
Forcing the fan of/off is only supported on Toshiba laptops. 
No Toshiba ACPI extensions were found. 
```


Here is the install process

```
toshiba@ubuntu:~$ sudo apt-get install acpitool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  acpitool
0 upgraded, 1 newly installed, 0 to remove and 17 not upgraded.
Need to get 47.3kB of archives.
After this operation, 168kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe acpitool 0.5-7 [47.3kB]
Fetched 47.3kB in 2s (16.8kB/s)   
Selecting previously deselected package acpitool.
(Reading database ... 146493 files and directories currently installed.)
Unpacking acpitool (from .../acpitool_0.5-7_i386.deb) ...
Processing triggers for man-db ...
Setting up acpitool (0.5-7) ...
toshiba@ubuntu:~$ acpitool -F x=1
Forcing the fan of/off is only supported on Toshiba laptops. 
No Toshiba ACPI extensions were found. 
```

---

### Post by moviemaniac on 2010-04-28
bugger, that's what I feared. Another program made mostly for older hardware...

could you post the output of these commands: 
acpitool -e
acpitool -t
acpitool -T
acpitool -f

---

### Post by moviemaniac on 2010-04-28
Oh, and can you please try what this command gives you?

sudo modprobe toshiba_acpi

---

### Post by c00lwaterz on 2010-04-28
> **moviemaniac said:**
> bugger, that's what I feared. Another program made mostly for older hardware...

could you post the output of these commands: 
acpitool -e
acpitool -t
acpitool -T
acpitool -f

This

```
toshiba@ubuntu:~$ acpitool -e
  Kernel version : 2.6.34-020634rc20100121   -    ACPI version : 20100121
  -----------------------------------------------------------
  Battery #1     : present
    Remaining capacity : 37610 mWh, 90.00%, 00:39:19
    Design capacity    : 41070 mWh
    Last full capacity : 41790 mWh
    Present rate       : 6377 mW
    Charging state     : charging
    Battery type       : rechargeable, 
    Model number       : 10 mWh
    Serial number      : LIP909

  AC adapter     : on-line 
Segmentation fault
toshiba@ubuntu:~$ acpitool -t
  Thermal zone 1 : ok, 64 C
  Trip points : 
  ------------- 
  critical (S5):           108 C
  passive:                 101 C: tc1=30 tc2=30 tsp=50 devices=CPU0 CPU1 
  active[0]:               98 C: devices=FAN0 
  active[1]:               90 C: devices=FAN1 
  active[2]:               80 C: devices=FAN2 
  active[3]:               70 C: devices=FAN3 
  active[4]:               60 C: devices=FAN4 
  active[5]:               50 C: devices=FAN5 

toshiba@ubuntu:~$ acpitool -T
Sorry, but no Toshiba ACPI extensions were found on this system. 
toshiba@ubuntu:~$ acpitool -f
Segmentation fault
toshiba@ubuntu:~$ 
```

---

### Post by c00lwaterz on 2010-04-28
This sort of funny haha. when I am trying to test something for ubuntu and toshiba about high temp I go back windows reading the ubuntuforum then go back ubuntu to test hehe. the heat is fast from 55 deg celcius, it goes up fast

---

### Post by moviemaniac on 2010-04-28
Did you try this?

sudo modprobe toshiba_acpi

If that doesn#t give you an error, try this again afterwards:

acpitool -F x=1

---

### Post by c00lwaterz on 2010-04-28
ok i will try. going to ubuntu again hehe. it is like table tennis (pingpong) haha

---

### Post by c00lwaterz on 2010-04-28
> **moviemaniac said:**
> Did you try this?

sudo modprobe toshiba_acpi

If that doesn#t give you an error, try this again afterwards:

acpitool -F x=1

This
```

toshiba@ubuntu:~$ sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.34-020634rc5-generic/kernel/drivers/platform/x86/toshiba_acpi.ko): No such device
toshiba@ubuntu:~$ 
```

---

### Post by moviemaniac on 2010-04-28
Oh, I forgot: You're gonna have to boot into the 2.6.32-21 kernel to do that, it seems like the -34 kernel doesn't ship the necessary module...

---

### Post by c00lwaterz on 2010-04-28
ok i will try again hehe

---

### Post by c00lwaterz on 2010-04-28
> **moviemaniac said:**
> Oh, I forgot: You're gonna have to boot into the 2.6.32-21 kernel to do that, it seems like the -34 kernel doesn't ship the necessary module...

```
toshiba@ubuntu:~$ sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.32-19-generic/kernel/drivers/platform/x86/toshiba_acpi.ko): No such device
toshiba@ubuntu:~$ 
```

same error

---

### Post by moviemaniac on 2010-04-28
what does "locate toshiba_acpi.ko" give you?

---

### Post by c00lwaterz on 2010-04-28
> **moviemaniac said:**
> what does "locate toshiba_acpi.ko" give you?

this:

```
toshiba@ubuntu:~$ locate toshiba_acpi.ko
/lib/modules/2.6.32-19-generic/kernel/drivers/platform/x86/toshiba_acpi.ko
toshiba@ubuntu:~$ 
```

---

### Post by moviemaniac on 2010-04-28
Another dead end, the toshiba_acpi module doesn't work with your laptop either - the module is meant for older hardware as well :(

Off to bed now, it's way past midnight over here and I have an early start tomorrow... err... today :D

---

### Post by c00lwaterz on 2010-04-28
> **moviemaniac said:**
> Another dead end, the toshiba_acpi module doesn't work with your laptop either - the module is meant for older hardware as well :(

Off to bed now, it's way past midnight over here and I have an early start tomorrow... err... today :D

haha to be continued. hehe ok I will wait for reply :popcorn:

---

### Post by c00lwaterz on 2010-04-29
hi moviemaniac,

can you please check this out.

[http://ubuntuforums.org/showthread.php?t=1420247]("http://ubuntuforums.org/showthread.php?t=1420247")

this is about toshiba fan and the same issue. The fan work on them after some testing? I don't know how. I know you are better to understand this. Im not familiar with other distro, i have tried before but same problem. All linux that I have tried is installed inside windows. I don't know if that is the problem?

thanks

---

### Post by moviemaniac on 2010-05-02
We already tried this one before but in this case it's written a little differently:

try this first:
[http://ubuntuforums.org/showpost.php?p=8912862&postcount=7](http://ubuntuforums.org/showpost.php?p=8912862&postcount=7)

and then this

[http://ubuntuforums.org/showpost.php?p=9197545&postcount=24](http://ubuntuforums.org/showpost.php?p=9197545&postcount=24)

reboot afterwards

---

### Post by c00lwaterz on 2010-05-02
> **moviemaniac said:**
> We already tried this one before but in this case it's written a little differently:

try this first:
[http://ubuntuforums.org/showpost.php?p=8912862&postcount=7](http://ubuntuforums.org/showpost.php?p=8912862&postcount=7)

and then this

[http://ubuntuforums.org/showpost.php?p=9197545&postcount=24](http://ubuntuforums.org/showpost.php?p=9197545&postcount=24)

reboot afterwards

I saw that post. The first link is not solve. I have already ask the one that post if he had successful. He told me that he use vista because all of distro is same problem. The 2nd link I saw also but not yet tried. I will try if it will work then i am happy :lolflag:

---

### Post by c00lwaterz on 2010-05-02
> **moviemaniac said:**
> We already tried this one before but in this case it's written a little differently:

try this first:
[http://ubuntuforums.org/showpost.php?p=8912862&postcount=7](http://ubuntuforums.org/showpost.php?p=8912862&postcount=7)

and then this

[http://ubuntuforums.org/showpost.php?p=9197545&postcount=24](http://ubuntuforums.org/showpost.php?p=9197545&postcount=24)

reboot afterwards

I just finished the 2nd link. But it didn't work for me.
I think toshiba satellite is more compatible with linux than portege. I saw some people using toshiba portege still have this problem. Ashima is satellite and most satellite user can fix the problem than portege user. :confused:

---

### Post by moviemaniac on 2010-05-02
I wouldn't say the sattelite were more compatible - there's a list of Toshiba laptops certified by Ubuntu: [http://webapps.ubuntu.com/certification/list/?search=toshiba](http://webapps.ubuntu.com/certification/list/?search=toshiba)

---

### Post by c00lwaterz on 2010-05-02
> **moviemaniac said:**
> I wouldn't say the sattelite were more compatible - there's a list of Toshiba laptops certified by Ubuntu: [http://webapps.ubuntu.com/certification/list/?search=toshiba](http://webapps.ubuntu.com/certification/list/?search=toshiba)

yes i know but most of them have solution than portege. I saw some satellite users have problem and they got solution work for them.
I also notice that more satellite user than portege here.

---

### Post by kruntz on 2010-05-04
> **moviemaniac said:**
> I'll keep watching this upstream and see to it it doesn't get forgotten.

Would you mind posting the URLs of the resource you are monitoring?
I'd like to keep an (automatic) eye on them myself...

Thanks in advance
Carlo.

---

### Post by moviemaniac on 2010-05-04
There you go, Carlos: 

[https://bugzilla.kernel.org/show_bug.cgi?id=14529](https://bugzilla.kernel.org/show_bug.cgi?id=14529)

---

### Post by kruntz on 2010-05-04
> **moviemaniac said:**
> There you go, Carlos: 
[https://bugzilla.kernel.org/show_bug.cgi?id=14529](https://bugzilla.kernel.org/show_bug.cgi?id=14529)

Oh, sorry, I wasn't clear on my request...
I'd need  to know when ATI drivers with drm support will be in the official repository...

Btw, I tried (without success) to find the correct parameter for /etc/modprobe.d/radeon-kms.conf to force the GPU in low power mode.
Is there a list of the allowed parameters?

--
Carlo.

---

### Post by Untitled_No4 on 2010-05-04
Carlo, the drm kernel is already in the official repository: [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/)

Read this post, especially the section under Ubuntu Stuff for instructions of how to set PM in Ubuntu: [http://ubuntuforums.org/showpost.php?p=7773102&postcount=1](http://ubuntuforums.org/showpost.php?p=7773102&postcount=1)

---

### Post by kruntz on 2010-05-04
> **Untitled_No4 said:**
> Carlo, the drm kernel is already in the official repository: [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/drm-next/")

Oh, yes, this is the one I'm using now:
Linux kruntz-nb 2.6.34-020634rc6-generic #020634rc6 SMP Fri Apr 30 09:08:46 UTC 2010 x86_64 GNU/Linux
Obviously, I meant available without adding additional sources...

> **Untitled_No4 said:**
> Read this post, especially the section under Ubuntu Stuff for  instructions of how to set PM in Ubuntu: [http://ubuntuforums.org/showpost.php?p=7773102&postcount=1](http://ubuntuforums.org/showpost.php?p=7773102&postcount=1)

This is exactly what I did.
I'm now trying to find a parameter (like dynpm=1) to put my ATI Mobility Radeon HD 3670 in "*ForceLowPowerMode*", since dynpm leave my GPU at 71° C idle.

Many thanks for your prompt answers.
--
Carlo

---

### Post by moviemaniac on 2010-05-04
First things first: Yes, this is possible!

But you will have to compile your own kernel from the drm-radeon-testing tree [http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing](http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing)
You'll also need updated firmware: [http://git.kernel.org/?p=linux/kernel/git/airlied/linux-firmware.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/airlied/linux-firmware.git;a=summary)
See also: [http://www.x.org/wiki/radeonBuildHowTo#TroubleshootingExtraFirmwareforR600.2BAC8-R700.2BAC8-Evergreen](http://www.x.org/wiki/radeonBuildHowTo#TroubleshootingExtraFirmwareforR600.2BAC8-R700.2BAC8-Evergreen)

After that's done you can set the requested power mode using sysfs:
sudo bash -c "echo 1.0 > /sys/class/drm/card0/device/power_state"

However be sure to read this thread here first on how to use sysfs:
[http://www.phoronix.com/forums/showthread.php?t=23447](http://www.phoronix.com/forums/showthread.php?t=23447)
[http://www.phoronix.com/forums/showpost.php?p=125208&postcount=41](http://www.phoronix.com/forums/showpost.php?p=125208&postcount=41)

oh, and remember: This code is HIGHLY experimental and is only expected to land in the mainline 2.6.35 series.

If you should have no idea what I'm talking about and/or aren't comfortable compiling your own kernel, applying patches and changing firmware files the I would suggest you to use the fglrx driver for now.

---

### Post by kruntz on 2010-05-04
> **moviemaniac said:**
> If you should have no idea what I'm talking about and/or aren't comfortable compiling your own kernel

Fortunately, I've zero problem with compiling my own kernel. :-)
Unfortunately, this is for three collegues of mine that own a Dell Studio XPS 1640, and I'd prefer not to install a home-brew and not updatable kernel on their (roaming) machines...

> **moviemaniac said:**
> I would suggest you to use the  fglrx driver for now.

This whole mess started when I had to uninstall fglrx due to this bug:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988)
and the lack of a backfill patch for the xorg-server in Lucid:
[https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill]("https://launchpad.net/%7Eubuntu-x-swat/+archive/xserver-no-backfill")

[Edit]
Just found this:
[https://launchpad.net/~info-g-com/+archive/xserver-xorg-1.7.6-gc](https://launchpad.net/~info-g-com/+archive/xserver-xorg-1.7.6-gc)
Trying now...

--
Carlo

---

### Post by c00lwaterz on 2010-05-04
In the kernel Bug tracker i saw Assigned to zhang rui. is that the developer? or contributor? I don't know about the kernel bug tracker. I saw a lot name zhang rui in that website. Is he the team lead programmer?

Thanks

---

### Post by moviemaniac on 2010-05-05
> **c00lwaterz said:**
> In the kernel Bug tracker i saw Assigned to zhang rui. is that the developer? or contributor? I don't know about the kernel bug tracker. I saw a lot name zhang rui in that website. Is he the team lead programmer?

Thanks
If the bug is assigned to him the he is responsible for the subsystem as a developer, yes :)

@kruntz: Hoping the updated xserver fixes your issues :)

---

### Post by kruntz on 2010-05-05
> **moviemaniac said:**
> @kruntz: Hoping the updated xserver fixes your issues :)

Yes, GPU is back to 53° C when idle. Fan is quiet.
I'd really like not to resort on closed source software, though...

Cheers
--
Carlo.

---

### Post by moviemaniac on 2010-05-05
I feel your pain - I am SO glad I could finally move to the radeon driver with 10.04.

---

### Post by c00lwaterz on 2010-05-05
> **moviemaniac said:**
> I feel your pain - I am SO glad I could finally move to the radeon driver with 10.04.

Will the dev still provide solution or work around for the toshiba m900? i saw the link in kernel bug tracker. The user with problem has solve it with "acpi.power_nocheck". If we have the same model of laptop, then it should work with me or it is different case?

---

### Post by dino99 on 2010-05-06
look at synaptic and search "tosh": install toshutils, toshset and fnfxd

---

### Post by c00lwaterz on 2010-05-06
> **dino99 said:**
> look at synaptic and search "tosh": install toshutils, toshset and fnfxd

did not work for me. I tried last night

---

### Post by daliusd on 2010-05-09
In previous Ubuntu versions I was using radeonhd drivers (in this version I have not succeeded to make it work - I will try it again later).

I have read almost all discussion but nothing really helps me. I have tried upgrading kernel to drm one, and building radeon drivers from source. dynpm=1 based on logs seems to be working but that does not help to lower temperature less than to 70 degrees. Situation is pretty bad because after 2 hours computers reaches critical temperature (105 degrees) and I can't work anymore.

I'm developer myself so I can spend some time on this problem but I need help.

---

### Post by moviemaniac on 2010-05-09
@daliusd: Since you're a developer I'd suggest building the drm-radeon-testing three with these patches on top: [http://people.freedesktop.org/~agd5f/pm-drt/](http://people.freedesktop.org/~agd5f/pm-drt/)
also read the information in 0008-drm-radeon-kms-pm-rework-power-management.patch on how to use it since dynpm=1 has been deprecated in favour of setting it via sysfs. The newer code in d-r-t makes a huge difference vs. the old one in linux' 2.6.34-tree or the one in drm-testing.

---

### Post by daliusd on 2010-05-10
> **moviemaniac said:**
> @daliusd: Since you're a developer I'd suggest building the drm-radeon-testing three with these patches on top: [http://people.freedesktop.org/~agd5f/pm-drt/](http://people.freedesktop.org/~agd5f/pm-drt/)
also read the information in 0008-drm-radeon-kms-pm-rework-power-management.patch on how to use it since dynpm=1 has been deprecated in favour of setting it via sysfs. The newer code in d-r-t makes a huge difference vs. the old one in linux' 2.6.34-tree or the one in drm-testing.

OK. I will try to do that. That will take some time because I have not build linux kernel before and I spent only hour or two on this PC.

---

### Post by daliusd on 2010-05-11
> **moviemaniac said:**
> @daliusd: Since you're a developer I'd suggest building the drm-radeon-testing three with these patches on top: [http://people.freedesktop.org/~agd5f/pm-drt/](http://people.freedesktop.org/~agd5f/pm-drt/)
also read the information in 0008-drm-radeon-kms-pm-rework-power-management.patch on how to use it since dynpm=1 has been deprecated in favour of setting it via sysfs. The newer code in d-r-t makes a huge difference vs. the old one in linux' 2.6.34-tree or the one in drm-testing.

It looks like that patches you have suggested to use are already in drm-radeon-testing repository. Currently I'm building kernel (how much time it takes?). Later I will report my results.

---

### Post by daliusd on 2010-05-15
> **daliusd said:**
> It looks like that patches you have suggested to use are already in drm-radeon-testing repository. Currently I'm building kernel (how much time it takes?). Later I will report my results.

I have succeeded in using new kernel but that's not helping me. My PC is still hot (sensors show 90 degrees). As well I see following error multiple times:

[ 1975.846892] radeon 0000:01:05.0: efd38000 reserve failed for wait
[ 2022.020323] radeon 0000:01:05.0: efd38000 reserve failed for wait

---

### Post by moviemaniac on 2010-05-15
what happens if you execute these 2 commands?

sudo bash -c "echo profile > /sys/class/drm/card0/device/power_method"
sudo bash -c "echo low > /sys/class/drm/card0/device/power_profile"

---

### Post by daliusd on 2010-05-15
> **moviemaniac said:**
> what happens if you execute these 2 commands?

sudo bash -c "echo profile > /sys/class/drm/card0/device/power_method"
sudo bash -c "echo low > /sys/class/drm/card0/device/power_profile"

----------------------------------------------
dalius@dalius-laptop:~$ cat  /sys/class/drm/card0/device/power_method
profile
dalius@dalius-laptop:~$ sudo bash -c "echo profile > /sys/class/drm/card0/device/power_method"
[sudo] password for dalius: 
dalius@dalius-laptop:~$ sudo bash -c "echo low > /sys/class/drm/card0/device/power_profile"
dalius@dalius-laptop:~$ cat  /sys/class/drm/card0/device/power_methodprofile
dalius@dalius-laptop:~$ cat  /sys/class/drm/card0/device/power_profile 
low
----------------------------------------------

Temperature is about 78 degrees after I have stopped compilation. During compiliation it was between 90 and 100.

In general it is a little bit better.

---

### Post by moviemaniac on 2010-05-15
Okay, maybe this works a little better, this method is more aggressive:

sudo bash -c "echo dynpm > /sys/class/drm/card0/device/power_method"

if that works better you can enable it by default on boot by entering this line into your /etc/rc.local:

echo dynpm > /sys/class/drm/card0/device/power_method

---

### Post by daliusd on 2010-05-15
> **moviemaniac said:**
> Okay, maybe this works a little better, this method is more aggressive:

sudo bash -c "echo dynpm > /sys/class/drm/card0/device/power_method"

if that works better you can enable it by default on boot by entering this line into your /etc/rc.local:

echo dynpm > /sys/class/drm/card0/device/power_method

After 5 seconds: screen blinks like resolution is changed and computer freezes. That's too aggressive for me ;-)

Yet another question: radeonhd driver was working just perfect in previous version - it is not working now for me. Any ideas why?

---

### Post by moviemaniac on 2010-05-15
Yeah, I know - id doesn't freeze for me with dynpm but the mouse gets laggy... it's all WIP so this might change soon.

However you could revert to UMS by setting modeset=0 in /etc/modprobe.d/radeon-kms.conf

After that edit your xorg.conf to reflect this section:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "ClockGating" "on"
        Option          "ForceLowPowerMode" "on"
        Option          "DynamicPM" "on"
EndSection

You'll lose KMS (for now) but you'll gain a more tested powermanagement using the radeon driver.

I don't know anything about the radeonhd driver though as I've never used it myself, sorry.

---

### Post by abdusamed on 2010-05-17
heat issue in ubuntu is known..same with poor battery life..i'm experiencing it too...

---

### Post by c00lwaterz on 2010-05-17
hi moviemaniac,

Any news about fan in toshiba m900? I check last time the kernel and the thread is not moving. How is it? I hope I have chance to use linux.

Thanks

---

### Post by moviemaniac on 2010-05-17
Sorry, no news yet :(

---

### Post by c00lwaterz on 2010-05-17
> **moviemaniac said:**
> Sorry, no news yet :(

 :(

---

### Post by chaosz911 on 2010-05-19
I solved it...sort of...
After trying several distributions the only one that didn't have this problem is Linux Mint 9.0 :)
I have been torturing the laptop with 3D gaming on high quality and no thermal shutdown, it went to like 70-75C and quickly dropped back to 56C after. The fan is also a lot less loud.

Gotta bare with the green colors of Mint now though, hehe

---

### Post by Mike BFD on 2010-05-20
Fuff... I've read all the thread through))

Thank you guys, and special thanx to Moviemaniac! Some of your advices/workarounds helped me to make my fan work - well, now the temperature "floats" between 65 and 71 degrees which is much better than 83-95 (up to thermal shutdown at 100) I had before.

My laptop is not Toshiba, by the way. It's Compaq Presario A970eo - but had the same "no fan control" issue.

---

### Post by Mike BFD on 2010-05-20
By the way guys (returning to the question "which laptop to choose?" you discussed here a bit), does anybody know an online shop shipping Lenovo and Dell to Finland? Both brands seem to be just poorly distributed here...

---

### Post by jetsam on 2010-05-20
Suddenly, a hush falls upon the crowd...  Next is Mike Dell!

...no, sadly, it's his best lackey, somebody that advises you to buy used no matter what you're selling.

---

### Post by Mike BFD on 2010-05-20
> **jetsam said:**
> Suddenly, a hush falls upon the crowd...  Next is  Mike Dell!

...no, sadly, it's his best lackey, somebody that advises you to buy  used no matter what you're selling.

Sorry, didn't fully understand the post))

---

### Post by c00lwaterz on 2010-05-21
> **chaosz911 said:**
> I solved it...sort of...
After trying several distributions the only one that didn't have this problem is Linux Mint 9.0 :)
I have been torturing the laptop with 3D gaming on high quality and no thermal shutdown, it went to like 70-75C and quickly dropped back to 56C after. The fan is also a lot less loud.

Gotta bare with the green colors of Mint now though, hehe

what laptop do you use? and what model?

---

### Post by girishadat on 2010-05-22
No fix yet in Kernel.org? I am also waiting with CoolWaters... :(
Bookmarked [https://bugzilla.kernel.org/show_bug.cgi?id=14529](https://bugzilla.kernel.org/show_bug.cgi?id=14529)

Ubuntu 10.04 is n times faster... But over-heating killing it...

BTW, is there any BIOS fix from Toshiba? For M900 Portege? C00lWaters?

Update : Just updated the BIOS version to 2.40. And the temperature now is 84 degrees... :(

---

### Post by girishadat on 2010-05-22
Wow... Got the temperature reduced to 55-65 degrees...!

Just updated the BIOS to 2.40 version from Windows. Added grub changes as moviemaniac said...
> 
open up a terminal and enter "sudo gedit /etc/default/grub"
look for the line saying GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
after splash (within the quotation marks) add acpi.power_nocheck
Close gedit, save and execute sudo update-grub

Hurray... CoolWaters, It came down from 93 degrees which was shown when I started and now touched 53...!

:)

PS: I had installed the toshiba utils and all tosh related things before two boots. I think those have no effect on this change...

Also, does this power_nocheck have any -ve impact? What it actually do with the fans? Moviemaniac? Can you help us?

Linux is COOL again...

---

### Post by moviemaniac on 2010-05-22
Tee hee - I reccomended a BIOS-upgrade a few (several) pages ago in this thread - it seems coolwaters never upgraded it as I suggested or otherwise this would've been resolved long ago :D

acpi.power_nocheck does - in short - make linux compatible with certain Windows-powermanagement-thingies. You see, many vendors only test their machines with Windows and this leads to implementations that only really work on Windows because they sometimes don't follow standards. This boot option tells the kernel to expect these non-standard commands and act upon them. Well, that was a very non-technical, extremely simplified explanation, if you want to know more look here: [https://patchwork.kernel.org/patch/23156/](https://patchwork.kernel.org/patch/23156/)

---

### Post by girishadat on 2010-05-23
> **moviemaniac said:**
> Tee hee - I reccomended a BIOS-upgrade a few (several) pages ago in this thread - it seems coolwaters never upgraded it as I suggested or otherwise this would've been resolved long ago :D

acpi.power_nocheck does - in short - make linux compatible with certain Windows-powermanagement-thingies. You see, many vendors only test their machines with Windows and this leads to implementations that only really work on Windows because they sometimes don't follow standards. This boot option tells the kernel to expect these non-standard commands and act upon them. Well, that was a very non-technical, extremely simplified explanation, if you want to know more look here: [https://patchwork.kernel.org/patch/23156/](https://patchwork.kernel.org/patch/23156/)

Yeah, I saw you earlier post on BIOS update and thats why I checked for it. Earlier version was 2.20 and now it is 2.40. With 2.40 and acpi.power_nocheck now everything working fine. CPU temperature ranges from 48-55 degrees range.

Thanks for the new piece of information. :)

I thought this issue is not going to be solved, as the bug in kernel.org is already in closed status... Thanks for all the help, moviemaniac... Also, thanks to C00lWaterz, for posting this. I hope you can also do the same and make ur M900 COOL... Please post here once you are done... :)

Ubuntu 10.04 rocks...!

---

### Post by c00lwaterz on 2010-05-23
> **moviemaniac said:**
> Tee hee - I reccomended a BIOS-upgrade a few (several) pages ago in this thread - it seems coolwaters never upgraded it as I suggested or otherwise this would've been resolved long ago :D

acpi.power_nocheck does - in short - make linux compatible with certain Windows-powermanagement-thingies. You see, many vendors only test their machines with Windows and this leads to implementations that only really work on Windows because they sometimes don't follow standards. This boot option tells the kernel to expect these non-standard commands and act upon them. Well, that was a very non-technical, extremely simplified explanation, if you want to know more look here: [https://patchwork.kernel.org/patch/23156/](https://patchwork.kernel.org/patch/23156/)

Hi moviemaniac, 

I have upgraded but the latest bios available i see is 1.9 in the website for portege m900.

here is the link [http://pc.toshiba-asia.com/portal/public/searchDrivers.action?pgAction=searchDrivers.action&a=driverDlResult&currentTab=service]("http://pc.toshiba-asia.com/portal/public/searchDrivers.action?pgAction=searchDrivers.action&a=driverDlResult&currentTab=service")

Where is bios version 2.4 available?

---

### Post by c00lwaterz on 2010-05-23
> **girishadat said:**
> Wow... Got the temperature reduced to 55-65 degrees...!

Just updated the BIOS to 2.40 version from Windows. Added grub changes as moviemaniac said...


Hurray... CoolWaters, It came down from 93 degrees which was shown when I started and now touched 53...!

:)

PS: I had installed the toshiba utils and all tosh related things before two boots. I think those have no effect on this change...

Also, does this power_nocheck have any -ve impact? What it actually do with the fans? Moviemaniac? Can you help us?

Linux is COOL again...

hi girishadat,

where did you get bios version 2.4? I only seen 1.9 in the website. Can you post the link

thanks

---

### Post by c00lwaterz on 2010-05-24
Hi moviemaniac and girishadat,

I did not find the bios driver 2.4 in website then I tried google search but no luck then I tried again with the keywords toshiba m900 bios 2.4

Now I have the bios 2.4

here is the link [http://toshiba-asia.com/portal/public/driverDlDetails.action?pgAction=driverDlDetails.action&a=driverDlDetails&itemId=30515&currentTab=service&type=Drivers]("http://toshiba-asia.com/portal/public/driverDlDetails.action?pgAction=driverDlDetails.action&a=driverDlDetails&itemId=30515&currentTab=service&type=Drivers")

Now I will try the ubuntu 10.04 if it work. then if it works then I will try fresh install later when I got back home. 

Thanks moviemaniac and girishadat.

Thanks for keeping this thread alive and thanks for posting.

I appreciate so much the help people give me.

Thanks again

---

### Post by c00lwaterz on 2010-05-24
Thanks to bios 2.4

Now my fan is working and from 72 deg celcius it drop to 55 deg celcius.
the fan is blowing now.

and many many many thanks to moviemaniac and girishadat. :)


Moviemaniac,

Can you help me? I want to fresh install the ubuntu. because the only thing that work is grub adding acpi.power_nocheck and also the bios 2.4 so i want to make it normal and fresh install. I still want your guidance, I know im noob when it comes to linux.

After this issues I can learn now linux better because now I can use it. 

I also notice that my internet wifi is only 88% i saw wireless network connection 'auto linksys' active: linksys (88%). What is the 88%? is the the connection? my laptop is near the wireless router in office.

Thanks again and again you rock :guitar::guitar::guitar:

---

### Post by Mike BFD on 2010-05-24
Good to hear BIOS update worked with Toshiba... Unfortunately, there's none available for my Compaq. The temperature is lower than earlier (thanx again, guys!) - but still a little bit too high (70-75 degrees in average)

---

### Post by c00lwaterz on 2010-05-24
> **Mike BFD said:**
> Good to hear BIOS update worked with Toshiba... Unfortunately, there's none available for my Compaq. The temperature is lower than earlier (thanx again, guys!) - but still a little bit too high (70-75 degrees in average)

did you try acpi.power_nocheck ?

---

### Post by moviemaniac on 2010-05-24
@Mike BFD: I can look into it later this week - unfurtunately I'm too busy until at least Thursday. Just remind me on Thursday by bumping this thread ;)

@c00lwaterz: I'm glad you've found the firmware and it's FINALLY working for you! You don't have to reinstall if the system works fine right now!
88% is the quality (strength) of the connection, which is really, really good - nothing to worry about! 100% is a value you may only reach when putting your laptop right next to the router.

---

### Post by girishadat on 2010-05-24
Wow! Nice to see that it worked for C00lWaterz and other M900s. :)

Sorry, I was a bit busy with work... Here is the link from Indian site of Toshiba - [https://www.toshiba-india.com/laptop/DriversDetails.aspx]("https://www.toshiba-india.com/laptop/DriversDetails.aspx")

---

### Post by c00lwaterz on 2010-05-25
> **moviemaniac said:**
> @Mike BFD: I can look into it later this week - unfurtunately I'm too busy until at least Thursday. Just remind me on Thursday by bumping this thread ;)

@c00lwaterz: I'm glad you've found the firmware and it's FINALLY working for you! You don't have to reinstall if the system works fine right now!
88% is the quality (strength) of the connection, which is really, really good - nothing to worry about! 100% is a value you may only reach when putting your laptop right next to the router.

Hi moviemaniac,

I have reinstall the ubuntu last night because there is a problem in proprietary driver in ati. So now it is fix and I try to install also the compiz. the compiz i fine and no overheating but the rain effect is not working. and I also notice that the compiz now has few effects than before. why is that? any idea? i really love compiz/beryl/compiz fusion


Thanks so much moviemaniac and girishadat.:guitar::guitar::guitar:

---

### Post by Mike BFD on 2010-05-25
2 c00lwaterz: Yes, I tried it but with no visible result (surprisingly)

2 moviemaniac: Thank you a lot - and please take your time, no hurry  here. Finally at least "partial cooldown" was achieved so I'm not too  much afraid of thermal shutdown anymore...

An interesting fact: videochats in Skype heat my Compaq just like hell  while watching movies not that much. Seems like it depends on what's  involved the most, CPU or GPU.

---

### Post by c00lwaterz on 2010-05-25
> **Mike BFD said:**
> 2 c00lwaterz: Yes, I tried it but with no visible result (surprisingly)

2 moviemaniac: Thank you a lot - and please take your time, no hurry  here. Finally at least "partial cooldown" was achieved so I'm not too  much afraid of thermal shutdown anymore...

An interesting fact: videochats in Skype heat my Compaq just like hell  while watching movies not that much. Seems like it depends on what's  involved the most, CPU or GPU.

the only time you have overheat is when you are using skype?
What is your bios version and model? I will try to search

thanks

---

### Post by Mike BFD on 2010-05-25
> **c00lwaterz said:**
> the only time you have overheat is when you are using skype?
What is your bios version and model? I will try to search

thanks
Thank you!

Actually my temp never goes below 60-63 degrees (which is not too little), normally it's around 70-75 degrees (which is already too much). When the comp is working hard, it goes even higher but never above 82. Using Skype is the only case when it may reach 90 and more.

"According to noise heard", the fan is changing its speed depending on the temperature detected by sensors but never reaches its maximal speed (as it used to do in Windows).

The full model number is Compaq Presario A970eo, BIOS version F.33

On the HP/Compaq web, there's the version F.34 but in its release notes, the only change is mentioned: "Improves the security of pre-boot  authentication (BIOS-based) passwords by clearing data from volatile  memory". That has a few to do with PM, I guess))

---

### Post by c00lwaterz on 2010-05-25
> **Mike BFD said:**
> Thank you!

Actually my temp never goes below 60-63 degrees (which is not too little), normally it's around 70-75 degrees (which is already too much). When the comp is working hard, it goes even higher but never above 82. Using Skype is the only case when it may reach 90 and more.

"According to noise heard", the fan is changing its speed depending on the temperature detected by sensors but never reaches its maximal speed (as it used to do in Windows).

The full model number is Compaq Presario A970eo, BIOS version F.33

On the HP/Compaq web, there's the version F.34 but in its release notes, the only change is mentioned: "Improves the security of pre-boot  authentication (BIOS-based) passwords by clearing data from volatile  memory". That has a few to do with PM, I guess))

hi,

I have notice when using flash games my temperature goes up to 83 deg celcius then I close the flash games in firefox then after awhile it goes down. hmmmm I think we need professional help with moviemaniac:guitar::guitar:

But when I don't play flash games and I just use compiz fusion it is fine and no high temperature. Only when using flash games. maybe some games also will overheat my laptop.

---

### Post by Mike BFD on 2010-05-25
> **c00lwaterz said:**
> hi,

I have notice when using flash games my temperature goes up to 83 deg celcius then I close the flash games in firefox then after awhile it goes down. hmmmm I think we need professional help with moviemaniac:guitar::guitar:

But when I don't play flash games and I just use compiz fusion it is fine and no high temperature. Only when using flash games. maybe some games also will overheat my laptop.
Hi buddy,

You see, neither games nor Skype are able to heat up a comp! CPU and GPU do that so it would be interesting to know which of those two processors is responsible for overheating...

It seems to me, even the "fixed and improved" fan speed management in our comps is not working properly. My fan seems to react to only ONE of the procs (more likely CPU but maybe GPU) so when ANOTHER proc is heavily loaded, the fan doesn't react and the entire comp heats up... But I'm not a hardware engineer and all that is only my suggestion based on "common sense", not on a real knowledge.

...A later add-on: please excuse me if my post looks like any kind of complaining, I've never meant anything like that!! I do highly appreciate you guys to be ready to help anybody who needs help... Wish I could be more "technically advanced" to offer a solution.
And again, special thanx to moviemaniac))

---

### Post by c00lwaterz on 2010-05-25
> **Mike BFD said:**
> Hi buddy,

You see, neither games nor Skype are able to heat up a comp! CPU and GPU do that so it would be interesting to know which of those two processors is responsible for overheating...

It seems to me, even the "fixed and improved" fan speed management in our comps is not working properly. My fan seems to react to only ONE of the procs (more likely CPU but maybe GPU) so when ANOTHER proc is heavily loaded, the fan doesn't react and the entire comp heats up... But I'm not a hardware engineer and all that is only my suggestion based on "common sense", not on a real knowledge.

...A later add-on: please excuse me if my post looks like any kind of complaining, I've never meant anything like that!! I do highly appreciate you guys to be ready to help anybody who needs help... Wish I could be more "technically advanced" to offer a solution.
And again, special thanx to moviemaniac))

I notice that some application I use it goes up my temperature (random). example I restart right now then the laptop is cool and low temp. then I will restart then it will have high temp after awhile then I will restart (the laptop fan is working) im confuse.. maybe a little more work around will help.

---

### Post by c00lwaterz on 2010-05-25
I try to view many many wallpapers in the internet while i check the temperature. I notice it goes up and down.. so my suspect is GPU. the compiz won't heat so much as it's not use continues. then I try movies in the internet then it goes up high in some site. hmmmmm I really suspect that it is gpu.. =(

---

### Post by Mike BFD on 2010-06-10
...Maybe it's time to give the thread a bump?..

---

### Post by c00lwaterz on 2010-06-11
> **Mike BFD said:**
> ...Maybe it's time to give the thread a bump?..

hmm i don't know but i am still checking everyday. ):P

I still have issues about temperature, that's all :popcorn:

---

### Post by aeiouna on 2010-06-19
Bumping once again. I too am having an issue with overheating. Compaq Presario CQ60-615DX, dual booting Windows 7 and Ubuntu 10.04. Ubuntu was installed via Wubi.

I see no messages while in Ubuntu, but I get a message about my system shutting down "to prevent overheating" when shutting down Ubuntu to go back into Windows.

---

### Post by jozue_noon on 2010-06-25
Hi all!
I have a similar problem. Fan runs very slowly and when the temperature rises, nothing  changes. When I use GoogleEarth or play Nexuiz after about 20 minutes,  the computer reboots. I suspect that the problem is  somehow related to the GPU.

Ubuntu 10.04
HP probook 6540b (bios F.04)
Linux  2.6.32-23-generic-pae 
ATI Mobility Radeon HD 4500 Series (ATI proprietary driver 11/09/09,00:23:25)

---

### Post by c00lwaterz on 2010-06-27
> **jozue_noon said:**
> Hi all!
I have a similar problem. Fan runs very slowly and when the temperature rises, nothing  changes. When I use GoogleEarth or play Nexuiz after about 20 minutes,  the computer reboots. I suspect that the problem is  somehow related to the GPU.

Ubuntu 10.04
HP probook 6540b (bios F.04)
Linux  2.6.32-23-generic-pae 
ATI Mobility Radeon HD 4500 Series (ATI proprietary driver 11/09/09,00:23:25)

I also suspect that is with GPU. did anyone already submit this on launchpad?

---

### Post by Mike BFD on 2010-06-28
> **c00lwaterz said:**
> I also suspect that is with GPU. did anyone already submit this on launchpad?
Hi c00lwaterz, it's been a long time!

Surprisingly, one thing has recently helped me to lower "minimal working temp" from 63 to 55 degrees (all other "grades" have lowered respectively).

Keeping installed "the very new" Xorg (taken from where Moviemaniac showed), I tried to boot with the last "official Ubuntu" kernel (2.6.32-22 if I don't mix up). And that worked.

Frankly, I have no idea how exactly it worked)))))))))
- The 32-22 version may have a fix for the entire problem;
- The 32-22 version may have a fix, but working only with that "the freshest and still beta" Xorg driver package;
- The 32-22 version, with or without that "special" Xorg, may be solving the problem only together with some other package updated (however, it's all about updates received from Ubuntu via UpdManager, not about anything manually installed from "third" places)

But it worked - so I guess it's worth checking on other machines.

---

### Post by moviemaniac on 2010-06-28
@aeiouna and jozue_noon:

Try this:

open up a terminal and enter "sudo gedit /etc/default/grub"
look for the line saying GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
after splash (within the quotation marks) add acpi.power_nocheck
Close gedit, save and execute sudo update-grub
after that reboot and your fan should kick in much sooner.

---

### Post by FreaKO on 2010-07-28
Same problem here with Toshiba Satellite Pro L300D-SP5808R. Insyde H20 BIOS v. 1.90. In Linuxquestions they say it's a problem related with BIOS. I've been using the 'acpi_osi="Linux"' fix but only works sometimes after consecutive reboots (all so perfect) and only with AC adapter conected on boot. I've tried the "acpi.power_nocheck=1" fix, and both of them. Generally speaking, it won't work.

Somewhere I read it's gonna be fixed on linux 2.6.35 or soon with open source drivers. It's a pain in the... well, you know. Somewhere else I read it's an old problem related with acpid, but I don't believe so. There are even some fixes related with DSDT patching, but they only work partially. The thing is, somehow, the OS manages to work perfectly under some circumstances, so, it can work like a charm always... but how "lord only knows" :(.

By the way, I'm using Ubuntu 10.04 lucid lynx 32-bit (It doesn't matter if it's 64-bit, happens the same thing) and with my Radeon Mobility Xpress x1250, fglrx's not an option.

---

### Post by c00lwaterz on 2010-07-28
> **FreaKO said:**
> Same problem here with Toshiba Satellite Pro L300D-SP5808R. Insyde H20 BIOS v. 1.90. In Linuxquestions they say it's a problem related with BIOS. I've been using the 'acpi_osi="Linux"' fix but only works sometimes after consecutive reboots (all so perfect) and only with AC adapter conected on boot. I've tried the "acpi.power_nocheck=1" fix, and both of them. Generally speaking, it won't work.

Somewhere I read it's gonna be fixed on linux 2.6.35 or soon with open source drivers. It's a pain in the... well, you know. Somewhere else I read it's an old problem related with acpid, but I don't believe so. There are even some fixes related with DSDT patching, but they only work partially. The thing is, somehow, the OS manages to work perfectly under some circumstances, so, it can work like a charm always... but how "lord only knows" :(.

By the way, I'm using Ubuntu 10.04 lucid lynx 32-bit (It doesn't matter if it's 64-bit, happens the same thing) and with my Radeon Mobility Xpress x1250, fglrx's not an option.

I notice also that the problem is not yet fix but i think there is a way. maybe it's not yet improve or maybe they are already tired fixing. I will just wait for further releases and test it. for 10.04, I think it will always be overheat issue with some laptop. maybe soon it will be fix but now we need to wait.:(

---

### Post by FreaKO on 2010-07-30
> **c00lwaterz said:**
> I notice also that the problem is not yet fix but i think there is a way. maybe it's not yet improve or maybe they are already tired fixing. I will just wait for further releases and test it. for 10.04, I think it will always be overheat issue with some laptop. maybe soon it will be fix but now we need to wait.:(

Are you sure? As I see it, it's been 3 ubuntu releases with this same problem. I've been trying with every main distro I know except the "originary" ones (slackware, debian, gentoo...). It's the same problem with openSUSE, Arch Linux, Sabayon Linux, Linux Mint and PCLinuxOS. Maybe we could get some advice from advanced users and really try to figure out what's going on, you know, "dirty job".

---

### Post by theozzlives on 2010-07-30
No overheating here. Maybe clean some dust off your fan and make sure your air holes aren't blocked. Is your laptop on a smooth hard surface?

---

### Post by FreaKO on 2010-08-01
> **theozzlives said:**
> No overheating here. Maybe clean some dust off your fan and make sure your air holes aren't blocked. Is your laptop on a smooth hard surface?

Thank you very much but that's not the problem. Pretty sure. That was the first thing I thought even knowing it's a brand new laptop. The topic is: if I stress my computer it gets 105 C and shuts down.

To use GNU/Linux I have to watch out the core temperatures all the time,if it gets too hot then I'll have to use the powersave governor on cpufreq, if it gets a little cool I go back to ondemand governor. I can't have the performance governor working more than just some minutes.

If I use acpi.power_nocheck and use the laptop with little stress, then it's OK. But if I try to make some operations with GRASS, then it goes crazy and I gotta activate powersave governor because fan is stucked at the same state. If I manage to make it work with acpi_osi="Linux", EVERYTHING works PERFECT: I have Fn Keys, Fan Control, Brightness control, acpid events, correct temperature readings and a good battery performance, etc. How... how?

---

### Post by sillyboiz on 2010-09-05
Hi everybody. I'm new to Ubuntu 10.04 and I'm using a Toshiba Portege M900 Signature series laptop. The same one that coolwaterz has I think. 

Firstly, I would like to thank everyone for their suggestions especially moviemaniac for his wonderful contributions. However,I've been through and tried everything that everyone has said and all i see are errors and my laptop still keeps overheating. 

Can someone please help me? It would be great if I could recieve help from moviemaniac.

---

### Post by c00lwaterz on 2010-09-05
> **sillyboiz said:**
> Hi everybody. I'm new to Ubuntu 10.04 and I'm using a Toshiba Portege M900 Signature series laptop. The same one that coolwaterz has I think. 

Firstly, I would like to thank everyone for their suggestions especially moviemaniac for his wonderful contributions. However,I've been through and tried everything that everyone has said and all i see are errors and my laptop still keeps overheating. 

Can someone please help me? It would be great if I could recieve help from moviemaniac.

yes we have same signature laptop from toshiba portege m900 mine is brown with white led light for volume and media controls.

---

### Post by colin.p on 2010-09-05
I have a Dell 1545 laptop that is a dual boot with lucid and win7. In windows the temp usually was around 50-60 degrees celcius. In lucid around 55-65. However, I have not had this computer connected for 2 weeks (wireless modem was fubared) and had to use another one for dial up.
Now that my modem has been replaced, I of course fired up this laptop and did all my updates, which included a kernel update.
Now, in windows it seems that the temp remained at 50-60, but with this new kernel ( 2.6.32-24), I now have a temp running 40-50 degrees, even though in powertop, my "wake ups" remained the same (very high).
It maybe my imagination, but with the latest kernel update, my temps dropped by 15 degrees.

---

### Post by sillyboiz on 2010-09-05
@Coolwaterz - Haha I didn't realise we would have the same colored laptop too. Anyway, I've bee re-reading this whole topic over and over again when I saw moviemaniac's thread about adding this acpi no check thing to your grub. Apparently , it works!

Previously I followed another thread about how you can add a hardware sensors monitor to your panel and after applying the changes, my fan started working and the temperature of my laptop dropped from 96 degress to 60 and now its even going lower! Haha no words can describe how happy I am after being troubled over this issue for many months. 

Even though moviemaniac might not see this I would really like to thank him for ideas and suggestions and perhaps better help me understand ubuntu and my laptop better.

---

### Post by c00lwaterz on 2010-09-06
> **sillyboiz said:**
> @Coolwaterz - Haha I didn't realise we would have the same colored laptop too. Anyway, I've bee re-reading this whole topic over and over again when I saw moviemaniac's thread about adding this acpi no check thing to your grub. Apparently , it works!

Previously I followed another thread about how you can add a hardware sensors monitor to your panel and after applying the changes, my fan started working and the temperature of my laptop dropped from 96 degress to 60 and now its even going lower! Haha no words can describe how happy I am after being troubled over this issue for many months. 

Even though moviemaniac might not see this I would really like to thank him for ideas and suggestions and perhaps better help me understand ubuntu and my laptop better.

yes it would drop but when you play normal games with graphics it will go up again. maybe gpu i suspect. when using gpu the fan do not recognize the heat. try to explore using some graphics or play movies. if you notice some heat problem then post it here. if not then tell me how did you do it. at first my laptop was working fine with the solution here but when i was using after day by day, i notice the temp is going high again and my hands can't touch my laptop. 

Moviemaniac is great. maybe he is advance user. Im thankful he help me so much here

---

### Post by sillyboiz on 2010-09-07
Hi coolwaterz, I think I'm experiencing the same problem as you right now. My laptop's temperature keeps rising after I've made the change. In addition, sometimes while listening to music, my keyboard hangs and no matter what key i press it won't respond. 

Moviemaniac! Where are you!!!!!!! Coolwaterz and I really need your help!

---

### Post by moviemaniac on 2010-09-11
> **sillyboiz said:**
> @Coolwaterz - Haha I didn't realise we would have the same colored laptop too. Anyway, I've bee re-reading this whole topic over and over again when I saw moviemaniac's thread about adding this acpi no check thing to your grub. Apparently , it works!


I'm really glad you found that part in the thread (yeah, the information's really hidden... :D )

I'm also sorry I didn't get back to you sooner - I was down all week with the flu and now I have e shocking amount of backlog of mails and other things calling for my attention :(

Here's a suggestion for all of you who still struggle with power management: Try the new Maverick Beta and see if it changes things for you. I've been running Maverick since the very first day (rolling release) and have found it to be a very reliable, solid release so far. Give it a try if powermanagement still bugs you. I can't promise anything but lots of stuff has changed so there might be hope!

If trying maverick and all the hints in this tread still doesn't work, blame your hardware vendor (Toshiba) as there's nothing more I can do for now. The best option would be to sell the notebook to a happy windows user and buy a supported machine (just ask on the forums for experiences with the model you wanna buy). 99,x% of all laptops work flawlessly out-of-the box with linux (Ubuntu) so it's really sad it you get a machine that just doesn't want to do what you tell it to...

---

### Post by sillyboiz on 2010-09-12
Hey Moviemaniac! Erm your recommendation to upgrade to the new maverick did not work for me. Now I can't even log in to my laptop cause they keep asking me for my laptop log in name and password which I do not know of. Please help me!!!!!!
 
I tried all sorts of combinations but to no avail . Please reply as soon as you see this!!!!!!

---

### Post by moviemaniac on 2010-09-12
Oh dear... I should've been more clear:

My suggestion was to TEST maverick (new install, try it from the cd, install it alongside 10.04) not to REPLACE your current install with maverick. It is a very, very, very bad idea to dist-upgrade to a new release which is not finished yet. The release candidate would be the earliest suitable test-release where (knowledgeable) guys could/should update. So DON'T do it until the release candidate is out - until then you can use maverick as a fresh install or just test it from cd/dvd!!!

But now that you've already got a problem, post about it (tell the guys what you did, upgrade from xx to maverick and write about the problem) in the maverick development nd testing forum, you'll find the best help there as I'm not particularly experienced with the whole login-stuff: [http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by FreaKO on 2010-09-13
I did a fresh install with the Maverick Meerkat Daily Build CD. It's still happening. But it's not so bad as Lucid Lynx. The fan starts and never stops at ~80 C but now it's cooler at full speed, passed from ~65 C to ~55 C. I hope better performance with final release. You still can't stress your computer, but keep the ondemand governar and be careful it's not going back to performance. Is there a way to keep ondemand governor only between 800 MHz and 1.60 GHz not going any further?

---

### Post by moviemaniac on 2010-09-13
> **FreaKO said:**
> [...]Is there a way to keep ondemand governor only between 800 MHz and 1.60 MHz not going any further?

Short and long answer: No (AFAIK)

---

### Post by FreaKO on 2010-09-14
> **moviemaniac said:**
> Short and long answer: No (AFAIK)

Thank you, I guess. Well... now that I know that's not possible I'll stop trying to make it work. What could it be...? I can't even compile a new kernel with these heating problems and with 800 MHz it will take more than a few hours. The only way I could use ubuntu is with powersave governor, and still gets hot! Should I stop using the open source radeon driver and start using vesa driver for a while? Could that at least keep my laptop cooler?

Damn, once you use GNU/Linux you want to keep using it whatever it takes. One year and still trying...

---

### Post by sillyboiz on 2010-09-16
Hi Moviemaniac! It seems I just had to reload in my OS and reset everything. Once I've done that I realised that whenever I watch videos online, my temperature suddenly shoots up to like 97 degrees and stays there. However, once I close the window, it drops back to 68 degrees. So I probably think that you would tell me to not watch vidoes but I cant for buisness reasons.  So I was wondering whether you could tell me another solution to this problem. Thanks!

---

### Post by moviemaniac on 2010-09-19
@sillyboiz: Are you on Ubuntu 10.10 beta now? If so, add the following lines to your /etc/rc.local (add them BEFORE the line "exit 0"). To do this press ALT+F2 and enter (without exclamation marks) "gksu gedit /etc/rc.local" - you will be asked for your admin-password:

> 
echo profile > /sys/class/drm/card0/device/power_method
echo low > /sys/class/drm/card0/device/power_profile

these two lines force the power management of the video card to always use the lowest clock modes (=less heat). However there's still no way to control the power fan of this Toshiba laptop - go blame Toshiba for that, there's nothing we can do about it!
And not owning or being able to take a look at the machine in question myself makes this so much harder to troubleshoot over the internet... :(
By the way: You did update the Bios and to the ACPI_nocheck-thingy? Just to make sure... 

> **FreaKO said:**
> Should I stop using the open source radeon driver and start using vesa driver for a while? Could that at least keep my laptop cooler?

The Vesa driver will definitely be worse. For now the proprietary ATI driver is still the best in terms of power consumption AFAIK even though it got way better with the radeon-driver during the last months but that requires bleeding-edge stuff and lots of self-compiled packages.

---

### Post by sillyboiz on 2010-09-20
Hey Moviemaniac! Nope! I'm still on Lucid lynx Ubuntu 10.04. If these configurations are only for 10.10 then I'll patiently wait. However, do you have any solution for 10.04 currently? Thanks!

---

### Post by moviemaniac on 2010-09-23
These only work on 10.10 as the new version will feature power management for ATI cards with the open source radeon driver. It can be done with 10.04 too but it's a messy thing for inexperienced users.

---

### Post by c00lwaterz on 2010-09-25
im still checking feedback from toshiba user who has same problems before I will install. our internet here is not good so its hard to download and test. =(

---

### Post by c00lwaterz on 2010-09-30
bump

---

### Post by girishadat on 2011-02-19
hey coolwaterz, just one point. Plz see - [http://ubuntuforums.org/showthread.php?p=10474500#post10474500](http://ubuntuforums.org/showthread.php?p=10474500#post10474500)

```
acpi.power_nocheck=1
```try this instead of,
```
acpi.power_nocheck
```
if you are still having heating problems on ur m900.

I am not sure if the =1 has got some effect. I lost my power_nocheck after a kernel upgrade i think.


```
girish@girish-laptop:~$ uname -a
Linux girish-laptop 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux
```

---

### Post by c00lwaterz on 2011-02-22
> **girishadat said:**
> hey coolwaterz, just one point. Plz see - [http://ubuntuforums.org/showthread.php?p=10474500#post10474500](http://ubuntuforums.org/showthread.php?p=10474500#post10474500)

```
acpi.power_nocheck=1
```try this instead of,
```
acpi.power_nocheck
```
if you are still having heating problems on ur m900.

I am not sure if the =1 has got some effect. I lost my power_nocheck after a kernel upgrade i think.


```
girish@girish-laptop:~$ uname -a
Linux girish-laptop 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux
```

thanks btw, how can i edit the =1? i forgot already as i cannot use linux because of overheat. can u help me from start? =) thanks

---

### Post by c00lwaterz on 2011-02-24
is there any solution for this problem? as acpi.power_nocheck=1 is not working for me. the fan still now working properly on my toshiba m900. It only works on windows.

this is already a long issue in my laptop (1 year already)
I need help on this one. 

thanks

---

### Post by jowoxx on 2011-10-15
My apologies to anyone offended for replying on this old thread.

I read through pages 1-27 and sorted my issue, so thought I should log it here.

On my Toshiba Satellite L510, Ubuntu 10.04 has never given an issue.
However, on my new Toshiba Protege M900, there was a big issue of ovetheating.
The left side of the laptop where the heatsink and air vent outlet are located, was so hot I could not even put my left hand down on the keyboard.

Using gkrellm, I found the temperature to be 110'c.
Which is relatively crazy.

So after reading up alot of material, I tried the following step by step.

Activated ATI FGLRX drivers
not my cup of tea but 110'c is worse...

Temp went down marginally to around 100'c

Downloaded and installed BIOS 2.40
[http://pc.toshiba-asia.com/support/drivers/details/30516](http://pc.toshiba-asia.com/support/drivers/details/30516)

After reboot, temp dropped to around 85'c.
Which was good!

Next, I modified /etc/default/grub from
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi.power_nocheck=1"

followed by sudo update-grub

Now my temperature is hovering between 50-60'c,
which is normal again.

Thanks!

---

