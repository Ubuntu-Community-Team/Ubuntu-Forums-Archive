---
title: "I cant execute files with wine, &quot;Executable bit&quot; help!!"
date: 2010-10-28
forum: General Help
---

### Post by Lancro on 2010-10-28
This looks like an issue of 10.10, in 10.04 I execute my windows aplications with wine without a problem, now I cant, see the screenshot, I need a solution, how I disable that security issue?, or how can I activate the executable bit, because it doesnt allow me to change anything of my windows files because this security issue, please help needed, I need that aplications running.

Thanks.

---

### Post by Verbeck on 2010-10-28
go to file properties>permissions tab then check allow execution of file as a program

---

### Post by Lancro on 2010-10-28
I have seen the other topic, It dont allow me to activate it, as I check it it unchecks itself, and trying to open it with "other program" wine, doesnt work as well, so Im a little worried..., please help anyone.

PD. The program is in the NTFS partition of windows vista, so I cant change properties...

Thanks.

---

### Post by matt_symes on 2010-10-28
Hi

Try using chmod from the terminal

chmod 755 <path and filename>

Kind regards

---

### Post by WorMzy on 2010-10-28
This tutorial should help you with this: [[COLOR="Blue"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251")

---

### Post by 3rdalbum on 2010-10-28
[http://www.chrislees.info/ubuntu/easy-run-files.shtml](http://www.chrislees.info/ubuntu/easy-run-files.shtml)

And follow the bit about Wine.

The reason why you can't change the executable bit is because (a) the mounted CD is read-only and (b) it uses a filesystem that doesn't possess an 'executable bit' that can be set or unset.

On a different note, it looks like you're using a different default language, but the message you saw was in English. Maybe file a bug about the message not being in your system language?

---

### Post by Lancro on 2010-10-28
> **3rdalbum said:**
> [http://www.chrislees.info/ubuntu/easy-run-files.shtml](http://www.chrislees.info/ubuntu/easy-run-files.shtml)

And follow the bit about Wine.

The reason why you can't change the executable bit is because (a) the mounted CD is read-only and (b) it uses a filesystem that doesn't possess an 'executable bit' that can be set or unset.

On a different note, it looks like you're using a different default language, but the message you saw was in English. Maybe file a bug about the message not being in your system language?

Maybe, my languaje is spanish, and it appears in english, It may be a bug, your solution worked, the others didnt, thanks all for your help, now Im in the game, the wine trick was good.

---

### Post by ricey155 on 2011-02-16
> **Verbeck said:**
> go to file properties>permissions tab then check allow execution of file as a program

you my friend are a god :p just solved my problem straight away 

many thanks glad i kept searching :popcorn:

---

### Post by coth on 2011-07-02
> **3rdalbum said:**
> ...The reason why you can't change the executable bit is because (a) the mounted CD is read-only and (b) it uses a filesystem that doesn't possess an 'executable bit' that can be set or unset.
...

So, what if I HAVE to change the bit in order for it to work?, say that I have an iso of a cd with an exe-file on it. I mount it and want to run the exe-file but can't, cause I can't change the bit... any way to work around this?

---

### Post by 3rdalbum on 2011-07-02
> **coth said:**
> So, what if I HAVE to change the bit in order for it to work?, say that I have an iso of a cd with an exe-file on it. I mount it and want to run the exe-file but can't, cause I can't change the bit... any way to work around this?

You DON'T have to change the executable bit in order for it to work. Just follow the instruction on the web page I linked to (basically, typing 'wine' into the terminal, leaving a trailing space, and then drag the exe file onto the terminal).

---

### Post by Morbius1 on 2011-07-02
The problem is something called "cautious-launcher". Fix the thing permanently:

Right click an *.exe file and select Properties -> Open With -> Add -> Use a custom command > type in: wine

In the "Open With" tab mark the "wine" [COLOR=Blue]you just added [COLOR=Black]as the default[/COLOR][/COLOR] ( from the Wine that's already selected) now every time you run an exe it should select the wine without the cautious launcher script.

---

### Post by avix on 2011-12-12
oh man that solved my problem with trying to get Diablo II to get past the executable problem!. now I just gotta figure out how to get it to go to disk 2 lol.

thank you much for the information:popcorn:

---

