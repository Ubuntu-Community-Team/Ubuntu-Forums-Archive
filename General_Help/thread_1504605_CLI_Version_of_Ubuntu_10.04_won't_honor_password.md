---
title: "CLI Version of Ubuntu 10.04 won't honor password"
date: 2010-06-08
forum: General Help
---

### Post by Hudson78 on 2010-06-08
I have an old PC (130mb RAM, 6gb hard drive).

I installed a command-line version of Ubuntu 10.04 using the Alternate CD.  The machine was wiped, and I used most of the default settings.

I used a thirteen character user id which consisted of mixed case letters and numbers, and an eighteen character password that contains mixed case letters and numbers and a # sign. 

When I rebooted, the command-line login would not accept my password. I assumed I had somehow made a mistake, and just wiped the machine again and reinstalled. This time I was very careful with the user name/pw.

Again, the command-line login did not accept my password!

On a hunch, I took an old Ubuntu 7.10 Alternate CD and erased the machine again. I installed a command-line version of Ubuntu. AGAIN --- it will not accept my password even though I'm 100% sure it is correct.

What is going on here?

Thanks in advance for any advice.

---

### Post by oldos2er on 2010-06-08
What do you mean by "accept"? Nothing is echoed to the screen when entering a password in CLI. Apologies if you knew that already.

---

### Post by Hudson78 on 2010-06-08
> **oldos2er said:**
> What do you mean by "accept"? Nothing is echoed to the screen when entering a password in CLI. Apologies if you knew that already.

A message was displayed saying that the login was incorrect.

However, this problem appears to have gone away by formatting the drive as ext3 instead of ext4.

I have just got this working within the last ten minutes, so new problems might appear.

I have also noted that my BIOS is ridiculously old.  Maybe that is the core problem I was having.

---

