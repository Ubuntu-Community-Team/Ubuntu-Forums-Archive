---
title: "MS Office installation fails"
date: 2006-04-29
forum: General Help
---

### Post by 1002285 on 2006-04-29
If MS Office XP installation with Crossover (demo) fails and says sth like "can't go on, because installation source is corrupted" - what could this mean?
I don't think it has to do with the hidden files on cd - Crossover fixed this, I think.
I'm trying to install from the hard drive.

I really need MS Office at the moment, but it seems that it won't work here.

Thanks.

---

### Post by olsonar on 2006-04-29
Office has never worked well in wine/crossover. Use openoffice instead. If you absolutly must use office, try installing windows in an emulator like QEMU or VMWare.

---

### Post by garner_nc on 2006-04-29
The only thing Open Office lacks is Access like database support. For presentations, spreadsheets, and word processing itshould work fine. 

   Is there something MS Office provides that maybe we're missing? Let us know! 

All the Best,
Doug White

---

### Post by 1002285 on 2006-04-29
Yes, there is something that MS Office provides and that OpenOffice cannot understand correctly.
I have an MS Word document where every paragraph is numbered and several references are made inside the text to paragraphs on which you can click and get to the referenced paragraph. OpenOffice looses most of the paragraph numbers with this file and the references don't work.
My option - but not a good one - might be to make the translation in OpenOffice and later spend another couple of hours on another computer fixing this error.
I don't know at the moment ...
Thanks for trying though

---

### Post by olsonar on 2006-04-29
yeah, I've seen that knid of formatting error with .doc files in openoffice. Abiword seems to keep .doc formatting pretty well, so you might want to give it a try.

---

### Post by morbidlinux on 2006-04-29
just use the good ol' openoffice.
it's basically the free replacement to the microsux office

---

### Post by ZylGadis on 2006-04-29
Exactly. The fact that it does not understand .doc correctly isn't really openoffice's fault - if Microsoft open it completely, people will be able to understand it.
Openoffice has a database, it simply works in a different way from the MS thing. Openoffice allows cross-referencing and linking both within a document and among different documents; again, the way is very different (and, in my opinion, much more intelligent) than the MS thing.
You'd best switch completely to Openoffice and drop MS in the dirt where it belongs. Openoffice has all kinds of cool features that not only do the job, but are really amazing: for example, if you format your documents correctly (with heading styles, paragraph styles, etc), and you export them to pdf, the pdf then automatically has an index with the headings and sub-headings :) I love open-source.

---

### Post by 1002285 on 2006-04-29
Hmm,
thanks for that AbiWord tip, I will try. That is, I did. The file did not open and AbiWord said that my version of Gnome is old - 2.12.1. Strange, I did not know that. Is it?
Update Manager does not offer me any new updates.
I just marked "gnome" in the Synaptic and am going to have it installed - will this be the newest version then?

---

### Post by 1002285 on 2006-04-29
to ZylGadis:
I believe you might be right.
But I cannot switch to OOo completely - I am a translator and get my works from Brussels, the European Union institutions. And they want them back the way they sent them.
Of course, the best thing for open-source would be, if the EU switched to open standard.
Why don't they?
But until that MS word cannot be thrown away in my line of business.

---

### Post by ZylGadis on 2006-04-29
That is understandable, and very sad indeed. Microsoft has locked in most of the world, and most of that same world doesn't really care.
My fiancee and I personally refuse to use .doc for anything, including important documents that various people require. That actually turned out to be a good thing - my fiancee found a dream job last year, and one of the reasons was that she refused to send her resume in .doc, explaining thoroughly her reasons for that. Her (then future) boss appreciated the explanation, and respected her firm  beliefs.
Anyway, never doubt that MS Office is already behind. It does things differently and in a proprietary way to prevent people from switching, but it can't compete with progress. Openoffice 1 had its issues, but Openoffice 2 is way ahead of MS Office.

---

### Post by olsonar on 2006-04-29
> The file did not open and AbiWord said that my version of Gnome is old - 2.12.1.

You could try using the 'force version' option on the 'package' menu in synaptic to install an older version of Abiword. Abiword worked perfectly on my computer, but I'm using the Dapper beta, which has Gnome 2.14.

---

### Post by garner_nc on 2006-04-29
I have  customers that run AutoCAD for their drafting package. I can't afford AutoCAD thus I use another CAD pacakge that isn't compatible with AutoCAD's NEWEST file format. When I have issues with them I usually ask them to either send me a .dxf file of save the file as an older AutoCAD file.

   I understand your situation with your customer. I'm not saying you should do this, it's just what I do.

   There's really little reason for software vendors to change file formats except to create incompatability with other systems. That's precisely why I try to stick with open source and open file format (HAIL .odf!).

    WinFS is going to be the next Microsoft file format displacing NTFS. I wonder if they're going to open it up? So many other things they could do to help the computer users of the world rather than just helping themselves.

All the Best,
Doug White

---

### Post by olsonar on 2006-04-29
Actually, The next office formats will be open. To quote microsoft:

> Office XML Formats are based on industry standard XML and ZIP technologies, support full integration by any technology provider, and are available via a royalty-free license. The Format specification will be published and made available under the same royalty-free license that exists for the Microsoft Office 2003 Reference Schemas—openly offered and available for broad industry use.

full article [here]("http://www.microsoft.com/office/preview/itpro/fileoverview.mspx")

---

### Post by ZylGadis on 2006-04-29
I will believe it only when it is released and after I see a large number of open-source knowledgeable people confirm that it is indeed open, with no catches and no "embrace and extend." Microsoft does not exactly have a trustworthy history relevant to the matter.

---

