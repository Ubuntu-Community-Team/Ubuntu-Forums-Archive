---
title: "ACPI Lockup Thread"
date: 2010-09-28
forum: General Help
---

### Post by coffee412 on 2010-09-28
**Who is this thread for?**

Your system is locking up for no apparent reason that you can find. You have already investigated the following:

1. System Overheating - Make sure you check for proper fan operations and have reseated your heatsink with heatsink compound.

2. Video Card - Make sure to check that the cooling fan (if equipped) is running on your video card. Check to make sure its not a driver issue.

3. Power Supply - Poor or failing? Swap out the PS to a known good one.

4. Kernel Crashing / Software issue - Read your logs (/var/log/messages) for clues.

5. Hard Drive / Memory issues - Check them!

**This brings us to the dreaded ACPI. **

Ok, Iam going from my experiences and some reading. So, Dont accept this for gospel truth. So, Lets go.

Manufactuers of Cheap computers like eMachines, HP (yes hp!) and others use cheap parts. Simple eh? The motherboards are cheap and the chips on them are very cheap. Thats the whole problem. 

Take a more detailed look at your logs. Specifically look for the following entry in your logs:

> Clocksource tsc unstableIf your getting this then you are the lucky owner of a cheap motherboard. I have gotten this on Foxconn boards. This is actually the source of your lockups. The clocksource tsc is unstable and causing a glitch in your system. What we need to do is tell linux not to use this as a clocksource. But to do that we need to know what we have available for clocksources.

Open a term window and take a look at the file available_clocksource like below:

> cat /sys/devices/system/clocksource/clocksource0/available_clocksourceThis file contains the available clocksources you can use on your system. We are going to basically pick another, configure grub to use it and reboot.

To see what clocksource you are presently using (tsc by the error message) you can look at the file current_clocksource the same way as above.

Best I can say on which source to use is try one if it works great. Otherwise try another.

**Changing grub for clocksource**

1. Edit your grub file /etc/default/grub and add the line acpi=hpet (or whichever your going to try)

2. Save the file and run "grub-update" (If I remember correctly). This updates your grub configuration.

3. Reboot and see if your lockups are gone.

Believe me, I had a customer with a new install of lucid that absolutely went crazy with all kinds of lockups. I also tried karmic and fedora and ran into the same issues. The default for linux (the kernel) is acpi=on. Therefore, You have poor hardware then pretty much any distro is going to experience this problem. But, This fixed it for my customer who reports no further problems for over a week.

I hope this helps someone out there and wasnt a waste of my time.

:)

---

