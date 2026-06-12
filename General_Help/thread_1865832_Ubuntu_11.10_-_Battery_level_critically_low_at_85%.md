---
title: "Ubuntu 11.10 - Battery level critically low at 85%?"
date: 2011-10-20
forum: General Help
---

### Post by linuxuser12345 on 2011-10-20
I am running Ubuntu 11.10 on an HP Mini 110 netbook, and I only use my computer for around 30 minutes off the charger, and it then tells me the battery level is critically low. I take a look at the percentage, and it shows me 85%. Also, the battery icon doesn't show the percentage in picture form. I literally have to click on the picture to see the %. Maybe there is a driver issue?

What is happening and how can I fix this? How do I report this to Canonical and the developers?

---

### Post by techvish81 on 2011-10-20
it will take time to show real values, it depends on cpu usage and several other factors, mine is showing real after two days

---

### Post by linuxuser12345 on 2011-10-20
But thirty minutes? Come on! The battery is not going to be drained in 30 minutes! I had a problem with previous Ubuntu versions reading the battery right, too. In 11.04, the percentage would show (though I doubt it was accurate), and no remaining time would show up!

---

### Post by matt_symes on 2011-10-20
Hi

Not sure if i can help here as it sounds like a bug but this may glean some information.

Question: After you get the critical power message does it suspend, hibernate or shutdown if you don't plug in the power adaptor ?

Anyway, with the adaptor plugged in, open a terminal (terminal 1) and type

```
sudo apt-get install acpi
```

Enter your password. It will not be echoed to the screen.

Then type

 ```
watch -n 5 acpi -b
```

Leave this running.

Copy and paste  below into another terminal (terminal 2) but don't hit the  enter key. We want these readings when you get the critical battery  message.

```
cat /sys/class/power_supply/*/present && 
cat /sys/class/power_supply/*/charge_now &&
cat /sys/class/power_supply/*/charge_full &&
cat /sys/class/power_supply/*/current_now &&
cat /sys/class/power_supply/*/voltage_now
```

Unplug your adaptor and continue working. When you get the critical  batter message press ctrl and c in terminal 1 and hit the enter key in terminal 2.

Then quickly plug in your power adaptor in case it decides to shut down.

Post the results back here.

Kind regards

---

### Post by rihardius on 2011-10-21
Hello [WARNING: I'm new in forums and just a bit new to Ubuntu]!

So, I had this bug - I unplugged the cord for about 20 seconds and it poped up that message about critical battery state AND computer went sleep.
After that happened I decided to search for help and got here, and did everything that was in previous message. Here's the result:

```
rihardius@ubuntu:~$ cat /sys/class/power_supply/*/present && 
> cat /sys/class/power_supply/*/charge_now &&
> cat /sys/class/power_supply/*/charge_full &&
> cat /sys/class/power_supply/*/current_now &&
> cat /sys/class/power_supply/*/voltage_now
1
3706000
3924000
0
11931000
```
[Oh crap, I might have done instructions wrong! And I waited for message about 14 minutes and it didn't pop up again...]
My system is Compaq Presario CQ50-110EN

---

### Post by ironcrush on 2011-10-22
Having similiar problem with my Toshiba satellite laptop. Battery State Shows Critical on Full Charge then computer goes straight hibernation. My laptop running perfect on battery on windows, used to ran ok on previous ubuntu as well.

Every 5.0s: acpi -b                                     Sun Oct 23 01:59:47 2011

Battery 0: Unknown, 100%




cat /sys/class/power_supply/*/present && 
> cat /sys/class/power_supply/*/charge_now &&
> cat /sys/class/power_supply/*/charge_full &&
> cat /sys/class/power_supply/*/current_now &&
> cat /sys/class/power_supply/*/voltage_now
1
3920000
4000000
0
14800000

Any help with that please?

---

### Post by linuxuser12345 on 2011-10-22
```
jessica@HP-mini:~$ cat /sys/class/power_supply/*/present && 
> cat /sys/class/power_supply/*/charge_now &&
> cat /sys/class/power_supply/*/charge_full &&
> cat /sys/class/power_supply/*/current_now &&
> cat /sys/class/power_supply/*/voltage_now
1
1054000
1505000
cat: /sys/class/power_supply/BAT1/current_now: No such device
jessica@HP-mini:~$ 


```

---

### Post by matt_symes on 2011-10-25
Hi

> **linuxuser12345 said:**
> ```
jessica@HP-mini:~$ cat /sys/class/power_supply/*/present && 
> cat /sys/class/power_supply/*/charge_now &&
> cat /sys/class/power_supply/*/charge_full &&
> cat /sys/class/power_supply/*/current_now &&
> cat /sys/class/power_supply/*/voltage_now
1
1054000
1505000
cat: /sys/class/power_supply/BAT1/current_now: No such device
jessica@HP-mini:~$ 


```

That looks alright. You have charge in the battery from what i can see. Let's check upower.

When the battery goes to critical open a terminal and type (or have typed and hit enter)

```
upower -d | grep low-battery && cat /sys/class/power_supply/*/charge_now
```Plug power back in and post results back here.

Kind regards

---

### Post by f_padia on 2011-10-26
I also get this message on a HP Pavilion dv5 laptop. However, I only get the 'battery critically low' message only after resuming from suspend. If I charge the laptop while using it then take it off charge the message does not appear. So it sounds like its something to do with the resume.

---

### Post by matt_symes on 2011-10-26
Hi

I have occasionally had this issue in my 11.10 install. However, it happens on mine because of a delicate power cable. It is also incredibly inconsistent and difficult to replicate on my laptop (does not happen very often at all; 2 - 3 times).

I know my battery has charge so the problem is not there. It leaves no trace in the logs for some reason.

Therefore, i am hoping that someone who can consistently replicate this issue can shed some light as to what is happening on my laptop as well - after all the symptoms, if not the causes, are the same.

It is quite possible there is more than one issue here though.

Kind regards

---

### Post by gesquive on 2011-10-27
My Dell Latitude E6510 does this as well. I only get that message after resuming from a suspend. One time I noticed that even though my laptop only has one battery, after resuming from suspend, the system tray battery icon menu shows that I have two batteries, one at X% (usually close to full) and one at 0%. I'm wondering if that 0% battery is triggering the critically low battery message.

Don't know what else to do from here at the moment.

---

### Post by sirzeke on 2011-10-27
I have the same issue. I have a Toshiba A205 laptop. One thing that I have noticed, when I plug in the power and fully charge it, when I pull the plug out it, I get the error, even though it charged for more than 35 minutes.
I get an option, press ok to shut down or plug it back in and press cancel.
I even get the error when I unplug before 100% charged.
I am not sure what is going on but, it can be a bit annoying.

---

### Post by linuxuser12345 on 2011-10-27
I switched back to 11.04. Even though it still doesn't read the battery 100% correctly with all the numbers, it's still much better and less annoying than what 11.10 does! lol

---

### Post by gesquive on 2011-10-28
From fix/workaround found in this thread [here]("http://ubuntuforums.org/showpost.php?p=11378614&postcount=5"):

For 11.04 and older just run:

```
gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false
```

For 11.10 run:

```
gsettings set org.gnome.settings-daemon.plugins.power 'use-time-for-policy' 'false'
```

This worked for me. It doesn't fix my underlying issue, but it keeps my laptop from continuously suspending.

---

### Post by linuxuser12345 on 2011-10-28
I have been saying this for a while now, and I think word needs to spread out:

Every time a new Ubuntu release comes out to the public, it is just as bad as Vista was. There are errors everywhere, and many computers running the new releases have frequent crashes. Even installing supposedly "approved" programs through the Software Center can screw up your system in numerous ways! Canonical needs to get in the game by allowing longer beta testing to be done before actual final release. This can be done by extending the release cycle from every six months to every, say, seven, eight, or nine months. Some have even recommended a "rolling" release cycle. This will allow Canonical and the community to perform beta testing on Ubuntu for a much longer time, allowing errors to be cleaned up and fixed before release.

---

### Post by tpprynn on 2011-10-28
Yep, I'll second that - one edition a year is absolutely plenty.

This is not any longer unlikely though - apparently 12.04 will now have five years' support, presumably this is the new deal for LTS releases, so maybe they will think of adjusting the lifespan of the regular editions. In a way frequent editions are an advert for Ubuntu, keeping it in the public eye, but as often as not the advert is potentially a bad one.

I'll be staying with 12.04 until 2017. I haven't strongly entertained going to Fedora or elsewhere because with Ubuntu the need to upgrade is less hassle and less frequent, but could be better.

*One edition a year is plenty.*

---

### Post by BazookaAce on 2011-11-15
Same here! I get "critical low" at 100% and then it suspends, so my laptop is now stationary. Compaq Presario CQ62.

---

### Post by t4thfavor on 2011-11-27
The "gsettings set org.gnome.settings-daemon.plugins.power 'use-time-for-policy' 'false'" workaround stopped the suspend issue, but it still tells me I have 0:02 left on my battery.

I purposely waited until 11.10 came out, and was out for a month in order to update, and now it has me seriously considering Debian. I have a few PPC machines, and they all tend to run nicely with Debian 6.0.

I think I am done with updates if things like this continue to happen.

---

### Post by gesquive on 2011-11-27
Hey, my issue can be found here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852406](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852406)

It looks like a fix has been patched and is available. It hasn't been released to everyone though.

---

### Post by alcatille on 2012-01-05
Thanks Matt. This fix worked for me in the sense that I get my indicator after I complete the process. I, however, have to do it every single time I log in and I do not know why the system is not reading the battery info.

---

### Post by craigx on 2012-03-21
Thanks - this worked for me. My laptop gave a critical low battery alarm and then closed everything down even if I reconnected the power immediately. Now if behaves itself.

---

