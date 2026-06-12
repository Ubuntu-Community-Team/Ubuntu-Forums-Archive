---
title: "Installing HantekDSO | no KDE libraries installed"
date: 2012-05-31
forum: General Help
---

### Post by Fenris88 on 2012-05-31
Hi,

I'm trying to install HantekDSO([http://sourceforge.net/projects/hantekdso/](http://sourceforge.net/projects/hantekdso/)) on Ubuntu 12.04.
But when I try ```
/.configure
``` eventually it says:
```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
```What I already tried:
I installed kdelibs5-dev.

I think that installing kdebase-dev would solve the problem.
But:
```
$sudo apt-get install kdebase-dev
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut      
Statusinformationen werden eingelesen... Fertig
E: Paket kdebase-dev kann nicht gefunden werden
```For all non-Germans :): 
Package kdebase-dev cannot be found

So, do you have any idea, what I could try next?

Yours sincerely
Fenris

---

