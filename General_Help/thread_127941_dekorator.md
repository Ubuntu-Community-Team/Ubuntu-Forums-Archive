---
title: "dekorator"
date: 2006-02-10
forum: General Help
---

### Post by eeknay on 2006-02-10
Hi.

Anyone who got dekorator working on drapper? I got myself the latest version including the fix, but the compiler keeps dying.

[COLOR="Navy"]deKoratorclient.moc:200: error: 'KDecoration' has not been declared
deKoratorclient.moc: In member function 'virtual bool DeKorator::DeKoratorClient::qt_property(int, int, QVariant*)':
deKoratorclient.moc:206: error: 'KDecoration' has not been declared
deKoratorclient.cc: In member function 'virtual bool DeKorator::DeKoratorFactory::reset(long unsigned int)':
deKoratorclient.cc:203: warning: control reaches end of non-void function
make[3]: *** [deKoratorclient.lo] Fehler 1
make[3]: Leaving directory `/home/eeknay/Desktop/dekorator-0.2-fix1.orig/client'
make[2]: *** [all-recursive] Fehler 1
make[2]: Leaving directory `/home/eeknay/Desktop/dekorator-0.2-fix1.orig/client'
make[1]: *** [all-recursive] Fehler 1
make[1]: Leaving directory `/home/eeknay/Desktop/dekorator-0.2-fix1.orig'
make: *** [all] Fehler 2[/COLOR]

And I can't find any ubuntu packages for this.

eeknay

---

### Post by Jucato on 2006-02-10
I found a .deb for deKorator somewhere. I forgot where. it works on Breezy, but I'm not sure if it will work in Dapper.

---

### Post by eeknay on 2006-02-10
Nice. Could you point me to it? I went back to breezy, drapper has to many bugs imho.

---

### Post by Neo Ex on 2006-02-10
[deKorator]("http://www.kde-look.org/content/show.php?content=31447")
[.deb of deKorator]("http://www.cheetux.org.il/~motyr/deKorator/0.2/")
I'm using deKorator compiled from the source and it works, but in the past I've also used the deb package and it also worked.

---

