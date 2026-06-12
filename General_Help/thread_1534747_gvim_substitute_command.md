---
title: "gvim substitute command"
date: 2010-07-20
forum: General Help
---

### Post by rudy_b on 2010-07-20
Hi all, 
I would truley thank you if you can help me with my issue. It's been few
hours I am trying to solve this, but no luck yet!!

I want to do a substitution using the (/s) command. But I am ONLY interested
in substituting multiples of 100th line. 
In other words, I have a huge file (thousands of lines); and, I want to go
through this file, and look for lines #100, #200, #300, #400, ... and append
the word "checked" at the end of these line. 
for example:
1. this is my line #1
2. this is my line #2
3. this is my line #3
... 
100. this is my line #4 (CHECKED) 
101. this is my line #101
...
199 this is my line #199
200. this is my line #200 (CHECKED)
...
and so on...

Does anyone know how can I do this?

I tried to look into substituting with the aid of visual selection. (e.g.
:$s/\v) but was not able to do such a selection to select multiples of 100th
line.

thanks for your help in advnace.

Rudy

---

