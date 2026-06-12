---
title: "Changing OS's! Win 7/Ubuntu/Mac"
date: 2011-11-21
forum: General Help
---

### Post by EpikRageQuit on 2011-11-21
Okay, So I have a few questions!

First off, thank you guys for previous help. I love these forums, the people are so willing to help and I greatly appreciate the quick timing and detailed answers I get!

So my issue. I have done this before but don't remember all the steps. What I'm trying to do is, remove Linux from my laptop. It dual boots Win 7 and 11.04. Since I have started college I really haven't played around with Linux since I put it on. My plan is to remove Linux and put on a Mac OS.. Any ideas, or where to start are greatly appreciated, Thanks in advance!

Also, I have done some googling I didn't just run here. I am curious if there is an easier way then removing the partition as a whole and then recovering the windows loader. Also because when I did this before I was unable to stretch my windows 7 partition back over the unalocated space!

THANKS!

---

### Post by mikegior on 2011-11-21
Hello,

Did you install Linux via Wubi (within Windows) or from a CD?

---

### Post by EpikRageQuit on 2011-11-21
I installed wih a live CD.. Wubi in my opinion isn't as good.

---

### Post by Elfy on 2011-11-21
> if there is an easier way then removing the partition as a whole and then recovering the windows loader.not that I am aware of - and I'd do it the other way around :)

> when I did this before I was unable to stretch my windows 7 partition back over the unalocated space!I'd not be able to offer much help here - but I'd have to assume that as long as the unallocated space is there next to the win7 partition it's disk tool would be able to do it - but that is in fact a guess ...

---

### Post by EpikRageQuit on 2011-11-21
> **forestpiskie said:**
> not that I am aware of - and I'd do it the other way around :)

Okay. So how do I recover the windows loader first then? When I did it on my other laptop I had to use a repair cd and I didn't like it. I was a little worried doing it that way...

---

### Post by Elfy on 2011-11-21
You have to use the repair cd afaik. 

I'd not be too worried about doing it that way - if you do it the other way round then you'd not be able to boot anything as grub will fail as the ubuntu install will have gone.

---

### Post by EpikRageQuit on 2011-11-21
Okay. So I make a repair cd, then delete the ubuntu partition, restart my computer, get in the bios? change boot order to the cd? and then I forget from there. Do I go into system repair I think and i run fixmbr or fixroot or something. Its been a while since I did it.I do have Windows 7, I'm pretty sure that makes a difference as to what commands i run

---

### Post by EpikRageQuit on 2011-11-21
Does anyone have some helpful link that go into a little more detail?

---

### Post by digithal on 2011-11-21
Check out **[this article]("http://www.sevenforums.com/backup-restore/62209-remove-grub-restore-windows-7-a.html")**, it's explained very well. :)

---

### Post by kagz on 2011-11-21
thats a helpful link that digithal has given...thanks:)

---

### Post by EpikRageQuit on 2011-11-21
> **digithal said:**
> Check out **[this article]("http://www.sevenforums.com/backup-restore/62209-remove-grub-restore-windows-7-a.html")**, it's explained very well. :)

Yes thank you. I have google it 1000 different times and this is te best link so ffar. Thank you!

---

