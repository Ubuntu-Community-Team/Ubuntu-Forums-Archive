---
title: "*frustration* Computer Constantly Crashing"
date: 2010-02-04
forum: General Help
---

### Post by timZZ on 2010-02-04
Sadly I have not been able to diagnose this issue.

My laptop think pad r40 running 9.10 now crashes within 20 seconds of opening a browser.

History.

**OS 8.04**

Couldn't find a solution to get my netgear WG111 usb wireless to work.

-Upgraded-

**OS 9.04**

Able to work with the netgear WG111 out of the box.

However when using a browser at random intervals the computer will hang.

Symptoms
--------

- Processor seems over worked easily sitting at 100% for long periods of time.
- Screen + controls freeze.
- At random times the caplock light will flash on and off.
* System cannot be recovered without a hard restart.

-Upgraded-

**OS 9.10**

Processor load issue gone but now if I launch a browser the computer will crash.  Same symptoms except now it's within 20 seconds of use.

Problem is so bad I had to use an alternative machine just to write this.

**Other information**
------------------

The machine did not show any signs like this with Fedora Core 9 -Fedora Core 11.

I just loved ubuntu on my desktop I thought I would use it on my laptop.

---

### Post by Barriehie on 2010-02-04
What's in the logfiles???

---

### Post by audiomick on 2010-02-04
And what are the specs on the laptop?

---

### Post by timZZ on 2010-02-04
> **Barriehie said:**
> What's in the logfiles???

Which log file??

---

### Post by Barriehie on 2010-02-04
> **timZZ said:**
> Which log file??

Let's start with syslog, and if you could make a note as to what time the last crash occurred it would be helpful.  That file is probably going to be rather large.

---

### Post by timZZ on 2010-02-04
> **Barriehie said:**
> Let's start with syslog, and if you could make a note as to what time the last crash occurred it would be helpful.  That file is probably going to be rather large.

I found this entry roughly co-ordinating with crashes ...

'Feb  4 18:49:36 laptop1 kernel: [   99.672046] Clocksource tsc unstable (delta = -131179484 ns)'

When looking it up .. Frequency changes are common for Pentium M's for power saving.

Any thoughts?

---

### Post by warfacegod on 2010-02-04
> -Upgraded-

OS 9.10


I'm wondering if doing an upgrade install exacerbated what was a "minor" issue before. Have you tried running a LiveCD of 9.10 to see if the problem persists there?

---

### Post by timZZ on 2010-02-04
Yes the smart thing would of been to run the live CD.

Unfortunately in my frustration of trying something, I just did the upgrade.

P.s. You would have to be a pretty patient person to trial the live cd for long periods of time on a Pentium M 1.90 ha ha

---

### Post by warfacegod on 2010-02-04
If you can, do it from a USB jump drive. Either way, you'd probably know within an hour or so if Live was having the same problem.

---

### Post by Barriehie on 2010-02-04
I reread your original post so when you launch a browser it crashes so lets log that, from the terminal:
```

strace -o ~/fftrace firefox

```
After you recover from the crash post ~/fftrace.

Edit: Might be better to attach the file, it's going to be large!

---

### Post by timZZ on 2010-02-04
> **Barriehie said:**
> I reread your original post so when you launch a browser it crashes so lets log that, from the terminal:
```

strace -o ~/fftrace firefox

```
After you recover from the crash post ~/fftrace.

Edit: Might be better to attach the file, it's going to be large!

Note: Chrome also causes this issue.

---

### Post by warfacegod on 2010-02-04
The troubleshooting section may be of some use:

[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by bakegoodz on 2010-02-04
Try uninstalling flash, and see if that helps. 99% of all my browser crashes are caused by flash.

This will remove it:
apt-get remove flashplugin-nonfree

---

### Post by timZZ on 2010-02-05
The browser usually crashes immediately..

I.e. my home page is Google.

Sometimes it doesn't get past initial load of firefox or chrome.

Note: Unlike 9.04 which the browser consumed a lot of processor power.  For the odd times firefox does run.  The memory and processor levels are good and relatively low in 9.10.

So I am not sure if this is a performance issue.

Also based off crash points I am not sure this is content related.

---

### Post by warfacegod on 2010-02-05
Try running your browser offline. See if it still crashes.

---

### Post by timZZ on 2010-02-05
> **warfacegod said:**
> Try running your browser offline. See if it still crashes.

I actually did something to this effect by pulling the usb netgear wireless stick.  To see if this was causing an issue by being directly on the bus.

The computer still crashed.

Weirdly since last night (for unknown reasons) the computer has not crashed.

For fun I left the syslog displayed and continually refreshing to see if it would humour-sly crash and it would be the last entry shown on the frozen display.

Funny thing is ... since yesterday this computer hasn't crashed.

An update has been installed roughly an hour ago.

---

### Post by Cue2 on 2010-02-07
> **timZZ said:**
> I actually did something to this effect by pulling the usb netgear wireless stick.  To see if this was causing an issue by being directly on the bus.

The computer still crashed.

Weirdly since last night (for unknown reasons) the computer has not crashed.

For fun I left the syslog displayed and continually refreshing to see if it would humour-sly crash and it would be the last entry shown on the frozen display.

Funny thing is ... since yesterday this computer hasn't crashed.

An update has been installed roughly an hour ago.

can I ask what the update was? I'm having a similar problem when firefox is open in 9.10. it crashes spontaneously and there is no way to recover other than a hard reset, not even the old REISUB does anything.

---

