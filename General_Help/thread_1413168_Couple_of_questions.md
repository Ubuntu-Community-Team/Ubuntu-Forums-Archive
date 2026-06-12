---
title: "Couple of questions"
date: 2010-02-22
forum: General Help
---

### Post by Poddy on 2010-02-22
Hello, ive a few questions to ask and i apologise if they have been asked before.

my friend has ubuntu on her notebook and over the past few days it hasnt let her log into any online application. i.e facebook, gmail, yahoo mail etc. Any reason for this or someway of fixing that?

secondly she says her notebook should be 160gig. its a fairly new one and the only harddrive i can see is 6.8. im guessing some1 made 2 partitions and didnt install the other one. anyway i can check if this is true or whatever? 

Thanks alot for your time, im familar wit windows but not this os.

Regards,

Poddy

---

### Post by skymera on 2010-02-22
Hmm, try clearing the Firefox cache. (CTRL + SHIFT + DELETE)
Then try logging in again.

Can you post the output of 
```
 sudo fdisk -l 
```

That's a lower case L :)

---

### Post by Poddy on 2010-02-22
everytime firefox opens that comes up - clear firefox cache.

i do it and still same problem. i then go and manually do it via tools still same problem.

excuse ignorance but how do i do the sudo fdisk thing

---

### Post by skymera on 2010-02-22
Sorry,

Applications > Accessories > Terminal

Then copy that command and then post the output here.

You will need the password :)

---

### Post by Poddy on 2010-02-22
ok it says

[sudo] password for brooklyn: (which is guess is the name of the person that had this notebook b4 my friend. my friend is unaware of any password how can i find it.

---

### Post by NCLI on 2010-02-22
You don't have the password for the netbook? ... This is going to be a problem...

Follow [this guide]("http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/"), though if you're using the latest version of Ubuntu, you'll have to hold down shift instead of pressing ESC to get GRUB up.

Also, be aware that nothing will be happening on the screen while entering the new password, this is normal.

---

### Post by skymera on 2010-02-22
> **Poddy said:**
> ok it says

[sudo] password for brooklyn: (which is guess is the name of the person that had this notebook b4 my friend. my friend is unaware of any password how can i find it.

How did you login then?

Is it automatic? 
The login password is the one you need.

---

### Post by Poddy on 2010-02-22
thanks alot i dont see any grub loading screen only thing i see is

MBR 2FA:

---

### Post by Poddy on 2010-02-22
yeh automatic login

---

### Post by NCLI on 2010-02-22
> **Poddy said:**
> thanks alot i dont see any grub loading screen only thing i see is

MBR 2FA:

Just hold shift while your computer is starting 'till GRUB shows up.

---

### Post by Poddy on 2010-02-22
I held shift when it starts up and nothing comes up

---

### Post by Poddy on 2010-02-25
*bump*

---

