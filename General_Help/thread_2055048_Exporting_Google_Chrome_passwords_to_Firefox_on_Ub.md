---
title: "Exporting Google Chrome passwords to Firefox on Ubuntu"
date: 2012-09-08
forum: General Help
---

### Post by lukjad on 2012-09-08
I recently upgraded to Ubuntu 12.04 and am trying to switch to using XeePassX instead of relying on Chrome and Firefox to each try and save my passwords to a format that it can use. Unfortunately, Chrome started encrypting the passwords and refuses to export them. I do not want to sign into google and have over all my passwords.

All the guides I find seem to point toward the concept of using a program called ChromePass, but using that in wine gives me this
```

lukjad007@StationY:~/Desktop/ChromePass$ wine ChromePass.exe /skeepass /home/lukjad007/Desktop/ChromePass/
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:iphlpapi:NotifyAddrChange (Handle 0xebe8cc, overlapped 0xebe8b0): stub
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
wine: configuration in '/home/lukjad007/.wine' has been updated.
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
lukjad007@StationY:~/Desktop/ChromePass$ sudo wine ChromePass.exe /skeepass /home/lukjad007/Desktop/ChromePass/
[sudo] password for lukjad007: 
wine: /home/lukjad007/.wine is not owned by you
lukjad007@StationY:~/Desktop/ChromePass$ gksudo wine ChromePass.exe /skeepass /home/lukjad007/Desktop/ChromePass/
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:iphlpapi:NotifyAddrChange (Handle 0xe9e8cc, overlapped 0xe9e8b0): stub
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
wine: configuration in '/root/.wine' has been updated.
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory

lukjad007@StationY:~/Desktop/ChromePass$ 
```

Wine also gives me "Error 5" in a popup box.

So, do any of you know how to export Chrome saved passwords?

---

### Post by lukjad on 2012-09-09
Bump

---

### Post by tartalo on 2012-09-09
Would this help? [https://en.wikipedia.org/wiki/LastPass_Password_Manager](https://en.wikipedia.org/wiki/LastPass_Password_Manager)

---

### Post by vasa1 on 2012-09-09
> **tartalo said:**
> Would this help? [https://en.wikipedia.org/wiki/LastPass_Password_Manager](https://en.wikipedia.org/wiki/LastPass_Password_Manager)

And for what reason, does OP want to use wine? Is that because of ChromePass? If I don't trust my passwords with Google, I just wouldn't use Chrome/Chromium at least for sites that need passwords. Then it's just a one-off case of copying the Chrome passwords or even taking screenshots of the settings page and manually entering them into a trustworthy browser.

---

### Post by lukjad on 2012-09-11
> **tartalo said:**
> Would this help? [https://en.wikipedia.org/wiki/LastPass_Password_Manager](https://en.wikipedia.org/wiki/LastPass_Password_Manager)

I have seen it, but I'm unsure how this would work. Would I export the passwords LastPass then back into KeePass?

> **vasa1 said:**
> And for what reason, does OP want to use wine? Is that because of ChromePass? If I don't trust my passwords with Google, I just wouldn't use Chrome/Chromium at least for sites that need passwords. Then it's just a one-off case of copying the Chrome passwords or even taking screenshots of the settings page and manually entering them into a trustworthy browser.

I was using Wine to run ChromePass, and I am planning on deleting all my passwords from Chrome, it's just that I was looking for a simple way to import them as I have quite a few logins.

---

