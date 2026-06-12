---
title: "KDE enviroment using high CPU"
date: 2006-05-15
forum: General Help
---

### Post by sabredog on 2006-05-15
Decided to give KDE a go and installed the KDE desktop package via several of the good guides on the forum.

All went well and KDE works nicely...except when I run an app, CPU use goes through the roof and hovers between 90-100%. I do not get this using Gnome!

My Ubuntu box is a Duron 1.3Ghz based PC with 768Mb RAM and a 32mb Nvidia Gforce2 mx220 video card.

I would like to continue using KDE as my wife likes that desktop enviroment.

Can anyone help at all to resolve this problem?

---

### Post by Gannin on 2006-05-15
What process is using all of the cpu?  To find out, open an application so all of your cpu is being used, then open a terminal and type "top".  See what process is on the top of the list and using the most cpu.  When you're done, "q" exits.

---

### Post by sabredog on 2006-05-15
[QUOTE=Gannin]What process is using all of the cpu?  To find out, open an application so all of your cpu is being used, then open a terminal and type "top".  See what process is on the top of the list and using the most cpu.  When you're done, "q" exits.[/QUOTE]

Will try that out ands report on it when I get home tonight.

thanks

---

### Post by ComplexNumber on 2006-05-15
on the commandline, type "free"(without the quotes). then get a screenshot or simply copy down the usage here.

---

### Post by sabredog on 2006-05-16
[QUOTE=ComplexNumber]on the commandline, type "free"(without the quotes). then get a screenshot or simply copy down the usage here.[/QUOTE]

```
madmike@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        776548     506104     270444          0      22632     352812
-/+ buffers/cache:     130660     645888
Swap:       417648          0     417648
madmike@ubuntu:~$

```

As requested

Though it is CPU use which is the issue, not RAM

cheers and thanks

---

### Post by sabredog on 2006-05-16
[QUOTE=Gannin]What process is using all of the cpu?  To find out, open an application so all of your cpu is being used, then open a terminal and type "top".  See what process is on the top of the list and using the most cpu.  When you're done, "q" exits.[/QUOTE]

The process was Bittornado

When ran again, CPU was good, around 20% with Firefox active as well.

I have been playing with KDE's eyecandy transparent menu's and this seems to have degraded performance a bit. Seems the 32Mb Nvidia card is a tad underpowered.

Not sure what caused the 100% CPU use and if it will occur again!

---

### Post by Gannin on 2006-05-16
If it does occur again, make sure to check "top" again, and post about what you find.

---

### Post by sabredog on 2006-05-16
[QUOTE=Gannin]If it does occur again, make sure to check "top" again, and post about what you find.[/QUOTE]

Found the problem. It was Karamba causing the issue.

No fancy widgets for KDE. In Gnome the gdesklets behave well....sigh...

---

### Post by njf on 2006-05-16
I can confirm that, and it is breezy specific. In dapper, karamba performs *much* better.

---

