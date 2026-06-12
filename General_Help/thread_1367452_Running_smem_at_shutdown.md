---
title: "Running smem at shutdown"
date: 2009-12-29
forum: General Help
---

### Post by homemadejam on 2009-12-29
Hey,

So I want the command smem to run when my laptop is shutting down. (smem whips your RAM securly)

I have had a try at adding my script to /etc/rc0.d/ & /etc/rc6.d/ and when I shutdown / reboot I get an error something like "out of memory, Killing process: smem"

Could someone please give me some pointers to what I am doing wrong?

The command I'm running is:
```
sudo update-rc.d smem start 10 0 6 .
```
Is this right?

And in the smem script (located in /etc/init.d/) has the following command:
```
/usr/bin/smem -f -l -l -v
```


Thanks in advance!
Jam

---

### Post by homemadejam on 2009-12-29
I have just tried changing the name S20mem (what it is called in /etc/rc0.d/) to S01mem... but this only seems to make more errors like before.

I have been reading up on how to do this, but I'm just getting very confused now! If anyone has the answer, I would really appreciate it.

Thanks,
Jam

---

### Post by dcstar on 2009-12-29
> **homemadejam said:**
> Hey,

So I want the command smem to run when my laptop is shutting down. (smem whips your RAM securly)

I have had a try at adding my script to /etc/rc0.d/ & /etc/rc6.d/ and when I shutdown / reboot I get an error something like "out of memory, Killing process: smem"
.........

Firstly, apart from the utter pointlessness of wiping something that is reset when the power goes off, the shutdown/reboot procedures are still using the memory that you are now trying to "wipe".

---

### Post by homemadejam on 2009-12-29
> **dcstar said:**
> Firstly, apart from the utter pointlessness of wiping something that is reset when the power goes off, the shutdown/reboot procedures are still using the memory that you are now trying to "wipe".


I'm able to run this command whilst logged in though?


Jam

---

### Post by dcstar on 2009-12-30
> **homemadejam said:**
> I'm able to run this command whilst logged in though?

Jam

So what is it actually "wiping" then?, it can't be any RAM that is actually in use because then that would immediately crash your system.

If it just wipes unallocated memory, then that is constantly changing during the shutdown process anyway and again, what is the point?

---

