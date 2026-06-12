---
title: "shutdown problem Karmic"
date: 2010-11-11
forum: General Help
---

### Post by Scallyph on 2010-11-11
Hello,

Hope someone has solving suggestion.

Previous:
I've upgraded Ubuntu 9.04 to 9.10. That worked fine and i've never had shutdown problems before upgrading on this system.
Used it for 2 days or so without a problem. I dont remember me (de)installing/changing anything in those 2 days exept for decompressing a gzip file.  

Problem:
Now it wont shutdown.(or better said, powerdown) Hangs at &quot;system halted&quot; 

tried:
sudo shutdown -h now = does not work
reboot system > not log in > shutdown  = does not work
reboot system into recovery mode > sudo shutdown -h = does not work
Deactivate proprietary drivers > reboot = does not work
to the /boot/grub/menu.lst I added: 
acpi=force apm=power_off  < exactly as I typed it here = does not work
also added: 
GRUB_CMDLINE_LINUX=&quot;noacpi acpi=off acpi=force apm power_off=1&quot; < exactly as I typed it here = does not work
and tried: 
GRUB_CMDLINE_LINUX=&quot;noacpi acpi=off apm power_off=1&quot; < exactly as I typed it here = does not work

etc/modules.conf is empty (looking at the woring one?)
etc/default/grub is empty (looking at the woring one?)
and if would find the right one, what line would I be looking for.


Can I still add the single line:&quot;apm_off=1&quot; in the etc/modules.conf. If yes, how would the complete line exactly look like?

Since etc/default/grub is empty and boot/grub/menu.lst is not, I'm using Grub legacy? 
Whatelse can I do to solve this problem?

---

### Post by TeoBigusGeekus on 2010-11-11
The correct command is
```
sudo shutdown -h now
```

---

### Post by Scallyph on 2010-11-11
> **TeoBigusGeekus said:**
> The correct command is
```
sudo shutdown -h now
```


I did use that command.
Also tried:  sudo shutdown -p now.

(Corrected commandline in thread)

Thnx

---

### Post by alphaamanitin on 2010-11-11
> **Scallyph said:**
> I did use that command.
Also tried:  sudo shutdown -p now.

Thnx

According to my _Linux in a Nutshell_ it should be:

```
sudo shutdown -P now
```

I know that the BASH terminal is subject to letter case, so maybe give that a try?

AlphaA

---

### Post by Scallyph on 2010-11-11
> **alphaamanitin said:**
> According to my _Linux in a Nutshell_ it should be:

```
sudo shutdown -P now
```I know that the BASH terminal is subject to letter case, so maybe give that a try?

AlphaA

Thnx 

But that doesn't work either.

But it does give me information on my display. 
Unfortunatly I dont know how to dump it to a file
It starts with : Call trace , if try to repeat it, the "shutdown -P now" (from terminal) it doesn't show up any more.
While writting this.
I booted into recovery mode and then drop to root. It shows the info again starting with
[ 84.567004] Call Trace:
[ 84.576004]<c0571fe2>] ? hrtimer_cpu_notify+0x7a/0x8b
going on for about 20 lines or so. Every line has different infoermation accept for the 
[84.576004]

---

### Post by Scallyph on 2010-11-11
btw:
 sudo shutdown -v now brings system to Recovery menu.

From terminal or commandline the result on option "-v" is the same.

---

### Post by Scallyph on 2010-11-11
Update:
booting with kernel 2.6.31-22 or kernel 2.6.31-22 recovery generates the shutdown problem.
Using kernel 2.6.28-19 does not generate this shutdown problem on my system.
So I was planning to remove the.... 31-22 kernel. 
But listing all kernel images by doing: dpkg --list | kernel-image gave me no overview of the images.
ls vmlinuz* did.
Then I ran sudo apt-get remove linux-image-[version]-generic
then sudo update-grub
Then checked menu.lst deleted the lines refering to the kernel i just removed. 
(I think this would'nt be needed, but I choose to keep the modified menu.lst when it was ask wich one to keep)
system is shuttin down now. Still dont know what caused it in the first place thou.

---

