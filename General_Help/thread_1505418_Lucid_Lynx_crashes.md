---
title: "Lucid Lynx crashes"
date: 2010-06-09
forum: General Help
---

### Post by ubupatzer on 2010-06-09
The only thing I really know is Lucid Lynx crashes almost every session. 

This is what comes up: 

process: (235): "GLib-WARNING**: getpwuid_r():  failed due to unknown user id (0)"

What can I do with next to no understanding of Linux?

---

### Post by junapp on 2010-06-09
you can provide more detail. Did you have a previous version working? How did you install Lucid? Where/when do you seen this error? Immediately after the bios screen? After login?

---

### Post by john newbuntu on 2010-06-09
There is a launchpad bug on this:
[https://bugs.launchpad.net/ubuntu/+bug/531027](https://bugs.launchpad.net/ubuntu/+bug/531027)
I have seen this just once and ended up doing a ctrl+alt+del which rebooted the comp.

---

### Post by ubupatzer on 2010-06-09
Hardy Heron never crashed. Intrepid Ibex crashed only twice. Lucid Lynx crashes all the time. 
                                                  Every version after  Hardy installed by upgrade. 

(process: 235): GLib-WARNING**: getpwuid_r(): failed due to unknown user id (0)

Top of the blank screen after the crash followed by a flashing screen.
Computer must then be turned off and restarted.

---

### Post by ubupatzer on 2010-06-14
Still crashing, still dreaming...

---

### Post by AlanR8 on 2010-06-14
> The only thing I really know is Lucid Lynx crashes almost every session.

Be careful what you post for the World to see. "The only thing I know is....." 

Lucid has never crashed for me on five separate machines.

---

### Post by u-slayer on 2010-06-14
> **ubupatzer said:**
> Hardy Heron never crashed. Intrepid Ibex crashed only twice. Lucid Lynx crashes all the time. 
                                                  Every version after  Hardy installed by upgrade. 

(process: 235): GLib-WARNING**: getpwuid_r(): failed due to unknown user id (0)

Top of the blank screen after the crash followed by a flashing screen.
Computer must then be turned off and restarted.

I had intrepid 64 bit installed and it crashed all the time. (especially when playing videos or doing large file transfers). I upgraded to lucid and when with the 32-bit PAE and it hasn't crashed yet.

---

### Post by ezsit on 2010-06-14
Half the time I cannot get Lucid to boot at all. Once running, it crashes quite frequently. I stick with the "buggy" Karmic Koala and experience no crashes. Every LTS has been worse for me than the October releases, and those were the ones that were supposedly problematic. Go figure. Wait til 10.10 comes out and I bet it will be far better that 10.04.

---

### Post by ubupatzer on 2010-06-19
OK, the only thing I really know is MY Lucid Lynx crashes almost every session when apparently someone else's doesn't crash at all.                                                                                                                                                                                                                                     There was never a problem for me with Hardy Heron and only a few with Intrepid Ibex but my experience with Lucid Lynx has been disappointing.                                                     This is all the more frustrating because I have no way to even begin to understand let alone deal with this. At least it restarts every time.

---

### Post by ubupatzer on 2010-06-23
If I had a dollar for every time this thing crashed I could afford to buy a real computer operating system.

---

### Post by ubupatzer on 2010-06-24
A day without crashing is like a day without Ubuntu.

---

### Post by yanivi on 2010-07-01
> **ubupatzer said:**
> OK, the only thing I really know is MY Lucid Lynx crashes almost every session when apparently someone else's doesn't crash at all.                                                                                                                                                                                                                                     There was never a problem for me with Hardy Heron and only a few with Intrepid Ibex but my experience with Lucid Lynx has been disappointing.                                                     This is all the more frustrating because I have no way to even begin to understand let alone deal with this. At least it restarts every time.

Hi,

I had the same problem: when I looked at my /var/log/messages, I saw many messaging regarding the bluetooth. 
Since I don't need bluetooth 99.99% of my time, I just disabled it (on your tray - top right corner of your screen), and from that point it stopped crashing. I hope this helps.

yaniv

---

### Post by ubupatzer on 2010-07-20
Now why would just receiving an update crash the system, among any number of other things?

---

### Post by ubupatzer on 2010-07-20
Or it could crash for no reason at all.
Alter ego: Maybe it's the computer and not the operating system.
You might be right.

---

### Post by JaimeFrontero on 2010-07-22
i'm running 10.04 on:
A quad-core generic I built.
A dual-core generic I built.
An MSI Wind U-100
A Fujitsu Lifebook P1600

...without this particular problem - the GLib-Warning**: getpwuwid & etc.

In fact, without any problems at all.

But on a Dell Inspirion 1100 it just plain crashes all the time, with the GLib Warning.

I note that, anecdotally at least, the majority of these GLib crashes that are appearing here and on Launchpad seem to be on various Dell computers.  Hmmm...

---

### Post by ubupatzer on 2010-08-10
ISSUE RESOLVED:

The problem was VirtualBox OSE

The solution was terminal command: sudo apt-get remove virtualbox*

---

### Post by JaimeFrontero on 2010-08-15
Removing VirtualBox is not an especially palatable solution.

I *need* VirtualBox.

Is it a particular version of VirtualBox?  Got link to this resolution thread?   Or is this something that worked on just your system?

---

### Post by dewdrop_world on 2010-08-15
I'm getting frequent crashes too. The honeymoon is definitely over!

MSI A6200, intel core i3. Often running jack + [supercollider/emacs]("http://supercollider.sourceforge.net").

Last crash: scrolling over a facebook photo in firefox, fairly innocuous.

I didn't go with, say, arch linux 'cuz I thought it would be nice to have some goodies preinstalled, but the instability (and the reported trend toward more instability with later releases) is making me reconsider.

James

---

### Post by dewdrop_world on 2010-08-17
For the record -- I found out what was causing my crashes. Thunderbird 3.0.6. I thought that was supposed to fix the crashing problems against lucid?

Anyway, I haven't launched Thunderbird in the last couple of days and I haven't seen any odd behavior either.

Kind of sucks because I like to use a mail client rather than Gmail/web, but on the other hand, getting some work done is nice too :p

---

### Post by ubupatzer on 2010-11-28
The most recent crash occurred during an update and

"An error occurred

The following details are provided:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

So,

"michael@freegeek:~$ sudo dpkg --configure -a
[sudo] password for michael: 
dpkg: parse error, in file '/var/lib/dpkg/updates/0117' near line 0:
 field name `
michael@freegeek:~$"

Does anyone have any idea what should be done next?

---

### Post by Thrasyllus on 2010-11-28
I have to confirm ubupatzer's observations. My 10.04 crashes several times a day, whereas many earlier versions of Ubuntu and Red Hat never did (including two or three previous versions of Ubuntu on the same hardware). The top half of the screen becomes filled with a row of vertical white and black bars which flash on and off with a period of a few seconds.

---

### Post by demilord on 2011-01-26
I find that the development is a bit stalled...
There are some reviews where they were very disappointed with lucid lynx.. With gnome help and slow/crashing graphic performances and nautilus netshare.. source: [http://lcorg.blogspot.com/2010/04/bugs-in-ubuntu-1004.html](http://lcorg.blogspot.com/2010/04/bugs-in-ubuntu-1004.html)
we will see whats going to happen and if the bugs every will get fixed... :(
for me ubuntu feels like a sinking ship...

---

