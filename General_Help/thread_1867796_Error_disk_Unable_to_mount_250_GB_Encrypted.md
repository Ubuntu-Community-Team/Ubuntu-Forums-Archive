---
title: "Error disk: Unable to mount 250 GB Encrypted"
date: 2011-10-23
forum: General Help
---

### Post by laresistance2 on 2011-10-23
Hello, 
I have the following error message that appears at the opening of my encrypted disk ```
Error unlocking device: cryptsetup exited with exit code 251: device-mapper: reload ioctl failed: Invalid argument
Failed to setup dm-crypt key mapping for device /dev/sdb1.
Check that kernel supports aes-xts-plain64 cipher (check syslog for more info).
Failed to read from key storage.
```

P.S. The disk was encrypted with fedora 15 but I formatted my pc and now I am with Ubuntu 10.10.

Thank you.

---

### Post by Paddy Landau on 2011-10-23
Is this a completely fresh installation? Or are you trying to reuse your Fedora's encrypted /home directory with a new installation of Ubuntu?

Please explain how specifically you formatted your drive and installed Ubuntu.

Please also explain when the error messages appears: when you boot or when you log in?

---

### Post by laresistance2 on 2012-04-03
I first encrypt the drive with Fedora then I format my pc to install Ubuntu with a live CD and I no longer know the password.
This message appears when I try to access my hard drive.

---

### Post by Paddy Landau on 2012-04-04
> **laresistance2 said:**
> I first encrypt the drive with Fedora then I format my pc to install Ubuntu with a live CD and I no longer know the password.
This message appears when I try to access my hard drive.
That was a long time before responding. Do you still have this problem?

Unfortunately, I still do not fully understand what you have said. You said that you encrypted the drive with Fedora but then formatted your PC with Ubuntu. How did you back up and restore your data?

If you have lost your passphrase for the encrypted data, unfortunately your data is lost.

---

