---
title: "problem with installation of molden"
date: 2010-05-12
forum: General Help
---

### Post by brzyt on 2010-05-12
hi,
I just started using Ubuntu, so please be patient with me. I'm totaly newbie :)

I need to install molden/gmolden, but I've got some problems. I fallowed instruction from this site [http://www.cmbi.ru.nl/molden/howtoget.html](http://www.cmbi.ru.nl/molden/howtoget.html) - I downloaded the archive file, I extracted it and then during trying to make the "make" commend or "make gmolden" I had such error:
g77   -c -o atomdens.o atomdens.f
make: g77: Polecenie nie znalezione  // command not found
make: *** [atomdens.o] B&#322;&#261;d 127  //  error 127

I've already went through this topic [http://ubuntuforums.org/showthread.php?t=962732](http://ubuntuforums.org/showthread.php?t=962732) , I've installed every packages, but error still occurs.

I'd be grateful for any help :)


sorry for my english, this language is new for me ;)

---

### Post by acuzzio on 2010-09-18
sudo apt-get install xutils-dev

---

