---
title: "one billion windows"
date: 2009-07-03
forum: General Help
---

### Post by derekeverett on 2009-07-03
I just had the strangest thing happen.

I was copying a file from my external hard drive to my desktop. I dragged the file to the desktop and the file transfer started. About half way through the transfer a second window for the contents of my external drive popped up. I closed it. Then a third window popped up. Then they started popping up faster than I could close them. In a few seconds I had more than I could count.

I launched a terminal so I could look at my processes and a few dozen terminals started to pop up...

ctrl/alt/backspace fixed it no problem but I'm curious as to what the hell happened. Anybody else had this occur or know what that was all about?

I think I'll do my copying from the command line from now on....

---

### Post by steveneddy on 2009-07-03
One [COLOR=Red]**billion**[/COLOR] windows?

So do you use Hardy or have you upgraded?

---

### Post by derekeverett on 2009-07-03
> **steveneddy said:**
> One [COLOR=Red]**billion**[/COLOR] windows?

So do you use Hardy or have you upgraded?

I'm still with Hardy. I tried Jaunty but didn't have any luck establishing a VPN connection with my workplace which I require...

---

### Post by steveneddy on 2009-07-14
Seriously - a BILLION windows?

You would still be ticking the little x's if it were actually a billion.

---

### Post by derekeverett on 2009-07-14
> **steveneddy said:**
> Seriously - a BILLION windows?

You would still be ticking the little x's if it were actually a billion.

killall firefox
:)

---

### Post by earthpigg on 2009-07-14
i <3 dramatic thread titles

---

### Post by vinutux on 2009-07-14
```
killall nautilus
```

---

### Post by JohnnySage50307 on 2009-07-14
Sounds like your system has a virus.  I don't know if you've every heard of the famed Fork-Bomb, but this is how it operates:

When Fork is executed, it opens a process exactly identical to itself at that exact moment in time; should the Fork syscall be in an infinite loop, the number of processes grow exponentially.
 
Given your symptoms, this sounds accurate.  However, given what you said, the only way I can supose that happened is if part of your kernel code was modified and reinstalled.
 
Given that could be the case, whenever you invoke a new process (the OS calls fork at that point), it could just keep looping around the creation of that process, thus opening windows at an exponential rate.
 
Granted, this is only speculation, but if this keeps repeating, I'd consider either opening in a restricted mode or flashing the HD and reinstalling your kernel.

---

### Post by vinutux on 2009-07-14
> **JohnnySage50307 said:**
> Sounds like your system has a virus.  I don't know if you've every heard of the famed Fork-Bomb, but this is how it operates:

When Fork is executed, it opens a process exactly identical to itself at that exact moment in time; should the Fork syscall be in an infinite loop, the number of processes grow exponentially.
 
Given your symptoms, this sounds accurate.  However, given what you said, the only way I can supose that happened is if part of your kernel code was modified and reinstalled.
 
Given that could be the case, whenever you invoke a new process (the OS calls fork at that point), it could just keep looping around the creation of that process, thus opening windows at an exponential rate.
 
Granted, this is only speculation, but if this keeps repeating, I'd consider either opening in a restricted mode or flashing the HD and reinstalling your kernel.


nope........itz not a virus

it is freez error in nautilus

---

### Post by danwood76 on 2009-07-14
I would highly doubt a virus.
Considering fork bombs are not transmitted as viri.

Its possible that you entered something into the terminal that started this processes.
Although I have noticed behavior like this with really old versions of firefox but not with the gnome terminal.

---

### Post by JohnnySage50307 on 2009-07-14
See, what concerned me was the fact that as he opened Terminal, multiple Terminal windows started popping up on him.  That isn't normal, hence my suspicion of something viral.

---

### Post by vinutux on 2009-07-14
Just Restart ....Force

or alt+ctrl+F1 then type 

```
sudo reboot
```

---

### Post by steveneddy on 2009-07-14
It could have been caused by the harmonic resonance left over if he were to have traveled through the irradiated vapor trail of a photon torpedo that was disapated in a small cloud of hydrogen gases, mainly inert.

But I'm just guessing. It happened to me only once.

---

