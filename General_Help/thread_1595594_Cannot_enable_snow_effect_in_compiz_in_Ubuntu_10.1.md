---
title: "Cannot enable snow effect in compiz in Ubuntu 10.10"
date: 2010-10-13
forum: General Help
---

### Post by SuperUserDO on 2010-10-13
hi,when i try to enable the snow effect in compiz it disable itself :confused: 
where is the problem??
Thank you.

---

### Post by JackNocturne on 2010-10-13
Hi,
What do you mean it disables itself?   

Also what graphics card do you have?  IF you are not sure ,type the following in the **terminal**
    ```
lspci | grep -i graphics

```

---

### Post by SuperUserDO on 2010-10-13
> **JackNocturne said:**
> Hi,
What do you mean it disables itself?   

Also what graphics card do you have?  IF you are not sure ,type the following in the **terminal**
    ```
lspci | grep -i graphics

```

my graphic card is: ATI Technologies Inc RS690 [Radeon X1200 Series]:)
thanks for the fast reply.

---

### Post by SuperUserDO on 2010-10-13
> **JackNocturne said:**
> Hi,
What do you mean it disables itself?   

Also what graphics card do you have?  IF you are not sure ,type the following in the **terminal**
    ```
lspci | grep -i graphics

```

my graphic card is: ATI Technologies Inc RS690 [Radeon X1200 Series]:)
this effect was working well in Ubuntu 10.04,but i cant enable it in Ubuntu 10.10 :(
thanks for the fast reply.

---

### Post by JackNocturne on 2010-10-13
Hi again,

I think it is a problem related to the driver issues. People have been reporting trouble with drivers in Ubuntu 10.10.  
Unfortunately i lack the knowledge in this. 
It's good that we know what the problem is, i'm sure someone with knowledge of ATI graphics card drivers will point you to the right way.

---

### Post by Quarkrad on 2010-10-20
I'm getting the same problem with Nvidia graphics.

---

### Post by gohsthb on 2010-11-30
This solved it for me:

[http://sathyasays.com/2009/02/01/how-to-snow-plugin-in-compiz-fusion/](http://sathyasays.com/2009/02/01/how-to-snow-plugin-in-compiz-fusion/)

Just follow the directions there.  If snow was installed by default, it is broken.  Remove the old snow plugin and replace it with this one.

---

