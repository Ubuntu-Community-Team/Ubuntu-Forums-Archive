---
title: "php-gtk"
date: 2009-10-19
forum: General Help
---

### Post by sethhikari on 2009-10-19
When trying to compile php-gtk it fails durring configure. Is there a fix or a method to get php-gtk working? here is the error

```
reating main/php_gtk_ext.c
./configure: line 11725: LTOPTIONS_VERSION: command not found
./configure: line 11726: LTSUGAR_VERSION: command not found
./configure: line 11727: LTVERSION_VERSION: command not found
./configure: line 11728: LTOBSOLETE_VERSION: command not found
checking for a sed that does not truncate output... (cached) /bin/sed
./configure: line 11803: syntax error near unexpected token `lt_decl_varnames,'
./configure: line 11803: `lt_if_append_uniq(lt_decl_varnames, SED, , ,'

```

---

### Post by fomaa on 2009-10-20
I had the same problem. I resolved with following commands.

```
./buildconf --with-phpize=/usr/bin/phpize5
./configure --with-php-config=/usr/bin/php-config5
```

---

### Post by wiscalico on 2010-02-18
I've got it compiling an put it in [my PPA]("https://launchpad.net/~jacob-emcken/+archive/ppa/")... for those too lazy to build themselves :)

It is build with the following: --with-extra --with-html --with-libsexy --with-spell --enable-php-gtk --enable-scintilla --with-mozembed

---

