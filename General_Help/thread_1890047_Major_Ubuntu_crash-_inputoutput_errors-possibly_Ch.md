---
title: "Major Ubuntu crash- input/output errors-possibly Chrome's fault?"
date: 2011-12-02
forum: General Help
---

### Post by maaarg on 2011-12-02
This is going to be something of a frustrating post-- Ubuntu is fubar right now, so I'm posting from my Windows partition. A lot of information could be hard to find.

Earlier today, while browsing Chrome, I got a timeout error, which (considering my wireless) seemed innocent-- until the other programs I was running (emacs, umlet) stopped working as well. 

From terminal, I got an i/o error dev sda
From the gui I would get a popup reporting an Input/Output error

The entire system froze-- couldn't shut down by normal methods, so I had to force it. Rebooted in recovery mode, and everything seemed fine. Rebooted in normal mode, and everything seemed fine again. Went to Disk Utility and found no bad sectors; checked the filesystem and everything was reported in working order. 

While I usually use Chromium, I started Firefox to try a quick backup of my most necessary files. Worked well for a while, then froze up. Tried starting Chromium at this point (probably a bad idea) and it was back to Input/Output errors when I tried to run anything (emacs, for example).

The only information I've been able to find on i/o errors is either due to hardware failure or a damaged filesystem, but as far as I can tell I've got neither. Any suggestions?

Running Maverick, but I've forgotten the exact version and I'm too afraid to switch back to the other partition :\

---

### Post by pretty_whistle on 2011-12-02
> **maaarg said:**
> This is going to be something of a frustrating post-- Ubuntu is fubar right now, so I'm posting from my Windows partition. A lot of information could be hard to find.

Earlier today, while browsing Chrome, I got a timeout error, which (considering my wireless) seemed innocent-- until the other programs I was running (emacs, umlet) stopped working as well. 

From terminal, I got an i/o error dev sda
From the gui I would get a popup reporting an Input/Output error

The entire system froze-- couldn't shut down by normal methods, so I had to force it. Rebooted in recovery mode, and everything seemed fine. Rebooted in normal mode, and everything seemed fine again. Went to Disk Utility and found no bad sectors; checked the filesystem and everything was reported in working order. 

While I usually use Chromium, I started Firefox to try a quick backup of my most necessary files. Worked well for a while, then froze up. Tried starting Chromium at this point (probably a bad idea) and it was back to Input/Output errors when I tried to run anything (emacs, for example).

The only information I've been able to find on i/o errors is either due to hardware failure or a damaged filesystem, but as far as I can tell I've got neither. Any suggestions?

Running Maverick, but I've forgotten the exact version and I'm too afraid to switch back to the other partition :\
I had Chrome Chromium freeze up my computer so I had to dump them off.  The freezing quit so apparently the browsers were causing it for whatever reason.

---

### Post by oldtimer7777 on 2011-12-02
That happens sometimes. Sounds like data corruption, perhaps if you have done a recent update on your system over the wifi with a really poor signal. I usually avoid this with a hardwired connection at all times, but that is just my own preference.  If you have a really unreliable wifi router, it may be time to check the logs to see if it having any issues. And this is assuming you know what you are talking about when you say your hardware "appears to be ok".. There is no real way to know if you are having an  io controller issue on the MB.  None of this is like fine wine that gets better with age. 

> **maaarg said:**
> This is going to be something of a frustrating post-- Ubuntu is fubar right now, so I'm posting from my Windows partition. A lot of information could be hard to find.

Earlier today, while browsing Chrome, I got a timeout error, which (considering my wireless) seemed innocent-- until the other programs I was running (emacs, umlet) stopped working as well. 

From terminal, I got an i/o error dev sda
From the gui I would get a popup reporting an Input/Output error

The entire system froze-- couldn't shut down by normal methods, so I had to force it. Rebooted in recovery mode, and everything seemed fine. Rebooted in normal mode, and everything seemed fine again. Went to Disk Utility and found no bad sectors; checked the filesystem and everything was reported in working order. 

While I usually use Chromium, I started Firefox to try a quick backup of my most necessary files. Worked well for a while, then froze up. Tried starting Chromium at this point (probably a bad idea) and it was back to Input/Output errors when I tried to run anything (emacs, for example).

The only information I've been able to find on i/o errors is either due to hardware failure or a damaged filesystem, but as far as I can tell I've got neither. Any suggestions?

Running Maverick, but I've forgotten the exact version and I'm too afraid to switch back to the other partition :\

---

### Post by virtualomega on 2011-12-07
> **maaarg said:**
> This is going to be something of a frustrating post-- Ubuntu is fubar right now, so I'm posting from my Windows partition. A lot of information could be hard to find.

Earlier today, while browsing Chrome, I got a timeout error, which (considering my wireless) seemed innocent-- until the other programs I was running (emacs, umlet) stopped working as well. 

From terminal, I got an i/o error dev sda
From the gui I would get a popup reporting an Input/Output error

The entire system froze-- couldn't shut down by normal methods, so I had to force it. Rebooted in recovery mode, and everything seemed fine. Rebooted in normal mode, and everything seemed fine again. Went to Disk Utility and found no bad sectors; checked the filesystem and everything was reported in working order. 

While I usually use Chromium, I started Firefox to try a quick backup of my most necessary files. Worked well for a while, then froze up. Tried starting Chromium at this point (probably a bad idea) and it was back to Input/Output errors when I tried to run anything (emacs, for example).

The only information I've been able to find on i/o errors is either due to hardware failure or a damaged filesystem, but as far as I can tell I've got neither. Any suggestions?

Running Maverick, but I've forgotten the exact version and I'm too afraid to switch back to the other partition :\
I've had the same exact problem you described which pretty much started last week. My filesystem is clean and no bad sectors. It got so bad with the crashing and then freezing on reboot that I tried reinstalling the o/s but still to no avail. I'm posting this message from the LiveCD right now. :(

---

