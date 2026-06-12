---
title: "Ubuntu only boots successfully about one in three times"
date: 2010-05-30
forum: General Help
---

### Post by svivian on 2010-05-30
When I startup my computer, Ubuntu doesn't always load. It goes through the GRUB bootloader stage fine, and I get the message

> Boot from (hd0,4) ext3 ....[something here]
Starting up...

It stays on that for a while (maybe 30 seconds), then the screen either just goes black or white and nothing else happens. No Ubuntu logo, no GUI, no mouse etc. No keyboard combinations appear to work like Ctrl+Alt+Backspace.

I tried running the recovery mode but all that does is give me a command prompt and no indication of any errors. I ran memtest86 and it showed no errors.

My system is a Dell Inspiron 531, dual-booting with Windows Vista.

It makes no sense that Ubuntu will boot some times but not others! Can anyone help?

---

### Post by ajgreeny on 2010-05-30
I used to occasionally have exactly the same problem, but certainly not once every three boots, mine was more like once a month at most.  I think mine was down to a poor connection between the IDE disk and the ribbon cable, as after a fiddle inside the machine, disconnecting and then reconnecting the disk, all seems OK and I have not had that particular problem for a long time.

It may also have been a power supply problem, as I occasionally even now have a problem in the POST, where the screen display says "Detecting disks", and then goes no further.  Pressing the reset button does not help here as the sequence will repeat same thing again.  Only by switching off completely, even for a couple of seconds will it work next time, hence my suspicion of the power supply.  It is so uncommon, however, and so easy to put right on this old desktop, that I have not investigated further, as I don't think it would be an economic repair at this stage of the machine's life;  I just live with it.

---

### Post by etdsbastar on 2010-05-30
during installation have you used ext4 as your file system, i have noticed that this file system is causing problems with some systems, try reinstalling your distro with ext3 support.

---

### Post by ajgreeny on 2010-05-30
> **etdsbastar said:**
> during installation have you used ext4 as your file system, i have noticed that this file system is causing problems with some systems, try reinstalling your distro with ext3 support.
The problem I noted above in my post was when I was on ext3 not ext4, so that may be a bit of a red-herring, I'm afraid.  If anything I see the problem less now that ext4 has taken over my machine.

---

### Post by svivian on 2010-05-30
Thanks for the replies.

> **etdsbastar said:**
> during installation have you used ext4 as your file system, i have noticed that this file system is causing problems with some systems, try reinstalling your distro with ext3 support.

I upgraded from 9.10 which was on ext3. AFAIK the filesystem hasn't changed. Plus it says "ext3" during bootup, as I said in the first post.

Also, I don't know if this is relevant but when bootup works, that 'terminal' message stays on the screen for most of the boot, I get like half a second flash of the ubuntu logo. Previously it stayed with the ubuntu loading bar for most of the boot. I also get a horrid flash of black and white horizontal stripes.

ajgreeny, I checked connections etc inside the case and everything seems fine. Still having the same problem.

Is there some way to debug what is happening to try and find the cause?

---

### Post by ajgreeny on 2010-05-31
I would probably go with the power supply problem in that case, and short of replacing it, I think it is a bit more difficult to diagnose further.

---

### Post by akakingess on 2010-05-31
> **svivian said:**
> Thanks for the replies.



I upgraded from 9.10 which was on ext3. AFAIK the filesystem hasn't changed. Plus it says "ext3" during bootup, as I said in the first post.

Also, I don't know if this is relevant but when bootup works, that 'terminal' message stays on the screen for most of the boot, I get like half a second flash of the ubuntu logo. Previously it stayed with the ubuntu loading bar for most of the boot. I also get a horrid flash of black and white horizontal stripes.

ajgreeny, I checked connections etc inside the case and everything seems fine. Still having the same problem.

Is there some way to debug what is happening to try and find the cause?

I wouldn't worry too much about the lack of a "splash" screen and witnessing a lot of the actual boot-up process, I believe that that has something to do with Lucid Lynx not using Usplash but something new that I can't remember the name of for the life of me, and I think others (including myself) are having the same issue. I believe that there is a workaround, but shouldn't have anything to do with not booting 1 out of 3 times.  Have you checked Launchpad.net (need to create an account, but good to have one anyway)?

---

### Post by svivian on 2010-05-31
> **ajgreeny said:**
> I would probably go with the power supply problem in that case, and short of replacing it, I think it is a bit more difficult to diagnose further.

Hmm, OK thanks. Seems odd that a power supply problem would allow the OS to boot to ~90% then stop.

I might try reinstalling Ubuntu from scratch, see if that fixes anything.

---

### Post by etdsbastar on 2010-06-01
> **svivian said:**
> Hmm, OK thanks. Seems odd that a power supply problem would allow the OS to boot to ~90% then stop.

I might try reinstalling Ubuntu from scratch, see if that fixes anything.

Better to try reinstalling from scratch... good luck friend.

---

