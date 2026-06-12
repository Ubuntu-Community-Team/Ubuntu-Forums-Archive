---
title: "DVD writing is broken in Ubuntu 10.10"
date: 2010-10-17
forum: General Help
---

### Post by lucasart on 2010-10-17
I've just installed Ubuntu 10.10 amd64, and can't get DVD creator to work. I just slide in a blank DVD-R, and copy/paste the files onto it, and click "write on disc", the usual way... It does it, and then goes on with a checksum calculation which is almost longer than the copy itself. And then it says the copy failed, and sure enough, all files are corrupted. Is there any fix for that ?

PS: I don't know how it happens, but with every new relase of Ubuntu they break something with UDF DVDs.
10.04 couldn't read UDF DVDs until the RC stage, a few days before the actual release (they'd broken the /etc/fstab)
10.10 couldn't read UDF in the early beta stages. And now even after release it still can't burn data DVDs.

---

### Post by BKochick on 2011-01-18
i'm having this same prob is there any help or link i can get to help me fix it? this is happening on 2 different computers with 2 different DvD writers and failed with different burning programs on Ubuntu 10.10

Thanks

---

### Post by mastablasta on 2011-01-18
what if you use K3B?

---

### Post by bikodog on 2011-01-18
try using growisofs in the command line.

to burn iso of dvd:

```
growisofs -dvd-compat -Z /dev/dvd=somefile.iso
```

do ```
man growisofs
``` for other options

---

### Post by JC Cheloven on 2011-01-18
A quick googling will make clear to you that it's a known problem with Brasero in particular. It has some more problems than burning dvd's in my experience. Many people's advice, for example[ here]("http://codingexplorer.wordpress.com/2010/02/18/failure-burning-dvd-on-brasero-in-ubuntu/"), is to simply use a different burner.

K3b is a usual recommendation. 
If you want to remain closer to the Gnome desktop (to install fewer dependencies) I can suggest GnomeBaker. It works well for me.

---

