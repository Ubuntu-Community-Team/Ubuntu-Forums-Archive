---
title: "Did I encrypt twice?"
date: 2011-06-08
forum: General Help
---

### Post by PGScooter on 2011-06-08
While using the alternate CD I used the option to encrypt LVM.

But then I think the installer also asked me if I wanted to encrypt home and I put yes.

Should I have only done the first?

Now when I start up my computer I have to enter one encryption key and then later I get to the login screen and I have to enter my password.

Thanks

---

### Post by Junkieman on 2011-06-08
Short answer: Do you have a Private directory in your home? If so then yes you encrypted twice. But not as you thought, so don't worry too much.

Long answer: An encrypted LVM asks for the password at boot to decrypt your home files which need to be available to the system to show you the login screen, you then enter your login password.

There is also an option in the installer to setup a "Private" directory within your home, this actually links to ~/.Private and everything you put in there is automatically encrypted, no password required as it works off your login credentials.

Generally people who do not use LVM encryption may opt for this Private directory instead, for secret things like your email client or instant messaging client configs.

*View all files (hidden ones too)*
```
ls -al ~/Private
```

So if you have a ~/Private with no files inside, you can [safely remove it]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#How to Remove an Encrypted Private Directory Setup") (You might want to skip the last #5 step though! I recommend skipping it in case something else depends on it.)

You will still be asked for the boot time password though, but now you will only have one encryption. You can opt to configure auto-login in this case if you keen, seeing as your home is already an encrypted LVM.

---

### Post by PGScooter on 2011-06-08
Thanks for the help Junkieman.

I actually have to do a fresh install for other reasons.

Are there any advantages over an LVM encryption to a home encryption?
If I do not create a separate partition for home, does that mean that LVM encryption encrypts both root and home? Does it also encrypt swap? I'm trying to decide whether I want those encrypted or not

---

### Post by Junkieman on 2011-06-11
LVM has many differences, like disk pooling and full disk encryption. I don't think you can encrypt if your home and / share the same partition, they need to be separate.

---

### Post by PGScooter on 2011-06-11
> **Junkieman said:**
> LVM has many differences, like disk pooling and full disk encryption. I don't think you can encrypt if your home and / share the same partition, they need to be separate.

ok, thanks

---

