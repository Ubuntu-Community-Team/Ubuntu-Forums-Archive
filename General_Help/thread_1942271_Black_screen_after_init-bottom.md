---
title: "Black screen after init-bottom"
date: 2012-03-17
forum: General Help
---

### Post by Yehonal on 2012-03-17
hello guys
i've a problem on my little server with ubuntu server 11.04 ( minimal installation with gnome-core and all security/reccomanded updates ) installed on asrock with intel integrated graphic and intel cpu, using a 500gb HD partitioned with /boot and LVM2.

at **cold start** the system runs until it hangs.

Here is the last bit of text that appears just before the black screen:

Begin: Running /scripts/init-bottom ...


At this point, the font style changes slightly. Then the text is replaced by the solid black screen. There is no blinking cursor, and the hard drive activity ceases. _i can wait also 1 day..it doesn't go forward_.

i've to _reboot it different time before it runs correctly_.

It hurts me a lot, please give me an hand.

---

### Post by matt_symes on 2012-03-17
Hi

Can you boot into an older Kernel ? 

If you can try recreating your initramfs file.

Kind regards

---

### Post by Yehonal on 2012-03-17
Yes i've the same problem with older kernel , i've also tried to reinstall latest generic kernel.

but nothing changes

---

### Post by matt_symes on 2012-03-17
Hi

Do you have any ntfs drives connected ? If so remove them and try again. That's the only thing that the init-bottom script does on 11.10.

Take a look in the log files specifically /var/log/kern.log and /var/log/syslog.

Post them back here if you want.

Kind regards

---

### Post by Yehonal on 2012-03-17
No i don't have any ntfs connected at startup, i've just an external ntfs HD but i connect it occasionally.
Maybe the problem is the LVM2?

[http://pastebin.com/raw.php?i=1ts2y06U](http://pastebin.com/raw.php?i=1ts2y06U)  kernel log

[http://pastebin.com/raw.php?i=d28KkxV1](http://pastebin.com/raw.php?i=d28KkxV1) sys log

it seems to be the error when the problem appears:

```

Mar 17 10:28:55 hw2nas kernel: [  294.450019] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro,commit=0
Mar 17 10:28:55 hw2nas kernel: [  294.479272] EXT4-fs (sda1): re-mounted. Opts: commit=0
Mar 17 10:28:58 hw2nas pulseaudio[1543]: module-x11-bell.c: XkbQueryExtension() failed
Mar 17 10:28:58 hw2nas pulseaudio[1543]: module.c: Failed to load  module "module-x11-bell" (argument: "display=:1 sample=bell.ogg"): initialization failed.
Mar 17 10:29:01 hw2nas kernel: [  300.004046] [Hardware Error]: Machine check events logged

```

but i'm not sure..

---

### Post by matt_symes on 2012-03-17
Hi

> [Hardware Error]: Machine check events logged

Never come accross that one before.

I would start taking out hardware and trying to reboot to trap the hardware problem.

Put the drives in a known good box and run a SMART test on them. Same with memory; into a known good box and run memtest on it.

Also, try to boot from a LiveCD/USB.  Run

```
sudo lshw
```

from the LiveCD/USB. Does it fail ?

EDIT:

Read this.

[http://manpages.ubuntu.com/manpages/natty/man8/mcelog.8.html](http://manpages.ubuntu.com/manpages/natty/man8/mcelog.8.html)

Kind regards

---

### Post by Yehonal on 2012-03-18
"sudo lshw" runs correctly 

however, this is the error from /var/log/mcelog

CPU 0 BANK 0 
TIME 1332110101 Sun Mar 18 23:35:01 2012
MCG status:
MCi status:
Uncorrected error
Processor context corrupt
MCA: Internal Timer error
STATUS a200000084010400 MCGSTATUS 0
MCGCAP c0204 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 15 Model 3

---

### Post by matt_symes on 2012-03-18
Hi

Check all hardware. 

Are you overclocking ? If so then don't.

Check CPU temps and power supply.

It may be software but i would check hardware first. Also boot from a LiveCD/USB. Do you get the same issue ?

Maybe there is some information in here ? It's a pdf file from suse labs

[http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CCsQFjAA&url=http%3A%2F%2Fwww.halobates.de%2Fsupp-mce.pdf&ei=aHZmT7KhNqrE0QXX2cC8CA&usg=AFQjCNFnXRD5L99yX6Y9HGagH02JJDeuqg](http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CCsQFjAA&url=http%3A%2F%2Fwww.halobates.de%2Fsupp-mce.pdf&ei=aHZmT7KhNqrE0QXX2cC8CA&usg=AFQjCNFnXRD5L99yX6Y9HGagH02JJDeuqg)

I have not had chance to read it yet.

You could try resetting the BIOS. There may be a jumper on the motherboard for this. Flashing the BIOS may also help but this is not without risks.

When did this start happening ? Did it happen after an update ? Was the server moved ?

Kind regards

---

### Post by Yehonal on 2012-03-19
for now i've checked the RAM with memtest, and it's all ok

i've not overclocked it, just downclocked some times ago, but now it's at standard frequency.

the temps are quite stable, 30-40°C

however using ubuntu on USB , with kernel 3.0 , the error doesn't appear

i'll read the pdf as soon as possible , thanks :)

however i would keep the bios flashing as the last chance.

---

### Post by matt_symes on 2012-03-19
Hi

> **Yehonal said:**
> for now i've checked the RAM with memtest, and it's all ok

i've not overclocked it, just downclocked some times ago, but now it's at standard frequency.

the temps are quite stable, 30-40°C

however using ubuntu on USB , with kernel 3.0 , the error doesn't appear

I'll read the pdf as soon as possible , thanks :)

It could well be software then. It's difficult to say. It's not an error i have ever had.

When did it start happening ? After an update ? Did it happen from fresh install ?

Have you considered chrooting in and upgrading to Oneiric if 3.0 kernel does not show this. If you do decide to do this then backup as normal before attempting such an upgrade.

> 
however i would keep the bios flashing as the last chance.

Very wise indeed. It can brick your motherboard.

Kind regards

---

### Post by Yehonal on 2012-03-23
Hello , i'm here again

i finally solved all my problems , but after long tests and research..

the black screen disappeared after upgrade to 11.10, but...it's a pain with LVM configuration upgrading at 11.10 ( in most cases you'll have problems with udev and initramfs and the system won't boot automatically )

so i started the long process of LVM converting to standard ext4 partition , reconfiguring the initramfs/grub/fstab and now it is alive again.

I would suggest not upgrading to 11.10 if you use LVM and your system is working, because its LVM support is very bugged for now.

---

### Post by matt_symes on 2012-03-24
Hi

Thanks for reporting back Yehonal. I'm glad it's fixed.

Kind regards

---

