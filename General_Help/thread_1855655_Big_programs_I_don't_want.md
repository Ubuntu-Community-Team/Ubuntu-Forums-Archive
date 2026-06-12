---
title: "Big programs I don't want"
date: 2011-10-06
forum: General Help
---

### Post by Perplexed Pat on 2011-10-06
What if I've been downloading Google Earth and it didn't work? Will it be clogging up my system with loads of residual shirt?

---

### Post by dave01945 on 2011-10-06
when using synaptic if you mark for complete removal it will delete all config files as well so there shouldn't be anything left over if you remove it from command line use purge instead of remove

```
sudo apt-get purge programname
```

---

### Post by WorMzy on 2011-10-06
Yes. Any user files the program generates are stored in your home folder. They will remain there until you delete them.

Look in ~/.googleearth, or ~/.cache/googleearth, and other places like that.

or else run

```
du -hx --max-depth=1 ~ | sort -h
```

to see where the msot space is being used in your home folder.

---

### Post by Perplexed Pat on 2011-10-06
Thanks fellas.

---

