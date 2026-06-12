---
title: "bash commands"
date: 2010-05-03
forum: General Help
---

### Post by andrebarradas on 2010-05-03
Hi,

How i put `hostname` in uppercase in this case:

date +"%Y%m%d%T" > date_`hostname`.txt 

Best wishes,

André Barradas

---

### Post by Portmanteaufu on 2010-05-03
> **andrebarradas said:**
> Hi,

How i put `hostname` in uppercase in this case:

date +"%Y%m%d%T" > date_`hostname`.txt 

Best wishes,

André Barradas

```

date +"%Y%m%d%T" > date_`hostname | perl -e '$str=<STDIN>;print(uc($str));'`.txt 

```
That oughta do it.

---

### Post by Portmanteaufu on 2010-05-03
If you wanted to avoid a perl dependency, you could use:

```

hostname | tr '[:lower:]' '[:upper:]'

```
in the backticks instead.

---

### Post by andrebarradas on 2010-05-03
> **Portmanteaufu said:**
> ```

date +"%Y%m%d%T" > date_`hostname | perl -e '$str=<STDIN>;print(uc($str));'`.txt 

```That oughta do it.

i solved right now.Here is my resolution:

date +"%Y%m%d%T" > date_`hostname | tr [a-z] [A-Z]`.txt

Anyway,thanks for your help.Your resolutions worked too.

---

