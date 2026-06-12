---
title: "Ubuntu hijacked by unknown process."
date: 2011-11-08
forum: General Help
---

### Post by Rebelli0us on 2011-11-08
Process cannot be terminated, if killed it restarts, likewise for its parent.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206666&stc=1&d=1320759897[/IMG]

This complies with the definition of a virus -- an unknown, unwanted process on my property doing unauthorized things, under the guise of “root”. If even arrogantly announces that I have “no permission” to know more. Really? Should I shut this thing down?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206665&stc=1&d=1320759897[/IMG]

---

### Post by Rebelli0us on 2011-11-08
I shut down all apps and Virtualbox to see which app is responsible for this, but process “phy0” continues. CPU usage bounces between 0% and 100%.

---

### Post by nosirrah111 on 2011-11-08
Im not familiar with this process, so I'd have to say its likely a virus, first things first, shut down your internet connection on the computer with it (as long as you can get access on another) so as to make sure its not sending any of your info out. As for removing it (if it even is in fact a virus) I'm not knowledgeable enough to help.

---

### Post by hwttdz on 2011-11-08
I'd do 
```
ps -ww -eo pid,ppid,%cpu,%mem,command|grep phy0
MYPPID=`ps -ww -eo pid,ppid,%cpu,%mem,command|grep phy0|grep -v grep|awk '{print $2}'`
ps -ww -eo pid,ppid,%cpu,%mem,command|grep $MYPPID
```

And post the output, this will tell us the real names of the process in question and the parent proces.

I wouldn't worry too much, you shouldn't expect to be able to peep on root's processes as not root.  Maybe if you started gnome-system-monitor as root it would let you.  Sounds like the worst that might be happening is your wireless is misbehaving.

Also keep in mind when you shut down all apps, nothing is expected to change.  In fact even if you were to log out nothing would be expected to change, root is running the process not you.  We have no reason to believe this is a virus at the moment.

---

### Post by Rebelli0us on 2011-11-08
> **hwttdz said:**
> I'd do 
```
ps -ww -eo pid,ppid,%cpu,%mem,command|grep phy0
MYPPID=`ps -ww -eo pid,ppid,%cpu,%mem,command|grep phy0|grep -v grep|awk '{print $2}'`
ps -ww -eo pid,ppid,%cpu,%mem,command|grep $MYPPID
```

And post the output, this will tell us the real names of the process in question and the parent proces.

I wouldn't worry too much, you shouldn't expect to be able to peep on root's processes as not root.  Maybe if you started gnome-system-monitor as root it would let you.  Sounds like the worst that might be happening is your wireless is misbehaving.

Also keep in mind when you shut down all apps, nothing is expected to change.  In fact even if you were to log out nothing would be expected to change, root is running the process not you.  We have no reason to believe this is a virus at the moment.

Thank you. I logged in as root and tried to kill the process and its parent, to no avail. 

The command you posted is one long line or a 3-liner?

---

### Post by Rebelli0us on 2011-11-08
What does this mean?

```

 ps -ww -eo pid,ppid,%cpu,%mem,command|grep phy0
  983     2  2.3  0.0 [phy0]
 6469  6445  0.0  0.0 grep --color=auto phy0
```

---

### Post by collisionystm on 2011-11-08
anything in your dmesg?

[http://info.solomonson.com/content/phy0-spikes-cpu-and-dmesg-says-ath5k-phy0-gain-calibration-timeout](http://info.solomonson.com/content/phy0-spikes-cpu-and-dmesg-says-ath5k-phy0-gain-calibration-timeout)

---

### Post by matt_symes on 2011-11-08
Hi

phy0 ? 

What network cards do you have in your system ?

```
matthew@matthew-laptop:~$ ps aux | grep [p]hy0
root       945  1.0  0.0      0     0 ?        R    11:35   1:46 [phy0]
matthew@matthew-laptop:~$ 
```

```
matthew@matthew-laptop:~$ rfkill list
0: acer-wireless: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
matthew@matthew-laptop:~$ 
```

Kind regards

---

### Post by Rebelli0us on 2011-11-08
> **nosirrah111 said:**
> Im not familiar with this process, so I'd have to say its likely a virus, first things first, shut down your internet connection on the computer with it (as long as you can get access on another) so as to make sure its not sending any of your info out. As for removing it (if it even is in fact a virus) I'm not knowledgeable enough to help.

There's nothing of value in this particular computer, so I'm letting **IT** run, in the public interest.

---

### Post by Rebelli0us on 2011-11-08
> **collisionystm said:**
> anything in your dmesg?

[http://info.solomonson.com/content/phy0-spikes-cpu-and-dmesg-says-ath5k-phy0-gain-calibration-timeout](http://info.solomonson.com/content/phy0-spikes-cpu-and-dmesg-says-ath5k-phy0-gain-calibration-timeout)

What is dmesg?

---

### Post by BillyBoa on 2011-11-08
Look here
[http://ubuntuforums.org/showthread.php?p=7479544]("http://ubuntuforums.org/showthread.php?p=7479544")
[https://bugzilla.redhat.com/show_bug.cgi?id=506659]("https://bugzilla.redhat.com/show_bug.cgi?id=506659")

---

### Post by collisionystm on 2011-11-08
> **Rebelli0us said:**
> What is dmesg?


open a terminal

type

dmesg

post output

---

### Post by Rebelli0us on 2011-11-08
> **matt_symes said:**
> Hi

phy0 ? 

What network cards do you have in your system ?

```
matthew@matthew-laptop:~$ ps aux | grep [p]hy0
root       945  1.0  0.0      0     0 ?        R    11:35   1:46 [phy0]
matthew@matthew-laptop:~$ 
```

```
matthew@matthew-laptop:~$ rfkill list
0: acer-wireless: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
matthew@matthew-laptop:~$ 
```

Kind regards

There's a wired LAN on the mobo and a wireless D-link card, both running. Does that answer your question?

---

### Post by Rebelli0us on 2011-11-08
> **collisionystm said:**
> open a terminal

type

dmesg

post output

dmesg spits out more than the terminal buffer will hold...

```

[70787.881593] ath9k: Two wiphys trying to scan at the same time
[71058.008886] ath9k: Two wiphys trying to scan at the same time


```

---

### Post by davdo2004 on 2011-11-08
Is it not the same problem as on this thread......
[http://ubuntuforums.org/showthread.php?t=1191012](http://ubuntuforums.org/showthread.php?t=1191012)

---

### Post by matt_symes on 2011-11-08
Hi

Try unloading your WIFI driver and then check to see if phy0 is a running process. To give you an idea here is an example on my system.

```
matthew@matthew-laptop:/home$ ps aux | grep [p]hy0
root     10755  1.5  0.0      0     0 ?        S    14:44   0:01 [phy0]
matthew@matthew-laptop:/home$ sudo modprobe -r ath9k
matthew@matthew-laptop:/home$ ps aux | grep [p]hy0
matthew@matthew-laptop:/home$ sudo modprobe ath9k
matthew@matthew-laptop:/home$ ps aux | grep [p]hy0
root     11035  5.6  0.0      0     0 ?        S    14:46   0:00 [phy0]
matthew@matthew-laptop:/home$ 
```My driver will be different than yours.

If the process phy0 is stopped - and i expect it will - then you know the problem is with your WIFI driver.

> Does that answer your question?The above steps will :)

Kind regards

---

### Post by Rebelli0us on 2011-11-08
> **matt_symes said:**
> Hi

Try unloading your WIFI driver and then check to see if phy0 is a running process. To give you an idea here is an example on my system.

```
matthew@matthew-laptop:/home$ ps aux | grep [p]hy0
root     10755  1.5  0.0      0     0 ?        S    14:44   0:01 [phy0]
matthew@matthew-laptop:/home$ sudo modprobe -r ath9k
matthew@matthew-laptop:/home$ ps aux | grep [p]hy0
matthew@matthew-laptop:/home$ sudo modprobe ath9k
matthew@matthew-laptop:/home$ ps aux | grep [p]hy0
root     11035  5.6  0.0      0     0 ?        S    14:46   0:00 [phy0]
matthew@matthew-laptop:/home$ 
```My driver will be different than yours.

If the process phy0 is stopped - and i expect it will - then you know the problem is with your WIFI driver.

The above steps will :)

Kind regards

I don't know how to to unload my WIFI driver, but I searched for "wifi" in the KDE system monitor and I found a process "WIFI radar", ended it and the cpu usage stopped, but my wireless network is also down. Looks like I'll have to reboot to get wireless back.

I installed "WIFI radar" a couple of days ago, it showed that I was using the same channel as 2 of my neighbours. I changed the channel and speed/dropouts stopped, but I'm sure I'd closed the applet.

---

### Post by matt_symes on 2011-11-08
Hi

The problem is connected to your WIFI then. That's good. The problem has been identified.

I gather from the tenor of your last post that you were having drop outs with WIFI before and now you don't as you have changed the channel but you now have high CPU usage whereas before you did not ?

> I changed the channel and speed/dropouts stoppedYou changed it on your wireless router of course ?

This may be caused by WIFI-radar. I have to be careful about any advice i give here because i have not used WIFI-radar before (and i may be wrong anyway).

> KDE system monitorI also don't use Kubuntu; another reason to tread carefully.

Have you considered uninstalling it.

Wait for other responses. See what others think.

Kind regards

---

### Post by Lampi on 2011-11-08
Kubuntu has it's own network manager for wired/wifi connections -> did you switch it off before you installed wifi-radar? Otherwise they might conflict each other, and give you the high cpu load.

---

### Post by Rebelli0us on 2011-11-08
> **matt_symes said:**
> Hi

The problem is connected to your WIFI then. That's good. The problem has been identified.

I gather from the tenor of your last post that you were having drop outs with WIFI before and now you don't as you have changed the channel but you now have high CPU usage whereas before you did not ?

You changed it on your wireless router of course ?

This may be caused by WIFI-radar. I have to be careful about any advice i give here because i have not used WIFI-radar before (and i may be wrong anyway).

I also don't use Kubuntu; another reason to tread carefully.

Have you considered uninstalling it.

Wait for other responses. See what others think.

Kind regards

Thank you. I don’t know what caused the high CPU usage or what “phy0” is, but it stopped when I killed "WIFI radar" in the System Monitor.

CPU usage is back to normal and after a reboot my wireless is working again.

Yes, the channel change was on the Linksys wireless router, it should have no effect on the OS. I can spot problems, I’m an inventor & industrial designer, I write Windows apps occasionally but I know nothing of Linux. I do remember "WIFI radar" hung the system for a while and then died, very buggy, but that may just be a coincidence. Linux sure needs one or more gifted leaders to guide the project.

I’m using straight Ubuntu, not Kubuntu. Occasionally I install stuff through the Ubuntu software center but I assume that if it’s there it’s safe to use. I installed the KDE System Monitor because the Ubuntu one is deficient. Dolphin and Konqueror also sneaked in, though I never installed them.

Thanks again, hope this helped somebody.

---

### Post by Slim Odds on 2011-11-08
> **Rebelli0us said:**
> <cut> Linux sure needs one or more gifted leaders to guide the project.<cut>

At the risk of going off topic, I just want to make a comment about your comment.

Linux is not a project. There are literally hundreds, if not thousands, of Linux distributions. Linux is most definitely not a warm cozy place that will always take care of all you needs and never surprise you. But then again, other operating systems will give you many surprises as well. At least with Linux, everything that it does is out in the open for all to see.

---

### Post by Rebelli0us on 2011-11-08
> **Slim Odds said:**
> At the risk of going off topic, I just want to make a comment about your comment.

Linux is not a project. There are literally hundreds, if not thousands, of Linux distributions. Linux is most definitely not a warm cozy place that will always take care of all you needs and never surprise you. But then again, other operating systems will give you many surprises as well. At least with Linux, everything that it does is out in the open for all to see.

Thank you, no argument from me on that one.

Linux has only 1% market share, but Windows is NOT 99 times better. Why not some gifted leadership and focus so that Linux can be a real alternative for average people?

---

### Post by blind2314 on 2011-11-08
> **Slim Odds said:**
> At the risk of going off topic, I just want to make a comment about your comment.

Linux is not a project. There are literally hundreds, if not thousands, of Linux distributions. Linux is most definitely not a warm cozy place that will always take care of all you needs and never surprise you. But then again, other operating systems will give you many surprises as well. At least with Linux, everything that it does is out in the open for all to see.

Erm..that last statement of yours isn't correct.

---

### Post by Roasted on 2011-11-08
> **blind2314 said:**
> Erm..that last statement of yours isn't correct.

Do I dare ask how it isn't?

---

### Post by blind2314 on 2011-11-08
> **Roasted said:**
> Do I dare ask how it isn't?

Sigh. I suppose not, based on that statement.

---

### Post by Slim Odds on 2011-11-08
LOL

Ubuntu forum thread hijacked by unknown comment.....

---

