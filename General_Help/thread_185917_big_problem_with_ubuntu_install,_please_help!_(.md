---
title: "big problem with ubuntu install, please help! :("
date: 2006-06-01
forum: General Help
---

### Post by hypertevi on 2006-06-01
dear ubuntu community

gotta big problem.. i can't install the new ubuntu dapper drake on my pc, coz i get an error message. the cd is not able to boot correct. it hangs at the 'mounting root file system'. i documentated the procedure with my mobile phone:

[IMG]http://hypertevi.net/kepek/Image(17).jpg[/IMG]
[IMG]http://hypertevi.net/kepek/Image(18).jpg[/IMG]
[IMG]http://hypertevi.net/kepek/Image(19).jpg[/IMG]
[IMG]http://hypertevi.net/kepek/Image(20).jpg[/IMG]
[IMG]http://hypertevi.net/kepek/Image(21).jpg[/IMG]
[IMG]http://hypertevi.net/kepek/Image(22).jpg[/IMG]

the install cd is 100% heal, because i used it already on my laptop.

the optical drive in my desktop pc is a standard drive by hewlet packard. i already tryed other cdroms, but the same error.

please help, i want to loose windows forever! :)

sorry for my bad english, i just learned it as a hobby.. :[

tibi =)

---

### Post by kornelius on 2006-06-01
I have the same problems. CD is fine, i used it at my other computer, but when i try on my laptop it hangs on "mounting root file system..."

---

### Post by TheNewGuy on 2006-06-01
There are kernel boot options that will fix this I dont remember the exact command line but you can find a list of all the options in the kernel source area.

A couple to try would be "irqpoll" or "noacpi" or "noapic" or "acpi=noirq" I dont know if those are exact. I dont have a linux machine handy right now but those are some of things I had to try to get my laptop to work with out that message about a confused drive.

---

