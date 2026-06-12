---
title: "Update install failed 12.04 onto USB stik"
date: 2012-05-20
forum: General Help
---

### Post by Advait on 2012-05-20
Hi All,

See attached error log report. I've got up-to-date 12.04 on a 4gb USB stik with about 2gb persistent  file space. I tried to install updates and got the attached error  report. Any way to fix the error? Thanks!

I have this same error report each time I try to update. Does the error have something to do with updating Ubuntu on a USB stik?

Keep in mind I'm new to Ubuntu and know very little about the command line.

Thanks in advance for any help on this. Kind Regards,

Tom

---

### Post by sikander3786 on 2012-05-20
I am not sure if it is a USB-install specific problem. But I am concerned about this:

> cryptsetup: WARNING: could not determine root device from /etc/fstab
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Please post the output of this command to let us take a look at your fstab:

```
cat /etc/fstab
```

---

### Post by wilee-nilee on 2012-05-20
> **Advait said:**
> Hi All,

See attached error log report. I've got up-to-date 12.04 on a 4gb USB stik with about 2gb persistent  file space. I tried to install updates and got the attached error  report. Any way to fix the error? Thanks!

I have this same error report each time I try to update. Does the error have something to do with updating Ubuntu on a USB stik?

Keep in mind I'm new to Ubuntu and know very little about the command line.

Thanks in advance for any help on this. Kind Regards,

Tom

Basically you don't want to really update at all on a persistent usb, especially kernels. The persistent is not cleanable and will fill up eventually anyway.

A persistent is really good for having extra installs not included in the standard download, but updating is problematic really.

---

### Post by Advait on 2012-05-21
OK, see attached pic that shows the output of the command per your instructions.  See anything interesting? 

The other person said updating Ubuntu on a persistent USB stik creates problems. That is news to me. Can a persistent USB stik be configured somehow so that updates happen with no problem?

I have a small external USB 40gb hard drive. I presume I could install Ubuntu on that and it would update no problem? Is that true?

I don't want to install Ubuntu on my main hard drive cause it's getting close to full and I'm using all the space for other files. In the future I may totally get rid of Windows, but not able to make that step just yet.

I'm really loving the 12.04 Unity interface! It's great for a newbie like me. Beautiful and so easy to use! Great work.

Thanks!

Advait

> **sikander3786 said:**
> I am not sure if it is a USB-install specific problem. But I am concerned about this:

Please post the output of this command to let us take a look at your fstab:

```
cat /etc/fstab
```

---

### Post by sikander3786 on 2012-05-22
> **wilee-nilee said:**
> Basically you don't want to really update at all on a persistent usb, especially kernels. The persistent is not cleanable and will fill up eventually anyway.

A persistent is really good for having extra installs not included in the standard download, but updating is problematic really.
Actually, this is the right answer.

If you still want to keep updating your Ubuntu install, install Synaptic:

```
sudo apt-get install synaptic
```

Start it and search for 'linux-generic' and lock all the related packages by going to 'Package > Lock Version' after selecting them.

But I am not sure if you would be able to install Synaptic successfully unless you fix the dpkg issues. Please try and let us know if it works.

---

