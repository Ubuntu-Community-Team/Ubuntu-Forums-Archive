---
title: "PDF note taking and Zotero"
date: 2011-02-28
forum: General Help
---

### Post by d!srupt!on on 2011-02-28
So, I read a lot of PDFs and I would like to be able to take notes on it and export as a pdf so it can be read by other PDF viewers. I've read a few older posts about this and xournal sounded like a good option. I've tried whytboard a little and didn't really seem like what I wanted. 

I also like zotero for research stuff and the note taking they have for webpage SS and documents is GREAT but I haven't been able to get pdf to work for note taking or maybe it isn't implemented yet? If there was a way to make Zotero notes to work with pdf that would be perfect!

Also, its been a few years since the last pdf notes post that I could find, what are people using these days? any noteworthy programs?

---

### Post by adam.smith on 2011-02-28
Zotero doesn't have pdf annotation. One thing to have a look at is the brand new libertexto tool: [www.libertexto.org](www.libertexto.org)
The other alternatives for pdf annotation are okular (which I don't like much) or running pdfXchange through wine (which works quite well, though it's non-open freemium software).

---

### Post by SaintDanBert on 2011-02-28
I import PDF into XOURNAL and make my notes.
I then print to PDF and my scribbles appear in the output.
I use Zotero to record my webliography as I go.

Hope that this helps,
~~~ 0;-Dan

---

### Post by d!srupt!on on 2011-03-01
alright I'm gonna check xournal out. Are there any firefox add-ons that could do pdf annotations?

---

### Post by nathan28 on 2011-03-12
> **SaintDanBert said:**
> I import PDF into XOURNAL and make my notes.
I then print to PDF and my scribbles appear in the output.
I use Zotero to record my webliography as I go.

Hope that this helps,
~~~ 0;-Dan


I annotate in Mendeley. It is not ideal b/c I cannot share the annotations.

[size="1"]IDK how you fanboys can stand using it. I can only guess that I am the only non-hard-science academic--you know, "reading" means more than one page--in the world using linux. Worse is when you all start sayng "import into OOO then export as PDF". This is kind of like having a library book and someone saying "you can't read from it, you have to make a low-res scan, print the scan, then re-scan that hard copy". NOT ALL FOSS USERS ARE GEEKS OR CODE NINJAS.[/rant][/SIZE]

If Okular's devs ever decided to improve the annotation abilities it will be close to ideal except for its bloated K UI.

Meanwhile, the Spanish gov't is developing Libertexto, an eVince branch / Firefox plugin to allow annotation across multiple doc formats. Probably worth trying. I need to learn Spanish anyway. Communism FTW.

[URL="http://blogs.igalia.com/eocanha/?p=221"]
http://blogs.igalia.com/eocanha/?p=221[/URL]

---

### Post by SaintDanBert on 2011-03-13
I have used 'xournal' as follows:

1. attended an academic colloquia
2. most "handouts" were online as PDF. A few were DOC or PPT. (sigh)
3. gathered a pile of PDF's each evening
4. opened a session's PDF with xournal; made digital ink and typed notes in the margins or where ever on the document.
5. xournal gave me a choice:
5.a  save the document as a xournal file
5.b  save the document as PDF
6. I chose PDF in most cases
7. colleagues would ask for my notes, I could then give them the annotated PDF any way that they could accept it.
8. I could re-visit any PDF ad lib to add follow-on comments
9. I could get PDF's from colleagues and make my notes there, too.

Sadly, the linux 'xournal' and the windows 'journal' do not share a file format.

Cheers,
~~~ 0;-Dan

PS/  I agree that Okular would be swell with better annotation features and less UI bloat.
PPS/ There are other PDF editor tools that are too geekish for routine use.

---

### Post by jankyHellface on 2011-03-20
This is where there is a big gaping hole in software options for Linux. I have been a student using linux for years and my method includes: Zotero + PDF Xchange viewer in wine + keepnote for note-taking. (which imo, xchange viewer is the best PDF reader for annotating on any major platform) As mentioned before, libertexto looks like it will be something that will replace xchange viewer for me in the near future. They just need to update the plug-in for firefox 4. It would also be nice if they could somehow integrate it with zotero to take over zotero's built-in annotation management.

So yeah, there really isn't a direct way (that I've found) that allows you to integrate your annotation of PDFs in zotero. One thing I've been trying lately is to pop out the zotero notes window and have it alongside the PDF as I read it. Then, I just write down my annotations as notes. For me, this is almost better than annotating because it allows you to collect reports of your notes and print them out. (another thing that libertexto looks to excel at)

---

### Post by adam.smith on 2011-03-21
> **jankyHellface said:**
> 
So yeah, there really isn't a direct way (that I've found) that allows you to integrate your annotation of PDFs in zotero. 
I'm note quite sure what you're referring to - but you're aware that if you open pdfs from within Zotero with pdfXchange, then annotate and save them thy annotations will be saved, right? That's as good as it gets - at this point - on any other platform, either.

I think libertexto has major potential, but right now feels more like a 0.1 than a 1.0 tool - you can't even save the annotations to the file, there is no save button etc. Zotero devs are aware of it though and looking for an alternative annotation tool anyway - the old one is not maintained anymore.

---

### Post by jankyHellface on 2011-03-21
> **adam.smith said:**
> I'm note quite sure what you're referring to - but you're aware that if you open pdfs from within Zotero with pdfXchange, then annotate and save them thy annotations will be saved, right? 

I think you misunderstood what I was saying. If you make annotations using pdf xchange from within zotero, those annotations will not be available in zotero itself. So yes, while you are able to make annotations by opening a separate program, you aren't able to use those annotations from within zotero.

As you're very active over in the zotero forums, you might have a better idea for alternative ways to deal with this. (one, that as a newish user, I may not be aware of)

---

### Post by adam.smith on 2011-03-21
> **jankyHellface said:**
> I think you misunderstood what I was saying. If you make annotations using pdf xchange from within zotero, those annotations will not be available in zotero itself. So yes, while you are able to make annotations by opening a separate program, you aren't able to use those annotations from within zotero.
well, I wasn't quite sure if I understood you correctly. You're right that not possible, but while that's certainly a limitation, it doesn't have anything to do with linux - you don't have that type of access on any other platform either (at least not with Zotero) - and I was probably confused by the fact that you referred to this as "a gaping hole in linux".

I'm not sure where Mendeley is wrt pdf annotations - they're certainly closer to tying pdf annotation into the lit management software, but they licensed proprietary software for their pdf viewer annotator if I understand correctly. In any case, if you don't mind proprietary software, it's available for linux.

The two other examples of tight integration I can think of are qiqqa and papers - both run only on one platform (which I think is completely unacceptable to start with) and have a whole host of other issues - qiqqa can't do citation management at all and papers2 is apparently super buggy and unreliable.

---

### Post by rent0n on 2011-03-21
No seriously, I'm surprised this discussion is still going on! :)

[Mendeley]("http://www.mendeley.com") is the answer: Papers collection and organization + PDF highlighting and annotation + Integration with Firefox for importing articles + Integration with Openoffice for bibliography/references management. 

What else?

---

### Post by jankyHellface on 2011-03-21
> **adam.smith said:**
> well, I wasn't quite sure if I understood you correctly. You're right that not possible, but while that's certainly a limitation, it doesn't have anything to do with linux - you don't have that type of access on any other platform either (at least not with Zotero) - and I was probably confused by the fact that you referred to this as "a gaping hole in linux".

ah, yeah. Sorry about that. I was actually saying 2 things there. (I realize it wasn't that clear)

---

### Post by Svictor on 2011-07-04
> **rent0n said:**
> No seriously, I'm surprised this discussion is still going on! :)

[Mendeley]("http://www.mendeley.com") is the answer: Papers collection and organization + PDF highlighting and annotation + Integration with Firefox for importing articles + Integration with Openoffice for bibliography/references management. 

What else?

As long as Mendeley is closed source, the library you build with it is dependent on their commercial choices and the success of their business model. One of the big issues in academic uses of internet is long-term reliability. Considering the hours I spend building up a proper digital library, Mendeley seems too much of gambling in this respect (at least for me).

Still looking for a pdf annotator though (real annotations, not drawings on top of pdf background like xournal or okular). At the moment I use pdf-xchange-viewer through wine, but I wish there was a more straightforward solution in linux.

---

### Post by orduek on 2012-06-11
Still now change.
It is sad that Linux community has no real PDF annotator yet.
I really want to stay on Zotero. I also use pdf-x-change with wine but I'm waiting for a native linux pdf annotator.
Who uses Mendeley? did someone immigrated from Zotero to Mendeley?

---

