---
title: "how to tell if system being compromised"
date: 2009-06-29
forum: General Help
---

### Post by awec56a8 on 2009-06-29
hi guys/gals,:KS

just wonder if there's way to tell if my system is being compromised. any telltale sign? or any log file to check?


thank you for your help!

regards,

awec56a8

---

### Post by muteXe on 2009-06-29
I'm not sure really, but your log files can be found at /var/log.  This is a nice summary of the files that can be found in there:
[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

---

### Post by Soul-Sing on 2009-06-29
auth.log/syslog, but when compromised logs can easily be erased.

---

### Post by t0p on 2009-06-29
> **awec56a8 said:**
> 
just wonder if there's way to tell if my system is being compromised. any telltale sign? or any log file to check?


Any particular reason you're asking?  Something not right?  Or is it just a general enquiry?

If you're just asking out of curiosity, the answer is: it depends. :p

One giveaway would be online activity that you can't identify.  A major reason for crackers compromising a machine is to add it to a botnet, so it can send spam, engage in distributed denial of service attacks and the like.  So it your online activity is crazy but you haven't initiated anything, that would be a clue.

---

### Post by 3rdalbum on 2009-06-29
If your system has been compromised, usually the attacker will remove traces of their own entry, and the first time you'll realise something is amiss is if you notice an unintended side effect of their entry. Sometimes an attacker will install their own copy of "ls", for instance, that might not accept all the parameters you're used to giving it.

A good start would be to install chkrootkit and rkhunter, and run those. They can check for a variety of off-the-shelf rootkits.

If you have no specific reason to suspect entry, then check that you are not running any outward-listening services, and if you are that you are firewalled so the services cannot be accessed outside your local network. If for instance you keep SSH running and accessible, take a look at some HOWTOs about how to make SSH more secure (for instance, disabling root logins, switching it to a different port, disabling password login in favour of a hexidecimal key).

---

### Post by awec56a8 on 2009-06-29
hi guys/gals,

the reason I brought it was b'cos i must've click on something and i was taken to porn site, since then the mouse doesn't respond to double click and single click select w/o holding the shift or ctrl keys. reboot doesn't restore the mouse respond. I have to power down for 5 mins. start it up and deactivate my session manager cache and the deactivate the parcellite, too. then only the system back to normal(i hope)....so my question is can a remote web site control my mouse or my pc literaly


thank you for the help 

regards,


awec56a8:KS

---

### Post by sirhalos on 2009-06-29
Sounds like a Firefox addon got installed. Do this Nautilus (The file manager) Go up to view then Show hidden files/folders. Something similar like that not on a Linux computer right now. Delete the folder .mozilla. Now start up Firefox like normal. You'll lose any bookmarks and settings of Firefox and put you back to the default doing this but it should fix the problem.

---

### Post by awec56a8 on 2009-06-29
Hi guys/gals

thank you for all your suggestion, although some of it are way beyond my league. so i try sirhalos method. mouse works great. btw where do get the rootkit scanner. 

regards,

awec56a8

---

### Post by t4thfavor on 2009-06-29
I was going to say look for port 25 traffic on your outbound ethernet interace I hates me some spammers, but sounds like you all got it handled.

---

