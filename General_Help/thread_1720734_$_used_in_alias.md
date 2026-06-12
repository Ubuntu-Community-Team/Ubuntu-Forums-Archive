---
title: "$ used in alias"
date: 2011-04-03
forum: General Help
---

### Post by Zucriy Amsuna on 2011-04-03
In a tcsh shell, I've been trying to make a few aliases for listing and counting files/directories. Here's the example for listing directories (not like using **ls -al | egrep drwx | awk '{print $9}'**):

```
alias listd "ls -1aR \!* | egrep '[:]$'"
```But it keeps saying that it's an illegal variable name. I use the up arrow, and it gives me:

```
alias listd "ls -1aR \!* | egrep '[:]$\'"
```Without the single quotes, the backslash still appears after the $.

Why? And how can I do this with alias?

---

