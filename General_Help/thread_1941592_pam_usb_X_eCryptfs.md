---
title: "pam_usb X eCryptfs"
date: 2012-03-15
forum: General Help
---

### Post by nbr on 2012-03-15
Has anybody been successful using pam_usb (login authentication with a USB flash drive) with an encrypted home directory?

I configured pam_usb and I was able to authenticate with a flash drive.
However, when I restarted the computer, GDM no longer would log me in. Testing with an unencrypted home worked, revealing that the problem is the encrypted home.

There is a directory ~/.pamusb/ where pam_usb stores the one-time pad and it seems it searches for this file upon login. Since my home in encrypted, it can't find it.

I moved my ~/.pamusb/ to an unencrypted area and made a symbolic link to my unencrypted home directory. Now pam_usb can open my unencrypted home, but still won't log me in to my (des)encrypted home.

Because pam_usb is blind to the user password, it makes sense that it can't open an encrypted home. This is the same reason why gnome-keyring asks for a password. In this case, pam_usb sucks...

I don't know if I am doing something wrong, or if this is a problem with pam_usb. None of the how to's I found talk about encrypted homes.

So if anybody is using pam_usb with encrypted home, please, let me know how you did it.

Thank you.

p.s. I searched the forum and there was one post that mentioned ecryptfs + pam_usb, but the OP said he was going to start a new thread on the topic, which I couldn't find.

---

