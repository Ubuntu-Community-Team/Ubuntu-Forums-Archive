---
title: "Ubuntu 12.04 /etc/environment, settomg LD_LIBRARY_PATH fails."
date: 2012-06-22
forum: General Help
---

### Post by jiapei100 on 2012-06-22
Hi, all:

Environment:
OS: Ubuntu 12.04

I only put the following line
> LD_LIBRARY_PATH="/usr/lib:/usr/local/lib"
into /etc/environment, however, even after rebooting, when I did

```
$echo $LD_LIBRARY_PATH
```
Nothing appeared.


BTW, all the other settings, including setting those parameters including: PATH, JAVA_HOME, JRE_HOME, etc., all are correct.
The only expection is LD_LIBRARY_PATH. But, It used to be ok in Ubuntu 11.10.


Can anybody give me a hand?


Cheers
Pei

---

### Post by dino99 on 2012-06-22
here is a default config of /etc/environment:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

so i suspect you need to respect the : PATH=" blah blah" thing

---

### Post by kanikilu on 2012-06-22
Supposedly LD_LIBARY_PATH can't be set in /etc/environment since 9.04:

[https://help.ubuntu.com/community/EnvironmentVariables#List_of_common_environment_variables](https://help.ubuntu.com/community/EnvironmentVariables#List_of_common_environment_variables)

---

