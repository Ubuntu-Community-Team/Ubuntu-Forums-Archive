---
title: "DELL m5010 laptop 11.04 mouse cursor freezes - help"
date: 2011-07-15
forum: General Help
---

### Post by aspidistra on 2011-07-15
Dell inspiron m5010 laptop -- mouse cursor keeps freezing - after some time > 1 - 3 days (this time) with ubuntu 11.04 -- all updates installed.  The system is completely operational but mouse locked.  Now looking at going to xubuntu 
because I can't fix this.  This time I was doing something card payments on chrome -- thought maybe If I stop using chrome - no idea.   :o

Not really sure if it chrome -- just happened to be using it for something important when it froze. ...

the system when it reboots you can move the cursor up until hitting return on password  after logging in -- screen shows desktop - cursor locked

I have a suspicion this is compiz/gnome interaction - I select classic view (no effects) but I don't think this completely turns off compiz (only unity) .. is there any way to detect that compiz is not running from the command line?  / turn it off permanently.

---

### Post by wildmanne39 on 2011-07-15
> **aspidistra said:**
> Dell inspiron m5010 laptop -- mouse cursor keeps freezing - after some time > 1 - 3 days (this time) with ubuntu 11.04 -- all updates installed.  The system is completely operational but mouse locked.  Now looking at going to xubuntu 
because I can't fix this.  This time I was doing something card payments on chrome -- thought maybe If I stop using chrome - no idea.   :o

Not really sure if it chrome -- just happened to be using it for something important when it froze. ...

the system when it reboots you can move the cursor up until hitting return on password  after logging in -- screen shows desktop - cursor locked

I have a suspicion this is compiz/gnome interaction - I select classic view (no effects) but I don't think this completely turns off compiz (only unity) .. is there any way to detect that compiz is not running from the command line?  / turn it off permanently.Hi, compiz is turned off in classic no effects.

Chrome has been know to cause freezing on some systems. 

Also right after a freeze you can look at the dmesg log file using log file viewer to see if you can find the cause of the freeze.

Here is a link for freezing issues.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by aspidistra on 2011-07-15
> **wildmanne39 said:**
> Hi, compiz is turned off in classic no effects.

Chrome has been know to cause freezing on some systems. 

Also right after a freeze you can look at the dmesg log file using log file viewer to see if you can find the cause of the freeze.

Here is a link for freezing issues.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

This has helped me a lot.   X freeze article good - have been trying to help people with driver problems unity/compiz

chrome - I am glad to hear that.  it hits you when you have used chrome for something SPECIFIC a few times (as earlier on - critical transaction (what's that about)).  I am ditching chrome no way I touch it anymore.  userscripts don't run the same way as firefox anyway.  

As I have had OBSCURE networking problems on 11.04 with the same hardware I have run for >= 1 year on 10.04 (ref another post I made today [http://ubuntuforums.org/showthread.php?t=1804251 ](http://ubuntuforums.org/showthread.php?t=1804251 )) without any problems. Haven't got the time to iron out obscure problems appearing for basic system facilities so I am going back to 10.04.  Also vinagre (remote desktop) problems betwixt 10.04 / 11.04.  Never seen that before.

I note  that people are waiting for a oneiric (11.10) to address a great number of bugs.  I will stick with the more mature product.

---

### Post by wildmanne39 on 2011-07-16
Hi, there is nothing wrong with using 10.04 with its LTS. By the time 12.04 comes out it should have a lot of the bugs ironed out. 

I personally have no problems using unity, it has been very stable for me but I know that is not the case for everyone. Enjoy 10.04.

---

