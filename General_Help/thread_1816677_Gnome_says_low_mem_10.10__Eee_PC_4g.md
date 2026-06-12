---
title: "Gnome says low mem? 10.10 / Eee PC 4g"
date: 2011-08-02
forum: General Help
---

### Post by Jacob72 on 2011-08-02
Hello, I am getting a memory warning message from Gnome. It prevented me from loging in. I have hardly any programmes running and this never happend when I was running windows? I am wondering if I have installed ubuntu incorrectly?

I went into the bios and was able to boot using safe mode (Sorry I do not have the Eee pc open now and don't remember the exact terminology). I logged in and my memory display shows it is almost used up on the OS and openofice?

Can't remeber now but I htink I have 1-2g mem.

Please advise what I need to do.

Thanks

---

### Post by pqwoerituytrueiwoq on 2011-08-02
during boot at the grub menu run the memory test to make sure the ram is good

---

### Post by pAsM on 2011-08-02
Hello,
    Try entering a TTY (Pres ALT+CTRL+F3) and type "free -m" andter you login. Place the output here. It should look something like


```
myerkx@l03myerkx ~ $ free -m
             total       used       free     shared    buffers     cached
Mem:          **3905**       1937       1967          0        239        991
-/+ buffers/cache:        707       3198
Swap:         3975          0       3975

```

This will show you the amount of RAM you have. May I also ask if you are using Gnome 2.x or 3.x

---

### Post by Jacob72 on 2011-08-05
Hi, thanks for your replies.

>          during boot at the grub menu run the memory test to make sure the ram is good     Yes the memory is good.

> Try entering a TTY (Pres ALT+CTRL+F3) and type "free -m" andter you login. Place the output here. It should look something likeAfer pressing 'ALT+CTRL+F3' I get a black screen that asks for 'login' then 'password'. This may sound silly but I don't know what to put for 'login' and 'password' does not let me type anything?

Edit:

I typed the command "free -m" in 'Terminal' and got this:

-------total          used           free        shared       buffers        cached
Mem:            2004            892     1111               0------ 131-----331
-/+ buffers/cache:        430       1574
Swap:          220          0        220



Thanks

---

### Post by Jacob72 on 2011-08-05
I am also getting warning message:

"hard disk may be failing"

---

### Post by cgroza on 2011-08-05
> **Jacob72 said:**
>  This may sound silly but I don't know what to put for 'login' and 'password' does not let me type anything?

Just type your password there and hit Enter. It is the normal behavior.

---

### Post by Jacob72 on 2011-08-05
Ok thanks.

Did you see my edit above with mem info?

---

### Post by Jacob72 on 2011-08-06
I tried to remove Open Office via Synaptic Packet Manager to see if this would have any efect on my memory. I left the programme running for hours but it did not remove Open Office.

How long should it take to remove a programe and is this the correct way to do it?

---

### Post by Jacob72 on 2011-08-06
> **pAsM said:**
>  May I also ask if you are using Gnome 2.x or 3.x
Sorry, I over looked this.

I am running version 2.32.0

---

### Post by Jacob72 on 2011-08-06
> **cgroza said:**
> Just type your password there and hit Enter. It is the normal behavior.
I did this but it keeps saying password incorrect?

I did provid the Terminal data, looks like the mem to me?

---

