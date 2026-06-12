---
title: "karmic hibernates after idle -- unwanted!"
date: 2010-01-12
forum: General Help
---

### Post by bodhidharma on 2010-01-12
karmic koala (2.6.3.31-17-generic on a Dell Optiplex 745):
if I don't touch the thing, after 5 minutes the screensaver
comes on ... then after 10 it hibernates.

How do I turn this off (the hibernate)?  Please, any ideas!!!
In Sytem->Preferences->Power Mangement it says
"Never" under "Put computer to sleep when inactive for:"

Also I ran gconf-editor and under apps->gnome-power-manager->actions
everything is "nothing", while under ->general everything is
unchecked except "installed_schema" is 3 and "use_profile_time" is
checked (the comments say to leave checked unless debugging).

Please, any help would be really great!

This is a machine that should be on all the time (in fact, it has
a UPS to cover frequent campus brownouts), can anyone knowledgeable
about these matters tell me how to disable all hiberate (and
suspend) always, no matter what?  (Maybe deleting some script...?)
Clearly, that would be a suboptimal solution (the optimal solution
would be if the preferences I selected *worked*), but better than
loosing the machine whenever I am away from it for more than 10
minutes!

---

### Post by spiderbatdad on 2010-01-12
How about run: 
```
dmesg > ~/Desktop/dmesg.txt
```
Copy that file to pastebin here:
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Then supply a link to the pastebin in another post.

---

### Post by bodhidharma on 2010-01-12
Sure, if it helps, why not?  Here is that dmesg output:

[http://paste.ubuntu.com/355771/](http://paste.ubuntu.com/355771/)

(Did that work?)

Thanks!

---

### Post by spiderbatdad on 2010-01-12
I think you need to enable two boot parameters for the kernel to run properly on your hardware: noapic pci=routeirq
This used to be done in a file called /boot/grub/menu.lst. On karmic, I believe you are looking for /etc/default/grub. The line to edit looks like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Make it look like:
```
GRUB_CMDLINE_LINUX_DEFAULT="noapic pci=routeirq"
```
Please add a new pastebin after booting with those options.

---

### Post by bodhidharma on 2010-01-12
Well, I put in those new boot parameters, and here now is the
dmesg output:

[http://paste.ubuntu.com/355795/](http://paste.ubuntu.com/355795/)

Could you please tell me:
1) Why you thought I needed those parameters?  (The machine booted
   OK, I have no idea if they changed anything ... and I have to
   leave this situation for about 18 hours so I cannot explore
   further....)
2) Whether they were for the hibernation issue?  Or should I try
   something else for that problem?

Thanks!

---

### Post by spiderbatdad on 2010-01-12
> **bodhidharma said:**
> Well, I put in those new boot parameters, and here now is the
dmesg output:

[http://paste.ubuntu.com/355795/](http://paste.ubuntu.com/355795/)

Could you please tell me:
1) Why you thought I needed those parameters?  (The machine booted
   OK, I have no idea if they changed anything ... and I have to
   leave this situation for about 18 hours so I cannot explore
   further....)
2) Whether they were for the hibernation issue?  Or should I try
   something else for that problem?

Thanks!
Indeed I am trying to help you address an unwanted hibernate issue. That said, in truth, I am about as far from a linux kernel expert as one can get. However I have been running Ubuntu for more than 4 years on a variety of hardware and have learned a couple of tricks to resolve unwanted behaviours.
It seemed you did all the right things through power manager, so looking at the kernel diagnostic message seemed like a logical step. Compare the two yourself, you'll see the latter is much shorter and cleaner...fewer (what I would call) conflicts, and hardware enabled without error. Is your problem solved? Please let us know when you have had time to test the issue.

Edit: Sometimes the bios can cause suspend and if this is not resolved by power manager either in windows or Ubuntu, then check your bios suspend settings.

Also I left out the parameter most likely to address your issue (acpi=off) I inadvertently told you noapic. Sorry. I would edit the cmd line as follows:
```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off noapic pci=routeirq"
```

---

### Post by bodhidharma on 2010-01-13
Spiderbatdad -- thank you so much, your "acpi=off" idea solved my
unwanted shutdown on idle problem!!!  (Well, actually, I've not
yet done extensive testing, but after rebooting with this parameter,
it sits idle for up to half an hour without hibernating.  YEAH!
(I will know more after I go home tonight (US Mountain Time) and
leave the thing on overnight.))

So, just in case anyone else has these problems, here is some
final info:
1) the modification was in menu.lst, as Spiderbatdad suggested,
   but: it is in /boot/grub, and the format of the line is a bit
   different from what SBD suggested.  The line is in the section
> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=acpi=off noapic pci=routeirq

   (actually, that is the version with the new bootparams... the old
   ones were "quiet splash" I think...; note odd construction where
   you change the stuff *inside the comment* (with that leading #),
   since then running update-grub does some monkeying with the file
   and pulls the actual bootparams out of that comment.)  Oh, and if
   anyone else every needs to do this, you have to edit this inside
   sudo (sudo nano yaddayadda or whichever editor you like to use)
   and don't forget to run that update-grub afterwards and then to
   reboot.
2) I have not yet experimented with changing any of the other power
   management options, on top of the "acpi=off", I don't know if they
   are now all unavailable.  This wouldn't be much of an issue for me
   since this machine is a desktop which is supposed never to be off...
   but I eventually do want to get the UPS working, which might be an
   issue.
3) SBD: can you suggest somewhere to read up on bootparams?  I want
   to be as smart/knowledgeable as you!


Thanks again!

---

