---
title: "Find out the file extension for an unknown file type?"
date: 2012-03-11
forum: General Help
---

### Post by Rytron on 2012-03-11
Is there a terminal or GUI method to find out the file extension for an unknown file type?

I right click and goto Properties and get "unknown (application/octet-stream)".

In this case I know it is a truecrypt file but if I did not know - how could I find out?

This would be handy for future reference.

---

### Post by MG&amp;TL on 2012-03-11
```
file <file you want to know about>
```

Will tell you as much as linux knows about them. Truecrypt seems to create a binary file (?), so unless TrueCrypt has a MIME type, it probably won't say much.

---

### Post by Rytron on 2012-03-12
> **MG&TL said:**
> ```
file <file you want to know about>
```

Will tell you as much as linux knows about them. Truecrypt seems to create a binary file (?), so unless TrueCrypt has a MIME type, it probably won't say much.

Thanks.

```
file myfile
```

output 
```
myfile: data
```

---

### Post by sudodus on 2012-03-12
***PhotoRec ***is good at identifying files from the file content, so maybe it can identify some file, that ***file*** cannot manage.

---

### Post by Rytron on 2012-03-12
> **sudodus said:**
> ***PhotoRec ***is good at identifying files from the file content, so maybe it can identify some file, that ***file*** cannot manage.

Thank you sudodus.

---

### Post by Dave_L on 2012-03-12
> **Rytron said:**
> In this case I know it is a truecrypt file but if I did not know - how could I find out?

I know you're using Truecrypt only as an example, but it's desirable that Truecrypt containers not be easily identifiable as such, since they're used to hide information.

---

### Post by Rytron on 2012-03-12
> **Dave_L said:**
> I know you're using Truecrypt only as an example, but it's desirable that Truecrypt containers not be easily identifiable as such, since they're used to hide information.

Yes, good point.

---

