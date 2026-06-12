---
title: "Update manager - &quot;Not all updates can be installed&quot;"
date: 2011-04-20
forum: General Help
---

### Post by frankiethepill on 2011-04-20
Update manager keeps telling me that there are 512 updates available, but then tells me that not all can be installed, and I can do a partial upgrade. This has been so for about 2 weeks and I still have 512 updates outstanding, even with a partial update. Am I missing something or do I leave it be?

---

### Post by collisionystm on 2011-04-20
What version of ubuntu? Check your software sources. I am sure you have extra junk in there that did not come with ubuntu. When it trys to update, what file is it stuck on? THis could give a good indication of what the bad software source is. Try apt-get -f install

---

