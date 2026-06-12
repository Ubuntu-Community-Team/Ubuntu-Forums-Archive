---
title: "Spoofed MAC Address wont &quot;Un-Spoof&quot;"
date: 2009-08-21
forum: General Help
---

### Post by Greg Xix on 2009-08-21
Like some other people, I have my reasons for changing(Spoofing) my MAC addresse on my NIC card on occasion.

Here is how I do mine via the Terminal for example:

[B]$sudo ifconfig eth0 down hw ether 00:2B:71:2A:9D:F4
$sudo ifconfig eth0 up[/B]

I always have gotten the desired results.

Now on Tuesday I had to change out my motherboard in my machine. So I bought a new one and installed it. All my components get along with the new M-board fine(Graphics Card, memory, HD, Ubuntu, etc.).

But when I went to Spoof my MAC Address. It did the job, but it also apparently made the change permanent. On my old M-board when I rebooted my machine, the spoofed MAC would be wiped out.

On this M-board, when I reboot the machine. The Spoofed MAC is still there. So I tried a cold shutdown/boot, same thing. Then I unplugged my machine and that did the trick.

Also, every Spoof & reboot results in eth0 being removed and eth1, then eth2, eth3, etc. everytime I spoof, then reboot.

My spoofing apparently is writing the Spoof to some sort of ROM, because when I reboot, even before my GRUB options comes up the POST show the "Internal MAC Address" and its of course the spoofed one.

Is there an ***ifconfig*** option that removes the spoof? Or Is there something in BIOS to change because I have tinkered with options in there for a while with no luck. I'd prefer not to have to unplug my computer everytime I wanna spoof.

Also, the NIC is onboard as it was with my old motherboard.

---

### Post by Greg Xix on 2009-08-22
bump

---

### Post by michy99 on 2009-08-22
Can you just "spoof" it back to the original address?

---

### Post by aesis05401 on 2009-08-22
> **Greg Xix said:**
> *snip* Also, every Spoof & reboot results in eth0 being removed and eth1, then eth2, eth3, etc. everytime I spoof, then reboot. *snip*

Can you clarify this.  Are you saying each spoof/reboot results in your interface being assigned with a higher number when your machine comes back up?

---

### Post by Greg Xix on 2009-08-22
> **aesis05401 said:**
> Can you clarify this.  Are you saying each spoof/reboot results in your interface being assigned with a higher number when your machine comes back up?

Yeah. I just want the spoof to go away when I reboot, like before. But the spoof remains, and when I spoof over the top of another, then reboot, the **eth's** start incrementing, as well.

---

### Post by sefs on 2009-08-22
I believe your answer may lay in 

/etc/udev/rules.d/70-persistent-net.rules

open this file and see how many eth* they are

if you see a list of them ... delete them all and reboot and let the machine rebuild that file from scratch on reboot and you will be back at eth0 again.

I believe each new mac address found creates a new line in this file ergo...your increasing ethX incrementation.

---

### Post by Greg Xix on 2009-08-23
> **sefs said:**
> I believe your answer may lay in 

/etc/udev/rules.d/70-persistent-net.rules

open this file and see how many eth* they are

if you see a list of them ... delete them all and reboot and let the machine rebuild that file from scratch on reboot and you will be back at eth0 again.

I believe each new mac address found creates a new line in this file ergo...your increasing ethX incrementation.

Well, it might stop the incrementation but it won't stop the Spoof from writing it to some sort of memory on my computer. Like I said even after powering down, and cold booting, the spoofed MAC would still be there. POST lists it as: **Internal MAC Address 00:2B:71:2A:9D:F4** or whatever my most recent spoofed MAC Address happens to be, this line is displayed _before_ GRUB announces itself during the POST. When I did a LIVE CD boot, it registers as eth0 because of the "net.rules" not being written to, but the MAC I spoofed on the "fully installed" Ubuntu was still the current(permanent) MAC address on the LIVE CD.

In other words when I spoof on Ubuntu, its writing it to some sort of computer memory. I even tried resetting the BIOS via the "2-3 Jumper pin method" without luck.  Only unplugging my machine for 10 seconds made the spoof go away. This is not really a LINUX/Software issue, but rather a Hardware one.

After my last post I went out and bought a PCI Network Card, and it actually was registering as 'eth4'. So I did a google and found out about what you suggested. Sure enough all those old spoofs were listed there. So I wiped all of those out of the file and rebooted, disabled the onboard NIC in BIOS and now the newbie registers as eth0. And when I spoofed, and rebooted, the spoof is not retaining.

BTW, if anybody ever asks you on here or in person needing to install a PCI or PCIe NIC card thats compatible with LINUX. Tell them US Robotics "is known to work". Mine was plug and play with no hassles.

---

### Post by aesis05401 on 2009-08-23
Thanks for posting back with the results.  I tried replicating your experience on my various installations and couldn't come up with anything.

---

### Post by hxleet on 2009-09-29
do what sefs said and also try sudo gedit /etc/interfaces/network and remove any line that look like hwaddress <interface> 00:01:02:03:04:08  if thats not it try Edit the ifcfg-eth0 file (or other similar file if you’re changing different interface) and remove any MACADDR=12:34:56:78:90:ab  hope that helps

hxleet

---

