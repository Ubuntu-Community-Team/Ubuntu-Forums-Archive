---
title: "Upgraded to 10.4, and now goes to busybox while booting"
date: 2010-05-01
forum: General Help
---

### Post by bomber991 on 2010-05-01
Well, I did the update from within 9.10 to 10.4.  Now when Ubuntu boots up, something happens and it goes to busybox.  I tried sitting there and waiting, but nothing happened.  So I tried typing exit, and then about a minute or two later it finally finished booting.

It's real nice that everyone else is reporting 20-30 second boot times, but before with 9.10 my boot time was around 60 seconds or so, and now it's around 5 minutes.

So how can I fix this?  Is there a way to post the boot log here?  Where would it be located at on my computer?

---

### Post by bomber991 on 2010-05-01
Well, I fixed my problem.  It kept giving me some uuid error before it went to busybox.  So what I did was:

First edited etc/default/grub
```
sudo nano etc/default/grub
```

Then I uncommented this line (The # makes the line a comment, so I removed the # infront of GRUB_DISABLE_LINUX_UUID=true
```
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
GRUB_DISABLE_LINUX_UUID=true

```

I saved the changes, then I did:
```
sudo update-grub
```

I restarted, and this time during booting it didn't stop and drop into busybox.  It just booted up like normal, and I guess it is a little quicker than 9.10 was.

---

