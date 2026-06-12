---
title: "Network Manager Disabled"
date: 2010-04-09
forum: General Help
---

### Post by kittiikat on 2010-04-09
A friend of mine put kubuntu on my laptop. I have no idea how to fix things, and now it says 'Network Manager Disabled' how do i re enable?

---

### Post by bobcollard on 2010-04-10
> **kittiikat said:**
> A friend of mine put kubuntu on my laptop. I have no idea how to fix things, and now it says 'Network Manager Disabled' how do i re enable?
Do you have a button or switch for use on airplanes to turn off the wifi?  Check to see if that is enabled.

---

### Post by iRiUX on 2010-04-30
> **kittiikat said:**
> A friend of mine put kubuntu on my laptop. I have no idea how to fix things, and now it says 'Network Manager Disabled' how do i re enable?

I have exactly the same problem. My kubuntu 10.4 suddenly crashed when updating, and upon reboot the network manager is disabled. The only way I have found to connect to a network again is via command line, obviously this is not a solution. I think its a major bug.

---

### Post by chaosgrimm on 2010-05-02
If the network manager isn't crashing check these, should be set as:

/etc/NetworkManager/nm-system-settings.conf

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

-------
and

/var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

---

### Post by ivan.tg on 2010-05-03
Hi chaosgrimm,

Thank you for the solution! I had exactly this problem. I have no idea what made this variables turn 'false' all the sudden. I've been using Kubuntu 10.04 for some days now and networking was just fine so i was not messing around with these settings.
Although i did change some power saving setting before the 'disabled' networking problem appeared i doubt it has anything to do with it. Looking at other people's posts it seems to appear randomly.

Cheers
ivan

---

### Post by spikyjt on 2010-05-06
Thanks for this. It happened on my boss's laptop so most embarrassing! No idea why, but NetworkingEnabled was set to false.

---

### Post by agniruc on 2010-05-08
> **chaosgrimm said:**
> If the network manager isn't crashing check these, should be set as:

/etc/NetworkManager/nm-system-settings.conf

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

-------
and

/var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

Thanks for posting this, chaosgrimm! Saved my day!

All happened when I tried to put my laptop on 'sleep mode'. For some reason it did not sleep and stopped working (no response at all, even the SysReq + R, E, I, S, U, B trick wasn't working).

After I reset it, the networkmanager seemed dead. 'dhclient' was working, though. Then I found this post and discovered that all the options in those configuration files were set to 'false'!  #-o

---

### Post by epavlica on 2010-05-09
Thanks for the fix, chaosgrimm!

This has happened to me on two separate systems now; it may be a bug in 10.04 LTS. Both times it occurred the system failed to go into the sleep state, froze, and upon restart had these networking flags changed to "false". 

Has anyone submitted a bug report for this yet?

---

### Post by ewka on 2010-05-17
Exactly the same problem on a Dell.  Not sure how to submit a bug report, but it should be done. Hopefully someone more experienced will do it. 

Thanks for the help chaosgrimm!

---

### Post by paulbarratt on 2010-05-18
Hi, I think Agniruc and Epavlica are on the right track: it's something connected with the power management failing to go into or resume from standby, and the network manager being left in a disabled state.

I recently upgraded to Kubuntu 10.04 from 9.10 (with previous 9.04 etc previously on the same system - probably not a good idea!) - so not a clean system.

My laptop is a Sony Vaio VGN-FW11E and the standby/resume has never worked properly - it just hangs on resume and needs a power-off to get it running again.  Last night, since I had not tried the standby/resume with 10.04, I tried it to see if it was working and got the same hang as usual. The following morning I got the same situation the the previous posters and the fix also worked for me.

Thanks for your help.

---

### Post by elivs on 2010-05-20
The same thing happened for me on an HP 6930p laptop with kubuntu 10.04.

The settings got switched to "false" during a sleep / hibernation mode.

I can't find this in the bug tracking system, but I'm not familiar with submitting bugs to ubuntu. Has anyone submitted it yet?

elivs

---

### Post by Bucky Ball on 2010-05-23
Are these instructions for 10.04? Using 8.04 and don't have any of these files to check or change.

Should I create them and add the changes?

---

### Post by dughutch on 2010-05-26
Bump. Similar issue on Dell E6500 laptop. In the NetworkManager.state file WirelessEnabled=false happens as soon as I do service network-manager start.

---

### Post by freecates on 2010-06-02
Thanks a lot chaosgrimm.
After going back from a sleeping session on my Dell Latitude E4200, the Knetworkmanager said: "unmanaged". Both files:

[I]/etc/NetworkManager/nm-system-settings.conf
/var/lib/NetworkManager/NetworkManager.state[/I]

had turned to "false" on

[I][ifupdown]
managed=false[/I]

[I][main]
NetworkingEnabled=false[/I]

Again thanks a lot chaosgrimm. You've saved my day ;-)

---

### Post by timrichardson on 2010-07-09
Here is my fix (this bug is reported in launchpad but it's marked low priority)
in directory /etc/pm/sleep.d as root (or with sudo) 
create a file called 11_clearNetwork

```
#!/bin/bash
case "$1" in
    hibernate|suspend)
        #ACTION BEFORE SUSPEND/HIBERNATE
	rm /var/run/network/ifstate
	logger "deleted ifstate when suspending or hibernating"
        ;;
    thaw|resume)
        #ACTION AFTER RESUME
	rm /var/run/network/ifstate
        service network-manager stop
 	service network-manager start		
 	logger "deleted ifstate and restarted network manager"
        ;;
    *)
        ;;
esac
exit $?

```

---

### Post by krezkey on 2010-07-11
> **chaosgrimm said:**
> If the network manager isn't crashing check these, should be set as:

/etc/NetworkManager/nm-system-settings.conf

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

-------
and

/var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
Thanks for this very helpful info,but I can't seen to edit the files you have listed. what commands does a newbee like me need to know to correct these in bash and get things working again. Thanks for the help in advance.

---

### Post by spiky001 on 2010-07-11
hi open termial type this in
```
gedit /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by guymcarthur on 2010-07-11
Same problem on two different laptops (both Dell). This bug should be marked very high priority!

---

### Post by mindaslab on 2010-07-11
I don't know why Ubuntu guys have marked it low. This one is really serious! I became mad when I couldn't connect to Internet. This what makes Windows and Mac prevail over Ubuntu

---

### Post by LifeTheHound on 2010-07-23
> **mindaslab said:**
> I don't know why Ubuntu guys have marked it low. This one is really serious! I became mad when I couldn't connect to Internet. This what makes Windows and Mac prevail over Ubuntu

Totally agree. There's really no excuse for this level of utter incompetence.

1. Critical problem, occurred in multiple versions of Ubuntu and Kubuntu on multiple laptops.
2. Shows how ridiculously buggy things are right under the surface. It took a while to rear its ugly head, but once it did, the system was toast. So much for Linux "system security" if users have to get rid of the damn thing to use their computer again.
3. "Low priority" status on something as critical as not being able to connect to the internet is easily a display of incompetence.

I'm using Vista now. I couldn't even connect to the internet in linux to get on these forums because of this insanely critical ***"low priority"*** issue. Vista is slow, buggy, requires antivirus software, costs money, and countless other annoyances, but never a lick of problems as critical as this and many other critical "system nukes" that unfortunately comprise the mine-field of the "desktop Linux experience." There's a reason many people aren't enthusiastic about using linux -- you have to be a terminal wizard to painstakingly work around all the critical glitches. I don't want to believe that in windows this never happens because the code is particularly well written, but having the option to click on the network manager and "Diagnose and repair" is critical. Instead of screwing around with making graphics pretty and cutting "boot time," make the dang thing stable and error resilient. Even if it gets less than half of the errors of a Windows machine, Windows can fix them all somewhat easily or intuitively, and there's real recovery modes. There's no excuse for this. 

The commandline tools are ridiculously fragmented, too. There's no one networking commandline. I screwed around with "ifconfig" for hours (and "iwconfig") but didn't know there was a (ridiculous) "ifup" program too, along with countless others which, quite frankly, should obviously be merged into a single intuitive program and then given a flippin' GUI.

---

### Post by alpreston on 2010-07-28
I have a similar problem on a desktop system with a wired ethernet connection - eth0 is disabled on startup. A quick check of Chaosgrimm's suggestions revealed that the first file ( /etc/NetworkManager/nm-system-settings.conf ) wasn't present on my system, and in the second file ( /var/lib/NetworkManager/NetworkManager.state ) the NetworkingEnabled parameter was set to false. I can only conclude that was reset by an recent update as until a couple of weeks ago, everything worked fine.  I'l give your settings a try...

---

### Post by walter_jnr on 2010-08-01
> **agniruc said:**
> Thanks for posting this, chaosgrimm! Saved my day!

All happened when I tried to put my laptop on 'sleep mode'. For some reason it did not sleep and stopped working (no response at all, even the SysReq + R, E, I, S, U, B trick wasn't working).

After I reset it, the networkmanager seemed dead. 'dhclient' was working, though. Then I found this post and discovered that all the options in those configuration files were set to 'false'!  #-o

This happened to me just now. I guess sleep mode is broken. Thank the Gods I had a laptop here so I could Google the answer. I had to reboot after changing the file though. Logout didn't fix.

---

### Post by andreselsuave on 2010-08-01
> **walter_jnr said:**
> This happened to me just now. I guess sleep mode is broken. Thank the Gods I had a laptop here so I could Google the answer. I had to reboot after changing the file though. Logout didn't fix.

You don't need to reboot, just restart the network manager service:

```
sudo /etc/init.d/network-manager restart
```

I made a small script to repair network, might be useful for you. You just make a file with the following code:

```
sudo rm /var/lib/NetworkManager/NetworkManager.state 
sudo /etc/init.d/network-manager restart

```

Call the file network_repair and give it execution permissions:
```
chmod +x network_repair
```

Then you can repair the network just typing ./network_repair 

By the way, can you give the link to the launchpad bug please?

And now, a message to LifeTheHound:
utter incompetence?
Don't be a hater. Are you aware that linux developers are many times volunteers that in their free time they program stuff for other people? That's what made linux the incredible computing experience that it is right now. It's not only about security, it's about the right to access the code you are running, the freedom to do with your system whatever you want and the possibility to participate in a community of people making this possible. I think you should think about it and be more grateful.

---

### Post by walter_jnr on 2010-08-02
> **andreselsuave said:**
> You don't need to reboot, just restart the network manager service:

I tried doing that but it didn't seem to work. Of course I'm still pretty new to Linux so I was most likely doing something wrong. 

> I made a small script to repair network, might be useful for you.

Thanks for going to the effort of helping me but, to be honest, at this point I'd rather stay away from scripts just so I can learn as much as I can about all the various command line functions. I don't think I'll learn as much just running scripts that other people have written for me. The effort is definitely appreciated though so thanks.


> By the way, can you give the link to the launchpad bug please?

[https://bugs.launchpad.net/ubuntu/+bug/555571](https://bugs.launchpad.net/ubuntu/+bug/555571)

This is where I got the idea to edit the NetworkManager.state. I'm not sure exactly what this bug is caused by (for me it was waking up after suspending to RAM) or whether it is related to my problem but it helped.

---

### Post by andreselsuave on 2010-08-02
Nice attitude Walter_jnr!

I also like to always learn somethiing in the way. But I think in this case, rebooting is the way you wont learn something. I am not a linux expert, but I think I can help you understand how this works, since you like to learn:

There is something called daemons in linux, which is similar to services in MS windows. They are programms that normaly start when you boot up and run in the background waiting for you to do something to produce some kind of output. For example:

there is a bluetooth daemon waiting for you to connect with a mobile phone to make the proper connection. Other daemons make many different tasks. If you want to see which programs you are currently running, you can do it in the console:
1)Interactively (like a task manager):
```
top
```
2)Statically (like a process list):
```
ps -aux
```
-aux is to tell ps to give you all the programs instead of only your user's. you can learn even more here:
```
man ps
```

So, arriving to the point... There is a network manager daemon, running in a background and managing your connections, to ease the task of connecting to the internet. Because of this bug related to sleep to RAM, or something like that, it stays disabled, so to restart it, you can use a program stored in /etc/init.d  where they are more daemon-controlling programs, by doing (you need superuser privileges)
```
sudo /etc/init.d/network-manager restart
```
There is a more modern way to do this, im not sure but I think its something like 
```
sudo services network-manager restart
```

Hope you learnt something today :p and keep on with that attitude ;)!
Andres.

---

### Post by kingttx on 2010-08-03
At work so I haven't tried this yet with my home laptop. Using an older Alienware laptop, it has this very same problem with 10.04 after booting but not every single time. 9.10 had no such issue. I didn't know how to re-enable the network, even using 'service networking restart' didn't work. Booting into GNOME and using the nm applet to re-enable the network did work. After that, I could log out then back into KDE and have network access. 

Without doing this, there was no network icon in any KDE panel, and going through the network config GUI wouldn't fix it either. 

Here's hoping this is cleared up. Thanks for the workaround for the interim!

---

### Post by se7ensamurai on 2011-03-12
> **chaosgrimm said:**
> If the network manager isn't crashing check these, should be set as:

/etc/NetworkManager/nm-system-settings.conf

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

-------
and

/var/lib/NetworkManager/NetworkManager.state



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

Hola, this almost worked for me, but my Network Manager was still unavailable. However I did find this, which worked perfectly in conjuntion with the above. Thanks!

[http://linux-software-news-tutorials.blogspot.com/2010/06/kubuntu-1004disabled-](http://linux-software-news-tutorials.blogspot.com/2010/06/kubuntu-1004disabled-)
network.html?m=1

---

### Post by ss2pheonix on 2011-05-12
happened to me when i was in a rush so i forced shutdown by holding down power. that was a mistake:)

---

### Post by homayonifar on 2011-06-22
The same problem on Kubuntu 10 and Dell latitude D360. After it went on RAM going out of battery the next restart made all keys equal to false ! After editing them and setiing to true, the network runs normal as before. Thanks for the solution.

Regards
M. H.

---

### Post by black87 on 2012-02-24
> **agniruc said:**
> Thanks for posting this, chaosgrimm! Saved my day!

**All happened when I tried to put my laptop on 'sleep mode'.** For some reason it did not sleep and stopped working (no response at all, even the SysReq + R, E, I, S, U, B trick wasn't working).

After I reset it, the networkmanager seemed dead. 'dhclient' was working, though. Then I found this post and discovered that all the options in those configuration files were set to 'false'!  #-o

The same exact thing happened :C

---

