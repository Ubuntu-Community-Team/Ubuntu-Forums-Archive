---
title: "Force quit a screen terminal"
date: 2010-01-24
forum: General Help
---

### Post by Zilioum on 2010-01-24
I'm fiddling around with headless vuze on my server. I usually start vuze in headless mode in a terminal I opened on the server with screen. My problem is, that if vuze crashes in console view (which it does quite a lot) I cant shut it down without rebooting the server. Although I can reconnect the screen terminal, it doesnt it doesn't react to "ctr, c" and either to "quit" which normally prompts it to quit.
Is there anyway to still kill it?

Cheers

---

### Post by Saiko Berry on 2010-01-24
Whats its state? Zombie processes can't be stopped but they dont exactly do anything so its just annoying if you look at system monitor all the time.

Try xkill pid or killall appname. You probably tried those, and if they dont work then you probably wont be able to close it. Like I said, zombie processes are processes which are outside the linux sessuib so to speak.. they drifted there and they dont do much but exist until your computer is restarted.

---

### Post by Zilioum on 2010-01-24
It just states some java stuff like: ```
Exception in thread "UPnPMediaChannel:readSelector" java.lang.OutOfMemoryError: Java heap space
java.lang.OutOfMemoryError: Java heap space

```
It obviously crashed, because I cant access it anymore with my remote control plugin anymore. 
```
pidof vuze
``` doesnt return anything and ```
killall
```doesnt work either. I guess you're right, it became a zombie :P The problem is though, that if I restart vuze in an other console, it doesnt really start (I cant connect to it) and it says ```
^[[5~DEBUG::Sun Jan 24 16:52:30 CET 2010::com.aelitis.net.udp.uc.impl.PRUDPPacketHandlerImpl::receiveLoop::544:
  java.net.BindException: Address already in u
``` 
Looks like the original process isnt that dead.
Any ideas?
Or how could I find out what makes it crash in the first place?

---

### Post by Saiko Berry on 2010-01-24
Yes. Download htop, enable tree view and go through your processes to see whats turning it into a zombie? It should link to all the different things that are dealing with it through trees. Screenshot it and post it here?

Instructions;

apt-get install htop
htop
F2 - Down - Right - Enter (Turning on tree view)
F10 to exit
Up and down keys to scroll through processes

Look through until you see the vuze zombie process and find what it links to.

---

### Post by Zilioum on 2010-01-24
Sounds good, the problem is that its on a server with ubuntu server edition, so no GUI.

---

### Post by Saiko Berry on 2010-01-24
Htop isnt a gui, it's a bash/prompt program. It runs inside terminal windows. You can run it in tty1 if you like. It's not a gui.

---

### Post by Zilioum on 2010-01-24
Oh, sorry. I associated "tree view" with GUI.
I'll give it a try, thanks.

---

### Post by Saiko Berry on 2010-01-24
Tree view works like this
```

gnome-terminal
      `- bash
          `- htop
```for example.

---

### Post by jlb.think on 2010-01-24
> **Saiko Berry said:**
> Whats its state? Zombie processes can't be stopped but they dont exactly do anything so its just annoying if you look at system monitor all the time.

Try xkill pid or killall appname. You probably tried those, and if they dont work then you probably wont be able to close it. Like I said, zombie processes are processes which are outside the linux sessuib so to speak.. they drifted there and they dont do much but exist until your computer is restarted.


You can kill a zombie with "kill -9 PID"

just type "ps -e|grep yourprocessname" or use "pstree" to find the PID (process id) of the one you want to kill, and then send kill with the 9 signal.

If that doesn't work use "sudo kill -9 PID"

---

### Post by Saiko Berry on 2010-01-24
No you cant. Who told you that? Don't spread lies. Zombies are impossible to kill. You wait for it to stop, or you reboot.

---

### Post by jlb.think on 2010-01-24
> **Saiko Berry said:**
> No you cant. Who told you that? Don't spread lies. Zombies are impossible to kill. You wait for it to stop, or you reboot.

Just to a quick google search for how to kill zombie processes if you don't believe me.  Somehow I think you know I'm right but you are playing some sort of sick game to ruin people's day.

type "man kill", it will explain the use of the "-9" signal.

I'll give you the benefit of a doubt, start a process that you know will zombie out and give it the kill -9 signal, and if that doesn't work sent it a kill -9 signal as root.  Now you know how to do it and can try it.

---

### Post by Zilioum on 2010-02-03
I kind of solved it. ps -u worked fine to kill the running process. I could either kill the screen session or the process I started within. I couldnt try it when it was a zombie because it didn't crash during the last two weeks (But thanks to murphys law it will as soon as I have posted this ;)) 
I regard this thread as solved, but I'll post back if the zombie comes back.

---

