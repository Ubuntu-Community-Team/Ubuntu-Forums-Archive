---
title: "problem with pwmconfig"
date: 2009-07-10
forum: General Help
---

### Post by x2mirko on 2009-07-10
Hello,

I'm pretty new to linux (in fact this is the first time i really tried to get a system running ;) ) and i've got a problem with the fan control which i'm not able to solve myself. So here it goes:

I want to control my fans and found out that the usual way to do this is via fancontrol, which needs lm_sensors and pwmconfig to run properly. I've installed and configured lm_sensors without any problems and running sensors gives me back proper data, so i guess everything worked there. 

The problem starts with pwmcontrol. Everytime i run it, it tells me the following:

```
root@mirko:~# pwmconfig
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0/device is f71882fg
   hwmon1/device is coretemp
   hwmon2/device is coretemp
   hwmon3/device is coretemp
   hwmon4/device is coretemp

Found the following PWM controls:
   hwmon0/device/
/usr/sbin/pwmconfig: line 152: hwmon0/device/: Is a directory
   hwmon1/device/
/usr/sbin/pwmconfig: line 152: hwmon1/device/: Is a directory
   hwmon2/device/
/usr/sbin/pwmconfig: line 152: hwmon2/device/: Is a directory
   hwmon3/device/
/usr/sbin/pwmconfig: line 152: hwmon3/device/: Is a directory
   hwmon4/device/pwm[1-9]

Giving the fans some time to reach full speed...
Found the following fan sensors:
   hwmon0/device/fan1_input     current speed: 3030 RPM
   hwmon0/device/fan2_input     current speed: 0 ... skipping!
   hwmon0/device/fan3_input     current speed: 0 ... skipping!
   hwmon0/device/fan4_input     current speed: 0 ... skipping!

As you are not root, we cannot write the PWM settings.
Please run as root to continue.

```I am _definitly_ logged in as root (after sudo pwmconfig returned the above, i've also tried logging in via su, but it did not make any difference), so i don't understand what's the problem. 

Does anyone here have an idea, what i could do to solve this? Help would really be appreciated.

edit: I've forgot: I am running Kubuntu 9.04

---

### Post by kidders on 2009-07-12
Hi there,

That's very odd ... there's either something wrong with your version of pwmconfig, or your hardware is not compatible with it.

The error message you're seeing is spurious. Pwmconfig assumes that if it can't instruct your fans to change speed, you mustn't have the necessary privileges (ie you're not root). In reality, the problem is that it's gotten the path to your fan control files wrong, and *that's* why it's having problems sending instructions.

The first thing I would suggest is that you take a look for bug reports on this issue. You may well not be the first person to run into it. In the meantime, you and I can try a few things, just in case you need to file a bug report of your own ...

**Check out your version of pwmconfig**
I'm not running Kubuntu, so it would be interesting to check whether your pwmconfig and mine (Ubuntu 8.10) are significantly different. If you like, run **cat `which pwmconfig` > ~/pwmconfig.txt** and attach the .txt file in your home directory to your next post.

**Gather some debug info**
I know you're new to Linux, but if you have the stomach for it, stepping through some of what pwmconfig is doing when it screws up would be very useful in solving your problem.

I've attached a stripped-down version of pwmconfig to this post (with all the functionality taken away) that spits out some debug info at the end. Assuming your pwmconfig script turns out to be the same as mine, running it will tell us where it *thinks* your fan control files are. To use it, you would need to ...[LIST]
[*]Download the file (pwmconfig-debug.txt) to your home directory.
[*]Run **chmod 755 ~/pwmconfig-debug.txt** to make it executable.
[*]Run **~/pwmconfig-debug.txt** to execute it. (NB: You do _not_ need to run it as root.)
[*]Post back the output.
[/LIST]
With any luck, something obvious will crop up that you can tweak to get your fan control working.

---

### Post by DeMus on 2009-07-12
> **x2mirko said:**
> Hello,



[code]root@mirko:~# pwmconfig


As you can see, you did NOT start pwmconfig as root. Try it again but this time with sudo in front of it.

Oops, I just saw you were logged in as root. This is not necessary, just stay yourself and use sudo pwmconfig. It works, I have done the same.

---

### Post by The-ITu on 2009-07-12
the terminal does not care who your logged in as.
you have to type in the root command which is sudo in order to do something as root.
this is to keep your system virus free!!
```
sudo pwmconfig
```

---

### Post by kidders on 2009-07-12
> **DeMus said:**
> Try it again but this time with sudo in front of it.
> **The-ITu said:**
> you have to type in the root command which is sudo

Didn't the o/p already say this doesn't have any effect? In any case, the errors in pwmconfig's output are not the result of insufficient privileges.

---

