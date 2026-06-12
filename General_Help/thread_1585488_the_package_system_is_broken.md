---
title: "the package system is broken"
date: 2010-09-30
forum: General Help
---

### Post by walwal on 2010-09-30
when i try to remove a package using software center i get this message : the package system is broken. what should i do to fix it?

---

### Post by searchfgold6789 on 2010-09-30
try typing in the terminal: ```
sudo apt-get update
```

---

### Post by walwal on 2010-09-30
i did but it didnt help

---

### Post by sikander3786 on 2010-09-30
> **walwal said:**
> i did but it didnt help
Does it give back any error message? Please post the message if any.

Secondly try to remove the package via apt-get.

```

sudo apt-get remove name-of-software

```

It might be cause by unmet dependencies, broken packages etc. But will be sure only after you post the output.

---

### Post by walwal on 2010-10-01
this is error message i get :

"The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"
when i click details i get this :
"libk3b6"

---

### Post by plucky on 2010-10-01
> **walwal said:**
> this is error message i get :

"The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"
when i click details i get this :
"libk3b6"

Try running from a terminal ```
sudo apt-get install -f
``` as the error mentions.

Good luck

---

### Post by Quackers on 2010-10-01
Have you tried going to Synaptic Package Manager and looking at the bottomn left of the screen. It will say something like 32100 packages listed, 1520 installed then it gives a number for broken packages. If there is a number given go to the menu bar and click on edit then "fix broken packages" and watch the bottom left corner again. It will tell you if it fixed anything.

---

### Post by walwal on 2010-10-01
apt-get install -f solved the problem.thanks guys

---

### Post by Swooper on 2010-10-01
> sudo apt-get remove name-of-software

I used this to help me deal with "splashy-themes". Seems the themes installed but the program would error on install. Therefore, manually deleting it like this helped it and im grateful.
 cheers

---

### Post by rworloma on 2010-11-02
This this post at [Liberian Geek]("http://www.liberiangeek.net/2010/11/fix-package-system-broken-error-ubuntu-10-0410-10-maverick-meerkat/") to fix it.

---

### Post by rworloma on 2010-11-02
Read this post at [Liberian Gee]("http://www.liberiangeek.net/2010/11/fix-package-system-broken-error-ubuntu-10-0410-10-maverick-meerkat/")k to fix it.

---

