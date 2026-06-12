---
title: "Run a script at startup"
date: 2010-01-16
forum: General Help
---

### Post by kako13 on 2010-01-16
Hi,

I'm using KeePass with mono under Ubuntu 9.10 and it work fine.

But now I want that it run automatically, so I wrote the script below and inserted it on 

/etc/init.d and gives it root permission.  But when I do login, nothings happen.

I'm missing something?

```


#!/bin/bash

# make KeePass run at startup

mono /home/kelvin/Keepass/KeePass.exe


```

---

### Post by AlexDBall on 2010-01-16
If you want the script to run at login, maybe i can help you...

Call the script from ~/.profile

Just add a line at the end of the .profile script calling your script.

---

### Post by kako13 on 2010-01-17
> **AlexDBall said:**
> If you want the script to run at login, maybe i can help you...

Call the script from ~/.profile

Just add a line at the end of the .profile script calling your script.

Well, did the call from .profile but then the program load and the computer freeze and stop going Gnome. So I have to close the aplication and then the loading continue.

I want the application to load minimize in the task-bar, any other suggestion?

---

### Post by Leppie on 2010-01-17
put it in the startup processes? i don't know how to do this in gnome, but in xfce there's the Session and Startup menu entry (i suppose it should be under System>Preferences or System>Administration). especially since this is a oneliner it should be easier like that.

---

### Post by amsterdamharu on 2010-01-17
Put the & at the end of the line to run asynch:

```

#!/bin/bash

# make KeePass run at startup

mono /home/kelvin/Keepass/KeePass.exe&
```

Or under System -> preferences -> session
You can run stuff after gui has loaded.

---

### Post by kako13 on 2010-01-18
Ok, what I did was add the & as amsterdamharu said and then use Startup Application in System as Leppie said.

It is loading and taking the screen when I do login taking but I want it minimized in tray. So what I should do to accomplish that?

---

### Post by Leppie on 2010-01-18
apparently it doesn't minimize: [http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fcode.google.com%2Fp%2Fhfm-net%2Fissues%2Fdetail%3Fid%3D133&ei=kX1US6L_C9_I_ga7m7iYCw&usg=AFQjCNFPK3JbuN6Zkc5sfKppO3B89aCRrw&sig2=TyzeQL4z6ZvUvVZuO0qJeA](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fcode.google.com%2Fp%2Fhfm-net%2Fissues%2Fdetail%3Fid%3D133&ei=kX1US6L_C9_I_ga7m7iYCw&usg=AFQjCNFPK3JbuN6Zkc5sfKppO3B89aCRrw&sig2=TyzeQL4z6ZvUvVZuO0qJeA)

---

### Post by kako13 on 2010-01-18
> **Leppie said:**
> apparently it doesn't minimize: [http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fcode.google.com%2Fp%2Fhfm-net%2Fissues%2Fdetail%3Fid%3D133&ei=kX1US6L_C9_I_ga7m7iYCw&usg=AFQjCNFPK3JbuN6Zkc5sfKppO3B89aCRrw&sig2=TyzeQL4z6ZvUvVZuO0qJeA](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fcode.google.com%2Fp%2Fhfm-net%2Fissues%2Fdetail%3Fid%3D133&ei=kX1US6L_C9_I_ga7m7iYCw&usg=AFQjCNFPK3JbuN6Zkc5sfKppO3B89aCRrw&sig2=TyzeQL4z6ZvUvVZuO0qJeA)


But I can minimize it to tray manually...

---

### Post by Leppie on 2010-01-18
> **kako13 said:**
> But I can minimize it to tray manually...
i'm sorry, i don't use mono myself. have you checked the man page: [http://mono.wikia.com/wiki/Man_mono](http://mono.wikia.com/wiki/Man_mono)

---

### Post by kako13 on 2010-01-18
Ok I will check.

Thanks all for your help!

---

### Post by Leppie on 2010-01-18
> **kako13 said:**
> Ok I will check.

Thanks all for your help!
you're welcome.
if you find the solution, post it here so others can benefit from it ;)

---

