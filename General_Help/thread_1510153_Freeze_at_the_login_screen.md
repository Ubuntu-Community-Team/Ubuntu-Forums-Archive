---
title: "Freeze at the login screen"
date: 2010-06-15
forum: General Help
---

### Post by Forces on 2010-06-15
Hi,
Recently I have installed Ubuntu under windows and it worked perfectly the first time I booted up. It was really fast and wireless worked which was a plus. However the second time I tried to log into Ubuntu it froze at the login screen and no usernames were displayed. My mouse also didn't work.

In order to try to fix this I just rebooted and had the same issue, this time the drum sound played three and a half times then the same as before happened.

As a result I completely reinstalled Ubuntu (again under windows) and have been having the same problem, but this time I can actually see my user name.

I have noticed that when this freeze occurs the Hard Drive seems to just stop all activity which is interesting. By the way my computer is working perfectly if I boot into windows so all hardware is fine.

Thanks for any help

Edit: It seems that this problem only occurs when I am running my laptop off battery power

---

### Post by batfink on 2010-07-13
Hi There

I had this problem after upgrading to 10.04 and it's taken me weeks to get a working result - I was virtually at the point of reverting back to windass.

Either my mouse would freeze at or just after the login screen, or the 1st key I pressed in my password was repeated infinitely and then the system froze. Failsafe always worked.

Anyway I cured it by adding:

noapic noacpi noapm

into the kernel line in /boot/grub/menu.lst
i.e.

kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=564c0794-4a29-4154-8339-7801680196e9 ro quiet splash noapic noacpi noapm

Also added it into the default options so it doesn't get lost when menu.lst is updated:

# defoptions=quiet splash noapic noacpi noapm

Other things I tried but ultimately failed in case it helps:

adding the following kernel options in menu.lst:

    irqpoll
    i8042.reset
    radeon.modeset=0
    nodmaraid
    nomodeset
    nofb
    
Tried removing splash option from the kernel line.

Also found some interesting stuff on this page (although using a mainline kernel didn't help me):
[http://www.iol.ie/~stuartneilson/Bootup_fsck.html](http://www.iol.ie/~stuartneilson/Bootup_fsck.html)

Hope some of this might help. I found it extremely annoying when this happened and nearly gave up on Linux altogether. Glad I stuck with it though.

Cheers

---

