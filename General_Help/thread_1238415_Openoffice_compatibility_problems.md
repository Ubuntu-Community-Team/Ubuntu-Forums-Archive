---
title: "Openoffice compatibility problems"
date: 2009-08-12
forum: General Help
---

### Post by emrys on 2009-08-12
In my job I share lots of word and excel documents with windows users and end up having compatibility issues way too often.

The .docx format is unusable and .doc a nightmare when tables, figures, formulas or any other not trivial format is involved.

In my opinion, this is the single most important problem for windows users trying ubuntu. At least, it is for me (ubuntu user since Hardy) and the people I "converted" along this years (most of them returned to Windows because of this).

I started a Ubuntu Brainstorm idea to try to bring the spotlight to this important issue: [http://brainstorm.ubuntu.com/idea/20877/]("http://brainstorm.ubuntu.com/idea/20877/")

I do think this is a more critical issue than most that keep devs busy and if we don't solve it, bug #1 will remain open.

---

### Post by tvtech on 2009-08-12
> **emrys said:**
> In my job I share lots of word and excel documents with windows users and end up having compatibility issues way too often.

The .docx format is unusable and .doc a nightmare when tables, figures, formulas or any other not trivial format is involved.

In my opinion, this is the single most important problem for windows users trying ubuntu. At least, it is for me (ubuntu user since Hardy) and the people I "converted" along this years (most of them returned to Windows because of this).

I started a Ubuntu Brainstorm idea to try to bring the spotlight to this important issue: [http://brainstorm.ubuntu.com/idea/20877/]("http://brainstorm.ubuntu.com/idea/20877/")

I do think this is a more critical issue than most that keep devs busy and if we don't solve it, bug #1 will remain open.

open office officially supports the .doc format from 2003, including basic VBA macro support.  .docX does not work fully it is a specialized format and uses microsoft proprietary nonsense.  Advanced formatting does not transfer, they are working on this for openoffice 4.0  but you should really address this issue in their forums.  While conanical supplies open office and provides security updates for the version it supplies it does not develop it, sun microsystems does. THEIR FORUMS ARE THE ONES TO ADDRESS THIS, not ubuntu brainstorm.

---

### Post by emrys on 2009-08-12
> **tvtech said:**
> open office officially supports the .doc format from 2003, including basic VBA macro support.  .docX does not work fully it is a specialized format and uses microsoft proprietary nonsense.  Advanced formatting does not transfer, they are working on this for openoffice 4.0  but you should really address this issue in their forums.  While conanical supplies open office and provides security updates for the version it supplies it does not develop it, sun microsystems does. THEIR FORUMS ARE THE ONES TO ADDRESS THIS, not ubuntu brainstorm.


As long as Canonical is devoting resources towards improving all aspects of the desktop (Gnome, KDE, Linux Kernel, etc.) and given that Openoffice is a Critical application, I think this is a perfect place to discuss how we (the community and Canonical) can improve Ubuntu and its default office application.

---

### Post by emrys on 2009-08-12
> **tvtech said:**
> open office officially supports the .doc format from 2003, including basic VBA macro support.

The .doc format is officially supported but that doesn't mean too much when it is practically unusable in strong sharing environments. I don't know if tables, forms and formulas are considered advance formatting or not, but it is a fact that there are huge compatibility problems with them.

You learn to avoid those problems not using certain formating options and so on, but that is a bad way to deal with the problem...

---

### Post by emrys on 2009-09-28
I recently used IBM Lotus Symphony and, although it has lots of problems on its own, it does a better job in terms of compatibility. At least with some documents.

---

### Post by ErikEhlert on 2009-09-28
Well, aren't there other OpenOffice programs for when you don't want the file to be saved as .doc, it contains spreadsheet information, and it will still open in Excel? I am sure OO has a spreadsheet program somewhere included.

---

### Post by emrys on 2009-09-28
> **ErikEhlert said:**
> Well, aren't there other OpenOffice programs for when you don't want the file to be saved as .doc, it contains spreadsheet information, and it will still open in Excel? I am sure OO has a spreadsheet program somewhere included.


I think you misunderstand the point made. We are talking about compatibility problems of a .doc file created with Microsoft Office and then opened with Oo (or xls, etc.). Of course Oo has Spreadsheet and others.

---

### Post by Hagar Delest on 2009-09-28
OOo 3.0.1 and 3.1.0 have a terrible bug with tables saved in .doc files. It has been fixed but still some corner cases.

Have you tried the Sun version? See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

MS will never allow anyone to make a perfect filter (they will retain some key information for sure). Else, how make customers buy their product if a free alternative does it?

You're riding the wrong horse IMHO. The real battle is on the adoption of ODF. MS has announced its support in latest version of Office but it's not really implemented so results are rather poor.

NB: why use Ubuntu resources on such issues? Better use the official version (from Sun) IMHO, less troubles and less work for the Ubuntu team who can work on other problems.

---

### Post by emrys on 2010-02-18
> **Hagar de l'Est said:**
> OOo 3.0.1 and 3.1.0 have a terrible bug with tables saved in .doc files. It has been fixed but still some corner cases.

Have you tried the Sun version? See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

MS will never allow anyone to make a perfect filter (they will retain some key information for sure). Else, how make customers buy their product if a free alternative does it?

You're riding the wrong horse IMHO. The real battle is on the adoption of ODF. MS has announced its support in latest version of Office but it's not really implemented so results are rather poor.

NB: why use Ubuntu resources on such issues? Better use the official version (from Sun) IMHO, less troubles and less work for the Ubuntu team who can work on other problems.

I don't know about that. The adoption of Oo depends on it's compatibility with Word so we are trapped in a interesting circle.

If you work in a collaborative environment, linux fails simply because of Oo. Right know, thanks to wine and Microsoft Office 2007 running in it, I can keep my Ubuntu, but sadly that's the only way, at least for me.

The compatibility problems are huge and very important. Also they are hurting a lot linux adoption. I don't know a better place to spend resources. Don't know if canonical's, sun's or who's.

---

### Post by Hagar Delest on 2010-02-18
> **emrys said:**
> The adoption of Oo depends on it's compatibility with Word
Not at all!!!

MS Office will always prevent other applications to be compatible with their products. The best proof is that even the OOXML that has been ISO-certified is not supported by MS Office! They use a customized file format with slight changes. 

The key point is not the compatibility with MS Office products, it's making the users aware of the importance of using a truly documented and open standard like ODF to insure they keep the property of their own data.

The business model of MS is rather clear: use the vendor lock-in policy to keep their market share. It just means that they're afraid of OOo and not that confident in their own products: their features may not weight enough in the balance compared to a free application. So if they can't keep the customers by providing a better application, they will use the file format to keep them.

Why MS has tolerated the spread of pirated MS Office copies around the world? To increase the user base and make their file formats de facto standards. And it worked. Now everybody think that the .doc/.xls/.ppt are the only format they should use to exchange files (even if they don't have to be modified!!).

---

### Post by emrys on 2010-02-18
> **Hagar de l'Est said:**
> 
The key point is not the compatibility with MS Office products, it's making the users aware of the importance of using a truly documented and open standard like ODF to insure they keep the property of their own data.

While I agree about MS dirty tactics, I don't think increasing people awareness is a realistic solution at all.

Call me a pragmatic but in my daily life I ran into lots of troubles if I use Oo formats. Just because other people does not want to use a "inferior" program like Oo and, as you said, MS OD compatibility is not that good. 

Also, a bunch of people I "converted" to linux go back to Windows due to problems with Oo. The problems were mainly compatibility problems with doc files (sadly used by most Spanish institutions, universities, etc.).

Damn, recently I was asked to send again a document to a government institution (using a ODT template from their website) because they did not recognized the file format.

In a nutshell. I completely agree with you about the facts but I think we have to be more pragmatic in the solution.

---

### Post by Hagar Delest on 2010-02-18
I know we are facing a massive task! But anyway, .doc format is dead. As the new format is now .docx for MS Office, the problem will arise slowly, when users will also face problems opening this file format, especially on older configurations.

I fear that being pragmatic would lead to the same situation as currently: if people see that they have a good compatibility level with MS Office formats, why bother with another one, even if it's more robust?

National bodies should have their saying to promote the use of open standards but very often, there are lobbyists around... That's what happened in France and in Europe as well for the draft about interoperability for documents.

---

### Post by emrys on 2010-02-18
> **Hagar de l'Est said:**
> I know we are facing a massive task! But anyway, .doc format is dead. As the new format is now .docx for MS Office, the problem will arise slowly, when users will also face problems opening this file format, especially on older configurations.

I fear that being pragmatic would lead to the same situation as currently: if people see that they have a good compatibility level with MS Office formats, why bother with another one, even if it's more robust?

National bodies should have their saying to promote the use of open standards but very often, there are lobbyists around... That's what happened in France and in Europe as well for the draft about interoperability for documents.

Well, If You Want Something You Never Had You Have to Do Something You Have Never Done

People already have good compatibility because they are using MS products. The solution won't come by itself. That's may opinion anyway.

If people have to choose between an all MS configuration where all works in terms of compatibility and a mixed or all linux configuration where all its a mess (again, in terms of configuration) they will keep on choosing the MS config. But, if we offer them compatibility and a good product (Oo sucks at the moment), then we have a chance.

---

### Post by Pjotr123 on 2010-02-18
Open Office does a fine job in converting Microsoft Office documents, except for elaborate and convoluted documents. My experience, anyway.

If it's not good enough for you, I suggest installing IBM Lotus Symphony from the third-party partner source (enable it in System - Administration- Software Sources). 

As someone already said in this thread, IBM Lotus Symphony seems to do an even better job in converting Microsoft Office document formats. A bit peculiar, because it's based on an older version of Open Office. But the guys at IBM have done some successful tweaking, it seems. :)

---

### Post by emrys on 2010-02-19
> **Pjotr123 said:**
> Open Office does a fine job in converting Microsoft Office documents, except for elaborate and convoluted documents. My experience, anyway.

If it's not good enough for you, I suggest installing IBM Lotus Symphony from the third-party partner source (enable it in System - Administration- Software Sources). 

As someone already said in this thread, IBM Lotus Symphony seems to do an even better job in converting Microsoft Office document formats. A bit peculiar, because it's based on an older version of Open Office. But the guys at IBM have done some successful tweaking, it seems. :)

That is, I believe, a myth. If by elaborate documents you mean a document with a centered table, you got it.

It is true that Symphony has better compatibility (not perfect by a long shot) but the program runs veeeery slow and has lots of quirks itself.

Again, we can use an inferior program with bad compatibility or a awful program with a little less bad compatibility.

Someone sharing documents with windows users out there? I can't believe that I am the only one having problems with Oo.

---

### Post by djchandler on 2010-02-19
> **emrys said:**
> Someone sharing documents with windows users out there? I can't believe that I am the only one having problems with Oo.

I helped another user not too long ago who had become a bit obsessed with the difference in the appearance of fonts between MS Office and OOo. Between the two of us we detected a somewhat slight shift in font metrics that are used when installing the "free" msttcorefonts and the newer versions actually being used. Since he was dual booting, it was a simple matter of being able to access his Windows 7 fonts and use them in Ubuntu and also therefore in OOo.

These fonts are covered by copyright, and I am by no means advocating that particular solution although it worked. Alternatively you may try getting those with whom you exchange documents to adopt usage of the better fonts available in the Public Domain or licensed under one of several free licenses. If you do a little searching, they are easy to find, such as the Larabie families of fonts. Free fonts can even be downloaded from Apple if you know where to look.

Anybody can download and use the fonts used in Ghostscript from Sourceforge for instance. Bitstream's Vera and DejaVu can be used cross platform.

I'm not sure if this will help or not, but here's the thread. Font metrics are important in preserving formatting. Just because fonts have the same name doesn't mean they are identical versions, and we could see differences in the metrics between the different versions of fonts packaged with the various incarnations of Microsoft products, even differences between Vista and Windows 7. Seems crazy to me, but that could be part of your problem.

[http://ubuntuforums.org/showthread.php?t=1371945&page=2](http://ubuntuforums.org/showthread.php?t=1371945&page=2)

---

### Post by emrys on 2010-02-19
Thanks for the info about fonts. That is a part of the problem but my main problem is sheer compatibility: tables not remembering their position, problems with pictures, tables formating compatibility, justify, margins, formulas, text frames...

I can understand that font differences may make documents look alike, but not that a doc document becomes a complete mess when opened with Oo.

---

