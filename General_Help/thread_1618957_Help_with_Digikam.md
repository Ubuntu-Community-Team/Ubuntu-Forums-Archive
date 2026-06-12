---
title: "Help with Digikam"
date: 2010-11-11
forum: General Help
---

### Post by jaqian on 2010-11-11
I'm using Digikam 1.3 on LinuxMint9. On Monday (i think after an system update), Digikam crashed, it started up the splash screen and says "scanning albums" then disappears, nothing else. I've reported the crash but doesn't help me sort the problem now.

I've uninstalled Digikam and re-installed and problem still exists, which makes me think it could be a dependency left behind when uninstalled that is causing the problem.

Can someone tell me how I can completely remove digikam and all its dependencies and start fresh? Any CLI magic?

Thanks.

---

### Post by Hippytaff on 2010-11-11
You can try
```

sudo apt-get purge {programme Name}

```
then
```

sudo apt-get autoclean

```
then reinstall it
```

sudo apt-get install {Progamme Name}

```
where programme name is the name of the programme

---

### Post by jaqian on 2010-11-11
I tried the purge before re-install but didn't try autoclean, will give it a try. Thanks.

---

### Post by ajgreeny on 2010-11-11
You might get some answers and helpful error messages from starting it in terminal, if a reinstall is no help.

---

### Post by jaqian on 2010-11-11
> **ajgreeny said:**
> You might get some answers and helpful error messages from starting it in terminal, if a reinstall is no help.

Will give it a try. Thanks.

---

