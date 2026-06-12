---
title: "What is the output of &quot;date -u +%W$(uname)|sha256sum|sed 's/\W//g'&quot;?"
date: 2012-08-25
forum: General Help
---

### Post by npm1 on 2012-08-25
What is the output of "date -u +%W$(uname)|sha256sum|sed 's/\W//g'"?

---

### Post by kostkon on 2012-08-25
Huh?

---

### Post by codemaniac on 2012-08-26
> **npm1 said:**
> What is the output of "date -u +%W$(uname)|sha256sum|sed 's/\W//g'"?

sha256sum , calculates and verifies sha256 hashes .

In the above sed command , \W escape sequence match only nonword characters and replace them .

---

### Post by Elfy on 2012-08-26
[http://ubuntuforums.org/showthread.php?t=1843526](http://ubuntuforums.org/showthread.php?t=1843526)

---

