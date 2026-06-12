---
title: "Can't log in -- .ICEauthority ecryptfs libnss3.so problems -- can't access home."
date: 2011-09-21
forum: General Help
---

### Post by Earl_Maroon on 2011-09-21
I can't log in/unlock my home directory. Here's the story:

Last night I rebooted my laptop and found that I could not log in. Logging in to any DE (Unity, Unity 2D or GNOME Shell) brings up an error message abrout my ICEauthority file.
So I did a little looking around on the forums and found the suggestion that I just had to chown/chmod the file and that seemed easy enough, so I tried it.
Unfortunately, I could not do this because my home directory is locked (I logged into a TTY to try this).
So, as per the instructions in the README file I tried the command ecryptfs-mount-private and entered the passphrase, but it did not work and gave me a libnss3.so error.
So, I tried to reinstall libnss3 but I wasn't connected to the internet.
I then logged in to Unity successfully using the guest account. I was unable still to access the internet. I thought it might be restrictions of the guest account, so I opened a terminal, did su [my name] and tried to open nm and nm-applet, which gave me a libnss3.so error. I tried again as root and the results were the same.

SO... as far as I can tell the root error is with libnss3, but I'm struggling to work out how to fix this.

Please, give me any help you can.

EDIT:
I fixed this by downloading libnss3 and related debs from packages.ubuntu.com then transferring them to the affected computer by usb drive, then running "sudo dpkg -i libnss3*", after which I rebooted successfully.

---

### Post by PGScooter on 2011-09-22
Earl_Maroon,

Thanks for your post! I had a similar problem and did the same as you (downloaded on a usb and installed libnss3) and everything is fine now.

Did you file a bug report? If you do, please let me know so I can confirm. I'm too lazy right now to file one myself.

Thank you for posting back your solution. Too often people figure it out and then forget to post back their solution.

For me, this happened on Oneiric Beta 1 64-bit. Which version are you using?

---

