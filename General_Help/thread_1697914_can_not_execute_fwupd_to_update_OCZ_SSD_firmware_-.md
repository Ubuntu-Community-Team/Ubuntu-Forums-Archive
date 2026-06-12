---
title: "can not execute fwupd to update OCZ SSD firmware - no such file or directory"
date: 2011-03-01
forum: General Help
---

### Post by LonelyStar on 2011-03-01
Hi,

I want to update the firmware of my OCZ SSD. I am using the fwupd tool from the OCZ website. When I execute it, I get:
```

sudo ./fwupd /dev/sda
[sudo] password for nhuesken: 
fwupd v1.12: update drive firmware

updating /dev/sda

	Model Number     :   OCZ-VERTEX2                             
	Serial Number    :   OCZ-UE3WLE8Y35K7J98U
	Firmware Revision:   1.27    
Firmware update FAILED: drive is locked/frozen.
Please power cycle and retry.

```

Probably, because the system is located on the drive?

So, I booted from a ubuntu USB-Stick and tried to execute fwupd from there. I get a very strange error:
```

sudo: can not excute ./fwubd: no such file or directory

```
But the file exists (in the current directory!), I can see it when I do an "ls".

So I try, to first do "sudo -i" and execute it from this state, now I get:
```

-bash: no such file or directory

```

I do not get it, what could be wrong? How can I update my OCZ firmware?

Thanks!
Nathan

---

### Post by Zenguy on 2011-03-02
Here are a few things to consider.

1) You cannot update a drive that is in use. Try updating it while it is unmounted. That's why the update failed. The live CD is a good strategy.

2) It appears as though you typed in ./fwudp instead of ./fwupd. That probably accounts for the "no such file or directory" error.

3) Check your permissions and execute as sudo.

I just finished updating my drive under Lucid 64. Worked great.

Good luck.

---

### Post by LonelyStar on 2011-03-03
Hey,

Thanks for the reply and the tips!
I found out: The problem is, that I tried to start it from an 64Bit live cd.
Using a 32Bit live cd fixed the problem.

Regards,
Nathan

---

