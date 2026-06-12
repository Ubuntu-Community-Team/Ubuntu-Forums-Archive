---
title: "Seeing if the firewall starts on start-up"
date: 2010-07-29
forum: General Help
---

### Post by unknown user on 2010-07-29
I have just configured the firewall and gui front end (Firestarter) to start on system start-up, which I feel better about.

I heard that if you turn off or disable the Ubuntu load screen on start-up, I can then read the line to see if the firewall is starting up (as I think it is), when the laptop is booting. Is there a way that I can stop the Ubuntu start page (with the progress bar) so that I can check if the firewall starts all OK and then get it back again once happy all is ok?

---

### Post by Blackbird_13 on 2010-07-29
For a one-off boot (i.e. not remembered for subsequent boots) at the grub boot menu:

[LIST]
[*]press e to edit the ubuntu entry
[*]move to the linux line
[*]delete "quiet splash"
[*]press [control] x to boot
[/LIST]
You should now see the boot messages.

You may not be aware that firestarter is not supported and has been replaced by ufw ([https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)).

In any case firestarter and ufw are _not_ themselves firewalls. They provide an interface to configure the  iptables firewall rules. To see your iptables configuration run the following command.

```
sudo iptables -L
```

---

### Post by endotherm on 2010-07-29
if you just want to check your boot messages, they are in /var/log/dmesg and dmesg.0
you can access them from the system log file viewer, or run the command 
```
dmesg > <outputfilepath>
``` to send the contents to a file for analysis. every boot your dmesg is cleared, so it is jsut the info from the last boot. I believe that dmesg.0 contains information about the second to last boot.

you do not need to run firestarter or gufw on startup to have your configuration loaded on startup. as blackbird mentioned iptables -L is a good way to see your ruleset, so if you want, redirect the list to a file, reboot and check the list again to make sure they have the same configuration.

---

