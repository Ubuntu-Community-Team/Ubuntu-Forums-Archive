---
title: "binary to ascii"
date: 2010-06-25
forum: General Help
---

### Post by Milenkonslisboa on 2010-06-25
Anyone knows for good convertor?

---

### Post by KeyserSoze93 on 2010-06-25
Binary to ASCII:

```

perl -e 'printf "%c", 0b1000001'

```

Returns a capital A.

ASCII to binary:

```

perl -e 'printf "%b", ord(A)'

```

Returns 1000001.

Consult documentation for Perl's printf/sprintf function for more information. Binary numbers in Perl must be preceded by 0b

---

