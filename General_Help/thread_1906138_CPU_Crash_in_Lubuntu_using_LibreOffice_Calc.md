---
title: "CPU Crash in Lubuntu using LibreOffice Calc"
date: 2012-01-08
forum: General Help
---

### Post by M_Mynaardt on 2012-01-08
Hi, all!

My Lubuntu install on my laptop (a Toshiba Satellite A-100) has a little problem from time to time when I'm using *LibreOffice Calc*.  If I use it long enough, the CPU seems to get plugged.  At least the bar on my Conky display showing CPU usage goes solid.

This only seems to happen when I'm using *Calc*.  I've not seen this happen with any other app on my Lubuntu install.

Anyway, when this happens, Lubuntu won't respond to any kind of input and I have to power down the computer and reboot it.

Does anyone know why Lubuntu would behave this way?  I was wondering if, perhaps, it is some sort of Java problem?  I say this because if I'm doing major revision to a spreadsheet file, the graphics display becomes quite sluggish.

And is there any sort of solution to preventing this little "oopsies" from happening again?

Thanks in advance!

---

### Post by Rodney9 on 2012-01-08
Looks like a bug in LibreOffice Calc - 

[https://www.libreoffice.org/bugzilla/show_bug.cgi?id=37651](https://www.libreoffice.org/bugzilla/show_bug.cgi?id=37651)



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by marinara on 2012-01-10
if you type ctrl+alt+f1 you can go to the console, and you can login and check which process is locked up.

---

### Post by M_Mynaardt on 2012-01-11
> **marinara said:**
> if you type ctrl+alt+f1 you can go to the console, and you can login and check which process is locked up.

I just found out I'm not overly familiar (as in not familiar one little bit) with this console business.  I could get into it easily enough with ctrl+alt+f1 but then had no idea how to get out of that to get back into the GUI.

So…  How do I check the processes and how to get out out of the console to get back into the GUI (for future reference and all that)?

Thanks...

---

### Post by marinara on 2012-01-11
login (obviousy)

$sudo top

look for a process with 99% cpu.
but don't kill it.

I'm no expert but I think you can get a login by killing the x.org process, and then pressing ctrl+alt+f7 to get back to the login manager

---

### Post by vasa1 on 2012-01-11
> **Rodney9 said:**
> Looks like a bug in LibreOffice Calc - 
[https://www.libreoffice.org/bugzilla/show_bug.cgi?id=37651](https://www.libreoffice.org/bugzilla/show_bug.cgi?id=37651)
...
That bug relates to opening an 18 MB .xls file and may not be relevant to OP.

---

### Post by vasa1 on 2012-01-11
> **M_Mynaardt said:**
> ...
And is there any sort of solution to preventing this little "oopsies" from happening again?
...
Assuming you want to continue using lubuntu and Calc, will frequently saving, exiting and re-opening your work provide a temporary "workaround"?

Does your spreadsheet have a lot of charts?

And how much RAM do you have?

---

### Post by M_Mynaardt on 2012-01-11
> **marinara said:**
> login (obviousy)

$sudo top

look for a process with 99% cpu.
but don't kill it.

I'm no expert but I think you can get a login by killing the x.org process, and then pressing ctrl+alt+f7 to get back to the login manager

That looks straight forward...  I'll give that a go in a little bit.

Thanks!

---

### Post by M_Mynaardt on 2012-01-11
> **vasa1 said:**
> Assuming you want to continue using lubuntu and Calc, will frequently saving, exiting and re-opening your work provide a temporary "workaround"?

Does your spreadsheet have a lot of charts?

And how much RAM do you have?

That does seem to work, yes.  Although it can be a bit tedious.

This just happens when I'm working on a file with several sheets; no charts.  And usually when I've been working on editing and doing major changes to a Calc file.  If I just open a Calc file, add a bit of data, save, and close it, there doesn't seem to be any snags then.

My computer is a Toshiba Satellite A-100, with 1.5 GB RAM.  There's usually oodles of RAM to spare when running Lubuntu.  So I was a bit surprised when this happened.  Somehow, the CPU just seems to totally max out.  I'll try the other tip from above, using the console thing to see if I can find what's clogging up the CPU sort of thing.

---

### Post by vasa1 on 2012-01-11
> **M_Mynaardt said:**
> ...  I'll try the other tip from above, using the console thing to see if I can find what's clogging up the CPU sort of thing.
What about LibreOffice Quick Starter? Do you have that thing turned on? There have been reports of things being better off with it disabled.

---

### Post by M_Mynaardt on 2012-01-12
> **vasa1 said:**
> What about LibreOffice Quick Starter? Do you have that thing turned on? There have been reports of things being better off with it disabled.

I never thought of that.  I usually just use that to open a recent file sort of thing.

---

