---
title: "Is it 32 bit or 64bit?"
date: 2011-09-01
forum: General Help
---

### Post by amitsaini on 2011-09-01
please help...
i am a total novice at ubuntu.Finished installing and checked architechture using uname -a 
got this message:
 
Linux aks-Presario-C500-RU914PA-ACJ 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
 
please help?

---

### Post by howefield on 2011-09-01
32 bit operating system.

---

### Post by haqking on 2011-09-01
> **amitsaini said:**
> please help...
i am a total novice at ubuntu.Finished installing and checked architechture using uname -a 
got this message:
 
Linux aks-Presario-C500-RU914PA-ACJ 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
 
please help?

it is 32 bit.

best to use

uname -m

as it is more specific, if it shows i686 then 32 bit, if x64 then it is 64 bit

---

### Post by amitsaini on 2011-09-01
If its 32 bit then why is it not accepting the 32 bit driver i downloaded at this link
[http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)

---

### Post by amitsaini on 2011-09-01
Also with 64 bit it says wrong architechture...

---

### Post by amitsaini on 2011-09-01
How should i proceed further?Kindly advise.

---

### Post by haqking on 2011-09-01
> **amitsaini said:**
> If its 32 bit then why is it not accepting the 32 bit driver i downloaded at this link
[http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)

i dont know that depends on the error doesnt it ;-)

show us the error and what you are trying to do, try a screen dump

---

### Post by amitsaini on 2011-09-01
What is a screen dump i'm sorry i didnt get it. But while doing so i had been able to remove the drivers using this:
 
sudo apt-get remove bcmwl-kernel-source
 
Also in the synaptic software there isn't anything by bcm drivers maybe coz i might have removed it.

---

### Post by haqking on 2011-09-01
> **amitsaini said:**
> What is a screen dump i'm sorry i didnt get it. But while doing so i had been able to remove the drivers using this:
 
sudo apt-get remove bcmwl-kernel-source
 
Also in the synaptic software there isn't anything by bcm drivers maybe coz i might have removed it.

first lesson is not to do anything especially remove unless you know what you are doing, Linux always assume you do ;-)

a screen dump is pressing the PrtSc key when you want to take an image of your screen then it saves it as a file to where you lik then you can attach it in a post so we can see what is going on

i presume you are having issues with your broadcom device ?

---

### Post by amitsaini on 2011-09-01
Correct. I want to get my wireless on track

---

### Post by amitsaini on 2011-09-01
apart from that the os is working fine.

---

### Post by amitsaini on 2011-09-01
Please help with any additional help.sorry right now i have to move ,i have a long day ahead. Thanks haqking for your help but please add more. will definitely get back tomorrow...

---

