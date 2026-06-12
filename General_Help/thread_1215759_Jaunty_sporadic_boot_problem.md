---
title: "Jaunty sporadic boot problem"
date: 2009-07-17
forum: General Help
---

### Post by Rawblues on 2009-07-17
Hi there.

I have a system set up for dual boot with Windows XP Pro and Ubuntu Jaunty. The system works well using Grub to allow me to select either XP or Ubuntu but it frequently refuses to boot up from the Ubuntu partition. Booting from the XP partition via Grub always works, on the other hand. 

When I select Ubuntu from the Grub menu, if all goes well, I get the little animated graphic showing Ubuntu is starting up followed by the login screen in high resolution graphics. If it's going to fail, I don't even get as far as the animated graphic - my LCD monitor just reports "no cable", as if the system has completely and instantly halted.

I can get back to normal by using my Ubuntu boot CD and selecting the option to run Ubuntu from the cd in low resolution graphics, and then restarting. Upon restarting, the system boots normally.

I think it might be something to do with the way the system is trying to set graphics mode on bootup - something is causing it to fall over completely. Are there startup logs somewhere that document the sequence of processing on bootup, and if it is a graphics problem, is there somewhere where I can nail down the graphics parameters to avoid any hardware polling on startup to force things into the right mode straight away?

My system is based on an intel E5300 2.6Ghz Dual-core with 4GB ram and a Foxconn G31MX motherboard using integrated graphics and sound. My monitor is connected via a VGA cable (not DV).

---

### Post by Octagonal on 2009-07-17
My experience with boot up problems where the system hangs or takes an abnormally long time to boot typically point to usb devices being queried as potential boot devices and then failing.  If you have usb devices connected like external hard drives or even blackberries try unplugging those and see if the problem doesn't go away.  Long term you can restrict boot devices to only specific hard drives in the bios if this resolves the problem.

you can always run "dmesg" from a terminal to check the boot up log too.

---

### Post by Rawblues on 2009-07-18
Thanks, Octagonal. As it happens, I do use external drives, so I will try without and see if it cures the problem. Thanks also for the "dmesg" tip - as a Linux newbie, this is exactly the sort fo thing I need to know.

---

### Post by Rawblues on 2009-07-19
Ok. I have now established that this problem is nothing to do with USB devices - it does appear to be something to do with my display. I managed to get several ok bootups today with everything functioning normally, but this evening, the problem reappeared despite having made no changes. 

The system is sometimes refusing to get beyond the splash screen stage (i.e. my monitor just shows "no cable" as if te system is completely dead), and at other times, I get several flips between a text-mode console screen and the screen goind blank, followed by a little error panel being shown in low-res graphics saying 

Ubuntu is running in low-graphics mode. 

The following error was encountered. You may need to update your configuration to solve this.

(EE) intel(0) No valid modes
(EE) Screen(s) found, but none have a usable configuration.

Now, I know for sure that Ubuntu CAN work with my screen correctly in h-res graphics mode, so I need to know the following:

1. How can I reliably boot up in text-only mode (i.e. no Gnome desktop) to avoid the graphics problem?
2. When logged in as a text-only console user, what can I edit to nail the monitor mode to 1440x900, bog standard VGA at 60Hz?

Can it be done.....?

Your help would be most appreciated, as my system is... well... none too usable at present!

---

### Post by Rawblues on 2009-07-24
Still no resolution to this one - HELP APPRECIATED!!!!

Just to resummarise, I have a dual boot system with XP Pro and Ubuntu - XP always works, Ubuntu frequently fails to boot. I wish it wasn't so, but that's how it is.

I think Ubuntu is incorrectly concluding that I have a non-feasible configuration and just halting the system before completing the boot up. I haven't yet been able to spot any pattern to it, and my system is very simple with motherboard, internal DVD drive, ps2 connected keyboard and mouse, and monitor - that's it. No external devices attached and I even boot without the network attached just in case that's a factor.

Here's what happened this morning: (I noted it as I did it)

First cold boot - selected normal boot from grub - failed immediately - system halted and monitor reported "no cable" just after the grub messages
Reboot - selected recovery mode - saw a quick flash of logged text then monitor reported "no cable" and system stopped again
Inserted live cd and selected boot in safe graphics mode - booted up ok in low res mode
Selected "restart" from the control menu - selected normal boot from grub - failed immediately - monitor reported "no cable" just after the grub messages (again)
Switched everything off and did a cold boot again. Failed exactly as the first cold boot did.
Switched everything off again and did a second cold boot - succeeded!

... and it's from that last bootup that I am talking to you now. 

I'm at my wits end with this one. I feel there must be some evidence lurking somewhere as to what is causing this, but I don't know how to get it.

---

### Post by Rawblues on 2009-07-28
Admitted defeat, reformatted my Linux partition and reinstalled Ubuntu, but downgraded to 8.04..3.

Everything works perfectly every time, indicating that it's a Jaunty problem with intel onboard graphics.

---

