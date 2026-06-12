---
title: "Opening windows"
date: 2009-12-03
forum: General Help
---

### Post by MarcusA on 2009-12-03
:p Is there a way to open my windows partition while using Ubuntu? So that I can work with programs that don't work on Ubuntu without having to reboot to use them.

Thanx

---

### Post by pi4r0n on 2009-12-03
> **MarcusA said:**
> :p Is there a way to open my windows partition while using Ubuntu? So that I can work with programs that don't work on Ubuntu without having to reboot to use them.

Thanx

**MarcusA** let me make it clear for every one OK. You want to open Windows partition so you can run windows applications on Ubuntu ??

If this is what you want to do then there **[COLOR="Red"][B]is no way to do this**[/COLOR][/B] as Windows applications do not work under Linux OS's but you can use Wine emulator to run some windows applications on Linux.

---

### Post by oOarthurOo on 2009-12-03
You can access your windows partition from Ubuntu, but you cannot run those windows programs. All that you will be able to do is access data stored on those partitions, and work with them if you have a program installed on Ubuntu that can open them.

For example, if you have Excel installed on Windows you could open .xls files using Openoffice Calc, but clicking excel.exe. would do nothing. 

You have four options for running windows programs in Ubuntu.
1. Don't. Use existing linux applications (e.g., Openoffice calc instead of excel).
2. Wine. Allows you to install Excel and use it within Ubuntu. Note however, that you will have two instances of excel installed on the machine, one in Windows, one in Ubuntu.
3. Virtualmachine, e.g., Virtualbox. Allows you to install Windows within Ubuntu, turning it on or off as you desire without having to reboot. Note however, that you will have two instances of Windows installed on the machine, and you will still have to install any programs you want to use on the virtualmachine.
4. Don't. Continue dual booting.

---

### Post by MarcusA on 2009-12-03
Yeah, but never know if theres a way to do this :D Well maybe not 'this' but just a way for ubuntu and windows to magically be open at the same time ... It's almost 2010 for Christs sake! :lol:

And unfortunatelly wine doesn't work for every windows program.

---

### Post by MarcusA on 2009-12-03
> **oOarthurOo said:**
> 3. Virtualmachine, e.g., Virtualbox. Allows you to install Windows within Ubuntu, turning it on or off as you desire without having to reboot. Note however, that you will have two instances of Windows installed on the machine, and you will still have to install any programs you want to use on the virtualmachine.

Hmmm sounds interesting, I'll look into that. Thanx

---

### Post by pi4r0n on 2009-12-03
> **oOarthurOo said:**
> 3. Virtualmachine, e.g., Virtualbox. Allows you to install Windows within Ubuntu, turning it on or off as you desire without having to reboot. Note however, that you will have two instances of Windows installed on the machine, and you will still have to install any programs you want to use on the virtualmachine.

With regards to this point (3) you could have dual boot and then using either VirtualBox or VMWorkstation to access existing partition of windows and emulate existing windows in Ubuntu.

---

### Post by MarcusA on 2009-12-03
> **pi4r0n said:**
> With regards to this point (3) you could have dual boot and then using either VirtualBox or VMWorkstation to access existing partition of windows and emulate existing windows in Ubuntu.

Sounds like this might be the program I seek =)

---

### Post by gadolinio on 2009-12-03
> **oOarthurOo said:**
> You can access your windows partition from Ubuntu, but you cannot run those windows programs. All that you will be able to do is access data stored on those partitions, and work with them if you have a program installed on Ubuntu that can open them.

For example, if you have Excel installed on Windows you could open .xls files using Openoffice Calc, but clicking excel.exe. would do nothing. 

You have four options for running windows programs in Ubuntu.
1. Don't. Use existing linux applications (e.g., Openoffice calc instead of excel).
2. Wine. Allows you to install Excel and use it within Ubuntu. Note however, that you will have two instances of excel installed on the machine, one in Windows, one in Ubuntu.
3. Virtualmachine, e.g., Virtualbox. Allows you to install Windows within Ubuntu, turning it on or off as you desire without having to reboot. Note however, that you will have two instances of Windows installed on the machine, and you will still have to install any programs you want to use on the virtualmachine.
4. Don't. Continue dual booting.

+1; excellent reply.
Regarding option 3: remember that if you run a virtual machine with ubuntu, from windows, you are actually using windows, with its viruses, hang-up's, etc :P
I use ubuntu and virtualbox to run a windows virtual machine; when it hangs up or stg goes wrong, i just close that window and restart it, but not the whole system. I find ubuntu far mor stable than windows.

---

### Post by MarcusA on 2009-12-03
True that; Sux to reboot just to use photoshop and all :p but I finally got CS4 working with wine so for now I won't be needing any windows programs. I'm going to give that virtual machine a go if its easy enough to use :lol:

---

### Post by gadolinio on 2009-12-03
> **MarcusA said:**
>  I'm going to give that virtual machine a go if its easy enough to use :lol:

It's really easy to use. Someone recommended it in a thread here, so i installed it and now use it often, sometimes just for fun or to test other OS's.

---

### Post by gspat on 2009-12-03
just remember that 3d still has a way to go, so you won't be able to do much gaming with it.

---

