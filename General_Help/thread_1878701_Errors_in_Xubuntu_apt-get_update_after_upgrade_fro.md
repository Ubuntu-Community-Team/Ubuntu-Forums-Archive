---
title: "Errors in Xubuntu apt-get update after upgrade from 11.04"
date: 2011-11-10
forum: General Help
---

### Post by Rytron on 2011-11-10
Hi.

Last week I upgraded over the internet from Xubuntu 11.04 => 11.10
Here is my Software Sources Authentication tab [1st image].
I get these errors when I run sudo apt-get update [2nd image].

---

### Post by Toz on 2011-11-10
Try re-adding the GPG key via:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```
...then
```
sudo apt-get update
```

---

### Post by Rytron on 2011-11-10
> **Toz said:**
> Try re-adding the GPG key via:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```
...then
```
sudo apt-get update
```

Thanks. I will try that and get back to you.

---

### Post by Rytron on 2011-11-17
Sorry for late reply Toz.

I ran update today (BTW, does it make a difference if I do sudo apt-get update or sudo aptitude update when it comes to the errors?)

The original error seemed to go by itself [image 1].

I ran your code [image 2].

The current output still has an error [image 3].

---

### Post by Toz on 2011-11-17
The key in this error message is different, so:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```
...and
```
sudo apt-get update
```

---

### Post by raja.genupula on 2011-11-17
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

try that .all the best

---

### Post by Rytron on 2011-11-17
> **Toz said:**
> The key in this error message is different, so:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```
...and
```
sudo apt-get update
```

Oddly this did not solve that error.

---

### Post by Rytron on 2011-11-17
> **raja.genupula said:**
> [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

Method 2 did not work.

Method 1 got the job done.

Thank guys.

:)

---

