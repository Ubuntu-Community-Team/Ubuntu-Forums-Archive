---
title: "Delete file named \"
date: 2010-04-23
forum: General Help
---

### Post by jucas_lo on 2010-04-23
Hi I accidentally created a file callled "\", and now I don't know how to delete it!

Does anyone know how to do it?? 

Thanks in advance!

---

### Post by iponeverything on 2010-04-23
```
rm \\
```

---

### Post by sisco311 on 2010-04-23
```
rm '\'
```

See:
```
man bash | less +/^QUOTING
```

---

### Post by jucas_lo on 2010-04-26
thanks guys!! that worked like a charm!

---

