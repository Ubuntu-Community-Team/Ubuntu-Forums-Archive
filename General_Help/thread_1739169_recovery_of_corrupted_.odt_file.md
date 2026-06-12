---
title: "recovery of corrupted .odt file"
date: 2011-04-25
forum: General Help
---

### Post by Kopasakis on 2011-04-25
its about the end of the semster and about a week ago i go to open up my civil procedure notes and bam the whole thing is corrupted, 99 pages of notes gone, i had backed up all the notes from last semester so i have about 35 of the 99 pages, unfortunately its this semesters stuff thats gone, so can anyone give detailed steps on how to recover a damaged .odt file when i click on it it gives me the option to select the ascii option to open it in, when you click western its about 966 pgs of 

```
                                  ÿ#Q4#xÑj    &#9573;&#9474;&#9608;F&#9557;:6#Ü&#9618;&#8801;R~&#9554;»&#9555;~é&#9576;&#9532;HdrZ#î{&#8976;&#9561;CÇ&#9604;&#9556;ü#Ä&#9570;pa#>#&#9569;)&#8804;&#8745;Ggií&#9557;#&#8976;o«{#±¡RÖG&#9488;ºF#E¼#~&#9580;/\æ>xÆ&#964;1PL\ò 
```

---

### Post by Karlchen on 2011-04-25
Hello, Kopasakis.

.ODT files are in fact .ZIP archives. I.e. it is possible to open and inspect their content using any archive programme that can handle .ZIP files.
The text which you type is saved in a file named content.xml. This file is stored in the root folder of the .ODT zip-file.

I created an .ODT file with the help of Open Office 3.2 named doc1.odt. Next I started removing parts of the files and folders which Open Office adds around the content.xml. It turnt out to be amazingly hard to corrupt the .ODT file to such a degree that Open Office refused to even open the file.

In the end only the content.xml was left in the .ODT container. Only at this stage, Open Office refused to open the file, offered to repair it and failed. Great. Just what I needed. :)

Next a new empty Open Office document was created, a short line of random characters added and the document saved as doc2.odt.

With the help of the zip-archiver the content.xml file was transferred from doc1.odt into doc2.odt.

Open Office opened doc2.odt without problems. All the text was there. Only any imbedded objects like images were gone.

_Conclusion:_

You should use a ZIP-archiver to inspect the corrupt .ODT file. Let us name it Semester2.odt.
In case the content.xml file is still present and not empty, chances are not absolutely bad to recover at least all of your text.
In this case, create a copy of your backup .ODT file. Let us name the copy Semester1.odt.
Using the ZIP-archive programme, copy the content.xml file from Semester2.odt into Semester1.odt.
Try to open Semester1.odt in Open Office.
If you are lucky, most of your work has been recovered. :)
In case the content.xml itself is corrupt, well, bad luck. :cry:

[U]Disclaimer:
[/U]
No warranty is given that what worked for me will work in your case as well. It all depends on which components of your .ODT file are missing or corrupted.

[U]Lesson to be learnt for the future:
[/U]
Do not just create a single backup copy of your files at the end of a semester. Create backup copies on a daily basis. Do not rely on having one single backup. Keep at minimum 3 backup copy generations, today - yesterday - the day before. Make sure your backup copies can be opened.

Creating backups regularly is little hassle, much less hassle than you will have in case you lose half a year's hard work.

HTH,
Karl

---

