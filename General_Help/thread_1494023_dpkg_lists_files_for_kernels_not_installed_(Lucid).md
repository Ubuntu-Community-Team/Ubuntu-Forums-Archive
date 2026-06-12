---
title: "dpkg lists files for kernels not installed (Lucid)"
date: 2010-05-26
forum: General Help
---

### Post by Robertjm on 2010-05-26
Hi all,

Today I was trying to clean up my system and am a little bit stumped on something.

I used synaptic to clean up installed kernels, except for the one that was currently running. Once done I went ahead and restarted my computer.

Grub lists only one kernel available. However when I go to a prompt and

issue dpkg --list|grep linux-image I get several items listed:
[COLOR="Blue"][B]
rc  linux-image-2.6.32-12-generic               2.6.32-12.17
                Linux kernel image for version 2.6.32 on x86
rc  linux-image-2.6.32-13-generic               2.6.32-13.18
                Linux kernel image for version 2.6.32 on x86
rc  linux-image-2.6.32-14-generic               2.6.32-14.20
                Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-22-generic               2.6.32-22.33
                Linux kernel image for version 2.6.32 on x86
ii  linux-image-generic                         2.6.32.22.23
                Generic Linux kernel image[/B][/COLOR]

2.6.32-22-generic is the kernel I am running so I assume the "ii" files have something to do with the kernel in memory.

However, what are the "rc" files that are listed? Resource files? All three kernels referenced have been removed a LONG time ago and when I look for installed headers, or anything else, there is nothing installed for *-12, *-12 or *-14.

And when I check Synaptic for just the kernel number I get a list of packages with no version install, no latest version notation and no description (attached screenshot).

Just what are those references and how does one remove them?

Robert

---

### Post by gmargo on 2010-05-26
If you look at the headers provided by the dpkg command, it gives the meanings of those leading letters.  (Below is an example from my own system.) 

The "r" in column 1 means that the package has been removed.  The "c" in column 2 means that the package was not entirely purged and there may be configuration files left behind.  The " " in column 3 means there is no error.

```

$ dpkg -l libpcap0.7
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-===============
rc  libpcap0.7     0.7.2-9        System interface for user-level packet captu

```If you see an "ii " in the first columns, like in your installed kernel case, that just means the package is installed and ok.

Now, how do you remove that entry?  Still working on that one.  I thought "dpkg --purge" would do it, but now I've got a "pn " status entry.

---

### Post by Robertjm on 2010-05-26
Thanks!! Since there isn't anything in the third column I'm not going to be so worried then. :P

Will be looking forward to your info on removing. May seen rententive, but I'd just assume get rid of it if it's from something that's no longer being used.

---

