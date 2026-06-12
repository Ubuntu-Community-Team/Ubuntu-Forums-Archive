---
title: "php or mysql error messages never display"
date: 2011-02-09
forum: General Help
---

### Post by ryank76nz on 2011-02-09
I have a LAMP installation for learning php and mysql. My online trainer pointed out that we always get a white screen when the php is wrong, when we should get error messages that say which line in the code is wrong etc.

I recently reinstalled mysql so it is the latest version from the repositories for Ubuntu 10.04.2 LTS.

Is there a way to make error messages show up?

Thanks

---

### Post by [Snc] on 2011-02-09
PHP has error handling, since it would be extremely dangerous to have errors and people knowing about them, they are hidden by default. If someone with bad intentions sees errors, he knows how things work and why they break, than he can manipulate/attack, this is not good.

In your test/training environment it can be enabled, to see the problems.

[http://www.w3schools.com/php/php_error.asp](http://www.w3schools.com/php/php_error.asp)

---

### Post by indytim on 2011-02-09
If you are running a development site only (not open to outside connections), you may enable error display by updating your php.ini file for error display to:

```

error_reporting = E_ALL & ~E_NOTICE

```

The php.ini file location in standard LAMP installations is

/etc/php5/apache2/php.ini

Note : you will need root priv's to edit the file.  You will also need to restart your Apache server to see the effects on the mods to the php.ini file.

Hope this helps,

IndyTim / DataMan

---

### Post by ryank76nz on 2011-02-09
Awesome, thanks, I edited that line in the php.ini and the error messages show up now.

---

