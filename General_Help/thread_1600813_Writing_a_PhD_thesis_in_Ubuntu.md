---
title: "Writing a PhD thesis in Ubuntu?"
date: 2010-10-19
forum: General Help
---

### Post by Willy07 on 2010-10-19
I would like to get your advice on the best way of writing a PhD thesis. 

I need to write the thesis in a word processing program and I need to organize the references. I want to do it the easiest way. 

Currentlly I have Ubuntu and I thought I needed to switch to Windows 7. But if I stay with Ubuntu, what are my best options for Word/Reference manager ? 

Will this task be any easier in Windows 7 than Ubuntu?

---

### Post by Megaptera on 2010-10-19
You could have a look at Ubuntu -based 'Uberstudent'  "UberStudent is a free, user-friendly Linux desktop distribution for learning, doing, and teaching the essential skills of academic success at the higher education and advanced secondary levels. It is supported by a free virtual learning environment. Lifelong learners, researchers, and knowledge workers of all sectors will equally benefit."

[http://uberstudent.org/](http://uberstudent.org/)

---

### Post by perspectoff on 2010-10-19
> **Megaptera said:**
> You could have a look at Ubuntu -based 'Uberstudent'  "UberStudent is a free, user-friendly Linux desktop distribution for learning, doing, and teaching the essential skills of academic success at the higher education and advanced secondary levels. It is supported by a free virtual learning environment. Lifelong learners, researchers, and knowledge workers of all sectors will equally benefit."

[http://uberstudent.org/](http://uberstudent.org/)

The Uberstudent website does not display properly in my Kubuntu Lucid / Firefox browser window, even though it is a Moodle site (and I run Moodle in Kubuntu as well). Have you tweaked the Moodle settings correctly?

What are the Reference managers that Uberstudent uses? Are they different from what is discussed at OpenOffice:

[http://bibliographic.openoffice.org/](http://bibliographic.openoffice.org/) and

[http://wiki.services.openoffice.org/wiki/Bibliographic/Software_and_Standards_Information](http://wiki.services.openoffice.org/wiki/Bibliographic/Software_and_Standards_Information)

or this Crossover/Reference Manager/OpenOffice solution

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=3141](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=3141)

 or KOffice:

[http://wiki.koffice.org/index.php?title=Bibliography](http://wiki.koffice.org/index.php?title=Bibliography)

It is true that LaTeX is the scientific standard, and I think the good tools for integration with one of the open source word processors would simplify its usage (LaTeX can be tough for a newbie).

---

### Post by sonicj on 2010-10-19
Perhaps this may be what you're looking for :
[http://jabref.sourceforge.net/](http://jabref.sourceforge.net/)

---

### Post by perspectoff on 2010-10-19
Redacted.

---

### Post by Megaptera on 2010-10-19
> **perspectoff said:**
> The Uberstudent website does not display properly in my Kubuntu Lucid / Firefox browser window, even though it is a Moodle site (and I run Moodle in Kubuntu as well). Have you tweaked the Moodle settings correctly?

What are the Reference managers that Uberstudent uses? Are they different from what is discussed at OpenOffice:

[http://bibliographic.openoffice.org/](http://bibliographic.openoffice.org/) and

[http://wiki.services.openoffice.org/wiki/Bibliographic/Software_and_Standards_Information](http://wiki.services.openoffice.org/wiki/Bibliographic/Software_and_Standards_Information)

 or KOffice:

[http://wiki.koffice.org/index.php?title=Bibliography](http://wiki.koffice.org/index.php?title=Bibliography)

 or AbiWord?
I've nothing to do with Uberstudent I just posted the link so no I did not  "tweak the moodle" - is that Certificate 18?!
Full list of apps here:
[http://www.dedoimedo.com/computers/uberstudent.html](http://www.dedoimedo.com/computers/uberstudent.html)

---

### Post by Mark Phelps on 2010-10-19
Probably would also be a good idea to check with your thesis Advisor to find out if your institution REQUIRES the thesis to be submitted in any particular file format.

Would be a problem if they required them in MS Word format and whatever tool you used, after you did a LOT of work preparing your thesis, was unable to export the results into an MS Word document.

---

### Post by perspectoff on 2010-10-19
> **Megaptera said:**
> I've nothing to do with Uberstudent I just posted the link so no I did not  "tweak the moodle" - is that Certificate 18?!
Full list of apps here:
[http://www.dedoimedo.com/computers/uberstudent.html](http://www.dedoimedo.com/computers/uberstudent.html)

Ok, I looked through it. It looks like Uberstudent uses LyX, a GUI / document manager / frontend for using LaTeX-formatted documents. LyX can be installed on any *buntu system using a Package Manager, or from the command line:

 sudo apt-get install lyx

(I think it can also be used with the above referenced open source LaTeX bibliography manager (BibTex), jabref.)

LyX has a section on its wiki for using BibTeX: [http://wiki.lyx.org/BibTeX/BibTeX](http://wiki.lyx.org/BibTeX/BibTeX)

In my Kubuntu (KDE) system, there is both jabref and kbibtex:

 sudo apt-get install kbibtex

or

 sudo apt-get install jabref

I also see that biblatex is a package that is also available through the package managers, or installed from the command line:

 sudo apt-get install biblatex

(LyX has a wiki that describes using biblatex with it, for example: [http://wiki.lyx.org/BibTeX/Biblatex](http://wiki.lyx.org/BibTeX/Biblatex) )

Other than a lot of toys, the other things that I see in Uberstudent specifically of possible benefit in research are:

Zotero (a plugin for Firefox that allows you to download references and content found in online sources)

DocFetcher (a tool to search all the documents on your computer, available as a .deb package from sourceforge, similar to Strigi and Beagle)

Mendeley (an online bibliography manager, client is included in Uberstudent)

CiteULike (a free online bibliography manager, client is included in Uberstudent)

---

### Post by perspectoff on 2010-10-19
> **megaptera said:**
>  i did not  "tweak the moodle" - is that certificate 18?!


rofl!

---

### Post by Simian Man on 2010-10-19
If you are more technical, LaTeX combined with Bibtex is a great way to write things like this.  I would be willing to bet that your school even provides a LaTeX template which would mean you'd have little formatting work at all.

If LaTeX is too daunting, then Windows is your best bet in my opinion.

---

### Post by TBABill on 2010-10-19
I agree with several above comments. Most schools have standards for both software and submissions (file types). Until you know what those requirements are you may be short-changing yourself. This is for a PhD so you want it as formal and perfect as possible. If they will be reading it, for example, in MS Word, then that should be the tool to write it in for best formatting results. OpenOffice, for example, is great for many things, but for something so crucial it is best to make sure it is adequate for your needs (or whatever other program you choose).

---

### Post by deserthowler on 2010-10-19
My friend recently got his PhD.  He is an old-time Linux user and used LaTeX.  He used it for all of his papers through his Master Degree as well.  He said his profs often commented on the quality of the output.

I would recommend Lyx though as LaTeX has one hell of a learning curve.

Earl

---

### Post by perspectoff on 2010-10-19
> **sonicj said:**
> Perhaps this may be what you're looking for :
[http://jabref.sourceforge.net/](http://jabref.sourceforge.net/)

Can be installed through a Package Manager or from the command-line:

 sudo apt-get install jabref

---

### Post by bobterri on 2010-10-19
Five years ago (Maybe things have changed since.) I wrote my dissertation for my doctorate.  Unfortunately, I had to use Microsoft Word with Endnotes.  Why?  As has been mentioned in this thread, the educational institution I attended required a certain writing style and Endnotes provided templates, footnotes, etc. in that style.  Sorry I can't help more.

Perhaps Word and Endnotes will work in Wine?

---

### Post by blueridgedog on 2010-10-19
Last Linux using friend of mine that wrote a thesis used LaTeX.

---

### Post by hawthornso23 on 2010-10-19
I strongly recommend LaTeX. I did my PhD that way. However LaTeX is completely dominant in mathematics. Things may be different in your subject area. Your thesis advisor should be advising you on these things.

I also suggest that you check out the main journals in your subject and find out their preferred formats for submitted papers. It will make life easier for you if you spend your time mastering the authoring tool that will be of most use to you in your future career, and will also make it easier to calve papers from your PhD and submit them for publication. 

Don't focus so much on the PhD that you forget to think about what comes afterwards. Good Luck.

---

### Post by Anutesyn on 2010-10-19
I know a couple of people who've done their PhD thesis and their MA works using LaTeX, and continued to use it through their professional career. I also know a guys who uses Windows Word. Basically no right or wrong. I have to agree with the above posts, check with your advisor/mentor (or what you call it) and check if there's any formats that they prefer. 

If you're going with the LaTeX, I suggest going to some kind of class or really dig into tutorials before sitting down to write because it can be very hard trying to work for the first time in that system and expect results. 

Basically since you said the easiest way I'd go with [insert word processor here], that will probably be "easiest". I wish you good luck with what ever you chose.

---

### Post by oaxacamatt1 on 2010-10-19
I feel for you man... Writing thesis is a drag, Remember, backup, backup, backup.  Don't feel you have to learn something new to write the thesis.  Just get it over with the least amount of pain possible.  If you know Word use Word.  This is NOT the time to reinvent the wheel.  Don't draw out the writing process AND make it more difficult on top of it all.
That is simply my 2 cents,
M

---

### Post by Willy07 on 2010-10-19
Thanks for your suggestions. I am in accounting, so no math for me.

Perhaps I should start with Openoffice and Zotero and see where it leads me.

---

### Post by Megaptera on 2010-10-20
Good luck and I know you'll plan to, but do make sure you make frequent and regular backups of your work in several locations ... just in case!!!

---

### Post by seanbw on 2010-10-29
> **Willy07 said:**
> Thanks for your suggestions. I am in accounting, so no math for me.

Perhaps I should start with Openoffice and Zotero and see where it leads me.

I am trying to write a PhD proposal and do not use Windows. I wrote it in OpenOffice and used endnotes. However I discovered a problem I think you should be aware of. each time I saved in .doc format from .odt and then edited the document, the end notes seemed to mess up with no 1 and 2 endnote going to the last page, the header with references as the title disappears and no matter what I do, I can't get rid of it.
So now I am looking to use a manager for my references and not leave it to the wordprocessor.
My advise is to research the bibliography tool independent of your writing needs. I am researching Mendeley which is why I got to this post.
My 2cents. Wish you luck. My proposed PhD is in Accounting as well.

---

### Post by seanbw on 2010-10-29
There is also an extension in oOo that may be useful. It us called AuthorSupportTool by AST and it createsa separate list of your references whilst it attaches it to your paper. I  was going to try Mendeley but the permission request embedded in their EULA basically takes away from me any choice as to what I share. 
I am a bit worried about that. Apparently once I install it, It can share upload to their servers what is on my registered folders. I will read the blurb a bit more but I instinctively didn't like it.
[http://extensions.services.openoffice.org/project/AST](http://extensions.services.openoffice.org/project/AST)

---

### Post by martinofmoscow on 2010-10-29
I'm a Ph.D student and worked exclusively on Mint/Ubuntu until recently (sadly had to go back to Windows in order to use NVIVO - there is no good qualitative analysis software for Linux).

I find Zotero is by far the best bibliographic tool out there, and it's a Firefox plugin so works cross-platform. Better still - you can synchronise all your references/notes/PDFs with the online service so they're available on any of your PCs - Linux or Windows. There are accompanying plugins for Word and OpenOffice.

Once you get over the initial weirdness of using a Firefox plugin for your referencing, Zotero is actually a better tool than any out there, including Endnote, and did I mention it's free?!

Highly recommend Zotero.

---

### Post by seanbw on 2010-10-29
OK - I give up. I compared the existing reference managers and Mendeley was the most flexible with the ability to cite as I write. I was hoping Bibus could that but it could not. I am now installing it.

---

