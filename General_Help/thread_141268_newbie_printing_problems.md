---
title: "newbie printing problems"
date: 2006-03-07
forum: General Help
---

### Post by genesiss on 2006-03-07
Everything was alright but now when I try to print I can't see my printer, I have a HP 6110, when I go to System-Administration-printing I get the "CUPS server could not be contacted" Error 
here is the error log 

[PHP]I [07/Mar/2006:08:35:06 -0400] Listening to 0:631
I [07/Mar/2006:08:35:06 -0400] Listening to 7f000001:631
I [07/Mar/2006:08:35:06 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [07/Mar/2006:08:35:06 -0400] Configured for up to 100 clients.
I [07/Mar/2006:08:35:06 -0400] Allowing up to 100 client connections per host.
I [07/Mar/2006:08:35:06 -0400] Full reload is required.
E [07/Mar/2006:08:35:06 -0400] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [07/Mar/2006:08:35:06 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [07/Mar/2006:08:35:07 -0400] LoadPPDs: No new or changed PPDs...
I [07/Mar/2006:08:35:07 -0400] Full reload complete.
E [07/Mar/2006:08:35:07 -0400] StartListening: Unable to bind socket for address 7f000001:631 - Address already in use.
I [07/Mar/2006:17:08:17 -0400] Listening to 0:631
I [07/Mar/2006:17:08:17 -0400] Listening to 7f000001:631
I [07/Mar/2006:17:08:17 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [07/Mar/2006:17:08:17 -0400] Configured for up to 100 clients.
I [07/Mar/2006:17:08:17 -0400] Allowing up to 100 client connections per host.
I [07/Mar/2006:17:08:17 -0400] Full reload is required.
E [07/Mar/2006:17:08:17 -0400] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [07/Mar/2006:17:08:21 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [07/Mar/2006:17:08:25 -0400] LoadPPDs: No new or changed PPDs...
I [07/Mar/2006:17:08:25 -0400] Full reload complete.
E [07/Mar/2006:17:08:25 -0400] StartListening: Unable to bind socket for address 7f000001:631 - Address already in use.
I [07/Mar/2006:19:22:17 -0400] Listening to 0:631
I [07/Mar/2006:19:22:17 -0400] Listening to 7f000001:631
I [07/Mar/2006:19:22:17 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [07/Mar/2006:19:22:17 -0400] Configured for up to 100 clients.
I [07/Mar/2006:19:22:17 -0400] Allowing up to 100 client connections per host.
I [07/Mar/2006:19:22:17 -0400] Full reload is required.
E [07/Mar/2006:19:22:17 -0400] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [07/Mar/2006:19:22:19 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [07/Mar/2006:19:22:24 -0400] LoadPPDs: No new or changed PPDs...
I [07/Mar/2006:19:22:24 -0400] Full reload complete.
E [07/Mar/2006:19:22:24 -0400] StartListening: Unable to bind socket for address 7f000001:631 - Address already in use.
I [07/Mar/2006:19:37:37 -0400] Listening to 0:631
I [07/Mar/2006:19:37:37 -0400] Listening to 7f000001:631
I [07/Mar/2006:19:37:37 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [07/Mar/2006:19:37:37 -0400] Configured for up to 100 clients.
I [07/Mar/2006:19:37:37 -0400] Allowing up to 100 client connections per host.
I [07/Mar/2006:19:37:37 -0400] Full reload is required.
E [07/Mar/2006:19:37:37 -0400] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [07/Mar/2006:19:37:37 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [07/Mar/2006:19:37:37 -0400] LoadPPDs: No new or changed PPDs...
I [07/Mar/2006:19:37:37 -0400] Full reload complete.
E [07/Mar/2006:19:37:37 -0400] StartListening: Unable to bind socket for address 7f000001:631 - Address already in use.
I [07/Mar/2006:19:53:10 -0400] Listening to 0:631
I [07/Mar/2006:19:53:10 -0400] Listening to 7f000001:631
I [07/Mar/2006:19:53:10 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [07/Mar/2006:19:53:10 -0400] Configured for up to 100 clients.
I [07/Mar/2006:19:53:10 -0400] Allowing up to 100 client connections per host.
I [07/Mar/2006:19:53:10 -0400] Full reload is required.
E [07/Mar/2006:19:53:10 -0400] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [07/Mar/2006:19:53:11 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [07/Mar/2006:19:53:11 -0400] LoadPPDs: No new or changed PPDs...
I [07/Mar/2006:19:53:11 -0400] Full reload complete.
E [07/Mar/2006:19:53:11 -0400] StartListening: Unable to bind socket for address 7f000001:631 - Address already in use.
I [07/Mar/2006:19:53:48 -0400] Listening to 0:631
I [07/Mar/2006:19:53:48 -0400] Listening to 7f000001:631
I [07/Mar/2006:19:53:48 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [07/Mar/2006:19:53:48 -0400] Configured for up to 100 clients.
I [07/Mar/2006:19:53:48 -0400] Allowing up to 100 client connections per host.
I [07/Mar/2006:19:53:48 -0400] Full reload is required.
E [07/Mar/2006:19:53:48 -0400] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [07/Mar/2006:19:53:49 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [07/Mar/2006:19:53:49 -0400] LoadPPDs: No new or changed PPDs...
I [07/Mar/2006:19:53:49 -0400] Full reload complete.
E [07/Mar/2006:19:53:49 -0400] StartListening: Unable to bind socket for address 7f000001:631 - Address already in use.
I [07/Mar/2006:19:55:05 -0400] Listening to 0:631
I [07/Mar/2006:19:55:05 -0400] Listening to 7f000001:631
I [07/Mar/2006:19:55:05 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [07/Mar/2006:19:55:05 -0400] Configured for up to 100 clients.
I [07/Mar/2006:19:55:05 -0400] Allowing up to 100 client connections per host.
I [07/Mar/2006:19:55:05 -0400] Full reload is required.
E [07/Mar/2006:19:55:05 -0400] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [07/Mar/2006:19:55:05 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [07/Mar/2006:19:55:06 -0400] LoadPPDs: No new or changed PPDs...
I [07/Mar/2006:19:55:06 -0400] Full reload complete.
E [07/Mar/2006:19:55:06 -0400] StartListening: Unable to bind socket for address 7f000001:631 - Address already in use.
[/PHP]

---

### Post by swamytk on 2006-03-08
1. Ensure that loop back interface is running and you have assigned ip address of 127.0.0.1 for interface lo. This can be done by running "ifconfig lo" from command line.
2. Internet Printing Protocol (IPP) needs port 631 to listen for print service. If lo is fine, ensure that port 631 is not occupied by some unknow third party application. You ensure this by the following procedure:
      i. # /etc/init.d/cups stop
      ii. # telnet 127.0.0.1 631
If you are able to connect with some server with the above telnet command means, there is already an application listening on that port. Try to stop that application and start cups.

---

### Post by geniusvicks on 2006-03-08
My Canon S200Spx doesnt print color in Linux while it does in Windoze, What do I do?

---

### Post by swamytk on 2006-03-08
[QUOTE=geniusvicks]My Canon S200Spx doesnt print color in Linux while it does in Windoze, What do I do?[/QUOTE]

Please post your query in a new thread. Pl. don't hijack this thread!

---

### Post by genesiss on 2006-03-08
ok I tried it here is what happened
[PHP]ifconfig lo
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1431199 (1.3 MiB)  TX bytes:1431199 (1.3 MiB)
[/PHP]
then I ran the comands and here is what I got back 
[PHP]sudo telnet 127.0.0.1 631
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
[/PHP]
Also I changed te word cups  for cupsys because when I ran the comand with cups it displays  "/etc/init.d/cups: command not found"

---

### Post by genesiss on 2006-03-09
I guess no one knows.....:confused:

---

### Post by Sef on 2006-03-10
Oh you of little faith, try this by wondering jew:

(Note: The PSC 1610 and Office Jet 6110 use the same printer driver.)

> hey I just got my psc 1610 working for both scanning and printing (yay me!)...
first I did

sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

Then xsane told me it didn't find any scanning devices so I installed a package called libsane-extras from synaptic and tried xsane again and it worked.


[http://ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1600]("http://ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1600")

---

### Post by genesiss on 2006-03-11
that is the problem
when I go to System-Administration-printing it gives me a messege saying "the CUPS server could not be contacted"

---

