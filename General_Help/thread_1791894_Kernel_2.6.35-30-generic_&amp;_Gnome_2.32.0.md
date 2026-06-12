---
title: "Kernel 2.6.35-30-generic &amp; Gnome 2.32.0"
date: 2011-06-27
forum: General Help
---

### Post by GBray on 2011-06-27
Just installed the patches/upgrades for the 2.6.35.30 kernel.  Ubuntu will not boot without me typing "y" and hitting enter and later hitting the enter key again.  Just have a blank screen unless I do this.  Discovered what to do by booting into recovery mode.  Had to make a display selection.  Just guess at the enter key the second time the boot process stopped.  I new to Ubuntu so don't know where to look in the logs to provide additional information to help trouble shoot the problem.  If some one can guide me as to where to look I'll post log info.  Hope this is the right place to post this.  If I need to make a bug report let me know.

Forgot to add:  HP Pavalion dv5000 (dv5020us to be specific).  AMD Turion64 processor.  ATI Radeon Mobility 200M video.

---

### Post by insanity54 on 2011-06-27
Can you be a bit more specific?

What patches/upgrades did you install? If you're new to ubuntu, why are you messing with kernel patches? Do you mean automatic updates?

What message does ubuntu say when it makes you type "y"?

As for the logs, there is [this thread]("http://ubuntuforums.org/showthread.php?t=49925") which shows how to enable boot logging, but I'm not sure if this still works for recent versions of ubuntu.

You could also try this right after startup:```
dmesg | less
```

---

### Post by GBray on 2011-06-27
It was the automatic updates.  More to follow after I do what you suggested.

---

### Post by GBray on 2011-06-28
Recovery boot  stops displaying:

[1.575375] ACPI:  Video Device [VGA] (multi-head:  yes  rom:  no  post:  no)

After entering "y" and enter boot continues but things scroll by too quick to catch anything.  Video display mode changes and the messages stops at

Begin:  Rumming /scripts/init-bottom...done

Hit enter & the recovery boots completes.

Booting normally, the boot stops with a blank screen and a the cursor in the upper left.  I enter "y" and press enter and boot continues.  After a few seconds, all disk activity stops with the Ubuntu screen and the progress dots showing.  I hit enter and disk activity starts again.  The repeats two more times and then the boot process completes normally.

The dmesg | less displays the following:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-30-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #54-Ubuntu SMP Tue Jun 7 18:40:23 UTC 2011 (Ubuntu 2.6.35-30.54-generic 2.6.35.13)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077ea0000 (usable)
[    0.000000]  BIOS-e820: 0000000077ea0000 - 0000000077eac000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077eac000 - 0000000077f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077f00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) =:

---

### Post by insanity54 on 2011-06-30
Sorry, I left out some helpful info. I'll also explain the commands I'm telling you. (I'm learning as I go along so I'm sharing what I just found out.)

The command "dmesg" basically outputs the kernel log. The "|" is to pipe the output of a program to another program. The "less" is a program for viewing files.

When I told you to do:```
dmesg | less
```
The output of dmesg was being piped to the program less.

The program, "less" was showing the **start** of your kernel log, which would be the kernel messages from when ubuntu was just starting up. You can see the numbers on the far left column, I believe these are timestamps (measured in seconds?) We want to see the **end** of your kernel log, so we have to scroll down using arrow keys or PageUp/PageDown. "less" lets you scroll up *and* down, whereas the command "more" only lets you scroll down. I guess less is more! Also, to stop using "less" you can press the letter "q"

Scroll through those kernel messages and see if anything looks like the culprit. Post the output here if you need a second pair of eyes!

---

### Post by kungfoofool on 2011-07-01
I'm having a similar issue. Automatic upgrade to 2.6.35-30, after which I see the Ubuntu splash startup page, and it hangs up there. I haven't tried hitting "Y" or "Enter." I was able to boot up using the previous 2.6.35-28 kernel.

---

### Post by insanity54 on 2011-07-01
@GBray @kungfoofool Are you using a Dell laptop?

---

### Post by digisol1 on 2011-07-07
I am in the same boat.. any word on a solution?:confused:

---

