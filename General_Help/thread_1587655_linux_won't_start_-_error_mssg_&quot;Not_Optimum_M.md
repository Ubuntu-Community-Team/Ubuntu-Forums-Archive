---
title: "linux won't start - error mssg: &quot;Not Optimum Mode&quot;"
date: 2010-10-03
forum: General Help
---

### Post by snorkytheweasel on 2010-10-03
Compaq 64-bit using onboard nvidia geforce 6150 le
4 GB ram
[LIST]
[*]New hard drive, installed ubu 10.04
[*]This computer worked perfectly until the old hard drive crashed
[*]Installed from same install disk as previous
[*]In other words, nothing - except the new drive - changed
[/LIST]
This installation (twice!) went flawlessly. In each case, I did a 'standard' installation, i.e., I answered the prompts and let the installer do all the work - which is what I always do.

POST goes as expected.
But instead of ubu starting, I get a message:
[B][CENTER]"Not Optimum Mode
Recommend 1680 x 1050 60 hZ"
and a box with a question mark[/CENTER][/B]

It's not a hardware problem. This computer has, from day 1, shared a monitor via KVM. The other machine on the KVM is running windows and has no problem.

I tried switching the video ports on the KVM: the problem followed the ubuntu machine to the new port, and the windows machine continued to run fine.

What's happening and what's the fix?

---

### Post by psusi on 2010-10-03
Try taking the KVM out of the picture and connecting the monitor directly.  The message sounds like it is the monitor complaining that you are running in a video resolution it does not support, but it could be the KVM.

---

### Post by snorkytheweasel on 2010-10-04
> **psusi said:**
> Try taking the KVM out of the picture and connecting the monitor directly.  The message sounds like it is the monitor complaining that you are running in a video resolution it does not support, but it could be the KVM.

That didn't help.

---

### Post by snorkytheweasel on 2010-10-04
> **snorkytheweasel said:**
> Compaq 64-bit using onboard nvidia geforce 6150 le
4 GB ram
[LIST]
[*]New hard drive, installed ubu 10.04
[*]This computer worked perfectly until the old hard drive crashed
[*]Installed from same install disk as previous
[*]In other words, nothing - except the new drive - changed
[/LIST]
This installation (twice!) went flawlessly. In each case, I did a 'standard' installation, i.e., I answered the prompts and let the installer do all the work - which is what I always do.

POST goes as expected.
But instead of ubu starting, I get a message:
[B][CENTER]"Not Optimum Mode
Recommend 1680 x 1050 60 hZ"
and a box with a question mark[/CENTER][/B]

It's not a hardware problem. This computer has, from day 1, shared a monitor via KVM. The other machine on the KVM is running windows and has no problem.

I tried switching the video ports on the KVM: the problem followed the ubuntu machine to the new port, and the windows machine continued to run fine.



More info: a fast-moving message says
**SMBUS2 ** 
and it says
**error  probing smb1**
the message disappears after 1 - 2 seconds

---

### Post by snorkytheweasel on 2010-11-18
Not an answer that anyone wants to hear:

I installed Windows on the machine with the quirky video, and used an older, slower pc for the linux server.

Life is too short ... and banging my head against the wall hurts.

---

