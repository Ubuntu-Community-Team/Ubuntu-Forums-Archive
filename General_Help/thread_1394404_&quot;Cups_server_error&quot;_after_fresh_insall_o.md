---
title: "&quot;Cups server error&quot; after fresh insall of Karmic"
date: 2010-01-30
forum: General Help
---

### Post by flattop1 on 2010-01-30
When I try to configure a printer, I get the message "CUPS SERVER ERROR"- The CUPS scheduler is not running-...
my printer a (LEXMARK all in one X2600)and worked fine  since ubuntu 8.04..But now it doesnt work.
Lexmark even provide a linux driver.

---

### Post by flattop1 on 2010-01-31
When I try restarting it from the command line I get....

flattop-desktop:~$ sudo /etc/init.d/cups restart
 * Restarting Common Unix Printing System: cupsd                                
Warning: Fake start-stop-daemon called, doing nothing.

Warning: Fake start-stop-daemon called, doing nothing.
                                                                         [ OK 


Anybody know how to fix this.
By the way the scanner part of the printer works perfect under xsane??

---

### Post by flattop1 on 2010-02-02
Anyone?

---

### Post by flattop1 on 2010-02-05
OK...I didnt get any replies ...I need my printer to work so I guess I'll have to reinstall 9.04.

---

### Post by von Stalhein on 2010-02-07
In a terminal, ```
sudo service cups start
``` will start the printer service.

I have the same issue, in that it's not starting automatically on boot.

I am researching solutions for that now.

HTH.

---

### Post by flattop1 on 2010-02-07
> **von Stalhein said:**
> In a terminal, ```
sudo service cups start
``` will start the printer service.

I have the same issue, in that it's not starting automatically on boot.

I am researching solutions for that now.

HTH.
Hey thanks for the reply..

That doesnt work either...I tried it before and I get this:

* Starting Common Unix Printing System: cupsd                                  
Warning: Fake start-stop-daemon called, doing nothing.
                                                       

And it literally does nothing..So still searching for a solution.

---

### Post by von Stalhein on 2010-02-07
Hmmm, that's annoying.

I presume you've reinstalled cups through Synaptic?

---

### Post by flattop1 on 2010-02-10
> **von Stalhein said:**
> Hmmm, that's annoying.

I presume you've reinstalled cups through Synaptic?
Yeah I have..no joy

---

### Post by von Stalhein on 2010-02-12
Yeah, I still haven't found a way to get mine to start automatically.

It's a minor inconvenience for me, but an absolute disaster for the rest of the family, who only know Windows.

This machine is hooked up to the printer - it's the only one on the network :D

---

### Post by flattop1 on 2010-02-15
> **von Stalhein said:**
> Yeah, I still haven't found a way to get mine to start automatically.

It's a minor inconvenience for me, but an absolute disaster for the rest of the family, who only know Windows.

This machine is hooked up to the printer - it's the only one on the network :D

Thanks for the replies man..I still haven't reverted to 9.04 yet..I've been printing using my laptop which still has 9.04 on it.
I guess Im hoping some genius comes up with a fix or maybe the printer will work work with 10.04!

---

### Post by von Stalhein on 2010-02-16
hee hee - I got lazy and just start the service manually.

atm I'm the same as you - bring on the genius :-)))

---

