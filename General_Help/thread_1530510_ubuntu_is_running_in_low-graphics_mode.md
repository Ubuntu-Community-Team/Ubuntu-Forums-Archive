---
title: "ubuntu is running in low-graphics mode"
date: 2010-07-13
forum: General Help
---

### Post by Rip-Saw on 2010-07-13
I get the error when booting "ubuntu is running in low-graphics mode"
(EE) Failed to load module "1810" (module does not exist, 0)
(EE) config/hal: couldn't initialize context: unknown error (null)
This happened after updating unbuntu and an error happened while updating. I don't recall what the error was. I cannot run ubuntu in low graphics mode, it goes to black screen and nothing happens.

---

### Post by Rip-Saw on 2010-07-14
The problem has yet to miraculously fix itself.

---

### Post by Rip-Saw on 2010-07-15
The problem has yet to miraculously fix itself.

---

### Post by QIII on 2010-07-15
What is the manufacturer and model of your graphics card?

Also, please remember that we are all here on our own time as we have it -- voluntarily.  It may be that there is someone out there who has the  exact answer to you problem.  But he may live in Bangalore and be asleep  when you post.  When he wakes up, he may eat breakfast, pat the kids on  the head, kiss his wife (or her husband) and go off to work.

An acidic bump like yours might cause people to just move on, so it might be in your best interest to be as courteous as you expect us to be.

---

### Post by Rip-Saw on 2010-07-18
It's onboard graphics. I've no idea.
I know of no other way to bump a post. It's good to keep a topic refreshed if you're still having a problem.

---

### Post by Rip-Saw on 2010-07-18
Intel 82865g is all I can find.

---

### Post by QIII on 2010-07-18
Can you log into the recovery option?  If you can, select "root with networking" and at the command line, type

```
sudo apt-get update
```followed by 

```
sudo apt-get upgrade
```Have something handy to write with.  If you get errors, please copy down as much detail as you can.

If the updates work without error, try to boot again and see if you can run.

If not, then ...

If you have a LiveCD, boot from it.  Go to the terminal (Applications | Accessories | Terminal) and type (or cut and paste)

```
lspci
```and press enter.

You should get a fairly long list.  Cut and paste the whole thing back here, along with any errors you noted when you tried to update.

The forum policy is that you should bump no more often than 24 hours.  If you bump more often, remember that you push others down in the queue and their questions may get missed.

All you need to do is type "bump".

---

### Post by Rip-Saw on 2010-07-20
The hard drive was full. ](*,)](*,)](*,)](*,)](*,)
Leave it to ubuntu to give virtually no warning at all that the drive is full, and let me happily reboot it knowing full well it will be unable to start.
Deletes some stuff, ran update again, now it works. Thanks for the help.

---

