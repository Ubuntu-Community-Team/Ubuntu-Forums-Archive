---
title: "Wireless adapter stopped working"
date: 2011-07-26
forum: General Help
---

### Post by inoh on 2011-07-26
Yesterday I installed many updates on my compaq presario cq60-214dx running ubuntu 11.04.

This morning my 2 year old son was pressing buttons, generally playing with the notebook.  When he was done the wireless stopped working.  I cannot get it to come back on.  What could he have possibly done without entering the password.

I have restarted several times.  ifconfig does not show the wireless adapter.  iwconfig says its not active.  i turned on txpower using iwconfig but still nothing.

Where so I start?

---

### Post by Peter09 on 2011-07-26
Have you a hardware or software switch to turn your wireless on/off. Its often the <fn key>+<a function key>.

---

### Post by TBABill on 2011-07-26
+1 to Peter's post above. I have a Dell laptop that it is very easy to disable simply by accidentally striking F2 without need for the Fn key. Happens quite often when others use it.

---

### Post by inoh on 2011-07-26
I have a radio button right next to the power button.  I have tried several times to no avail.  This button has never worked with Ubuntu on this Notebook expect to turn blue to show it is working.  Yet it is blue right now and still not working.

---

### Post by Peter09 on 2011-07-26
first try

```
rfkill list
```

you can unblock any thing with:

```
rfkill unblock all
```

---

### Post by inoh on 2011-07-26
Between toggling rfkill and the radio on/off button its back.  Just weird to me.

At first the hp wifi would be hard kill off, soft kill on.  After some odd toggling all works.

Thanks to all who helped

---

### Post by Peter09 on 2011-07-26
One thing to consider when you use the on/off button is (in my experience) it switches off immediately, however it can take a long time (30 secs?) for the driver to pick up that the device is on. I spent some time once trying to turn a device back on - the temptation to try the button again (switching it off) was too strong.

---

