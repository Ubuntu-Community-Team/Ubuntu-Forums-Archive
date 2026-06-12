---
title: "At a complete loss with SATA link issue??"
date: 2011-10-02
forum: General Help
---

### Post by listerdl on 2011-10-02
I am completely baffled by this...

My log viewer keeps constantly (every 2 seconds) giving this error:

```
limiting SATA link speed to 1.5 Gbps
ata4: hard resetting link
```

I get this error wuth Ubuntu (latest distro) and any other previous version of Ubuntu using a normal magnetic HD Drive and a new SSD Drive....

This is really weird....is there any way to correct this error?
I am not sure even what this error means!

Any help would be appreciate here thanks!

---

### Post by matt_symes on 2011-10-02
Hi

Your getting read errors from one of the drives and it is limiting the speed. 

Test the SMART status of the drives. Check any cabling and connections. Remove each drive until the messages go to determine the drive that is causing the problem.

Exactly what is the make and model of the computer ?

Kind regards

---

### Post by listerdl on 2011-10-02
> **matt_symes said:**
> Hi

Your getting read errors from one of the drives and it is limiting the speed. 

Good to know that - 

> **matt_symes said:**
> Test the SMART status of the drives.

I did this with windows and also through ubuntu and there were no errors

> **matt_symes said:**
> Check any cabling and connections. Remove each drive until the messages go to determine the drive that is causing the problem.

I removed each drive from my laptop (which is the machine in question) and tried with another type of drive - SSD and regular HD - same issues. I havent got round to changing the actual cable or connection - mostly b/c I am not too sure how to change that within the machine itself - 

> **matt_symes said:**
> Exactly what is the make and model of the computer ?

It is a Panasonic Toughbook CF F8 bought in Japan but I installed dual boot onto it - its about 2 years old now - I can give you more specs if those help more.

Thanks for your help

---

### Post by listerdl on 2011-10-02
Might be worth also saying that I think it is an issue in the BIOS - the reason I say that is b/c I changed the drives.

Then again - the cabelling was the same that was used for both drives as well.....

This is certainly getting confusing...thanks for all help and inputs here.

---

### Post by matt_symes on 2011-10-03
Hi

It may be an issue with the SATA controller or the driver. i would definitely have a look at the BIOS settings as well.

Kind regards

---

