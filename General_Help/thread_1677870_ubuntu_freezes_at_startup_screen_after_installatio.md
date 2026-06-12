---
title: "ubuntu freezes at startup screen after installation"
date: 2011-01-29
forum: General Help
---

### Post by kaboo2 on 2011-01-29
hello, so i just installed ubuntu 10.04.1 using the wubi installer for windows. installation finished without problems so i restarted my laptop as i was aked to. then i selected to run ubuntu, there was the black screen "completing installation" and then came the startup where it stopped working.

i tried reinstalling but it did not help.

---

### Post by mikewhatever on 2011-01-29
Hi and welcome to the forum.
Can you provide some info about the computer. What model is it? How much RAM, and what cpu and gpu does it have?

---

### Post by sikander3786 on 2011-01-29
Another warm welcome to the forums :-)

In addition to what *mikewhatever* asked above, we'll be interested to know that are you facing just a blank screen, black screen or a blinking cursor or there is something on the screen? If there is something, what is it?

---

### Post by kaboo2 on 2011-01-29
sure

4gb ram
intel core2 duo (2.26ghz)
nvdia geforce 9600m gt (512mb)

this is where it freezes, just all the dots are red 

[IMG]http://jantechblog.files.wordpress.com/2010/03/ubuntu1004branding-large_004.jpg[/IMG]
[IMG]http://www.neowin.net/images/uploaded/UbuntuBoot.png[/IMG]

---

### Post by sikander3786 on 2011-01-29
I would first suggest to try the *nomodeset* boot parameter.

Press and hold down Shift key from Bios screen until you see the Grub menu. Highlighting the first entry there, press 'e' to edit it. Using arrow keys, navigate to "quiet splash" delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot. Lets see if you can get to the desktop this time.

Or if that doesn't help, repeat the same process, just don't delete "quiet splash" and type "acpi=off" at the end of that line (without quotes). Press Ctrl + X to continue boot.

Let us know how that goes. If that helps, you might need to install the graphics driver or make those changes permanent.

---

### Post by kaboo2 on 2011-01-29
with no mode set  there were some commands running until it came to 
```
init: ureadahead-other main process (3611) terminated with status 4
init: ureadahead-other main process (3612) terminated with status 4
init: ureadahead-other main process (3613) terminated with status 4
*setting sensors limit                                                            [ok]
```i waited for a while (~5min), but nothing happened, just caps and scroll lock indicators were flashing.


with acpi=off i got the same result as i posted in first post

---

### Post by sikander3786 on 2011-01-29
Delete "quiet splash" and try these terms one by one.

nomodeset xforcevesa noapic

nomodeset xforcevesa acpi=off

Which graphics card is there? And is there any wireless card inserted or built-in?

---

### Post by kaboo2 on 2011-01-29
graphic card - nvdia geforce 9600m gt (512mb)
wireless card - 802.11 b/g/n Wireless LAN with Bluetooth    (though im not sure if i understood "wireless card" correctly)

---

### Post by sikander3786 on 2011-01-29
I don't know if that Wireless card is built on your motherboard or it is a PCI one. If it is PCI, can you please remove it and try booting Ubuntu again? Or if it is motherboard integrated, you can turn it off in Bios menu and try booting again as wireless cards are sometimes known to cause problems like these.

Did you try the other 2 boot parameters in my above command?

---

### Post by kaboo2 on 2011-01-29
first i replied then tried. 
the "noapic" option worked, but now i have to change it everytime i restart pc, because if i dont i get error message: 

**ubuntu is running in low graphic mode**
the following errors were encountered....
(EE)VESA: Kernel modesetting driver in use, refusing to load.
(EE) No devices found.


then i press ok and get options how to continue:
-run ubuntu in low graph mode for one session
-... (i dont remember the others)
-reboot

---

### Post by sikander3786 on 2011-01-29
Ok try once more, don't add anything except *noapic* in your Grub line. Don't delete quiet splash and just add noapic at the end of that line. Don't add nomodeset or xforcevesa. Does it still boot successfully?

We'll make that change permanent once we know which parameter is working as there were 3 of them.

---

### Post by kaboo2 on 2011-01-29
nope it does not, got the error message i mentioned earlier

---

### Post by sikander3786 on 2011-01-29
> **kaboo2 said:**
> nope it does not, got the error message i mentioned earlier
Can you figure out which parameter is helping you boot successfully? It is noapic, xforcevesa, nomodeset, acpi=off or all of them?

---

### Post by kaboo2 on 2011-01-29
done some restarts and it looks like "nomodeset" alone works

---

### Post by sikander3786 on 2011-01-29
> **kaboo2 said:**
> done some restarts and it looks like "nomodeset" alone works
Ok. Then boot Ubuntu with nomodeset options and once on the desktop, go to System > Administration > Additional Drivers/Hardware Drivers and activate the current/recommended drivers. Reboot once installtion finishes and the issue should go away for ever.

---

### Post by kaboo2 on 2011-01-29
thank you very much :)

---

### Post by sikander3786 on 2011-01-29
> **kaboo2 said:**
> thank you very much :)
You are Welcome :-)

Please mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by ambein on 2011-05-07
A similar problem, with the ubuntu logo freezing after boot sequence, was solved with one of these suggestions. 

The solution was to change the GRUB boot file line from "quiet" to "quiet splash acpi=off".

Thanks!

Ubuntu 10.04 LTS (Lucid Lynx)
Dell Precision T7400, 4X Intel Xeon CPU
Dell 1920X1200 display

---

