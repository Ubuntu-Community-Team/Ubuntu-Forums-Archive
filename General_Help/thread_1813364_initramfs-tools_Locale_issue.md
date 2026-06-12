---
title: "initramfs-tools Locale issue"
date: 2011-07-27
forum: General Help
---

### Post by FizzerJE on 2011-07-27
Hello

When I run
```
update-initramfs -u
```

I get the following Warning:

**No support for locale: en_GB.utf8**

Been trying to sort out my locale as it was set to US.

I have the following set:

/var/lib/locales/supported.d/en

```
en_GB.UTF-8 UTF-8
```

vim /var/lib/locales/supported.d/local

```
en_GB.UTF-8 UTF-8
```

vim /etc/default/locale

```
LANG=en_GB.UTF-8
```

I have also

rm -rfv /usr/lib/locale/*

Now

```
locale-gen --purge
```

Produces:

```
Generating locales...
	en_GB.UTF-8... done
Generation complete.
```

Errors bug me!!

Is this purely cosmetic??

Can it be ignored?

Is it because the utf-8 part is in a different capitalisation to my locale files?

If it needs correcting where/how can I correct it.

I had to manually edit 

/boot/grub/grub.cfg

As I could not find how to set the language to GB...  GRUB2 is new to me..

```
From:
set lang=en_US

To:
set lang=en_GB
```


Any help is appreciated.

;

EDIT:

Forgot to add I have run:

```
apt-get install language-pack-en-base
```
and
```
apt-get install language-pack-en
```

Both upto date..

---

