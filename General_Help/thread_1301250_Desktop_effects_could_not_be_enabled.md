---
title: "Desktop effects could not be enabled"
date: 2009-10-25
forum: General Help
---

### Post by dbyjazz on 2009-10-25
I try and change my desktop effects, it says 'searching for drivers' then it comes up with this pop-up window.. I want to be able to use Awn Manager

---

### Post by dhysk on 2009-10-25
what kind of video card do you have?  And what drivers do you have installed for them?

---

### Post by shadow120 on 2009-10-25
i get that too.  it might be that you graphics card isnt supported run this command in the terminal and post the output here

```
lspci | grep VGA
```

---

### Post by dbyjazz on 2009-10-25
```
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
```

---

### Post by shadow120 on 2009-10-25
i think thats a 64 bit card are you running the 64 bit?

did you check to see if any drivers were avalible under system > administration > hardware drivers?

---

### Post by dbyjazz on 2009-10-25
> **shadow120 said:**
> i think thats a 64 bit card are you running the 64 bit?

did you check to see if any drivers were avalible under system > administration > hardware drivers?

the only ones that show up are 'Broadcom B43 wireless driver' and 'Software modem'

and no I'm not running the 64 bit

---

