---
title: "sudo apt-get --purge remove calligra only removes 73kb not 300mb ?"
date: 2012-04-16
forum: General Help
---

### Post by th1 on 2012-04-16
I installed Caligra suite to test it, now I want to remove it, I tried:

sudo apt-get --purge remove calligra

but it tells me it will remove only 73,7 kB of disk space, it installed 300mb

what's the proper command? thanks

(ps.: tried to check in synaptic but ther's no 'calligra'' package...)

---

### Post by cortman on 2012-04-16
Well for one thing your command is slightly wrong- try

```
sudo apt-get purge calligra
```

And see what that offers to remove.

---

### Post by th1 on 2012-04-16
it says exactly the same thing: 

(I have this running in portuguese)

> sudo apt-get purge calligra
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
Os seguintes pacotes foram instalados automaticamente e já não são necessários:
(The following packages were installed and are no longer needed:)
  calligra-map-shape libmarblewidget13 libkldap4 krita-data kdepim-runtime
  calligrawords libkpimtextedit4 libprison0 libkcalutils4 libmicroblog4
  calligra-data calligraflow libglew1.6 libopenshiva0.7 kthesaurus
  mysql-client-core-5.1 libgtlcore0.7 libboost-program-options1.46.1 krita
  libgps19 calligraflow-data akonadi-backend-mysql libkalarmcal2 libqrencode3
  libkmbox4 ruby1.8 mysql-server-core-5.1 libkcalcore4 ruby libmailtransport4
  libakonadi-kde4 libkabc4 libkresources4 libkpimutils4 libkrossui4
  libkpimidentities4 libakonadi-notes4 libkcal4 libakonadi-calendar4 libdcmtk2
  libkimap4 libopenctl0.7 calligra-libs karbon libkmime4 libspnav0
  calligraplan libakonadi-contact4 libakonadi-kabc4 libkholidays4
  libqtshiva0.1 akonadi-server libkdcraw20 libruby1.8 libgsl0ldbl marble-data
  libkdcraw-data libakonadiprotocolinternals1 libakonadi-kcal4 marble-plugins
  kexi libreadline5 libakonadi-kmime4 kdepimlibs-kio-plugins
  calligrawords-data libllvm2.8 calligratables libdmtx0a calligrastage
Utilize 'apt-get autoremove' para os remover.
Serão REMOVIDOS os seguintes pacotes:
  calligra*
0 pacotes actualizados, 0 pacotes novos instalados, 1 a remover e 16 não actualizados.
Após esta operação, será libertado 73,7 kB de espaço em disco.


---

### Post by snowpine on 2012-04-16
The key information is here (trimmed the list for clarity):

```
(The following packages were installed and are no longer needed
calligra-map-shape ... calligrastage
Utilize 'apt-get autoremove' para os remover.
```

So you should type:

```
sudo apt-get autoremove
```

---

### Post by mikaelcrocker on 2012-04-16
I don't know if you've tried it, but trying a apt-get remove then apt-get purge??  I don't know if there is a process for it, it's worked for me a couple of times.

---

### Post by cortman on 2012-04-16
> **snowpine said:**
> The key information is here (trimmed the list for clarity):

```
(The following packages were installed and are no longer needed
calligra-map-shape ... calligrastage
Utilize 'apt-get autoremove' para os remover.
```So you should type:

```
sudo apt-get autoremove
```

+1 for catching that, Snowpine!
OP, that command should take care of it.

---

### Post by apochry on 2012-04-18
Thanks [snowpine]("http://ubuntuforums.org/member.php?u=479885")!

I ran:
```
sudo apt-get remove calligra
sudo apt-get autoremove
```worked perfectly.

**Please mark thread as [SOLVED] if it worked for you.**

Christo

---

