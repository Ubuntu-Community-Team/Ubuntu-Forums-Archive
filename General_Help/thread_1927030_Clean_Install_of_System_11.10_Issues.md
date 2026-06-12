---
title: "Clean Install of System 11.10 Issues"
date: 2012-02-17
forum: General Help
---

### Post by Alpha99 on 2012-02-17
Hi there everyone
Just reinstall my o/s Ubuntu 11.10 as i was having a few issues namely with Firefox, evolution mail handler and KGP .

Issues as follows after clean install Firefox:-
1.  I have no access to bt yahoo login screen before or after new install - reply* is Firefox cannot establish a connection * But if i use windows no problem access is granted

2. Have no access to my Home Hub via Firefox - reply *Firefox cannot establish a connection.  * But if i use windows no problem access is granted. It seem that SSH is not being allowed.

3. I am still unable to send any email from evolution despite double checking and triple checking settings  - However i can receive emails 

4. In addition i evolution keeps asking for my pw despite it being enter already several times.

5. I have check my firewall settings and they are fine  as there has not been any changes to the system

6. every time i try to exit an xterm it seem to open more sessions 

7. How do i remove the .gnupg/gpg.conf file from the system so i can have a clean start as the system frozen during a process of creating a pair of keys and i am unable to access the program so i have uninstalled it with the hope of reinstalling and trying again the only thing is i do believe this may be the cause of my woe in relation to KGP.

Thanking you in advance for any help here.

---

### Post by dino99 on 2012-02-17
you might have a borked .local inside /home, rename it to .local_orig or whatever, then reboot it will be recreated cleanly.
the same thing can be done with .gconf

---

### Post by Alpha99 on 2012-02-18
> **dino99 said:**
> you might have a borked .local inside /home, rename it to .local_orig or whatever, then reboot it will be recreated cleanly.
the same thing can be done with .gconf

Thank you for the reply dino99

I am sorry to report that this has made no difference 
In addition i have tried other computers on my network of a different versions of Ubuntu and i have the same problem, so it leads me to believe that it is not the install of the O/S but something more fundamental as the only other difference that has changed is the upgrading of my broadband line.

Nevertheless i cannot explant as to why everthing is ok with W XP and i have full and unrestricted access to the net . It only leaves me to believe that it may be a firewall issue but i do not see that, as W XP has negotiated the firewall without any issues  why would Ubuntu now have a problem.

I would welcome any other opinions or help in this regard.
Thanks

---

### Post by Alpha99 on 2012-02-18
> **Alpha99 said:**
> Thank you for the reply dino99

I am sorry to report that this has made no difference 
In addition i have tried other computers on my network of a different versions of Ubuntu and i have the same problem, so it leads me to believe that it is not the install of the O/S but something more fundamental as the only other difference that has changed is the upgrading of my broadband line.

Nevertheless i cannot explant as to why everthing is ok with W XP and i have full and unrestricted access to the net . It only leaves me to believe that it may be a firewall issue but i do not see that, as W XP has negotiated the firewall without any issues  why would Ubuntu now have a problem.

I would welcome any other opinions or help in this regard.
Thanks


I don't believe it i have just loged into my Ubuntu server and seen anpdate for Firefox 10.0.2 
My system seems to now be working 

No restrictions to SSh and i can access yahoo.

I am not sure if this has anything to do with the other but i am now connecting and all seems to be well.
Thanks any ways.

---

