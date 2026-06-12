---
title: "Busy Box Question"
date: 2009-12-02
forum: General Help
---

### Post by twagner4287 on 2009-12-02
[FONT=Arial]Busy Box question[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]I received a 802.15.4 Transceiver from an overseas partner and the product has failed during testing.  It is running BusyBox v1.9.1.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]While I don't think I have the technical aptitude to repair it, I was hoping to view the configuration of this unit to see where the problem may lie.  I'm not a Linux/Unix user at any level, however I am wondering if anyone can tell me if a command line option exists that will allow me to view a configuration file or if a Windows based utility (other than Telnet/HyperTerminal) is available to do the same.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Thanks for your assistance.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Tom[/FONT]
[[FONT=Arial]tomw@wi.rr.com[/FONT]]("wlmailhtml:{57584E4B-804D-4557-A389-CA733392A6E7}mid://00000002/!x-usc:mailto:tomw@wi.rr.com")

---

### Post by andrewc6l on 2009-12-02
Assuming it's been compiled in, cat is the command you want.

cat /path/to/filename

Here's the whole list:
[http://www.busybox.net/downloads/BusyBox.html](http://www.busybox.net/downloads/BusyBox.html)

And ls will list the files, cd to change directories.

---

### Post by tonysonney on 2009-12-03
> **twagner4287 said:**
> [FONT=Arial]Busy Box question[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]I received a 802.15.4 Transceiver from an overseas partner and the product has failed during testing.  It is running BusyBox v1.9.1.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]While I don't think I have the technical aptitude to repair it, I was hoping to view the configuration of this unit to see where the problem may lie.  I'm not a Linux/Unix user at any level, however I am wondering if anyone can tell me if a command line option exists that will allow me to view a configuration file or if a Windows based utility (other than Telnet/HyperTerminal) is available to do the same.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Thanks for your assistance.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Tom[/FONT]
[[FONT=Arial]tomw@wi.rr.com[/FONT]]("wlmailhtml:{57584E4B-804D-4557-A389-CA733392A6E7}mid://00000002/!x-usc:mailto:tomw@wi.rr.com")

If your question is how to see the configuration file of busybox, I think you need the busybox build system on which it was built. According to your post for BusyBox v1.9.1. you will have a busybox-1.9.1.config normally in busybox root folder. Or you can try searching using the following command
```

find $(Path to your busybox) -name busybox-1.9.1.config
```

If you want to search for all the config files you can search
```

find $(Path to your busybox) -name *.config
```

Cheers,
Tony

---

