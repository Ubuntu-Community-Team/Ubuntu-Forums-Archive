---
title: "sudo kill -9 -1"
date: 2011-07-11
forum: General Help
---

### Post by adit on 2011-07-11
I am learning linux commands.  I just wanted to see what happens when I type
```
sudo kill -9 -1
```
The screen became blank.  Keyboard was not responding.  I couldn't do a proper shutdown.  I switched off computer by pulling out the plug.  When I restarted, I heard a series of beeps (approximately 10 beeps).  Then I was dropped to the grub prompt.
The problem now is I can not type anything into the grub prompt, because the character 'c' is continously printed across the screen like this

```
grub > cccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccc
ccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccc
ccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccc
cccccccccc  ....
```

I couldn't stop the character 'c' from printing (I tried pressing Esc, Ctrl+C)

The solution is easy.  I can reinstall grub from a livecd.  Or even reinstalling the entire operating system wouldn't take more than 30 minutes.  But I want to know

1) What exactly happened to grub?  What stage does this error belong to (1, 1.5 or 2)?  What is the error number?
2) How can running "sudo kill -9 -1" affect grub?

---

### Post by regala on 2011-07-11
> **adit said:**
> 
1) What exactly happened to grub?  What stage does this error belong to (1, 1.5 or 2)?  What is the error number?
2) How can running "sudo kill -9 -1" affect grub?


nothing happened to grub. something happened to your keyboard or keyboard controller when you pulled the plug. usually hitting the reset button is less destructive.

br,

Mathieu

---

### Post by Anonymous is Incognito on 2011-07-11
> **adit said:**
> I am learning linux commands.  I just wanted to see what happens when I type
```
sudo kill -9 -1
```

[FONT="Courier New"]kill[/FONT] allows you to send signals to processes you specify. By default, the TERM signal is sent.

To send the TERM signal to a process with a PID of [FONT="Courier New"]n[/FONT] use:

```
(sudo) kill n
```

When you put a [FONT="Courier New"]-[/FONT] in front of [FONT="Courier New"]n[/FONT] you tell the system to terminate every process with a PID above [FONT="Courier New"]n[/FONT].

```
sudo kill -9 -1
```

Will kill every process with a PID above 9 first, then terminate everything with a PID above 1, effectively killing all but PID 0, which is initiated by the kernel at boot. This is why you got a black screen.

Grub ***cannot*** be affected.

Beeps can occur when you press the keyboard before the OS is loaded. Check your keyboard please.

---

### Post by regala on 2011-07-11
> Will kill every process with a PID above 9 first, then terminate everything with a PID above 1, effectively killing all but PID 0, which is initiated by the kernel at boot. This is why you got a black screen.

not really, no one can kill PID 1, init, because the kernel goes panic when the init process dies, and it would be a serious security flow if root could kill a system that easily, even though the effect of sudo kill -9 -1 is quite nearly the same. but you can theoretically recover from a system with only the init process (how is yet to be determined, if no shell, no getty is alive) while a linux system with no process can't exist.

---

### Post by adit on 2011-07-11
The problem is not with grub.  The problem is as soon as the computer starts, the keyboard sends a continuous stream of the character 'c' around 5 per second.  As soon as the grub menu appeared the keyboard sent 'c'.  So I was dropped to grub commandline.
I booted from a livecd and disbled the grub menu from appearing.  The problem is temporarily solved.  I am able to boot into a complete gnome desktop.  Once I loaded gnome I do not see the keyboard repeating 'c'.  (Has the keyboard really stopped repeating or gnome just hides whatever the keyboard does)?  This is just a temporary solution.
Advice me what to do next?
1) Reinstalling the entire operating system is not going to solve the problem.  Problem is with the keyboard repeating the 'c' character.

---

### Post by psusi on 2011-07-11
> **Anonymous is Incognito said:**
> 
When you put a [FONT="Courier New"]-[/FONT] in front of [FONT="Courier New"]n[/FONT] you tell the system to terminate every process with a PID above [FONT="Courier New"]n[/FONT].

No, it means to send the signal to the process group n.  The pid of -1 is special, meaning send the signal to all processes except init and the kill command itself.

> **Anonymous is Incognito said:**
> ```
sudo kill -9 -1
```

Will kill every process with a PID above 9 first, then terminate everything with a PID above 1, effectively killing all but PID 0, which is initiated by the kernel at boot. This is why you got a black screen.


There is no pid 0.  This command kills ( with signal 9, or SIGKILL ) all processes except for init ( pid 1 ).

---

