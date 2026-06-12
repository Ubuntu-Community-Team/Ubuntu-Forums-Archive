---
title: "Apache Mangling Unusual Characters"
date: 2011-12-05
forum: General Help
---

### Post by hwttdz on 2011-12-05
My apache server is turning opening and closing, single and double quotes into crazy symbols (euro symbol, tm symbol...).  When I look at the source being served to my browser I see the crazy symbol, when I look at the file being served I see the correct open or close quote.  Any thoughts?

I've traced it to the page in my server being rendered as encoded as ISO-8859-1, but I want it to be UTF-8.

Added to headers: 
<meta name="generator" http-equiv="Content-Type" content="text/html; charset=UTF-8"/>

Solved.

---

