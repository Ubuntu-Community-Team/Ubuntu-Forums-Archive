---
title: "No authentification for Gweather"
date: 2011-12-22
forum: General Help
---

### Post by audiomick on 2011-12-22
Hallo.
The system is Ubuntu 11.04. It wanted to do some updates yesterday, and then complained about a missing authentification for three packages. The ones that don't install are

app-install-data-partner
libgweather-common
libgweather1

The error message (comes in German on my box) translates as
"This action would require the installation of Software packages from a non-authenticated source."

Has anyone had something similar? Does anyone know what to do to fix it?

I tried just removing the packages, as I don't think I need them. They are for displaying weather info. Problem is, it wanted to take Evolution and a whole lot of other stuff which I definitely do need off with it.

---

### Post by Frogs Hair on 2011-12-22
I have had this error and it was resolved by running the following command  .```
sudo apt-get update
```

---

### Post by audiomick on 2011-12-22
Nope, didn't help. Thanks for trying, though. ;)

---

### Post by dcstar on 2011-12-23
> **audiomick said:**
> Hallo.
The system is Ubuntu 11.04. It wanted to do some updates yesterday, and then complained about a missing authentification for three packages.
..........
The error message (comes in German on my box) translates as
"This action would require the installation of Software packages from a non-authenticated source."
..........

Change to a different Repository or wait until the one you are using updates itself correctly.

---

### Post by audiomick on 2011-12-23
> **dcstar said:**
> ... wait until the one you are using updates itself correctly.
I guess I'll have to. I don't actually know which repo gweather is in, but I think it is Ubuntu "main". Any rate, I have no idea which repo I could change from or to in order to solve this. Or what to do if authentifications are corrupted. I don't believe, however, that the latter is the case, otherwise nothing would update, would it?

Any further suggestions would be welcome. ;)

---

### Post by audiomick on 2011-12-28
Bumping this to see if there are any other takers.

I noticed that my 10.04 install on my laptop installed these packages the other day without a complaint... :-k

---

### Post by audiomick on 2012-01-02
Got a solution here.
[http://ubuntuforums.org/showpost.php?p=11581699&postcount=2](http://ubuntuforums.org/showpost.php?p=11581699&postcount=2)

---

