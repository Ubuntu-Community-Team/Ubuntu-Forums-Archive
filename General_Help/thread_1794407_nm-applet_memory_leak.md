---
title: "nm-applet memory leak"
date: 2011-07-01
forum: General Help
---

### Post by insert_name_here on 2011-07-01
My nm-applet has a super mega memory leak. It regularly uses >200mb of memory. I'm on Ubuntu 11.04 on a Thinkpad T60 with an Atheros Communications Inc. AR5212 802.11abg NIC (rev 01) using the ath5k module. 

Any ideas, y'all?

---

### Post by andrewthomas on 2011-07-01
Have you filed a bug yet?

---

### Post by insert_name_here on 2011-07-01
I haven't. I'm a python developer; since I live in a land of automatic garbage collection, I don't know how to deal with memory leaks... :P

I'd be happy to do so if you could guide me through what information I should provide besides my machine specs and the amount of memory nm-applet is using.

---

### Post by mc4man on 2011-07-01
It may prove interesting to see this before filing a bug
```
ps aux |grep nm-applet
```

---

### Post by insert_name_here on 2011-07-01
```
~$ ps aux | grep nm-applet
<username> 15089  0.1  7.7 279724 160220 ?       SLl  Jun30   1:59 nm-applet
<username> 19538  0.0  0.0   4156   848 pts/2    S+   13:41   0:00 grep nm-applet

```

I restarted nm-applet at some point last night (probably 16 hours ago) and it's already at 160mB of RAM. (or is it 280mB?)

Thanks for the help!

---

### Post by mc4man on 2011-07-01
> **insert_name_here said:**
> ```
~$ ps aux | grep nm-applet
<username> 15089  0.1  7.7 [COLOR="Blue"]279724[/COLOR] [COLOR="Red"]160220[/COLOR] ?       SLl  Jun30   1:59 nm-applet
<username> 19538  0.0  0.0   4156   848 pts/2    S+   13:41   0:00 grep nm-applet

```

I restarted nm-applet at some point last night (probably 16 hours ago) and it's already at 160mB of RAM. (or is it 280mB?)

Thanks for the help!
The red is actual (RSS), the blue doesn't much matter, the red is quite high as compared to here (16M

To file a bug you'd go  - 
```
ubuntu-bug network-manager-gnome
```
That should include what's needed, you will be asked about inc. some add. info, your choice there
(if inc. the add. info the bug will likely be filed as a 'private' bug, generally better to fle as public though not required.

You could maybe inc. a pidstat log of the process, or do to see for yourself how the mem leaks over time.
To do that
```
sudo apt-get install sysstat
```

Then from fresh boot get the pid on nm-applet from command in previous post, then something like this where XXXX = the pid, the blue is min.'s between reports and the red is the number of reports taken
The pid will change from boot to boot, for reference in  above post it was 15089
```
pidstat -r -p XXXX [COLOR="Blue"]180[/COLOR]  [COLOR="Red"]60[/COLOR] >> nm-applet.log

```
Then just min. the terminal and go about your normal routine, ect.
(the red and blue can be adjusted to suit

It may be possible to do a valgrind on nm-applet, that would be best but for that you'd need to read up on..

---

### Post by insert_name_here on 2011-07-01
this looks to be the same bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/780602](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/780602)

There's a similar one that was alleged to have been resolved in 0.8.4 in Natty, which is what I have (and where it clearly hasn't been fixed).

---

### Post by mc4man on 2011-07-01
That looks like it, the question would be when or even if it gets fixed in 11.04
(at some point the odds of seeing a fix start diminishing significantly


========================================================================
If you can't live with the occasional restart of nm-applet - you could try a different manager

As a test I installed wicd here, then after getting it up removed thenetwork-manager and network-manager-gnome packages
Seems to work fine, all I care about for an manager is connect to my router and stay connected.

If inclined to test I'd suggest first getting the current network-manager and network-manager-gnome packages so you can re-install them if need be. Available from packages.ubuntu.com or just re-install them, then you'll find them in /var/cache/apt/archives. 

Making sure wicd is working before removing the mn packages isn't unwise, it should connect automatically from a restart

In the case of wicd it doesn't come as a application indicator, (probably a good thing), so you'd want to add it to the systray whitelist
This can be done from gsettings or from dconf-editor, shown in screen.
(I've removed some defaults and added some, additions are simply this format added to end, ex. wicd
```
,'wicd'
```

or gsettings
first get your current
```
gsettings get com.canonical.Unity.Panel  systray-whitelist 

```
Then use that to set back edited
```
gsettings set com.canonical.Unity.Panel  systray-whitelist "[what was returned plus ,'wicd' in here]"
```

Ex.
> ~$ gsettings get com.canonical.Unity.Panel  systray-whitelist
['JavaEmbeddedFrame', 'vlc', 'audacious']

```
~$ gsettings set com.canonical.Unity.Panel  systray-whitelist "['JavaEmbeddedFrame', 'vlc', 'audacious', 'wicd']"
```

---

### Post by insert_name_here on 2011-07-01
I've tried wicd in the past and been less than impressed; what the hell, I'll give it a shot again later tonight.

Thanks for the tip!

-- 

If that doesn't work, I'll probably just write a cronjob to kill and restart nm-applet every 8 hours or so. (Or alternatively, to check the memory usage every hour and kill it if it's over 100mb or something.)

If that's what I do, I'll post it here for anyone else with this problem.

--

Interestingly, take a look at this pidstat log: the break at 4:13-4:28pm and 5:19-5:38pm are when I switched access points from my apartment to a coffeeshop and then from the coffeeshop to my apartment. The encryption was the same (WEP), but there was a profile saved for my apartment's wifi but not for the coffeeshop's. Do you think the profile could be the problem? 

```
03:43:08 PM       PID  minflt/s  majflt/s     VSZ    RSS   %MEM  Command
03:46:08 PM      1754      0.00      0.00  137396  19028   0.92  nm-applet
03:49:08 PM      1754      0.27      0.00  137660  19260   0.94  nm-applet
03:52:08 PM      1754      0.34      0.00  137660  19524   0.95  nm-applet
03:55:08 PM      1754      0.56      0.00  137792  19788   0.96  nm-applet
03:58:08 PM      1754      0.24      0.00  137792  20052   0.97  nm-applet
04:01:08 PM      1754      0.57      0.00  138948  20340   0.99  nm-applet
04:04:08 PM      1754      0.40      0.00  139212  20600   1.00  nm-applet
04:07:08 PM      1754      0.74      0.00  139736  21140   1.03  nm-applet
04:10:08 PM      1754      0.38      0.00  139996  21536   1.05  nm-applet
04:13:08 PM      1754      0.74      0.00  140640  22000   1.07  nm-applet
04:28:23 PM      1754      1.00      0.00  167936  25488   1.24  nm-applet
04:31:23 PM      1754      0.01      0.00  167936  25488   1.24  nm-applet
04:34:23 PM      1754      0.00      0.00  167936  25488   1.24  nm-applet
04:37:23 PM      1754      0.38      0.00  167996  25740   1.25  nm-applet
04:40:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
04:43:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
04:46:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
04:49:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
04:52:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
04:55:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
04:58:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
05:01:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
05:04:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
05:07:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
05:10:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
05:13:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
05:16:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
05:19:23 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
05:38:00 PM      1754      0.00      0.00  167996  25740   1.25  nm-applet
05:41:00 PM      1754      1.33      0.00  169028  26644   1.29  nm-applet
05:44:00 PM      1754      0.19      0.00  169160  26644   1.29  nm-applet
05:47:00 PM      1754      0.15      0.00  169292  26904   1.31  nm-applet
05:50:00 PM      1754      0.38      0.00  169556  27168   1.32  nm-applet
05:53:00 PM      1754      0.34      0.00  169556  27432   1.33  nm-applet
05:56:00 PM      1754      0.69      0.00  169952  27696   1.34  nm-applet
05:59:00 PM      1754      0.28      0.00  170212  27972   1.36  nm-applet
06:02:00 PM      1754      0.59      0.00  170608  28496   1.38  nm-applet
```

---

### Post by insert_name_here on 2011-07-07
Because I'm lazy, I just added

<something that didn't work at all>

to my crontab.

---

