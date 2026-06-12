---
title: "Microsoft Virtual pc Won't run Inside 7 but did in vista"
date: 2010-01-14
forum: General Help
---

### Post by Hyper Tails on 2010-01-14
I got windows 7 32-bit on my laptop (While having kubuntu 9.10) and I've been using microsoft virtual pc for 2 years now and I got 7 on my desktop and it runs like it did back in vista but why can't i run it inside 7 on my laptop?

It didn't work before on my desktop but eventually did

I tried windows virtual pc but neither of my computer will run it!!

every time i click it it says this program is blocked due to compatibility issues

According to the compatibility center from microsoft, it say it's compatible and requires no action.

see for yourself:
[http://www.microsoft.com/windows/compatibility/windows-7/en-us/Details.aspx?type=Software&p=Microsoft%20Virtual%20PC%202007&v=Microsoft&uid=6&pf=0&pi=0&s=microsoft%20virtual%20pc%202007&os=32-bit](http://www.microsoft.com/windows/compatibility/windows-7/en-us/Details.aspx?type=Software&p=Microsoft%20Virtual%20PC%202007&v=Microsoft&uid=6&pf=0&pi=0&s=microsoft%20virtual%20pc%202007&os=32-bit)

help will be appreciated

PS: I use virtual pc to run windows 3.1, 95 and 98

---

### Post by pirateghost on 2010-01-14
> **Hyper Tails said:**
> I got windows 7 32-bit on my laptop (While having kubuntu 9.10) and I've been using microsoft virtual pc for 2 years now and I got 7 on my desktop and it runs like it did back in vista but why can't i run it inside 7 on my laptop?

It didn't work before on my desktop but eventually did

I tried windows virtual pc but neither of my computer will run it!!

every time i click it it says this program is blocked due to compatibility issues

According to the compatibility center from microsoft, it say it's compatible and requires no action.

see for yourself:
[http://www.microsoft.com/windows/compatibility/windows-7/en-us/Details.aspx?type=Software&p=Microsoft%20Virtual%20PC%202007&v=Microsoft&uid=6&pf=0&pi=0&s=microsoft%20virtual%20pc%202007&os=32-bit](http://www.microsoft.com/windows/compatibility/windows-7/en-us/Details.aspx?type=Software&p=Microsoft%20Virtual%20PC%202007&v=Microsoft&uid=6&pf=0&pi=0&s=microsoft%20virtual%20pc%202007&os=32-bit)

help will be appreciated

PS: I use virtual pc to run windows 3.1, 95 and 98

make sure you are using the newest version.  VPC works fine (its how they got XPVM functionality in 7)..  

[http://www.microsoft.com/windows/virtual-pc/download.aspx](http://www.microsoft.com/windows/virtual-pc/download.aspx)

---

### Post by Hyper Tails on 2010-01-14
i said i tried xp mode and it doesen't work
My processor isen't compatable for some Beeping reason

---

### Post by pirateghost on 2010-01-14
> **Hyper Tails said:**
> i said i tried xp mode and it doesen't work
My processor isen't compatable for some Beeping reason
that means it doesnt support Virtualization Technology OR it is simply not enabled in your BIOS.  check your BIOS first, you may have a setting for VT, if you do, turn it on and XPVM should work just fine

---

### Post by MasterNetra on 2010-01-14
Did you try running it in Vista mode? Addtionally you could try running it as admin as well. See if that helps any.

---

### Post by running_rabbit07 on 2010-01-14
Run it in a VBox.

---

### Post by Hyper Tails on 2010-01-15
> **running_rabbit07 said:**
> Run it in a VBox.

I use vbox for 2000,xp,vista and distros of linux

I tried 3.1, 95 and 98 but the sound woulden't work, graphics, and other issues

Thats why i use virtual pc in 7 
> 
that means it doesnt support Virtualization Technology OR it is simply not enabled in your BIOS. check your BIOS first, you may have a setting for VT, if you do, turn it on and XPVM should work just fine

My laptop was from december 2007 and my desktp was from june 2008

I don't think they'll have that option in my bios

---

### Post by pirateghost on 2010-01-15
> **Hyper Tails said:**
> My laptop was from december 2007 and my desktp was from june 2008

I don't think they'll have that option in my bios

doesnt matter, i have machines from 2005 with VT...its a function of the processor and if your processor supports it, the BIOS will allow you to set it

---

### Post by Hyper Tails on 2010-01-16
> **pirateghost said:**
> doesnt matter, i have machines from 2005 with VT...its a function of the processor and if your processor supports it, the BIOS will allow you to set it

my desktop processor is an intel core duo 2 e4600
my laptop processor is an intel pentium dual-core t2330

---

### Post by Sef on 2010-01-16
Locked.   This subforum is for Ubuntu, Kubuntu, Edubuntu and Xubuntu.  If you wish to appeal this decision, then go to the Resolution Center under Forum Feedback & Help.   Thank you for being a part of the Ubuntu Community.

---

