---
title: "Unwanted shutdowns - caused by AptDaemon?"
date: 2010-05-23
forum: General Help
---

### Post by GingerAlex on 2010-05-23
Hello,

this unwanted shutdown issue seems to be different in nature to the others that I have read.

my recent upgrade to 10.04 has one rather serious issue. The system shuts down at seemingly arbitary intervals, when idle after about a minute and once while I was browsing a web page! The power settings are not set for any shutdown/sleep/powersave when on mains power, and besides in the latter case the computer was not idle because I had used the mouse to scroll the page.

I have pasted the following from my syslog, it seems that these are the relevant entries:

```
May 23 09:45:01 alex-laptop AptDaemon: INFO: Quiting due to inactivity
May 23 09:45:01 alex-laptop AptDaemon: INFO: Shutdown was requested
May 23 09:46:18 alex-laptop kernel: [ 3756.960065] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
May 23 09:46:18 alex-laptop kernel: [ 3756.960095] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.WMID.Z000] (Node f70128b8), AE_TIME
May 23 09:46:18 alex-laptop kernel: [ 3756.960171] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.WMID.WMBA] (Node f7012ae0), AE_TIME
```

This occurred after I had simply been using email and the internet for about ten minutes since logging in.

Note aptdaemon seems to be requesting the shutdown, although ACPI has made some logs as well. Any thoughts on what is going on? What should I do? Why can't I resist upgrades until I'm not really busy and can afford some downtime on my laptop?!?

I am using an Acer Aspire 5610z laptop and no this didn't happen on 8.04.

Thanks in advance for any help.

---

### Post by 2hot6ft2 on 2010-05-25
Looks to me like AptDaemon just shut down due to inactivity like Update Manager shutting down after not finding any updates.
ACPI seems to have had an error though.
At the grub menu I think it's the F6 key to edit the boot command line. You might try adding noacpi to the end of the kernel line and booting with it.
If it helps see the grub 2 guide in my sig. to find out how to add it to grub.
:popcorn:

---

### Post by GingerAlex on 2010-05-25
Thanks for this - actually I should have posted back, this has happened since, with no aptdaemon in the log.

So I've been monitoring the CPU temperature as suggested by some other threads, however, since installing computemp the problem hasn't recurred (and temperatures seem fine). So I guess I'll close this request and work with some of the other threads if the problem comes back.

---

### Post by GingerAlex on 2010-06-06
problem did continue after this - but is fixed now. See [http://ubuntuforums.org/showthread.php?t=1497384]("http://ubuntuforums.org/showthread.php?t=1497384"), it was basically some kind of apparent disagreement between an old BIOS and ACPI.

---

