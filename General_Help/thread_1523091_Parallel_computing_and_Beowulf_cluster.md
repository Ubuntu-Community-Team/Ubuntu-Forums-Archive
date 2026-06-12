---
title: "Parallel computing and Beowulf cluster"
date: 2010-07-03
forum: General Help
---

### Post by chernobila on 2010-07-03
I was browsing through the board to find the right place for this thread and I ended up here. Well mainly because that there was not 100% match for the thread through subforums.So in case this is violation I apologies in advance.

Here we go ...

As you can see from the title of the thread I am trying to build home made Linux cluster. I have about 10 different machines in my possession, specifications of which varies from desktops to laptops, from Celeron 1.5GHz to Core 2 Quad Q6600 (the last one is actually my main desktop computer) and so on. You get the idea.

Main reason why I want this cluster is that I deal with HD video editing, so I am looking for clustering solution which will work with some decent video editing software. I know there is something in 'Ubuntu software center' called "cluster management" but I can not get it to work (it does say that it is still experimental stage). Some people advised to use software called Veritas but it seems that is not a free solution. Yes I forgot to mention that I am looking for free solution. I also found some really great guides and tutorials for Red Hat 7.1 and later, but same problem, only for commercial distributions. One more software I came across was Mosix. It is free but on their website they had only demo version. I also checked Sun Microsystems applications and it seems like software itself is free but only works with their hardware. 

If anybody has any tips or has an experience clustering Ubuntu machines please help me out. Any advice will be very useful since I have never done this before. Whatever is there to learn about it I will be more then happy to absorb.

Thank you a million

---

### Post by dino99 on 2010-07-03
some related links:

[http://www.google.fr/search?as_q=cluster%2Bmanagement%2Bubuntu&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=cluster%2Bmanagement%2Bubuntu&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by cogier on 2010-07-03
I read your post and thought I can't help then I accidentally ran into this.
[http://sourceforge.net/softwaremap/?&fq%5B%5D=trove%3A141]("http://sourceforge.net/softwaremap/?&fq%5B%5D=trove%3A141"). Hope it helps.

---

### Post by chernobila on 2010-07-04
Thank you guys a lot. I will try that and post back. Meanwhile if anybody has more info please post. Anything will be very helpful

---

### Post by chernobila on 2010-07-04
> **dino99 said:**
> some related links:

[http://www.google.fr/search?as_q=cluster%2Bmanagement%2Bubuntu&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=cluster%2Bmanagement%2Bubuntu&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

OK I check that and I have seen it all. Of course before I came here I did google search. None of them mention anything about supporting video editing software.

But thank you for taking you time and posting

---

### Post by chernobila on 2010-07-06
so still nothing guys?

---

### Post by shel-hall on 2010-07-06
I would suggest asking the heavy users of your video editing software what they do.

In general, programs have to be written specifically to support any sort of parallel processing.  The OS can do some task division on its own, but unless the application is written to use the parallel processing "hooks" in the OS, you don't get much.

This is especially true in the case of clusters.  Unless you're able to run a single OS image across all the processors, the OS not only has to provide the parallel-computing hooks to a program that can use them, it has to parcel the work out to multiple copies of the OS on separate machines, the integrate the results to present them back to the application program.

This is real specialist territory.

If someone who uses your favorite video editor has solved this problem, you're much more likely to find them where the users of that software hang out.

-Shel

---

### Post by chernobila on 2010-07-08
> **shel-hall said:**
> I would suggest asking the heavy users of your video editing software what they do.

In general, programs have to be written specifically to support any sort of parallel processing.  The OS can do some task division on its own, but unless the application is written to use the parallel processing "hooks" in the OS, you don't get much.

This is especially true in the case of clusters.  Unless you're able to run a single OS image across all the processors, the OS not only has to provide the parallel-computing hooks to a program that can use them, it has to parcel the work out to multiple copies of the OS on separate machines, the integrate the results to present them back to the application program.

This is real specialist territory.

If someone who uses your favorite video editor has solved this problem, you're much more likely to find them where the users of that software hang out.

-Shel

Thanks a lot for very useful info. At this point it does not matter which video editing software it will be. I work with many different ones so getting familiar with new one will not be a problem.

I came across this video but its not really clear what they use. He does mention that he tells his friends to use old machines. So looks like it should not require that much. And whats more they specifically talk about video rendering. 

May be anybody is more familiar with the stuff they use in this video

I am not sure if I can post links here but here it is. add this to youtube dot com watch?v=NuD805OeukI

thanks everybody again

---

