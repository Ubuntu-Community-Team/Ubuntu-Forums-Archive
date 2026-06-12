---
title: "Thunderbird 7.0.1 crashes in Ubuntu 11.10"
date: 2011-10-16
forum: General Help
---

### Post by stefke on 2011-10-16
I've just updated to Ubuntu 11.10 everything seems to work fine but only Thunderbird keeps crashing when I try to compose a message. It seems that it's always happening when a new window has to open. 

I keep getting the folowing message in the therminal when I start thunderbird:

```

user@machine:~$ thunderbird

(thunderbird-bin:3759): GLib-GObject-WARNING **: cannot register existing type `DbusmenuServer'

(thunderbird-bin:3759): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(thunderbird-bin:3759): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed


```

I don't get these messages when I run thunderbird as an other user. I didn't had this problem before the dist-upgrade.
Does anyone also has this problem? Or does anyone know how to solve this?

---

### Post by Mouette&amp;Jambon on 2011-10-17
Same issue here..
Disabling the extension "Global Menu Bar Integration 2.0.1" seems to do the trick, for now...

Waiting for an update

---

### Post by Mouette&amp;Jambon on 2011-10-17
Remove an old messaging add-on (Messaging unity 0.6 in my case) which is not compatible anymore.

---

### Post by stefke on 2011-10-17
Thanks, this also fixed the problem for me!

---

### Post by mcgalactor on 2011-10-17
Thank you,

you saved my day.

---

### Post by marketleverage on 2011-10-17
Same here, but i use thunderbird without any extensions so i do not have what to remove

i install kubuntu plasma, xubuntu,  wiht no luck but ubuntu classical desctop do the job for me

```
sudo apt-get install gnome-panel
```

restart and select from sprocket Ubuntu classical desctop (without effects) login and thunderbird works normaly:KS:)

P.S I've got suggesstion about ubuntu 12 you can release next version with bonus to the main mail client not working,  without main browser working too, or even without networking so we can't complain about it :lolflag:

---

### Post by mdavies5 on 2011-10-20
I have same problem. Have disabled all add-ons as suggested above but does not solve problem.

---

### Post by Green_Vigo on 2011-10-21
Same issue here too. Am pretty new to ubuntu so not sure if I should try disabling add ons in the terminal as the program itself doesn't stay stable long enough for me to remove anything before hanging. Takes down the whole system more or less for about 5 minutes whilst trying to kill the process from task manager.

---

### Post by mdacova on 2011-10-25
> **Mouette&Jambon said:**
> Same issue here..
Disabling the extension "Global Menu Bar Integration 2.0.1" seems to do the trick, for now...

Waiting for an update


seems to help me also, opps thanks

---

### Post by xtremo on 2011-10-25
I had the same on 11.10.....along with a few other quirks. I just went back to 11.04.

---

