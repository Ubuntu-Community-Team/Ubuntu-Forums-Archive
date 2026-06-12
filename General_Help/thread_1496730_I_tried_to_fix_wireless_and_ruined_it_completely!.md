---
title: "I tried to fix wireless and ruined it completely!"
date: 2010-05-29
forum: General Help
---

### Post by lgalicki on 2010-05-29
Hello guys!

I know there's a lot of thread about this subject, but it's so vast I'm not even sure what I should try. I'm also afraid of ruining my computer trying everything I read.

I was having that problem with slow wireless which a lot of people is having. Even working slowly, it was working and it was detected "out of the box". I got the windows driver and tried to use it with ndiswrapper (Windows Wireless Drivers) to see if things would get faster, but it didn't work, so I wanted to return to the generic driver. The thing is that the generic driver configuration has been apparently lost.

[FONT="Courier New"]lsusb[/FONT] brings me [FONT="Courier New"]Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter[/FONT], but [FONT="Courier New"]iwconfig[/FONT] tells me there are no wireless extensions.

What do I have to do to revive my wireless connection?

Thanks a lot in advance,
Luciano.

---

### Post by quixote on 2010-05-30
Dumb question, but have you tried to run the plain old Hardware Drivers utility? (System > Administration > Hardware Drivers)  Make sure you have a wired connection first, and it should go out and at least get you your generic driver back.  ??  At least, I hope so!

---

### Post by lgalicki on 2010-05-31
Thanks for the reply, Quixote. :)

I've already tried that, but nothing about the wireless card comes up. There's only an option to install my modem, which has been disabled since the begining because it conflicts with my soundcard.

When booting from a live CD, the wireless works properly. Maybe there's something I could copy from this boot to my "hard disk boot". Is there?

Thanks a lot,
Luciano.

---

