---
title: "Make some files &quot;run-only&quot;"
date: 2011-05-29
forum: General Help
---

### Post by foerno on 2011-05-29
Is it possible to disable the run/display/cancel dialog *just* for some selected files and keep it for others? I want to be able to just click on some files which would run them instantly yet still being asked what to do if I click on other files.

Say, launching files a, b & c would make them execute but launching files d, e, f and all others would pop-up the dialog asking me what to do.

So can it be done? :)

---

### Post by BlouBlou on 2011-05-29
I didn't try this, but it may work.

```
chmod -rw <file>
```

and after this,

```
chmod +x <file>
```


The command *chmod -rw* will prevent being read or written. And *chmod +x* will allow being executed.

---

### Post by foerno on 2011-05-29
Nope. This just gives an error:
```
The file is of an unknown type
```

I am able to launch this file via command-line with sudo, so I technically *could* add it to my sudoers file and start it using the console every time, but that's not really what I'm looking for.

---

### Post by foerno on 2011-05-31
bump

---

### Post by foerno on 2011-06-15
Anyone? Please.

---

### Post by foerno on 2011-08-28
bump

---

### Post by dino99 on 2011-08-28
sudo chmod -rw /path/to/myfilename

sudo chmod +x /path/to/myfilename

---

