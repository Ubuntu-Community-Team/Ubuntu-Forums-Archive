---
title: "system won't boot"
date: 2010-08-05
forum: General Help
---

### Post by hollowhead on 2010-08-05
On lucid 10.04 my daughters laptop won't boot I get a "an error occurred while mounting / press S to skip mounting or M for manual recovery". Pressing S gives another error about not being able to find /tmp.  M puts you at the command prompt. I put the lucid 10.04 upgrade disk in and went to rescue mode but it started an install which I would hope to get away w/o.  Can anyone tell me what to do to recover the system?  Ta.

---

### Post by stlsaint on 2010-08-05
Boot the system again and enter M for manual as you did before. Then at the prompt...enter your login credntials(username/password) then you after you login enter command 
```
startx
```

If that does not get you to your desktop than boot the system to your livecd and come back to the forums here and run the bootinfoscript in my signature. You will get a txt document titled: RESULTS.txt after you run the script. Attach that script to your next post so we can see whats going on under the hood! ;)

---

### Post by hollowhead on 2010-08-06
Thanks for your reply.  No can do.  startx doesn't work I get a number of errors about a readonly filesystem and not being able to run upgrade notifier.  I cannot run your script since the I have an upgrade distro which doesn't have a livecd menu item.....

---

### Post by hollowhead on 2010-08-07
Anyone I'm still not made any progress after running the recovery mode on the upgrade cd or from the grub2 menu.  I keep getting readonly errors but I don't know whether these are normal.   Is it possible to run fsck from the upgrade CD?  Any other ideas anyone short of cleam install?  Ta.

---

### Post by wilee-nilee on 2010-08-07
You should be able to boot a live Ubuntu cd with a key prompt it says what it is on the screen at start to choose boot menu. Boot the cd run the boot script in my signature as post 2 suggests. With what information you have so far not much can be done. My computer gives me a choice of boot devices with a f12 prompt after turning it on.

The good thing is that if you can get the live cd to boot you can also access the installed system and pull out what is needed if you need to reinstall, so this booting from a live Ubuntu cd is quite important.

---

### Post by hollowhead on 2010-08-08
Thanks for your help but I have the upgrade CD and this seems to be missing the functionality of the full install CD although I can boot from it.  I cannot access the command prompt from the CD.  I have tried repair options from the live cd and from the grub list by pressing shift as I boot.  I can access the system to remove files using a USB stick its really X that isn't working...  I think I will have to do a reinstall....  F12 takes me to the same screen as described above.:(

---

