---
title: "Update fails"
date: 2010-04-20
forum: General Help
---

### Post by carusoswi on 2010-04-20
I get this message when Ubuntu 9.10 tries to update:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2010g-0ubuntu0.9.10_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2010g-0ubuntu0.9.10_all.deb)
  404  Not Found [IP: 91.189.88.30 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010g-0ubuntu0.9.10_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010g-0ubuntu0.9.10_all.deb)
  404  Not Found [IP: 91.189.88.30 80]

What could be the problem and how might I correct it?

Thanks.

Caruso

---

### Post by Dhee on 2010-04-20
The repository seems to be down, have you tried selecting a different one to check if that helps?

```
System > Administration > Software Sources
```Then select one from the dropdown menu/pop-up

---

### Post by carusoswi on 2010-04-24
> **Dhee said:**
> The repository seems to be down, have you tried selecting a different one to check if that helps?

```
System > Administration > Software Sources
```Then select one from the dropdown menu/pop-up

Thanks for that useful tip.  I had all of the sources checked under the first tab, non other the others.  I don't know if clicking the additional ones solved the problem or if the repository was back up this morning, but the update finished successfully.

Thanks again.

Caruso

---

