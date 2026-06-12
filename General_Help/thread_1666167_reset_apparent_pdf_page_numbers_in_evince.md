---
title: "reset apparent pdf page numbers in evince"
date: 2011-01-13
forum: General Help
---

### Post by tuxonapogostick on 2011-01-13
Does anyone now how to re-set the page numbers of a pdf file within evince (without modifiying the pdf file). The point is that I am reading an article, and I would like the set "page 1" as "page 43". I assume modifying page numbers of a pdf file is a bit tricky. So, I want to avoid that. What I wanna do is to make evince "think" page 1 is page 43.

Thanks.

---

### Post by svetiev on 2011-01-13
This might help. 

[http://ubuntuforums.org/showpost.php?p=5469675&postcount=6]("http://ubuntuforums.org/showpost.php?p=5469675&postcount=6")

The program used is pdftk. It also has a GUI frontend called PDF Chain. If you install the latter through synaptic you will get both functionalities.

Also maybe you would be better off with PDF-Shuffler which does exactly that - shuffles the order of pages through a user friendly GUI interface. You just drag the pages arround to the order you want.

---

### Post by tuxonapogostick on 2011-01-13
> **svetiev said:**
> This might help. 

[http://ubuntuforums.org/showpost.php?p=5469675&postcount=6]("http://ubuntuforums.org/showpost.php?p=5469675&postcount=6")

The program used is pdftk. It also has a GUI frontend called PDF Chain. If you install the latter through synaptic you will get both functionalities.

Also maybe you would be better off with PDF-Shuffler which does exactly that - shuffles the order of pages through a user friendly GUI interface. You just drag the pages arround to the order you want.
I quickly checked out the packages that you mentioned. I am not sure if they will do the job. Let me be more specific. Say I have a 10 page pdf file, and I would like to reset the page numbers as follows: 1->53, 2->54,..., 10->63. Note pages 53...63 does not physically exist as the total numbers of pages is 10. I just would like to in some sense reset the page counter in evince.

---

