---
title: "Several 64 bit distros refuse to boot."
date: 2010-01-04
forum: General Help
---

### Post by Infil on 2010-01-04
I recently bought a new laptop (Clevo W760CU) and I've tried several times running 64 bits distros on it. 

Both Ubuntu 9.10 and Fedora 12 live cd's simply won't boot into X. They both seem to freeze at the very ending of the loading process. 32-bit releases of both work fine. 

Using the alternate install CD I managed to install 9.10 but when I try to boot it freezes immediately after the cursor appears (which I assume is equivalent to where the live cd's freeze). If I try recovery mode I can see the following error:

[ time ] BUG: soft lockup - CPU#4 stuck for 61s! [some program]

Where and which program it is varies.

I've managed to install Archlinux and Windows 7 fine, both 64-bits. I haven't been able to update Arch yet because it wont't find my network card, as with Fedora 11 and 9.04 both of which install perfectly fine). It seems the kernels released in October or later cause my problems

How can I fix this? I really want to be running 9.10 64 bit because I have 4 GB of RAM.

---

### Post by J V on 2010-01-04
are you *suuuure* you're on 64 bit? ;)

Try downloading the disk again, check its md5, and burn it sloooowly... Then check the disk for defects... unlikley that its randomly doing this but... should try nonetheless...

---

### Post by Infil on 2010-01-04
I mostly use my USB stick as the live cds's. But I have also tried with a md5-checked CD: Same problem.

I know I'm running 64 bit because W7, Arch and F11 installed just fine :P

---

### Post by sylvester_0 on 2010-01-04
I've seen that error on a machine before (Dell Studio 540 running Hardy) and it turned out to be a poor ACPI implementation. Although this isn't a longterm fix (especially on a laptop), you can test this by appending acpi=off to the kernel boot string at boot time.

How new is the machine? It may take the kernel folks a few months to catch up if it's fairly new. Any other interesting dmesg entries?

---

### Post by Infil on 2010-01-04
Thanks for the tip. Right now I don't have 9.10 64 bit installed but I will try your tip as soon as possible. How would I go about getting the dmesg messages? Could I access the root partition from another install and fetch the kern.log or something like that?

The machine is fairly new I think. I bought it mid-December. It's a [Clevo W760CU]("http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=216")

---

### Post by Jive Turkey on 2010-01-04
Rule of Thumb: If the validated live CD wont boot, don't install from it either.

You should try the "acpi=off" boot option with a live CD and at least see if it will boot for you.  

I use 64-bit 9.04 on my desktop due to 9.10 having too many bugs that affect me, Jaunty handles 8GB ram just fine. There didn't seem to be any must-have features in Karmic Desktop edition for me to put up with the bugs there.

---

### Post by Infil on 2010-01-04
Thanks for your reply.

I haven't installed from any CDs that didn't boot :P The alternate install CD booted just fine. How would you do that, anyway?

What are the consequences of "acpi=off" for me? I could have used 9.04 but there seems to be a [bug]("https://bugs.launchpad.net/ubuntu/+bug/400297") there which makes my internet connection drop out about every 8 seconds.

---

### Post by dcstar on 2010-01-05
> **Infil said:**
> 
........
I've managed to install Archlinux and Windows 7 fine, both 64-bits. I haven't been able to update Arch yet because it wont't find my network card, as with Fedora 11 and 9.04 both of which install perfectly fine). **It seems the kernels released in October or later cause my problems**

How can I fix this? I really want to be running 9.10 64 bit because I have 4 GB of RAM.

You may be able to find a Beta 9.10 install CD (with an earlier kernel) and try to install that, and if it is ok then lock that kernel to prevent it being upgraded to a version that won't work with your hardware.

---

### Post by Infil on 2010-01-05
Success! Sort of.

I've tried acpi=off, noapic and nolapic, and combinations thereof. It appears that the regualar 9.10 live CD works correctly if I set nolapic. The other to may then be set or not set.

But isn't acpi=off a "shortcut" for both noapic and nolapic?  If that is the case then this was all a coincidence because setting acpi=off (with and without noapic) does not fix the problem, only nolapic remedies it.

I will try a 9.10 beta CD later this evening.

---

