---
title: "Firefox Default Programs For Files"
date: 2011-11-04
forum: General Help
---

### Post by rykel on 2011-11-04
Hi, I am running Firefox 7.0.1. However, when I click on a PDF or any other file on a website, Firefox ONLY offers me to download the file. I wish to see a dialog that says, "Open with XYZ program" along with the option to download the file. I think this is called the "mime" type or something...

How may I make that Firefox dialog change into what I mentioned above? Thanks for advice!

---

### Post by lovinglinux on 2011-11-04
When it offers to choose, browse the document viewer folder, which should be under /usr/bin/evince, select it, then click the option to remember this choice.

---

### Post by rykel on 2011-11-05
I am unable to do what you say. The (unwanted) dialog I am referring to is attached as a screenshot here.

---

### Post by vasa1 on 2011-11-05
What do you see when you Click on Edit, Preferences, Applications against PDF files?

Could you put up your equivalent of this?

---

### Post by rykel on 2011-11-05
Hi, mine says "Save File". Now I know how to solve this problem - simply change the default action in the button. Thank you so much!

---

### Post by vasa1 on 2011-11-05
> **rykel said:**
> Hi, mine says "Save File". Now I know how to solve this problem - simply change the default action in the button. Thank you so much!

You are welcome!

I'd just like to add that, as a precaution, it's better to keep things in the "always ask" mode (as far as you're comfortable). Some people link to huge PDF files that could, on computers with limited resources, bring the browser to a crawl.

It's also a bit of a security measure to set as many things to "always ask" so that you can know if a site is up to some tricks :D

---

