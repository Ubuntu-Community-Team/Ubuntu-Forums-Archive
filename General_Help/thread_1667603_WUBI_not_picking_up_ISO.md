---
title: "WUBI not picking up ISO"
date: 2011-01-15
forum: General Help
---

### Post by kikloo on 2011-01-15
Hello,

I downloaded WUBI and latest version of Ubuntu. When I try to run WUBI with ISO then it does'nt picks it up and tries to get Ubuntu through internet.

If i turn off the internet then it gives an error and exits.

What to do ?

Thanks.

---

### Post by Rubi1200 on 2011-01-15
Hi,
put the wubi.exe and ISO in the same folder and then try again.

---

### Post by kikloo on 2011-01-15
> **Rubi1200 said:**
> Hi,
put the wubi.exe and ISO in the same folder and then try again.

Hello,

I did but that was not working. So what i did was: I installed Deamon Tools Lite and mounted the ISO in it and then ran WUBI from it and it worked.

Thanks.

---

### Post by bcbc on 2011-01-15
You probably picked up the wubi.exe from [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer"). This is at release 10.04.1. 

If you don't have the exact release it will ignore the .iso. Doing it from the wubi.exe within the .iso always gets the correct release. Sometimes people have problems installing from an .iso mounted with daemon tools, for unclear reasons.

---

### Post by kikloo on 2011-01-16
> **bcbc said:**
> You probably picked up the wubi.exe from [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer"). This is at release 10.04.1. 

If you don't have the exact release it will ignore the .iso. Doing it from the wubi.exe within the .iso always gets the correct release. Sometimes people have problems installing from an .iso mounted with daemon tools, for unclear reasons.

Hi,

Yes i picked it from there. Whats the point of putting it there if it will not work with the available download of Ubuntu.

Anyways why WUBI devs do not put a browse button in WUBI ?

Thanks.

---

