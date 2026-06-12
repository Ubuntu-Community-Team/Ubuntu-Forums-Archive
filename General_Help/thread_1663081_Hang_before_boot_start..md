---
title: "Hang before boot start."
date: 2011-01-09
forum: General Help
---

### Post by bloggerdude on 2011-01-09
Guys, can anyone help me with my problem. I'm trying to install ubuntu 10.10 on my machine, I don't know what is/are my problems. 

My machine is running in Pentium(R) 4 CPU 1.7Ghz, Nvidia legacy Riva tnt/tnt2 and a 512mb ram. I have a Network adapter, Realtek RTL8139 Family PCI Fast Ethernet NIC. Please help me. I have installed Ubuntu in my Window Xp, and used the ACPI workaround to install ubuntu on my PC. Now that I have installed Ubuntu, when I try to boot ubuntu, it always hang before it start to boot.

Sorry if my english is bad.

(This is a repost)

---

### Post by theasprint on 2011-01-09
Hi,

I would like to know what you mean by "hang". In fact I would like more specific details on the situation, for example when and what do you see during the hang-time.

However, I may suspect that something is wrong with your Grub2, so therefore I would like you to do this: 

1. Boot from a LiveCD (that means Try Ubuntu without Changes)
2. Have internet access and go to the link in my signature below and download the bootinfoscript.
3. Follow the instructions on the link.
4. Then post the results (results.txt) in this thread, with the [CODE] tags to wrap it in a nice box.

This would give you an overview of your system.

* Also another problem may be your hardware compatibility. You should check the requirements for Ubuntu:
[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by bloggerdude on 2011-01-09
Sir, after I choose Normal boot. The screen turns to black and prints these codes
```

[numbers]Disabling IRQ #5
[numbers]Disabling IRQ #10
[numbers]Disabling IRQ #10

```

after that, the screen turns to black again and these code prints after..

```

[numbers] Bug soft lockup - CPU#0 stuck for 61s! [modprobe:483]
[numbers] Process modprobe (pid:483, ti=d8398000, task=d9ed4c20 task.ti=d8398000)
[numbers] Stack:
[numbers] Call trace:
[numbers] Code: some binary codes 

```

---

### Post by bloggerdude on 2011-01-09
another thing sir, how can I use the bootinfoscript if I have not yet run my ubuntu completely even once? and When I try the LiveCD, it still hang up, the only thing that let me install it is to run it in ACPI workaround.

---

### Post by theasprint on 2011-01-09
Hi,

When you try the LiveCD it still hangs up?

Two statements:
1. Do you want to try redownloading your Ubuntu .iso file? It may possibly also be a faulty .iso file which is causing problems.

2. Or either your computer is not compatible with Ubuntu. You can try other Linux distributions for your pleasure, like Linux Mint or Fedora instead.

I suspect these because this is the first time I seen people having problems with booting from LiveCD. So far it only means that their .iso is spoilt or their PC is not compatible.

---

### Post by efflandt on 2011-01-09
What ACPI workaround did you use during install?  You may need to do that from grub menu during normal boot until you get that plugged into /etc/default/grub.  If you hit **e** during grub menu you can add a parameter (like **acpi=off** ) in the line that contains **quiet splash**, or maybe in place of those words so you will see boot messages.  Then press Ctrl+X to boot.

See [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt) for other choices about acpi= or other boot parameters.

Once you figure out what works, you can **gksu gedit /etc/default/grub**  (or sudo nano) and insert the parameter between quotes in one of the lines below.  The first line is for normal boot only and the second line applies to all boots including (recovery).  So if you need that parameter for all boots, put it in the second line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```Then do **sudo update-grub**

---

