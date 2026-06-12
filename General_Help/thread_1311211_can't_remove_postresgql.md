---
title: "can't remove postresgql"
date: 2009-11-02
forum: General Help
---

### Post by ameeck on 2009-11-02
Hi,

I'm trying to remove postresql and it keeps on failing, i really don't understand what's wrong...

```
vojta@vvondra-laptop:~$ sudo apt-get purge postgresql-8.4
&#268;tu seznamy balík&#367;... Hotovo
Vytvá&#345;ím strom závislostí       
&#268;tu stavové informace... Hotovo
Následující balíky budou ODSTRAN&#282;NY:
  postgresql-8.4*
0 aktualizováno, 0 nov&#283; instalováno, 1 k odstran&#283;ní a 1 neaktualizováno.
1 instalováno nebo odstran&#283;no pouze &#269;áste&#269;n&#283;.
Po této operaci bude na disku uvoln&#283;no 13,6MB.
Chcete pokra&#269;ovat [Y/n]? Y
(&#268;tu databázi ... nyní je nainstalováno 178979 soubor&#367; a adresá&#345;&#367;.)
Odinstalování balíku postgresql-8.4 ...
.: 19: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: chyba p&#345;i zpracovávání postgresql-8.4 (--purge):
 podproces instalovaný pre-removal skript vrátil chybový status 2
P&#345;i zpracování nastaly chyby:
 postgresql-8.4
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

