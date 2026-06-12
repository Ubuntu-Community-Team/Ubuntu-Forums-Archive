---
title: "Firestarter Not Working!"
date: 2006-05-11
forum: General Help
---

### Post by Gonzakpo on 2006-05-11
Hello everyone......

My problem is simple to explain but i think that's imposible to solve......it's very rare what happened to me...

I used to use gnome desktop ..(ubuntu) bt the other thay i decided to take a loos at kde by installing the kubuntu-desktop package...
In fact it's really nice ...i really like it and it's a little faster than gnome...

Well..........BUT .....a problem occured.......my firewall somehow stop working properly .........it's still running but it doesn't block incoming connections .........
when i was using gnome ...everytime the firestarter gui was adevertising connection that were blocked. ....BUT now ....i doesn't say anything....nothing is blocked...
and i verified it by conecting me to several chat programs and the can connect perfectly! (that can't happen if the firewall is working properly......and it has no rules/exceptions configured! )

Well ...i hope that you could help me ................THANKS

---

### Post by 23meg on 2006-05-11
Please post the output of the following command ```
sudo /etc/firestarter/firestarter.sh status
```

---

### Post by Gonzakpo on 2006-05-11
the output is that teh firewall is running ....it doesn't say anymore....

Any ideas?

---

### Post by Gonzakpo on 2006-05-12
nobody knows the answer? .......

pleaase! i'd tried everything .....i reinstalled the firewall ...the iptable ...

any ideassssss ?

---

### Post by steve.horsley on 2006-05-12
I don't know firestarter. But you can check if the rules are being implemented with the command **sudo iptables -L**. If it's not filtering, I don't know what to suggets. I note that there is a new thread in the beginners forum saying that firestarter isn't working. Two such threads inthe same evening may not be coincidence - I wonder...

---

### Post by Hoffmann on 2006-05-12
[QUOTE=Gonzakpo]the output is that teh firewall is running ....it doesn't say anymore....

Any ideas?[/QUOTE]

Since firestarter is running, probably, all is fine. I mean, no person is trying to take control of your machine. Try this test:

[http://scan.sygatetech.com/](http://scan.sygatetech.com/)

If you get:
(1) Unable to determine your computer name!
(2) Unable to detect any running services!

So, Firestarter is protecting you; it is blocking any intrusion.

Are you also using a router? In my case, I have a router for sharing (internet) access with my wife. My router is also a type of hardware firewall. So, when I am using both Firestarter and the router (in the majority of case), I get no warning from Firestarter. However, when I am connect to the internet without using the router, Firstarter blocks a lot of intrusions. So, if you are using two layers of protetion (router firewall +  Firestarter), the router will block the intrusions before they reach Firestarter (or anyother software firewall).
I am using GNOME (I do prefer this desktop), and Firestarter is working perfectly.
I hope this help.

Hoffmann

---

