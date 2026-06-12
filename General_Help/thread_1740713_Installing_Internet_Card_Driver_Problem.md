---
title: "Installing Internet Card Driver Problem"
date: 2011-04-27
forum: General Help
---

### Post by Jaket25 on 2011-04-27
Hey there.

Recently I've been having problems with the internet whilst using Ubuntu 10.10 (Dual booting with Windows Vista Home Premium x32).

The problem is I simply can't use my internet (can't connect and the option doesn't show up).
At first it said (using wireless internet by the way), firmware missing. After playing around for a bit, I managed to get a option to install my internet card driver (Broadcom).

As I try to install it says this:

```
SystemError: Failed to lock /var/cache/apt/archives/lock
```

This is really frustrating me as I need the internet on it.

If anyone could help me through this I'd be incredibly grateful.

---

### Post by Joe of loath on 2011-04-27
Are you running the command as root (sudo)?

---

### Post by 3rdalbum on 2011-04-27
How exactly are you trying to install it? If you're using the Additional Drivers program, note that you need to have no other package management programs open - so no Software Center, no Synaptic, no Update Manager and no Apt-get. Close these programs before trying to do Additional Drivers.

---

### Post by Jaket25 on 2011-04-27
Thanks for the reply.

Yeah, I'm using the additional drivers program to install it.
I tried to install it and it needed me to install 2 patches so I did.
Now it wants me to install another one but this appears.

```
CD/DVD 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)' is required

Please insert the above CD/DVD into the drive '/cdrom/' to install software packages from it.
```

I'm running it off of a USB and have no idea what to do now.

Thanks.

---

### Post by Joe of loath on 2011-04-27
Open the 'software sources' program in settings -> administration, and deselect the CD as a source.

---

### Post by Jaket25 on 2011-04-27
That didn't help.

All that happened is the driver not appearing now for install.

What do I do? :confused:

---

### Post by Joe of loath on 2011-04-27
You will need to be connected to the internet via a cable to do it.

---

### Post by Jaket25 on 2011-04-27
> **Joe of loath said:**
> You will need to be connected to the internet via a cable to do it.

That's not possible as I only have wireless.
Is it possible to download the driver and use it something? :confused:

---

### Post by Joe of loath on 2011-04-27
It is, but I'm not completely sure on how to do it, as the broadcom drivers were such a pain to install I just went on ebay and bought an Intel wifi card for £8.

---

### Post by Jaket25 on 2011-04-27
After more playing round, installing, and downloading patches I managed to get it working!

SOLVED!

---

