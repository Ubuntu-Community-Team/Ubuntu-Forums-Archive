---
title: "Stop a program from running?"
date: 2010-01-16
forum: General Help
---

### Post by PDA1 on 2010-01-16
Here's the error message I get when trying to run Thunderbird 3.

Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system.


I can't find it running anywhere.  I tried a re-start and that was no help.

How do I stop it?

---

### Post by pietjanjaap on 2010-01-16
Start pulldown, system - administration - system monitor
Then go to "processes", right click on the process, kill process.

---

### Post by PDA1 on 2010-01-16
Already tried that.  The process "thunderbird" doesn't appear anywhere.

---

### Post by malspa on 2010-01-16
Does the command **pkill thunderbird** stop it?

---

### Post by PDA1 on 2010-01-16
No....it doesn't

---

### Post by forsaken_pariah on 2010-01-16
Although I don't use Thunderbird, I frequently have this problem with Firefox. The command killall firefox always does the trick for me.

---

### Post by bulls_eye on 2010-01-16
in the terminal type

ps -e

it gives some numbers corresponding to the processes

note the number corresponding to thunderbird and type

sudo kill <number>

hope that it works...

---

### Post by malspa on 2010-01-16
> **forsaken_pariah said:**
> Although I don't use Thunderbird, I frequently have this problem with Firefox. The command killall firefox always does the trick for me.

Yeah, that's exactly why I wondered if **pkill** would work here -- I've used it to stop Firefox before.

---

### Post by PDA1 on 2010-01-16
Thunderbird doesn't show its ugly head using any of the processes mentioned before....so I can't find it or kill it.

Man, all I want to do is install Thunderbird 3 (not Shredder).  I had it working earlier today and them I just HAD to go an mess with the files.

---

### Post by gauthamnagpur18 on 2010-01-16
use kill all process ... i think it will solve the problem ...

---

### Post by PDA1 on 2010-01-16
What's the exact process for doing that?

---

### Post by forsaken_pariah on 2010-01-16
> **PDA1 said:**
> Man, all I want to do is install Thunderbird 3 (not Shredder).  I had it working earlier today and them I just HAD to go an mess with the files.

Have you tried rebooting your system and seeing if it's still running then?

---

### Post by bulls_eye on 2010-01-16
If nothing works then remove thunderbird and reinstall it..

thats what I would do...

---

### Post by PDA1 on 2010-01-16
Yes, I restarted 3 times and with the same results.

---

