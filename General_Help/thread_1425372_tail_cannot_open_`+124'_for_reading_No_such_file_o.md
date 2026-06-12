---
title: "tail: cannot open `+124' for reading: No such file or directory"
date: 2010-03-09
forum: General Help
---

### Post by 5v_great on 2010-03-09
tail: cannot open `+124' for reading: No such file or directory
gzip:  tmptarfile.tar.Z: not in gzip format
tar: This does not look like a  tar archive
tar: Error exit delayed from previous errors
extract  error, installation cannot proceed.

:?:](*,)what is the problem?

---

### Post by gmargo on 2010-03-09
**gzip(1)** should decompress a .Z file. If it cannot you can try **compress(1)**.  You will probably have to install the **ncompress** package since it is not installed by default.  Then try this:
```

uncompress.real -c tmptarfile.tar.Z | tar tfv -

```Replace "tfv" with "xfv" when you're ready to extract.

---

### Post by 5v_great on 2010-03-09
tail: cannot open `+124' for reading: No such file or directory
tmptarfile.tar.Z: not in compress format
tar: This does not look like a  tar archive
tar: Error exit delayed from previous errors
extract  error, installation cannot proceed.

:(

---

