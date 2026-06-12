---
title: "Ubuntu install resets bootloader?"
date: 2010-12-11
forum: General Help
---

### Post by woolyg on 2010-12-11
Hello everyone,

I bought a new hard drive to install Ubuntu Studio onto on my desktop pc, and upon returning to try to boot up my windows, the PC can only see the linux loader. Can anyone help? Here's what I did:

1. Unplug all of the SATA drives of my motherboard
2. Plug in the SATA of the new drive into SATA 1 port
3. Install Ubuntu Studio and get it running
4. Turn off the machine, and re-plug in the SATA ports from the windows drives (the ubuntu drive is disconnected) to get windows back up
5. Crank it up - boom. No joy.

Now, the boot screen simply displays:

Error: No such device:  xxx-xxxx--xxxx-xxxx-
grub rescue> _



Can anyone shed any light? I know I've done something wrong here, and hopefully it's a meat-head move with a simple enough fix.. something to do with editing the bootloader?

All input appreciated.

WoolyG

---

### Post by tredegar on 2010-12-12
Your post does not make sense:
You unplugged your windows drives (why?)
You plugged in a new drive and installed ubuntu. 
OK. grub will have been installed on your new drive with ubuntu.

At [4] you say you plugged in your windows drives, and unplugged the ubuntu drive.

But it is booting grub, which _must_ be on your new drive, which you say is unplugged.

If you are not able to describe the situation correctly, we can't help.

---

