---
title: "Problem with installing a printer"
date: 2009-09-25
forum: General Help
---

### Post by Anthony_D on 2009-09-25
[SIZE=2]Hello!

I have a problem installing my printer (canon ip1800) on my linux pc, and I believe there is at least one person in the lot who can help :-)

First I got the print drivers from the canon website and installed them successfully. 
I then installed CUPS - which shows all ok in Synaptic.

I also put myslef in the admin, then sudo groups from the Konsole (using useradd)

Then I did an lsusb, and the printer is really there : 
**Bus 002 Device 002: ID 04a9:10c2 Canon, Inc.**

Having done that, I am eventually doing a System | Administration | Printing and do a "Connect" to the localhost. 

I then receive this enigmatic error message : [B]CUPS  server error 
There was an error during the CUPS operation: 'httpConnectionEncrypt failed'

[/B][/SIZE][SIZE=2]On the top of that, I did an [http://localhost:631](http://localhost:631) on Firefox, Opera, Konkeror and they all say I am not authorized to access to this address.

Is anyone able to assist, please?

Many thanks in anticipation,

A[/SIZE][B][SIZE=1]
:popcorn:
[/SIZE][/B]

---

### Post by Anthony_D on 2009-09-26
No one? 
Please guys, I know there is a person somewhere who can fix it straight away. 

Thanks!

:guitar:

---

### Post by bbbhhh on 2009-09-26
unncessary usage if u want more ....................click here[http://www.printersusage.com](http://www.printersusage.com)

---

### Post by bbbhhh on 2009-09-26
:(hgj.,..............................[http://www.google.com](http://www.google.com):popcorn:

---

### Post by Anthony_D on 2009-09-26
> **bbbhhh said:**
> unncessary usage if u want more ....................click here[http://www.printersusage.com](http://www.printersusage.com)


link doesnt work.

Anyone else please ?

---

### Post by plucky on 2009-09-26
Try in a terminal ```
sudo /etc/init.d/cups start
``` and then see if you can login the the cups server via the Firefox address bar.


Good luck

---

### Post by Anthony_D on 2009-09-26
&#65279;Hello Plucky,
 
Thanks for your reply.
 
I did what you said and now, this is what I get :
 
anthony@GATEWAY:~$ sudo /etc/init.d/cups start
 [sudo] password for anthony:
 Starting Common Unix Printing System: cupsdcupsd: Child exited with status 1!
 failed!
 anthony@GATEWAY:~$




Any idea?

---

### Post by Anthony_D on 2009-09-26
I progressed a bit.

Now, I am looking for the PSTCANONIJ file, which is not on my computer, while I installed the official canon drivers ...

Would anyone have this file, please?

Thank you.


:-D

---

### Post by Anthony_D on 2009-09-26
I found the file.

But now, I receive no error message anymore when I send a test page... but .... the document won't print out. CUPS shows the job was done properly while the printer stays idle.

Why ????:confused:

---

### Post by Anthony_D on 2009-09-27
Guys, I progressed on my own as much as I could, since I have been using linux for couple of weeks. At this point, I could not progress anymore without a bit of help.

My printer, a canon ip1800 is currently turned on, and properly recognized in CUPS which is running fine now - I can get the CUPS homepage displayed. Cups is started, the printers are published, the jobs are set to "Accepted", the format is set to A4 by default.

All the print jobs I send to the printer will look ok on CUPS** while they won't print out.**

Would anyone know why, please?

Is there anything else I need to install or start or check or whatever ?

Please.

Thank you!

---

### Post by Anthony_D on 2009-09-30
I resolved my problem by installing the printer on a Windows based PC. 
 
It works perfectly now !!! 
 
 
 
Thanks for your help :popcorn:

---

### Post by nike984 on 2010-03-05
as Lutz pointed out in the following link, 
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/335898/comments/7](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/335898/comments/7)
it could be an AppArmor issue. 

Try ```

sudo aa-complain cupsd
sudo /etc/init.d/cups restart
```It worked for me. ;)

---

