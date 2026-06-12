---
title: "Ubuntu 9.04 regularly freezing and needing cold boot"
date: 2009-10-01
forum: General Help
---

### Post by brianmc on 2009-10-01
I recently got asked to look at a totally hosed Windows install and the diagnosis was unrepairable. No Windows install media available, so I booted with the 9.04 live CD and checked that the basics like graphics, sound, and WiFi all worked. That done, I wiped the HDD and did a full install.

I had no problems will doing all the post-install stuff like adding DVD playing, a bit of a fiddle due to problems with the el-cheapo sound bits on the motherboard (one output channel dead, confirmed machine previously did this with Windows). Stuck in a pretty good, but not particularly new Soundblaster card and to force that to be used I ended up blacklisting the onboard one.

When I had the machine here similar initial problems went away when I turned off some of the cacheing in the BIOS (with the unwanted side-effect of making the machine much slower). The rest of the time I had the machine here the only lockup I clearly remember was during shutdown when it went to remove/deactivate bluetooth support.

However, now returned to the owner it seems to randomly lock up even when there's next to nothing open and it has been sitting idle long enough for the screensaver to activate.

I've seen similar complaints from searching the forum archives - prior to 9.04. I can't remember off the top of my head the model of the machine, but the make is Packard Bell.

One suggestion was hardware problems, possibly memory.
How would I go about testing that or, more specifically, how do I tell someone non-technical to do that?
What other hardware tests can I run to make sure things are okay?
Is there any way to completely cut out any reference to or polling of the onboard sound in case that's the problem?
Ditto for bluetooth support (the machine has no bluetooth hardware)?
What other options might I look for in the BIOS that might eliminate or reduce the risk of a freeze?
Any logs that are worth checking to see if a warning indicating the cause is hidden away somewhere?

Any other ideas or suggestions what to try, bearing in mind that initially most of this will end up being done by talking someone non-technical through the process?

---

### Post by Inaia on 2009-10-02
I've also had a large number of seemingly random lock-ups in 9.04 myself. So far, I've heard a few theories on why, such as: ACPI, memory issues (especially when moving large amounts of files), and kernel crashes (especially in 2.6.28.x to 2.6.30.x). Also, I've never managed to successfully use AltGr + SysRq to REISUB out of the problem, which has worked for some other people.

---

### Post by user333 on 2009-10-02
I had a problem with a bad graphics card, and it coninually was frozen. try getting a better one if you don't have a good one.

---

### Post by HappyFeet on 2009-10-02
> **brianmc said:**
> 
One suggestion was hardware problems, possibly memory.
How would I go about testing that or, more specifically, how do I tell someone non-technical to do that?

Boot the live cd and memory test is one of the options, right below "try ubuntu without installing". Or something like that.

---

### Post by Inaia on 2009-10-03
Ok, the source of the problem has apparently been discovered, and it appears to be a distribution-wide problem. It's due to the clocksource tsc being unstable, which is why so many people are having this issue. From the mainline Ubuntu kernel up to but not including Karmic's kernel (2.6.31.x), there's a problem with the handling of the clock, and when an error is encountered, the clocksource tries to switch and can result in a total lockup requiring a cold reboot. Using Hardy's or Intrepid's kernels would avoid the lockup issue....but you may suffer software / hardware compatibility issues like I did, same for Karmic's kernels.

Note: maintaining a single frequency on your CPU(s) appears to help avoid such lockups, as the clock doesn't need to work as much in that case.

---

### Post by brianmc on 2009-10-03
The clock being part of the problem, and a core part of the kernel... Do you have a link to a bug report that explains this?

If the last-resort fix is to use an earlier kernel, can this easily be done without a complete reinstall? Instructions somewhere?

On my own machine (remember I'm reporting an issue with someone else's) I have an alternate kernel - but it's the same version, just the realtime variant. If it as straightforward as that was to install I'll happily give it a go.

---

### Post by Inaia on 2009-10-03
I DO have a link to the original bug report....but there's no universal fix (yet) and there were so many replies that the original got closed and the bug is now being worked on in a separate report. If you still want the link, here it is --> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155)

Note: I don't think it's the actual clock you see in the taskbar, but an internal clock that times and triggers events, frequency, etc. Whether or not that's correct, I'm not totally sure....can anyone verify? I'm fairly new to Linux, and only COMPLETELY switched to Jaunty the other day.

EDIT: If you look around hard enough, there should be instructions for installing new kernels in these forums, probably as a HOWTO. If you can't find any, most Linux veterans can probably give you a hand. I still depend on HOWTOs and such to do it myself.

Another note: I took some advice and added "notsc clocksource=acpi_pm" to my Kernel line in /boot/grub/menu.lst, and haven't had a lockup since.

---

### Post by brianmc on 2009-10-03
> **Inaia said:**
> Another note: I took some advice and added "notsc clocksource=acpi_pm" to my Kernel line in /boot/grub/menu.lst, and haven't had a lockup since.

Thanks much for that suggestion!

I knew it wasn't the desktop clock, but the internal scheduler's clock. Sorry if that wasn't clear in what I wrote.

---

### Post by b747pete on 2009-10-04
I have had this issue with the current 9.04 ever since installation, does not seem dependent on how many windows I have open.

Does anybody have the skinny on editing "menu.lst"?

Thanks.

Peter:confused:

---

### Post by Inaia on 2009-10-04
Use this command (replace gedit with your own local editor):

sudo gedit /boot/grub/menu.lst

then add this next line to the end of your KERNEL line(s) in the menu.lst:

notsc clocksource=acpi_pm


EXAMPLE (NOTE THAT KERNEL LINE WILL BE 2 LINES LONG):

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.30-02063003-generic
uuid        ef9f50d4-54b9-4fbc-aba8-3a16de192f71
***[COLOR=Magenta]HERE AT END OF THIS LINE ---->[/COLOR]*** kernel        /boot/vmlinuz-2.6.30-02063003-generic root=UUID=ef9f50d4-54b9-4fbc-aba8-3a16de192f71 ro quiet splash notsc clocksource=acpi_pm 
initrd        /boot/initrd.img-2.6.30-02063003-generic
quiet

---

### Post by Gemu on 2009-10-04
I just added that line to my boot grub menu.lst and rebooted without any issues. I have long been having the same problem with 9.04. I hope this solves the problem. I seldom had a problem with 8.10 intrepid.  9.04 has required that I run recovery mode pretty much daily to get up and running ever since I installed it.

---

### Post by brianmc on 2009-10-11
I have not - yet - been able to confirm this fixes the PC with the problem (it isn't mine, and far away).

Very reassuring to see other people getting this to work.

And, for whoever asked me privately, if it is a fix - I *will* post accordingly when I know.

---

### Post by rubikon on 2009-10-11
:( Inaia - I was hoping to hail you as a new god after your grub menu.lst 'fix' - however I've just had a ubuntu 'freeze' a few minutes after applying it.

As a newbie , (albeit one who has spent 3 complete weekends (all but) out of the last 4 attempting to load this o/s on to 2 different machines and then clean up the aftermath.
I had to give up and recover the first but the second machine , a 4yo laptop with intel pentium4 & radeon 9100 graphics running dual boot WXP & Ubuntu 9.04 -15 is virtually there) I've  a minimal load and up to the latest updates & everything working (sound/net/printing/mail ) but the bane of it is the random freeze which makes 9.04 unusable - could be 2 minutes or at the most 15 but soon there'll be a lockup - nothing working at all & all you can do is turn the machine off/on.

I have trawled so many threads that I am seeing stars , but its clear to me that many , many people are suffering from this freeze bug , including some pretty advanced major players - OK , alot of people are unaffected , but a lot of people are.
Thanks Inaia for at least having a go at fixing it - or do we take it that teams of boffins are working towards a solution as we speak.
Has anyone got any other approaches - I'm loathe to update the kernel being a newbie as I would probably struggle and probably not know how to get back.
Or do we wait and go for 9.10 ?

---

### Post by rubikon on 2009-10-21
sorted my problem -
[http://ubuntuforums.org/showthread.php?t=1296579](http://ubuntuforums.org/showthread.php?t=1296579)

---

### Post by giga_user_66 on 2009-11-04
Hi there,

My problem was solved when i changed the disk mode from IDE to AHCI in the BIOS. I had to do this for all the controllers though.
First I ran lspci -k to see which drivers the kernel actually used. It was clear that the kernel loaded up AHCI drivers but they were not being used.

I am running Ubuntu 9.04 with 2.6.28-16 kernel.
My computer would freeze whenever I started using the software-raid-array with more than 1 thread. There were no signs of failures in the logs everytime.
Eventually with a little help I switched the diskmode to AHCI and for now my problems seem to be gone. I can stress the array for hours without getting a freeze or that random little "beep" that i could hear when using the array alot.
I hope this helps for some out there.
Good luck.

---

