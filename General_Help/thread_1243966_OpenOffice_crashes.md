---
title: "OpenOffice crashes"
date: 2009-08-18
forum: General Help
---

### Post by Muscovy on 2009-08-18
Whenever I launch openoffice, I get a message that it's about the recover X documents. When I click yes or no, I get a crash, saying Y documents (where y is either nothing or the .odt I clicked) will be recovered next time.
  Is there an easy way to fix it? I imagine purging everything would, but that's a bit extreme.

---

### Post by oboedad55 on 2009-08-19
> **Muscovy said:**
> Whenever I launch openoffice, I get a message that it's about the recover X documents. When I click yes or no, I get a crash, saying Y documents (where y is either nothing or the .odt I clicked) will be recovered next time.
  Is there an easy way to fix it? I imagine purging everything would, but that's a bit extreme.

I think what you can do is delete your .home/user/openoffice.org folder then restart OO. I seem to remember this happening to me a few years ago. To be safe just move that directory to your desktop. I believe you'll lose any settings you had in OpenOffice but that's the least of your problems. Let us know what happens.

Jon

---

### Post by Muscovy on 2009-08-19
I tried booting in in another account, and it still misbehaved, so I guess it's not that. And I used it fine about a week ago.

Edit: When I launch through terminal, I get the following message when it goes down: 
```
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
```

---

### Post by Muscovy on 2009-08-22
I tried totally purging and reinstalling all oo packages, but it still didn't work. And it's only writer that's broken. I figure I'll just reinstall.

---

### Post by Zill on 2009-08-22
You may find more help on the [OpenOffice Forums]("http://user.services.openoffice.org/en/forum/").

---

### Post by ricardisimo on 2009-09-04
> **oboedad55 said:**
> I think what you can do is delete your .home/user/openoffice.org folder then restart OO. I seem to remember this happening to me a few years ago. To be safe just move that directory to your desktop. I believe you'll lose any settings you had in OpenOffice but that's the least of your problems. Let us know what happens.

Jon

This worked for me... it's a pain in the rear, but it worked. Thanks.

---

### Post by Hagar Delest on 2009-09-04
See also here (less impact on your configuration): [[Solved] Stuck in Document Recovery](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=2660).

---

