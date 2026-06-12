---
title: "Java, how do you install?!"
date: 2010-06-02
forum: General Help
---

### Post by alex_foreman on 2010-06-02
hi, 
i have been trying to do this for a week know and cant manage it, i have searched around but cant find anything that seems to help me.
i have ubuntu 10.04(the newest one) and all the updates,
i tried following the directions on java website, downloading the file giving it permission to run, running it then linking it into the plug-ins file on firefox but it still wont work! any help would be much obliged!!!

thanks, alex

---

### Post by philinux on 2010-06-02
Install the ubuntu-restricted-extras package.

You might want to read the General Help sticky re Java.

---

### Post by perham on 2010-06-02
> **alex_foreman said:**
> hi, 
i have been trying to do this for a week know and cant manage it, i have searched around but cant find anything that seems to help me.
i have ubuntu 10.04(the newest one) and all the updates,
i tried following the directions on java website, downloading the file giving it permission to run, running it then linking it into the plug-ins file on firefox but it still wont work! any help would be much obliged!!!

thanks, alex

press Alt+F2, type xterm, press Enter.

in the opened dialog, type this: 
```
sudo apt-get -y install ubuntu-restricted-extras
```

type in your password, and it should install flash and some other useful stuff. ;)

---

### Post by alex_foreman on 2010-06-02
cheers, ile give it a go and hopefully it should work
xx

---

### Post by alex_foreman on 2010-06-02
brilliant! it worked! cheers for the quick reply guys
xx

---

