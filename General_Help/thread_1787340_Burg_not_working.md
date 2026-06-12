---
title: "Burg not working"
date: 2011-06-21
forum: General Help
---

### Post by sanjithts on 2011-06-21
i have installed Burg using Burg maneger but when i reboot the burg does not appear Grub appears. i tried many times, also the Burg-emu in the Burg Manager does not work.

---

### Post by nzjethro on 2011-06-21
If the burg-emu command does not work, then it is likely that you have not installed burg properly. Are you install burg using the command

```
sudo burg-install "(hdX)"
```

where X is your HDD number (i.e. if you only have one HDD, use hd0).

Then running

```
sudo update-burg
```

If yes, does it come up with a message saying something along the lines of

```
Installation completed without error
```

---

