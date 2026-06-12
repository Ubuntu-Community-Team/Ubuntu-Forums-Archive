---
title: "Repository"
date: 2012-05-22
forum: General Help
---

### Post by nashtrik on 2012-05-22
Please enlighten me with all the details of a Repository which a Newbie ought to know.Thanks in advance.

---

### Post by carl4926 on 2012-05-23
Run this

```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list [http://www.medibuntu.org/sources.list.d/$(lsb_release]("http://www.medibuntu.org/sources.list.d/$%28lsb_release")  -cs).list && sudo apt-get --quiet update && sudo  apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring  && sudo apt-get --quiet update
```

---

### Post by oldos2er on 2012-05-23
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

