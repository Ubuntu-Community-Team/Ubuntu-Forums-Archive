---
title: "How to batch rename directories?"
date: 2010-12-05
forum: General Help
---

### Post by UranUtan on 2010-12-05
Hi,

I have several folders:
Archive_001
Archive_002
Archive_003
etc.

Is there any command to batch rename these directories to:
NewArchive_001
NewArchive_002
NewArchive_003

Thanks in advance.

---

### Post by asmoore82 on 2010-12-06
There is a `rename` command that batch renames based on a Perl expression.
I don't know Perl, but I've used the simple examples in its manpage:

```
man rename
```

Here's Archive_### to NewArchive_###
```
rename 's/^/New/' Archive_???
```

---

### Post by aeronutt on 2010-12-06
My perl has gotten rusty over the past 5 years...I've started using a gui based rename tool. pyrenamer . It's in the repository. The thing I like most, is that you can name photos based on some of the EXIF data, like dates. But, does generic renaming, date append, count, etc.

---

