---
title: "USB Drive Ubuntu - how to force login, lock screen for security"
date: 2011-08-09
forum: General Help
---

### Post by mesocyclone on 2011-08-09
I have a pen drive Ubuntu (11.04) that I use in an office environment, and I do not use the hard drive at all;

How can this be set up to demand a password on boot?

Also, when I am using it, how can I tell it to lock the desktop until it gets the password again?

I am not a very experienced Ubuntu user, so I don't know the various packages.

Thanks in advance.

---

### Post by spiky001 on 2011-08-09
Hi i dont use ubuntu from usb, When you installed were you asked for user name and password?just underneath 2nd radio button Require Password to log in. Did you set it

---

### Post by mesocyclone on 2011-08-09
> **spiky001 said:**
> Hi i dont use ubuntu from usb, When you installed were you asked for user name and password?just underneath 2nd radio button Require Password to log in. Did you set it
No, I wasn't asked.

I did try "sudo ubunto passwd" and set a password.

It didn't seem to change everything.

There's something odd about the usb version. It doesn't ask at boot, and there is no way to lock the screen (it's dimmed out in the menu).

---

### Post by dcstar on 2011-08-10
> **mesocyclone said:**
> I have a pen drive Ubuntu (11.04) that I use in an office environment, and I do not use the hard drive at all;

How can this be set up to demand a password on boot?

Also, when I am using it, how can I tell it to lock the desktop until it gets the password again?

I am not a very experienced Ubuntu user, so I don't know the various packages.

Thanks in advance.

You have to set up the "Persistence" feature in your USB device when you create it and then System-Administration-Login Screen to change the default behaviour.

---

### Post by mesocyclone on 2011-08-12
> **dcstar said:**
> You have to set up the "Persistence" feature in your USB device when you create it and then System-Administration-Login Screen to change the default behaviour.
Thanks, but still no go.

I believe I have persistence set, because I built the USB to allow read-writes. For example, it stores Firefox bookmarks on it. If I reboot, it remembers what I have done, and the only place it can do that is on the USB pen drive, since I don't access the disk.

However, the Login Screen page is grayed out when I do System->Administration->Login Screen.

---

### Post by mesocyclone on 2011-08-12
> **dcstar said:**
> You have to set up the "Persistence" feature in your USB device when you create it and then System-Administration-Login Screen to change the default behaviour.
Thanks, but still no go.

I believe I have persistence set, because I built the USB to allow read-writes. For example, it stores Firefox bookmarks on it. If I reboot, it remembers what I have done, and the only place it can do that is on the USB pen drive, since I don't access the disk. The file browser shows a 1.9GB casper-rw file system.

However, the Login Screen page is grayed out when I do System->Administration->Login Screen.

---

