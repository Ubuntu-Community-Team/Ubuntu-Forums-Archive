---
title: "Slash or backslash?"
date: 2012-02-16
forum: General Help
---

### Post by PadiSka on 2012-02-16
Is there any reason why Ubuntu uses "/" for file paths and windows uses "\" for windows file locations?

---

### Post by winh8r on 2012-02-16
Pointless Answer is here:

[http://tinyurl.com/78uzflp]("http://tinyurl.com/78uzflp")



:D

---

### Post by jonobr on 2012-02-16
Actually


I tend to disagree, 

thats ones of the "I must figure out some day why things are like that" questions

Good answer

---

### Post by haqking on 2012-02-16
i believe that the / (solidus) was used in Unix as it is a divisor in programming and Unix was programmed in C

So in Unix it was chosen as it **divides** or seperates the directories etc.

When Dos/Windows came about the / was used so they went with \ and MS at the time didnt use directories as it was all one big root

[http://blogs.msdn.com/b/larryosterman/archive/2005/06/24/432386.aspx](http://blogs.msdn.com/b/larryosterman/archive/2005/06/24/432386.aspx)

The end ;-).

---

### Post by PadiSka on 2012-02-16
Ya learn something new everyday!ha. Thanks.

---

### Post by mörgæs on 2012-02-16
Please mark the thread 'solved' using 'thread tools'.

---

### Post by Khayyam on 2012-02-17
> **PadiSka said:**
> Is there any reason why Ubuntu uses "/" for file paths and windows uses "\" for windows file locations?

Yes, *nix does it correctly (meaning it devised the standard) and MS (way back when implimenting MSDOS) couldn't stand to the let "/" be a standard for path designation, and so, eureka! .. reversed it! ... "Innovation!, Innovation!, Innovation!" 

C: <--- no prizes for what this means ... Cuthulu!!! .. just check our website at ptth:\\vvv.microsoft.com\cuthulu

Best ...khay

---

### Post by haqking on 2012-02-17
> **Khayyam said:**
> Yes, *nix does it correctly (meaning it devised the standard) and MS (way back when implimenting MSDOS) couldn't stand to the let "/" be a standard for path designation, and so, eureka! .. reversed it! ... "Innovation!, Innovation!, Innovation!" 

C: <--- no prizes for what this means ... Cuthulu!!! .. just check our website at ptth:\\vvv.microsoft.com\cuthulu

Best ...khay


Actually you can use both / and \ on MS.

go to command line and do

cd /<path>

cd \<path>

you will get same result

the DOS devs at the time were using Xenix so were used to \ so they programmed in both

the only reason / is used instead of \ is cos / was taken

[http://blogs.msdn.com/b/larryosterman/archive/2005/06/24/432386.aspx](http://blogs.msdn.com/b/larryosterman/archive/2005/06/24/432386.aspx)

---

### Post by Khayyam on 2012-02-17
> **haqking said:**
> rubbish. Actually you can use both / and \ on MS. [...] the DOS devs at the time were using Xenix so were used to \ so they programmed in both [...] the only reason / is used instead of \ is cos / was taken

It was my understanding that "86-DOS" when it was bought my Microsoft used "/" and that MS changed it. If I remember correctly, I read this in "COMPUTER!" way back. So, "rubbish" it may be, but a simple "thats not exactly true" would have sufficed. 

I've not used DOS for years, and never had an inkling to use "/" as this was prior to my exposure to *nix, but I'm pretty sure I never saw anything, code, tutorials, etc, with a forward slash, are you sure this is not a recent addition?

I'm not sure what you mean by "taken", do you mean due to AT&T's licence? I don't think it would be covered by the copyright, otherwise Berkeley BSD, GNU, etc, would not have been able to use it.

As for the Xenix connection, I thought this was based on AT&T's Sys III, and so "/" would have been the designator? I think this was the case with MS-XENIX (see [this image]("http://www.tenox.tc/tmp/ww/msxenix/pics/msword-xenix.jpg") for instance.)

Anyhow, I don't pass on information willy-nilly, that was how I understood the backslash to have come about, if I'm mistaken I stand corrected, but easy with the "rubbish", its dismissive and unfriendly.

Oh, and you did understand that I was playing with the well known fact that MS has a long history of "breaking standards" .. all hail cuthulu!
 
Best ... khay

---

### Post by haqking on 2012-02-17
> **Khayyam said:**
> It was my understanding that "86-DOS" when it was bought my Microsoft used "/" and that MS changed it. If I remember correctly, I read this in "COMPUTER!" way back. So, "rubbish" it may be, but a simple "thats not exactly true" would have sufficed. 

I've not used DOS for years, and never had an inkling to use "/" as this was prior to my exposure to *nix, but I'm pretty sure I never saw anything, code, tutorials, etc, with a forward slash, are you sure this is not a recent addition?

I'm not sure what you mean by "taken", do you mean due to AT&T's licence? I don't think it would be covered by the copyright, otherwise Berkeley BSD, GNU, etc, would not have been able to use it.

As for the Xenix connection, I thought this was based on AT&T's Sys III, and so "/" would have been the designator? I think this was the case with MS-XENIX (see [this image]("http://www.tenox.tc/tmp/ww/msxenix/pics/msword-xenix.jpg") for instance.)

Anyhow, I don't pass on information willy-nilly, that was how I understood the backslash to have come about, if I'm mistaken I stand corrected, but easy with the "rubbish", its dismissive and unfriendly.

Oh, and you did understand that I was playing with the well known fact that MS has a long history of "breaking standards" .. all hail cuthulu!
 
Best ... khay

I didnt mean the rubbish offensively so my apologies, lack of emoticon on my part there.

here is a blurb from larry osterman i just found on it, he is well known in MSFT circles as a long time dev at MSFT

he explains things better

[http://blogs.msdn.com/b/larryosterman/archive/2005/06/24/432386.aspx](http://blogs.msdn.com/b/larryosterman/archive/2005/06/24/432386.aspx)

I have edited and included the link in above posts
peace

---

### Post by Khayyam on 2012-02-17
> **haqking said:**
> I didnt mean the rubbish offensively so my apologies, lack of emoticon on my part there. [H]ere is a blurb from larry osterman

That clarifies things, I wonder though why they just didn't make "SWITCHAR=" the default. It meant breaking 86-DOS and IBM-DOS's users expectations either way, and so it was an odd compromise. Switching the chars would have also standardised MS-DOS paths with URI's, which would have been a major plus for networked resources.

No offense taken ..

best ... khay

---

