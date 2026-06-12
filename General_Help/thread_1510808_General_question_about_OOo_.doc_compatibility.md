---
title: "General question about OOo .doc compatibility"
date: 2010-06-16
forum: General Help
---

### Post by triplesick on 2010-06-16
I encountered a doc file recently that opened noticeably differently in OOo than it did in MS Office.  I think the difference was a small change in spacing that pushed some text onto the next line.  It's also feasible that the problem was on my end.

My question has this.
1. Should I expect OOo compatibility with text-only .doc files to be absolutely, 100% perfect?

2. If not, any insights on where the problems usually are?

Thanks :)

---

### Post by QIII on 2010-06-16
I am a big fan of OOo.  I would love to tell you it is 100% compatible with Microsoft products.

Unfortunately, I can only report that it is 99% so.

I have had similar issues, and they have often revolved around slight differences in fonts and font sizes.  If the font used in the original .doc is one of Microsofts closely-held "only for us" fonts, you may have problems.

One thing you might be able to do is install the common/open true type Microsoft fonts. It's been a while since I have bothered to do it, but I think you can install the fonts by enabling all the repos and 

```
sudo apt-get install msttcorefonts
```But even that won't help if the original author used one of Microsoft's private stock fonts.

---

