---
title: "Gedit swedish characters"
date: 2010-09-27
forum: General Help
---

### Post by dpbBryan on 2010-09-27
I wasn't really to sure where to ask this question, but I figured general help wouldn't be a bad place.

I'm trying to save HTML files to display the swedish characters like:
 
ä å ö and whatever the other one may be.

It looks just fine inside gedit, but the problem is when I try to view the html file, it looks like:

Ja, vad kan man sÃ¤ga.. Blir alltid lika stÃ¤lld varje gÃ¥ng jag ska skriva nÃ¥t om mig sjÃ¤lv..

Does anybody have an idea what causes this?

---

### Post by peakperformance on 2010-10-13
You have to add this in the html header:

<META http-equiv="Content-Type" content="text/html;charset=UTF-8">

Cheers

---

