---
title: "wget help"
date: 2010-08-15
forum: General Help
---

### Post by ShaolinF on 2010-08-15
Hi Guys

Is there any way I can increment through the following URL in wget:

display.php?18-Comparative-Forms/page

Basically, I want every url that matches that format to be d/led. e.g:

display.php?18-Comparative-Forms/page1
display.php?18-Comparative-Forms/page2
display.php?18-Comparative-Forms/page3

I've tried the following in wget but it doesn't work:

wget -A "display.php?18-Comparative-Forms/page*" "www.mysite.com?display.php?18-Comparative-Forms/" -r -l 0

I suspect the reason for this is because in the -A argument the "?" is being translated as some sort of regex. Is there any way I can escape it ?

---

### Post by KeyserSoze93 on 2010-08-17
Try:

```

i=1

while [ 1 ]; do

wget "display.php?18-Comparative-Forms/page$i" || break

i=$[i+1]

done

```

---

