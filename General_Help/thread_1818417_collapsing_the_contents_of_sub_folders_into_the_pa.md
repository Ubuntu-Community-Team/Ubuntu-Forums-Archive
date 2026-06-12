---
title: "collapsing the contents of sub folders into the parent folder via terminal?"
date: 2011-08-04
forum: General Help
---

### Post by fertileneutrino on 2011-08-04
hey all,

I have a parent folder, with a lot of sub folders. basically, i'd like to bring all the contents from the sub folders into the parent folder, and subsequently delete the sub folders. is there one command for this? or do i need to cp -r over and over again, and then manually delete?

thanks,

fertileneutrino

---

### Post by lkjoel on 2011-08-04
Try this:
```
for i in `ls`; do cp -R $i/* .; rm -rf $i; done

```

---

