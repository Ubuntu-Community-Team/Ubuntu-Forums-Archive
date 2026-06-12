---
title: "Root Privileges To Run Script!"
date: 2011-11-01
forum: General Help
---

### Post by Brooksy_FC on 2011-11-01
I'm trying to install ZendOptimizer, but when I run the script to install it, I keep getting the same message saying...
> 
ERROR: You need root privileges to run this script!

Any ideas on how get past this?

---

### Post by matt_symes on 2011-11-01
Hi

From a terminal type

```
sudo /path/to/script.sh
```

Enter your password. It will not be echoed to the screen. This will run the script with elevated privilages.

Kind regards

---

### Post by aeiah on 2011-11-01
put sudo (super user do) before your command, eg:
```

sudo ./nameofscript.sh
```

---

### Post by Brooksy_FC on 2011-11-01
Thanks for your replies. Got it working now. Cheers :)

---

