---
title: "a boring terminal problem"
date: 2010-06-01
forum: General Help
---

### Post by larmbr on 2010-06-01
everytime i launch the terminal ,on top of if always yields the stament below:

```
bash: warning: setlocale: LC_CTYPE: cannot change locale (zh_CN): No such file or directory

```

and i search the google to find a method like this but failured to solve it =_=||
```
sudo loclae-gen
sudo dpkp-reconfigure locales
```

by the way, it also bother me whenever i use [tab] to complete commands.

and when i use apt-get to download something .it will give out the warning :```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
   LANGUAGE = "en_US:zh_CN:zh:en",
   LC_ALL = (unset),
   LC_CTYPE = "zh_CN",
   LANG = "zh_CN.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```

i don't know what this means.could anyone help me ?THX.

---

### Post by marty1011 on 2010-06-01
type ```
locale
``` and see what you it is your preferred locale.

if not yout preferred locale then do this:

edit /var/lib/locales/supported.d/local to add your preferred locale.

then 

```
sudo dpkg-reconfigure locales
```

change the default locale as well, edit /etc/default/locale 

then reboot

run again ```
locale
``` to see if you have your preferred locale.

---

### Post by gmargo on 2010-06-01
I was able to get locales working with LANG="zh_CN" and LANG="zh_CN.UTF-8".

All I had to do was:
```

$ sudo locale-gen zh_CN
$ sudo locale-gen zh_CN.UTF-8

```There is no need to manually edit the /var/lib/locales/supported.d/local file.  "locale-gen" adds an entry to that file automatically.

I did not actually change my locale for the test; I just messed with the environment variables.  The "locale" command will give a warning like you are seeing with your perl script.

---

### Post by Brandon Williams on 2010-06-01
What is the output of 'locale -a'? Does it include zh_CN? The errors you are seeing generally result from specifying a locale setting that is not installed on the system.

---

### Post by larmbr on 2010-06-02
> **gmargo said:**
> I was able to get locales working with LANG="zh_CN" and LANG="zh_CN.UTF-8".

All I had to do was:
```

$ sudo locale-gen zh_CN
$ sudo locale-gen zh_CN.UTF-8

```There is no need to manually edit the /var/lib/locales/supported.d/local file.  "locale-gen" adds an entry to that file automatically.

I did not actually change my locale for the test; I just messed with the environment variables.  The "locale" command will give a warning like you are seeing with your perl script. 




Many thanks! I did as you did,and solved it ! 

I first typed  : locale ,and the below content came out :```
LANG=zh_CN.utf8
LANGUAGE=en_US:zh_CN:zh:en
LC_CTYPE=zh_CN
LC_NUMERIC="zh_CN.utf8"
LC_TIME="zh_CN.utf8"
LC_COLLATE="zh_CN.utf8"
LC_MONETARY="zh_CN.utf8"
LC_MESSAGES="zh_CN.utf8"
LC_PAPER="zh_CN.utf8"
LC_NAME="zh_CN.utf8"
LC_ADDRESS="zh_CN.utf8"
LC_TELEPHONE="zh_CN.utf8"
LC_MEASUREMENT="zh_CN.utf8"
LC_IDENTIFICATION="zh_CN.utf8"
LC_ALL=

```

Actually the locale i want herein.so i typed: ```
sudo dpkg-reconfigure locales
```
but the warning yielded:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US:zh_CN:zh:en",
	LC_ALL = (unset),
	LC_CTYPE = "zh_CN",
	LANG = "zh_CN.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```

I didn't exactly know what this means ,so i tried your method ,and i successed!


Now could anyone tell me why ? And for our non-english country,the locale is a big problem during using ubuntu .
Could anyone tell me where the locale-relevent configuration files reside,and so with the relevent command? If i could be given some documatations or manuals about it,i would pretty appreciated!!!
Thanks again!

---

