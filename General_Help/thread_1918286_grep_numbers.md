---
title: "grep numbers"
date: 2012-01-31
forum: General Help
---

### Post by conradin on 2012-01-31
Hi All,
Im reading the book Grep Handbook published from Oriely. There is an example that says something like to find all odd numbers using [13579].
Is that really the best way to do it? I was thinking that the only position we care about is at the end of a string of numbers, but the \> regex only applies to words. Am I over thinking this? Is there a better way to search for odd numbers with a regular expression?

---

### Post by squenson on 2012-01-31
I would try something like: \d+[13579]\b
\d+ indicates zero or more digits
[13579] means one of these digits must be present before \b which defines a word boundary

It will return '125' but also 'k125'

If you don't want the second type, try \b\d+[13579]\b

---

### Post by Vaphell on 2012-01-31
> \d+ indicates **zero or more** digits
1 or more
0 or more belongs to *

---

### Post by squenson on 2012-01-31
Thank you for spotting my mistake **Vaphell**! I should have added that I didn't thoroughly test the expression and it should be done before use!

---

