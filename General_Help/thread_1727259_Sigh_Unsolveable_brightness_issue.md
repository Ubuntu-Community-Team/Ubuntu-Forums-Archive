---
title: "*Sigh* Unsolveable brightness issue"
date: 2011-04-12
forum: General Help
---

### Post by danielgrosvenor on 2011-04-12
As much as it pains me to say this, if I'm not able to resolve this brightness problem soon I will be forced to put Windows back on this machine.  Dear Ubuntu peers: *please* save me from this fate!

_My Problem_:
Like many laptop owners, my screen brightness controls aren't working and my screen is stuck at 20% brightness.

_My System_:
Dell Inspiron 1307 with latest BIOS
512mb Nvidia GeForce G 105M

_OS_:
Ubuntu 10.10 x64 (but have also had this problem when trying out Linux Mint and Kubuntu as well)

_Failed Solutions_:
Go into Google and search for "ubuntu laptop brightness problem" and I've tried *everything* there I can find.  Both the recommended and the latest official Nvidia drivers make no difference. Neither does tweaking power settings, changing the buttons to 'media mode' via BIOS, [adding stuff into etc/acpi/]("http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html"), the whole "echo -n 100 >/proc/acpi/video/PEGP/LCD/brightness" thing... basically **nothing** works.

_The only thing that has done something_:
[B]Sudo apt-get install xcalib

xcalib -co 60 -a[/B]

-- This makes the screen DARKER each time I type it.  

Trying **xcalib -co 100 -a** does nothing to increase the brightness, however. :(



Basically, I'm at a loss.  I've exhausted all my options, and am really hoping that somebody on here can provide me with some more options to explore because I really don't want to go back to having a Windows machine.  Especially as I've stuck a lovely Ubuntu sticker on my laptop now.

---

### Post by realzippy on 2011-04-12
```
xcalib -c
```

should bring you to default settings.


what happens when running

```
xcalib -b 60 -a
```

?

---

### Post by Staaffy on 2011-05-28
I have the exact same issue with my Dell Inspiron 1370. Very enoying. Do please post the solution if you work something out :)

There is a bug report filed a while back here [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/489397](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/489397)

---

