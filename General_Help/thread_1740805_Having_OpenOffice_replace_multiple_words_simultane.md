---
title: "Having OpenOffice replace multiple words simultaneously"
date: 2011-04-27
forum: General Help
---

### Post by Avc1298 on 2011-04-27
Wasn't sure where to post this, didn't seem to fit any of the categories.

I have a list of approximately 50 words that I'd like to search documents for and delete those words. I was wondering if there is some type of automated process for removing multiple words rather than me manually putting each word into 'find and replace'

On that note I guess I could write the Macro in python if there isn't anything out there that does this. However I read that open office only works with python 2.3.5 or something of that nature, and I have already installed 3.1. Is that still going to be an issue?

Thanks in advance for any help.

---

### Post by Tamlynmac on 2011-04-27
One thing I might suggest is that OO has a forum of it's own located [here]("http://www.oooforum.org/"). It's packed with information and Q&A for all it's apps.

Good Luck

---

### Post by bodhi.zazen on 2011-04-27
I would use sed.

```
sed -i -e 's_old_new_g' file
```

Alternates would be to use tools such as awk or perl. Google search and you will find a few discussions and examples which may help depending on the complexity of what you are doing.

---

