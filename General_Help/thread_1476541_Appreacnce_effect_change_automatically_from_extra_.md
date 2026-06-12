---
title: "Appreacnce effect change automatically from extra effect to no effect"
date: 2010-05-07
forum: General Help
---

### Post by giteshpandya on 2010-05-07
Hi !

I have upgraded to 10.4 and and after try to install mac look in ubuntu.

My screen start flickering, I found it this due to in system => preference => appearance => effect become no effect automatically (as each and every time I select extra effect)
After some time.

for changing this setting i need to turn off the computer and restart  then after i can do it i.e. change effect to extra effect.   

Its done after following installation

[http://maketecheasier.com/turn-your-ubuntu-intrepid-into-mac-osx-leopard/2009/01/08](http://maketecheasier.com/turn-your-ubuntu-intrepid-into-mac-osx-leopard/2009/01/08)

Any help or Idea.

Thanks,

Gitesh

---

### Post by WorMzy on 2010-05-07
I think there's a problem with the drivers you're using. Could you go to System -> Administration -> Hardware Drivers, and **remove** any which are active (have a green circle)

[[img]http://www.ubuntu-pics.de/thumb/58875/hardware_drivers_099_FQSBo6.png[/img]](http://www.ubuntu-pics.de/bild/58875/hardware_drivers_099_FQSBo6.png)

Then restart your PC.

Now go back to Hardware Drivers and **activate** the [recommended] driver.

Restart the PC again.

Then re-enable System -> Preferences -> Appearance -> Effect.

---

### Post by CoreyB. on 2010-05-07
Netbook Edition doesn't use compiz, so no extra desktop effects.  If you want desktop effects, at login you might have to change the session to regular ubuntu, not ubuntu netbook edition.

---

### Post by giteshpandya on 2010-05-08
> **CoreyB. said:**
> Netbook Edition doesn't use compiz, so no extra desktop effects.  If you want desktop effects, at login you might have to change the session to regular ubuntu, not ubuntu netbook edition.

Yes its done after compiz setting.

---

### Post by CoreyB. on 2010-05-08
> **giteshpandya said:**
> Yes its done after compiz setting.

I don't understand?  A fresh install of UNE doesn't contain compiz.  Even if you tried to use it, I think the netbook interface won't use it which is why it resets every time you reboot.

---

