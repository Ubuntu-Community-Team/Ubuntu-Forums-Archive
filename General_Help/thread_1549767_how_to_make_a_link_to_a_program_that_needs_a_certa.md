---
title: "how to make a link to a program that needs a certain path ?"
date: 2010-08-10
forum: General Help
---

### Post by Andre-D on 2010-08-10
in order to play "Gish" - I need to 
cd .gish
./gish

- otherwise it won't find it's files - it need the working path,

- how can I put that in a sigle line in my games menu ?

---

### Post by Zorgoth on 2010-08-10
bash -c "cd .gish && ./gish" would work.

But it seems like there should be a better way.

---

### Post by Andre-D on 2010-08-10
yep, it works, thank you.

---

