---
title: "Chrome: Timer expired"
date: 2011-02-07
forum: General Help
---

### Post by lucatersi on 2011-02-07
Hi!

I've been using google chrome for a while on kubuntu maverick, but I recently found out that it cannot start anymore. In Terminal I get:

```

lt@lt-Satellite-kub:~$ google-chrome
/usr/bin/google-chrome: line 41: /opt/google/chrome/chrome: Timer expired
/usr/bin/google-chrome: line 41: /opt/google/chrome/chrome: Success

```But nothing happens afterwards..
I've tried to purge and re-install the application, but no luck.
Do you know what's going on?

Thanks

Luca

---

### Post by ubunyou on 2011-02-09
see next post for potential solution. How do you delete posts I wonder?

---

### Post by ubunyou on 2011-02-09
I found my problem (doubt we are having the exact same problem though). I am running a Sophos antivirus for linux (dont flame me I have no choice its policy im in a lab at work) and the antivirus on-access scanner was causing a timeout. That chrome binary is soooo big it was taking too long to scan. To reproduce the problem I did an md5sum on the binary and got the same timeout message!?

```

root@kyle-laptop:~# md5sum /opt/google/chrome/chrome
md5sum: /opt/google/chrome/chrome: Timer expired

```

Checked dmesg and saw the on access component was throwing errors scanning the binary:

```

root@kyle-laptop:~# dmesg
... Timeout occured while opening /opt/google/chrome/chrome on behalf of process md5sum[3041/3041] owned by 0(0)/0(0) <0>

```

After disabling the AV product on access scan mode chrome started without issue. I re-enabled the on access scanning and used the Sophos GUI to exlude /opt/google/chrome directory and I haven't had any issues with chrome after that.

---

