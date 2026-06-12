---
title: "problem in system"
date: 2011-12-30
forum: General Help
---

### Post by zxc_0 on 2011-12-30
hi everybody 

i want to introduce my problem

which is that the computer When the  run starts 
 
comes upuntu logo And written under the logo error and thank you  so much  and i hope That Unravel the problem

---

### Post by Rubi1200 on 2011-12-30
While we understand and appreciate that English is not your native language, if you expect us to help you then please provide more information and try and explain the problem in more detail.

Thanks for understanding.

---

### Post by zxc_0 on 2011-12-30
first  Engage   computer comes Square  above write  gun grub version 1.99-12 ubuntu 5

and under box Choice  four first choice written ubuntu , which linux 3.0.0-14 generic - pge

Second  ubuntu , which linux 3.0.0-14 generic - pge (recovery mode)

third previous liunx versions 

fourth  memory test ( memtest 86+)

fifth memory test ( memtest 86+ , serial console 115200


if press first choice come written error were found while checking disk drive for

---

### Post by Paqman on 2011-12-31
Were you previously able to boot Ubuntu ok, or have you just installed it?

---

### Post by zxc_0 on 2011-12-31
Previously it  worked but now 

never Not able not work comes  written error were found while checking disk drive for

---

### Post by oldos2er on 2011-12-31
Please use the default font, and do not bump your post more than once every 24 hours. Thanks.

---

### Post by zxc_0 on 2012-01-01
guys the computer not work what Solution and thank you

---

### Post by fdrake on 2012-01-01
go to > select option #2 "linux recovery"> select "root" > press "Enter"and type :
```

fsck -y

```


or you can use a live cd , boot from the cd and run "fsck -y" from the terminal!

---

### Post by zxc_0 on 2012-01-01
install from internet What i do 

and i cant enter computer

which Comes to me  

ubuntu , which linux 3.0.0-14 generic - pge

Second ubuntu , which linux 3.0.0-14 generic - pge (recovery mode)

third previous liunx versions 

fourth memory test ( memtest 86+)

fifth memory test ( memtest 86+ , serial console 115200
 
what  choice

---

### Post by yugnip on 2012-01-01
> **zxc_0 said:**
> install from internet What i do 

and i cant enter computer

which Comes to me  

ubuntu , which linux 3.0.0-14 generic - pge

Second ubuntu , which linux 3.0.0-14 generic - pge (recovery mode)

third previous liunx versions 

fourth memory test ( memtest 86+)

fifth memory test ( memtest 86+ , serial console 115200
 
what  choice

Choose the "Second ubuntu , which linux 3.0.0-14 generic - pge (recovery mode)" and then follow fdrake's good advice above.

---

### Post by zxc_0 on 2012-01-01
comes to me 

recovery menu 

resume       resume normal boot

clean        try to make free space

dpkg         repair broken packages 

grub         update grub boot loader 

netroot      drop to root shell prompt with networking 

root        drop to root shell prompt 

what choice

---

### Post by fdrake on 2012-01-01
> **zxc_0 said:**
> comes to me 

recovery menu 

resume       resume normal boot

clean        try to make free space

dpkg         repair broken packages 

grub         update grub boot loader 

netroot      drop to root shell prompt with networking 

root        drop to root shell prompt 

what choice

select "root - root drop to root shell prompt " > press "Enter"and type :
```

fsck -y

```

---

### Post by zxc_0 on 2012-01-01
And then

---

### Post by fdrake on 2012-01-01
> **zxc_0 said:**
> And then
then type
"reboot now" or just reboot and check fi you can boot normally

---

### Post by zxc_0 on 2012-01-01
i have for you Glad tidings computer is work 

Thank you very much and  i dont know what to tell you feeling 

Indescribable

---

### Post by fdrake on 2012-01-01
i am happy for you ! :D

---

