---
title: "Conky hddtemp works only intermittantly"
date: 2012-05-05
forum: General Help
---

### Post by strask on 2012-05-05
This is a minor, but annoying, problem. I have the following line in my .conkyrc```
${voffset 4}${font DroidSansMono:size=8}${offset 5}${color3}HDD  : ${alignr}${hddtemp /dev/sdb}
```Then I have this code in my .conky/bargraph_small.lua file (this is part of VinDSL's conky setup):```

            {    --[ Graph for SDB Temp ]--
                        name="hddtemp",
            arg="/dev/sdb",
            max=195,
            alarm=82,
            alarm_colour={0xFF0000,0.72},
            bg_colour={0xFFFFFF,0.25},
            fg_colour={0x00FF00,0.55},
            mid_colour={{0.45,0xFFFF00,0.70}},
            x=55,y=804,
            blocks=55,
            space=1,
            height=2,width=5,
            angle=90,
            smooth=true
            },

```Ok, so this produces a line that says "HDD  :" at the beginning, then has a bar graph of the temperature, then has the temperature in text after the bargraph.

The problem is that it only works some of the time. If I have my conky update interval set to 2 seconds, it seems to work for one cycle, then fail for two cycles, then work for one, then fail for two, etc. When it fails it says "N/A" for the text and the bargraph is drawn as if the temperature were zero. I've attached two screenshots showing the working and not-working version, look near bottom for the temperature section.

I've tried testing the hddtemp daemon with ```
nc localhost 7634
``` and that always works, no matter how frequently or quickly I try it. And the output is always in the same format, I'm not seeing anything that would cause conky to have trouble parsing it.

I'm completely baffled... any insight would be appreciated.

Edit: This is ubuntu, not lubuntu... any way to change the thread prefix?

---

### Post by pqwoerituytrueiwoq on 2012-05-05
do you have a firewall blocking the port?
if not probally a permissiion issue
can you run hddtemp from a terminal or do you get something like this:

Command 'hddtemp' is available in '/usr/sbin/hddtemp'
The command could not be located because '/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
hddtemp: command not found

this should get you the temp yuo may be able to pull something off messing with "name" and "args" in the .lua file
```
nc localhost 7634 | sed 's/|/\n/g' | tail -2 | head -1
```edit:
```
nc localhost 7634 | sed 's/|//;s/|/\: /;s/|/\: /;s/|/\°/;s/|//'
```this one will put a line break after the text output also includes output of hddtemp to compare it to```
nc localhost 7634 | sed 's/|//;s/|/\: /;s/|/\: /;s/|/\°/;s/|/\n/';sudo hddtemp /dev/sda
/dev/sda: WDC WD3200BEKT-00KA9T0: 43°C
/dev/sda: WDC WD3200BEKT-00KA9T0: 43°C
```

---

### Post by strask on 2012-05-05
> **pqwoerituytrueiwoq said:**
> do you have a firewall blocking the port?
Nope, like I said it works when I do nc from the command line.

> if not probally a permissiion issue
can you run hddtemp from a terminal or do you get something like this:

Command 'hddtemp' is available in '/usr/sbin/hddtemp'
The command could not be located because '/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
hddtemp: command not found
I wish it were that simple. Conky isn't calling the hddtemp command from /usr/sbin, it's making a network connection to port 7634 on localhost and reading the temperature from there. Also if it were some kind of permission issue I would expect it to fail all the time, not just sometimes.

---

### Post by pqwoerituytrueiwoq on 2012-05-05
both me and vindsl have had issues with 1.8.1-6 try using 1.8.1-5
[https://launchpad.net/ubuntu/precise/amd64/conky-all/1.8.1-5](https://launchpad.net/ubuntu/precise/amd64/conky-all/1.8.1-5)

if that fixes it this will stop it from updating you should also lock it in synaptic
```
echo "conky-all hold" | dpkg --set-selections
```

---

### Post by Sector11 on 2013-02-17
> **pqwoerituytrueiwoq said:**
> both me and vindsl have had issues with 1.8.1-6 try using 1.8.1-5
[https://launchpad.net/ubuntu/precise/amd64/conky-all/1.8.1-5](https://launchpad.net/ubuntu/precise/amd64/conky-all/1.8.1-5)

if that fixes it this will stop it from updating you should also lock it in synaptic
```
echo "conky-all hold" | dpkg --set-selections
```

I know this is old but if still needed try this:

> By Crinos512:

To recongigure hddtemp
sudo dpkg-reconfigure hddtemp
Three questions, and answer:
1. YES
2. Enter
3. NO

```
${execi 5 hddtemp -n /dev/sda}
```
will now give you just the temp:

```
 sector11 @ sector11
 17 Feb 13 | 12:27:25 ~
         $ hddtemp -n /dev/sda
39
 sector11 @ sector11
 17 Feb 13 | 12:27:28 ~
         $ hddtemp -n -uF /dev/sda
102
 sector11 @ sector11
 17 Feb 13 | 12:27:36 ~
         $ hddtemp -n -uC /dev/sda
39
 sector11 @ sector11
 17 Feb 13 | 12:27:46 ~
         $ 
```

---

