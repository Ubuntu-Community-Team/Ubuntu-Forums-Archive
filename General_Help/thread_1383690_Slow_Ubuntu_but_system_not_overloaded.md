---
title: "Slow Ubuntu but system not overloaded?"
date: 2010-01-17
forum: General Help
---

### Post by t1m on 2010-01-17
My mom's Ubuntu machine has been rather strange the last day or so. It takes a while to turn on, delaying apparently at loading "powernowd".

GDM seems to load fine, but then logging in to Gnome takes a long time. The panels ususally crash, as well as the desktop, but eventually everything loads again.

Most programs take a long time to load; also, "sudo" takes a long time to request a password, but after that the "sudoed" command runs normally.

Gksudo never seems to show up, so I can only access programs like "Software Sources" via terminal (e.g. *sudo program*).

Strangely, Gnome System Monitor says the processor and memory are not completly full.

Does anyone know what this is? Are there any commands I can run to diagnose it? I am happy to give information as needed.

Any thoughts?

---

### Post by cariboo on 2010-01-17
Using the system monitor adds extra overhead of it's own, can you paste the output of **top** in your next post? Open a terminal and type:

```
top
```

Please enclose the output in [noparse]```

```[/noparse] tags to make it easier to read.

---

### Post by t1m on 2010-01-17
Hi, thank you for the reply. Here's what I got:

Note: I did have an NTFS hard drive being mounted automatically from the /etc/fstab file. I noticed that there was an entry in top with "ntfs" in the name--and it was right near the top most of the time. I did try removing the line from fstab and rebooting...slowness was still there. I added the line back, and now the process doesn't appear in top. Hmmm.

```
top - 17:40:17 up 11 min,  2 users,  load average: 0.27, 0.28, 0.19
Tasks: 112 total,   2 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.5%us,  1.0%sy,  0.0%ni, 96.6%id,  0.0%wa,  0.5%hi,  0.5%si,  0.0%st
Mem:   1001032k total,   460452k used,   540580k free,    17804k buffers
Swap:  2931820k total,        0k used,  2931820k free,   215404k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5376 root      20   0 37748  11m 6360 S  2.0  1.2   0:26.82 Xorg               
 5924 lily      20   0 21260 8620 7132 S  1.0  0.9   0:03.24 multiload-apple    
 6240 lily      20   0 91028  21m  11m R  1.0  2.2   0:00.56 gnome-terminal     
    1 root      20   0  3056 1900  576 S  0.0  0.2   0:01.30 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 kblockd/0          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  115 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue             
  119 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  159 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush         
```

---

### Post by d3v1150m471c on 2010-01-17
Try running ubuntu as gnome safe by switching it on the login screen and see if you get better results.

---

### Post by t1m on 2010-01-17
Gnome failsafe mode started quick-and-sprightly, but gksudo and sudo still don't work properly. (sudo working slowly, gksudo not at all.)

Hmm.

---

### Post by d3v1150m471c on 2010-01-17
Do you ever accidentally try to open gui applications with sudo, or vice versa? This can unfortunately cause "damage" to certain files in your computer by erasing their executable permission.

You can fix this if you can find the files that were altered, if this is the case, and making them executable again.

---

### Post by rahrahmah on 2010-01-17
I'm not a techie, so I can't say a thing about the particulars that the OP gave, but this sounds a lot like what's happening to me. EVERYTHING is slow. Literally everything. It takes well over a minute to open any program whatsoever, from firefox to the system manager. Going to a new webpage will, without exception, cause the black and white think mode for about 30 seconds or more, at one point yesterday it became so slow that it crashed completely. It was trying to exit firefox for well over five minutes before it went to a black screen and just sat there, making computer think noises. I just turned it off at the powerbar, which is not something I want to have to keep doing. 

Today when I started it up, it sat there at black, trying to open so long that I went and had a smoke, and it wasn't done by the time I got back. When it did open, it seemed to be in some kind of ubuntu version of safe-mode, with an old-school basic window skin. It told me it was having trouble with the trash applet and asked if I wanted to delete it. I said no, obviously. The system updater was open at start-up, and was unresponsive when I tried to close it, and I had to force quit. 

I'm still working from this stripped down mode, and it's still slower than ****. I actually typed the entire first half of this at a lag, unable to see what I was typing. Just trying to get here, I had Firefox freak out about random scripts twice and shut down, and when I opened it again it couldn't remember my tabs both times. 

And the weird thing is, when I did manage to get the system monitor open, my CPU usage was super low. I would end different processes, but because I'm not familiar with ubuntu, I don't know what needs to be running or not. And even if I did end things, as I said, it's not like my system seems to be overworked from a numbers standpoint. 

I wish I could say that this happened after something specific, but I can't think of anything. It might have started after a recent update, but there's some new, unknown and probably useless thing to download every other day. I can't keep track.

My RAM is a little low, but I don't think that's the problem, because it's been running fine all this time. I'll be happy to provide any additional details you think you'll need to help me. Thanks in advance.

---

### Post by d3v1150m471c on 2010-01-17
Do a hard reset

I would look this up because it's been a long time since i've had to do one. It's different for laptops. For a laptop you have to kill the power and take the battery out for at least ten minutes and when you restart the computer you have to hold down the power button. again, i recommend googling it because i cannot remember it properly. You very well could be having poor hardware communication with your software which can often be fixed by hard resets.

---

### Post by t1m on 2010-01-17
re d3v1150m471c:   I haven't done this on the computer in question until the slowness showed up. (Thanks for the tip, though; I'll keep that in mind.)

Someone else using the computer may have, but it's very unlikely.

---

### Post by rahrahmah on 2010-01-17
what is a hard reset?

---

### Post by t1m on 2010-01-17
> **rahrahmah said:**
> what is a hard reset?

Exactly!

Sorry, no offence. Do you mean re-install Ubuntu?

---

### Post by d3v1150m471c on 2010-01-17
This is a layman way of explaining it but sometimes your hardware becomes confused and can make things run improperly especially in cases of hardware to software communication. It won't erase any of your data but it cycles the hardware back around to where it's supposed to be because at some point or another it became confused and can no longer function at standard effeciency.

---

### Post by d3v1150m471c on 2010-01-17
> **t1m said:**
> Exactly!

Sorry, no offence. Do you mean re-install Ubuntu?

No not at all. Again, google it to make sure you do it properly because otherwise you're just doing a ridiculously long normal reset. The goal here is to avoid doing anything like a reinstallation or actually having to do it.

---

### Post by d3v1150m471c on 2010-01-17
If the hard reset does not fix your issue i recommend doing a recovery with a live cd for your version of ubuntu.

---

### Post by rahrahmah on 2010-01-17
Please, what is a hard reset? I googled it, but since it takes a minute to open a new page, it just made me want to tear my hair out. They said something about hitting a reset button. I don't know what that is. I know what the power button is, but I doubt it's the same thing. Please help!

---

### Post by d3v1150m471c on 2010-01-17
"This is a layman way of explaining it but sometimes your hardware becomes confused and can make things run improperly especially in cases of hardware to software communication. It won't erase any of your data but it cycles the hardware back around to where it's supposed to be because at some point or another it became confused and can no longer function at standard effeciency."

What kind of computer are you on and is it a laptop? Let me know and i will search for the procedure for you, as I know you're machine is going super slow.

---

### Post by d3v1150m471c on 2010-01-17
[LIST=1]
[*]Push the power button until the laptop turns off completely. Wait for all lights to stop flashing.
[*]Step 2
Unplug the power cord and all peripherals connected to the machine. Exercising caution at this time prevents unexpected electric shocks on the user.
[*]Step 3
Turn the PC notebook over and disengage the battery cover in the back. A coin may be used to open the door.
[*]Step 4
Take out the battery pack. Lay it on a safe and clean surface.
[*]Step 5
Press the power button in the front again. Hold it for 60 seconds and release.
[*]Step 6
Install the battery pack back into the laptop and reconnect all cords.
[*]Step 7
Turn PC laptop around and power on. Check on the root of the problem if further operating system or application-related issues remain.
[/LIST]

---

### Post by rahrahmah on 2010-01-17
Thank you so much. It's not a laptop. It's just an ordinary computer. Pentium 4 tower-type by e-machines (who I've otherwise never heard of, I got it at a boxing-day sale at future shop a few years ago). 2.93Ghz. Do you need other information?

---

### Post by d3v1150m471c on 2010-01-17
Same thing as above ^ except your desktop will obviously not have a battery so unplug it instead. Make sure you unplug any cords and peripherals just as it says as well.

Stay in touch with the forum because the community is a wealth of knowledge. I did send you an email via the forum so feel free to write me back if you still cannot get the issue resolved.

---

### Post by t1m on 2010-01-18
I (t1m) tried a hard reset...It may have helped some. I can run VirtualBox now, which didn't run before, although it seems like the rest is pretty much the same.

Do you have any ideas?

---

### Post by rahrahmah on 2010-01-19
The hard reset worked for me. Thanks so much!

---

### Post by t1m on 2010-01-21
> **rahrahmah said:**
> The hard reset worked for me. Thanks so much!

Yay, rahrahmah! The entire Linux world would be happy for you if they knew...

I ended up just re-installing Ubuntu--simple way to avoid a perplexing problem!

Thanks again, d3v1150m471c, for your help!

Ta.

---

