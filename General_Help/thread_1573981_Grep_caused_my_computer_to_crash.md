---
title: "Grep caused my computer to crash"
date: 2010-09-13
forum: General Help
---

### Post by Johnsie on 2010-09-13
> grep -i -n -r 'zonal_sooty' /nameoffolder
(I've changed the name of the folder for security reasons)

I did the above command and my system locked up. Is this normal? Surely I should be able to search for a file without my whole system locking up?

---

### Post by TeoBigusGeekus on 2010-09-13
Why don't you try
```
find /nameoffolder -n *zonal_sooty*
```
?

---

### Post by scorp123 on 2010-09-13
> **Johnsie said:**
> Is this normal?  No, it's not. Might be defective RAM or CPU? I had that once. My PC would freeze whenever I tried to un-zip or un-tar something. In the end it turned out that both my RAM banks were defective.

> **Johnsie said:**
>  Surely I should be able to search for a file without my whole system locking up? Oh yes, definitely.

---

