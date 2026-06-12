---
title: "Load speed slowdowns overtime"
date: 2012-06-02
forum: General Help
---

### Post by Tombradyhasamachinehead on 2012-06-02
hello,
 Does ubuntu suffer load speed decreases overtime? What i mean is my 6 month old Macbook pro speed takes a little longer to load files than it did from freshly installed Lion. Does ubuntu suffer from this? I know both EXT4 and HFS+ (MAC OS X FILESYSTEM) dont fragment. But i think the slow downs would happen from files being scattered everywhere?

---

### Post by matt_symes on 2012-06-02
Hi

> **Tombradyhasamachinehead said:**
> hello,
 Does ubuntu suffer load speed decreases overtime? What i mean is my 6 month old Macbook pro speed takes a little longer to load files than it did from freshly installed Lion. Does ubuntu suffer from this?

Yes of course it does. For a whole number of reasons.

> I know both EXT4 and HFS+ (MAC OS X FILESYSTEM) dont fragment.

This is not true. Files on an Ext4 filesystem get fragmented. There is now a defrag utility called 

```
e4defrag
```

This is available on 12.04. ExtX file systems do a good job at keeping the file system metadata contiguous, but the files can get fragmented. 

The defragger for ext4 has been in development for years and years. It was deemed to risky to release until it had been thoroughly tested. Search for T'so comments about it.

> But i think the slow downs would happen from files being scattered everywhere?

ureadahead helps with this, but the more files on the filing system...

Kind regards

---

