---
title: "Karmic Re-enable system beep"
date: 2010-02-24
forum: General Help
---

### Post by pantherattack on 2010-02-24
Hi,

I like the system beep because I can tell checkgmail to beep when an email comes, that way my speakers don't have to be on.

Anyways, I did a fresh install of Karmic the other day. Something is being weird with me when I try to re-enable the beep. Karmic blacklisted pcspkr in /etc/modprobe.d/blacklist.conf . Here's what happens:

I leave "blacklist pcspkr" in blacklist.conf and restart. I do "sudo modprobe pcspkr" and then "beep", and it beeps. Good.

Then I comment out "blacklist pcspkr" in blacklist.conf and restart. I do "beep". Nothing. I do "sudo modprobe pcspkr" and then "beep". Nothing. I do "lsmod | grep pcspkr". It's listed there as it should be. I check with "sudo grep pcspkr  /var/log/dmesg" and find no errors.

Can anybody help me?

Ian

---

### Post by pantherattack on 2010-02-26
Hmm, does no one know what's going on?

---

### Post by Gonz_91 on 2010-03-07
Hi!

I know this is a week old, but I stumbled up on it and didn't want to open another one for the same thing.

I'm exactly in the same situation as the original poster: can use "beep", but can't echo '\a'.

I need my speaker to work since I have a programming assignment involving it, and can't test out my code because of this problem...

Thanks a lot

---

### Post by s26c.sayan on 2010-10-02
>> echo '\a'.

Should be echo -e '\a'.

The -e flag turns on interpretation of backslashed characters.

---

