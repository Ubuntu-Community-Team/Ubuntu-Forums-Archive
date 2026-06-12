---
title: "apt-get upgrade stops at clamav"
date: 2012-06-21
forum: General Help
---

### Post by AlexBooton on 2012-06-21
Hi,

When I run apt-get upgrade it stop with the following message:
[INDENT]
  This release of clamav no longer ships signature files in clamav-base so
  no signatures are available until after freshclam has run and downloaded
  them.  This is an upstream change.

 -- Scott Kitterman <scott@kitterman.com>  Fri, 15 Jun 2012 11:39:26 -0400[/INDENT]

This happens both from the command line and by running "Updates Available" from Unity.

How do I get past this?

Oops.  I just noticed that after the glitch I can't run "Update manager" from Unity and longer.  I click on "Install Updates" and an "Applying changes" window opens but it just sits on "Waiting".  The "Details" button doesn't work.  The only thing I can do is cancel.

Please help.

Thanks,

AB

---

### Post by ajgreeny on 2012-06-21
In the past frashclam was started at boot and a check made for updated virus signatures, if I remember correctly, so it is perhaps worth a reboot to see if that overcomes the problem.

---

### Post by AlexBooton on 2012-06-21
> **ajgreeny said:**
> In the past frashclam was started at boot and a check made for updated virus signatures, if I remember correctly, so it is perhaps worth a reboot to see if that overcomes the problem.

Hi ajgreeny,

That seemed like a perfectly logical thought; but it didn't help.  Rebooted and still have the same problem.

I'm surprised this isn't a known issue.  If it doesn't work for me I would think many others would be affected.

Thanks,

AB

---

### Post by AlexBooton on 2012-06-21
Well I managed to find a partial fix.

I ran ```
apt-get install clamav
``` and now I can run ```
apt-get update
``` w/o getting the error message.

HOWEVER, I still can't run software-update from Unity.  As before, the "Applying changes" window opens but it just sits on "Waiting".

Are the two problems related?  Is there a fix for the "Waiting" hang?

Thanks,

AB

---

### Post by AlexBooton on 2012-06-21
Well I think I've stumbled on to a fix.

I did the updates with synaptic.  Worked like a charm!

Why do we have two packages that seem to be designed to do the same job (synaptic and software-updates)?  Is there a reason for this?

Thanks,

AB

---

