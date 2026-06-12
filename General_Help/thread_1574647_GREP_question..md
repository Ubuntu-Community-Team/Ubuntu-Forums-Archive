---
title: "GREP question."
date: 2010-09-14
forum: General Help
---

### Post by cloverz7 on 2010-09-14
I'm almost positive you would have to use Grep and wc, but I'm attempting to use terminal to count the number of 4 letter words in a file. Anyhelp in this would be great.

woops figured it out: 


 grep '\<[A-Za-z]\{5\}\>' /path/to/file | wc -w

---

