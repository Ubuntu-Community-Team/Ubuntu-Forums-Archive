---
title: "Power Down Problem"
date: 2009-11-22
forum: General Help
---

### Post by hasbeenhonshu on 2009-11-22
[SIZE=4]Hello All,[/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4]I am a longtime prisoner of the Windows operating system syndrome and have grudgingly submitted to whatever that company (Microsoft) has decided to do to my experience with using a computer for many years. I view a computer as a tool not a mate, peer, comrade, buddy, etc. I have never wanted to become a computer or software engineer in order to use a computer to accomplish a task in my work. I am a professional electronic technician by the by. I include this prelude to set the perspective on my desire to learn the Linux operating system enough in order to be able to escape the MS Windows syndrome I am stuck in, currently Windows Vista Home Premium.[/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4]My Ubuntu Linux Problem: I have recently installed Ubuntu Jaunty Jackalope 9.04 onto a second partition on one of my laptops and am experiencing a Twilight Zone like problem which has me up against the wall. My computer has taken to shutting itself down after roughly a half hour of running Ubuntu 9.04. The keyboard got unusually hot in certain spots so I opened up the machine and observed the fan inside my machine turning off every time that I would attempt to boot the computer with Ubuntu at the GRUB menu. As soon as I hit the Enter key the fan stops. This does not occur when I boot with Windows Home Premium which I would consider par for the course. I can only use this setup when I force feed the machine cooling air via an external fan. Most irritating.[/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4]Okay, I believe that the CPU in my machine is getting overheated and consequently powering off the machine because the fan stops. I talked to customer service reps at Acer and Microsoft about trying to get info on the particulars on any built in temperature failsafe designed into my machine and I went to Intel for the CPU info and got nowhere with anybody I suppose because they wanted money to take the time to tell me what I needed to know. Nevertheless my cooling fan inside my computer is being turned off when I boot Ubuntu.[/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4]Does this arcane condition sound familiar to anybody? If so would you please help me make sense out of this, uh, anomaly. I know this laptop is not exactly skippy and I would like to put numerous large holes in it but until I have the money to purchase a better machine I am force to experiment with the Acer because my other machine, an HP laptop I use in my college work and I cannot jeopardize my studies with experimentation on a new operating system.[/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4]My computer: [/SIZE]
[SIZE=4]· Acer[/SIZE]
[SIZE=4]· Model = Aspire 5315-2326[/SIZE]
[SIZE=4]· Processor = Intel Celeron 550 @2Ghz[/SIZE]
[SIZE=4]· System RAM = 2GB[/SIZE]
[SIZE=4]· 160 GB hardrive[/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4]I set the main Ubuntu partition to a 68 GB Ext3 journal file system and a swap file partition of 1GB. If I left out any info required for this please specify.[/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4]Thank you[/SIZE]

---

### Post by blazemore on 2009-11-23
[SIZE=4]Hello. There is a tutorial written on this forum about controlling your fan speed.
I hope you find it helpful.
here is the link: [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)
[/SIZE]

---

### Post by crank_it_up on 2009-11-23
Hi, I had the same problem with an acer. The rebuilt kernel in this thread fixed it

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)

---

