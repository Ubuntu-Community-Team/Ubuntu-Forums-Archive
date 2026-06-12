---
title: "power issues"
date: 2009-10-29
forum: General Help
---

### Post by techrascal on 2009-10-29
hi all
i have a brand new sony vaio vgn z46gd
its dual booted with vista nd ubuntu 9.04
my battery life on vista is approx 4 hrs but with ubuntu its hardly 1.5 hrs
is there some bug with the power manager
plz tell what all information is needed to resolve this issue
i dont have an idea where to start debugging from....
thnx in advance..
cheers

---

### Post by hwttdz on 2009-10-29
Try looking at the powertop program.  That might be a place to start.  Also make sure that you have cpu frequency scaling working correctly.

---

### Post by techrascal on 2009-12-08
i was unable to respond further because i had limited access to internet for all this while.
the power top output is attached with this reply.
additional info:- i am running 32 bit version on my 64 bit processor, and my system has 6 gb ram..
kindly take a look at the txt file and help me locate the problem.
thanks

---

### Post by hwttdz on 2009-12-08
That's a little strange as my pc is at like 180 wakeup per second with firefox, rhythmbox a few terminals and thunderbird running.  If you run sudo powertop it will give you suggestions as to how to decrease power consumption. Of course powertop is a buggy program, however there isn't an alternative I know of.

---

### Post by techrascal on 2009-12-09
hi..
so the issue is the large number of wake ups..okk..
i am absolutely not able to use my brand new laptop while i'm moving on ubuntu nd i have to switch back to windows..its becoming really difficult for me.
powertop does give me suggestions and i tried 2 of them which didnt show drastic results.
so how do i get my system in a usable state...
sorry for being so noobish. but i cudnt make any improvements by trying out the suggestions given in powertop output.
please help me out in trying to correct this issue.
thanks

---

### Post by hwttdz on 2009-12-09
Well starting at the top, why don't you give this about rescheduling interrupts a read
[https://help.ubuntu.com/community/ReschedulingInterrupts](https://help.ubuntu.com/community/ReschedulingInterrupts)

Is this 9.10? or 8.10 as per sig?

---

### Post by techrascal on 2009-12-09
ohh..sry..
didnt update my sig..
i moved on to new system nd to 9.04.
i'll try out this thing nd gt back..
thanks a lot ..

---

### Post by techrascal on 2009-12-21
hi
1.i tried booting with noapic -- reduced powerconsumption by few watts and comparitively lesser kernel ipi interrupts.
but now there are some 300 interrupts from keyboard/touchpad/mouse 
so the power consumption remains in the order of 20-30 watts with nominal usage also and interrupts in the order of 500s.

2.when i booted with acpi=off kernel parameter it stopped showing the battery charge state in the top panel and not even in powertop.

3.when i booted with "acpi=noirq" there was minor improvement in power consumption but no major changes in interrupts somehow.



i have changed all these parameter in the menu.lst file and added these parameters to the kernel part of it.

am i setting these things wrong or the problem is something else..

additional info if skipped earlier --- i am using 32 bit version ubuntu 9.04 with 64 bit processor(intel centrino2)


thanks for help.

---

