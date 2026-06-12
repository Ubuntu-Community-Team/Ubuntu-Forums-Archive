---
title: "Problem: Installing JRE Please Help"
date: 2006-05-06
forum: General Help
---

### Post by kruupy on 2006-05-06
Hi all,

last night I managed to install the JDK onto my laptop my by the following:

```

fakeroot make-jpkg jdk.bin
etc..

```

but today, I tried to install the jdk onto my desktop using the same commands but i got this error whilst trying to run make-jpkg:

```

akruup@kruup:~$ fakeroot make-jpkg jdk.bin
Creating temporary directory: /tmp/make-jpkg.XXXXEMUwCZ
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

```

Does anyone know how to fix this?
Thanks!

---

### Post by ffferko on 2006-05-06
Try

sudo fakeroot make-jpkg jdk.bin

---

### Post by skaboss on 2006-05-06
You can also add SeveasPackages to your /etc/apt/sources.list :

[https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages)

This way, you will be able to install java using apt-get  :-\"

---

