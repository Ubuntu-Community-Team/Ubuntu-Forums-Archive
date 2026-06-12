---
title: "Strange colours on gtk applications"
date: 2012-01-13
forum: General Help
---

### Post by TdeM on 2012-01-13
Hi all,

I've recently installed lubuntu (oneiric ocelot) on my parent's computer. All updates are installed and it runs fine. The only problem is that often programs that use gtk get strange stripes and colours (mainly pale blue/green and red) across buttons and text fields. Any text becomes unreadable. Moving the mouse over the affected area sometimes turns it back to normal temporarily. I couldn't find anything searching, so here I am.

The computer is a somewhat aged desktop. Athlon Xp, 1.6ghz I think with 512mb ram. There is a dedicated graphics card but I'm not sure what exactly.

I am quite familiar with linux including digging into the internals, but don't use ubuntu myself.

Thank you for your time,
Thomas

---

### Post by ajgreeny on 2012-01-13
This sounds much like a graphic card driver issue, so it will help a great deal if you can find the card being used.

Can you show the output of ```
lspci
``` in terminal, or if that is no help ```
sudo lshw -C display
```

---

### Post by TdeM on 2012-01-14
Thank you for the reply. Here's the output of the latter command.

```
ouders@woonkamer:~$ sudo lshw -C display
[sudo] password for ouders: 
  *-display:0             
       description: VGA compatible controller
       product: RV280 [Radeon 9200 SE]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=32 mingnt=8
       resources: irq:16 memory:d8000000-dfffffff ioport:c000(size=256) memory:e9000000-e900ffff memory:e8000000-e801ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 SE] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=32 mingnt=8
       resources: memory:e0000000-e7ffffff memory:e9010000-e901ffff
ouders@woonkamer:~$ 

```

That sounds familiar, so it's probably correct (radeon 9200se). Some searching shows that there are no official drivers for a card this old. Is there anything else I could do?

Thomas

---

### Post by ajgreeny on 2012-01-14
Probably nothing at all, I'm afraid.

It's the exact same card as I have in my desktop, which runs all ubuntu version without a problem, right up to 11.10, but which is hopeless with unity or gnome-shell.  Gtk3 is the problem, I think.

The open source driver is the only option, so I am surprised that Lubuntu or Xubuntu will not run well on that machine and card, as both are fine on my machine.  I'm not sure I can help any more than that, I'm afraid.

---

### Post by TdeM on 2012-01-14
Well, it's not a big deal luckily. The problem doesn't appear 95% of the time, and my parents usually don't even notice. The nerd in me had to try and fix it though!
Thanks for your help,
Thomas

---

### Post by ajgreeny on 2012-01-15
Just a quick thought about the problem.

To get the best from my card I have a custom /etc/X11/xorg.conf file which does help a bit and gives better rendering speeds.  As the card is the same as mine you could always try using the same xorg.conf as I have, which I will attach as xorg.txt for you.  Just save it to the desktop, then rename and move it to /etc/X11/xorg.conf with ```
sudo mv /home/*username*/Desktop/xorg.txt /etc/X11/xorg.conf
```changing *username* to correct user, of course.  

My card is an AGP x8 card.  If yours is really different you may need to remove or comment out the ```
Option     "AGPmode"   "8"
```  at line 37.  You may also need to edit the display modes to fit your own resolution.

Now logout and in again to see if it helps.  If your graphics are worse with that file in place you can remove it with ```
sudo rm /etc/X11/xorg.conf
```

---

