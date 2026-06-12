---
title: "Linux eqivalent entries"
date: 2009-11-17
forum: General Help
---

### Post by Philip Gray on 2009-11-17
Good evening are there any equivalent entries in Linux that do what the Windows DIR/P and DIR/W do?

---

### Post by SuperSonic4 on 2009-11-17
What do DIR/P and DIR/W do?

---

### Post by DeMus on 2009-11-17
> **Philip Gray said:**
> Good evening are there any equivalent entries in Linux that do what the Windows DIR/P and DIR/W do?

Dir /W = ls
Dir /P = ls | more or ls -l | more (press space for next page)

---

### Post by Philip Gray on 2009-11-17
Hi the DIR/P commands pauses a directory and file listing screen by screen. DIR on its own does not pause the display, so if there are more entries than screen lines you will not see the top entries. This is what I have found with the ls command. The DIR/W puts the response into columns.

C:\Program Files>dir/p
 Volume in drive C is Philip Inc
 Volume Serial Number is 0410-3207

 Directory of C:\Program Files

2009/11/02  17:32    <DIR>          .
2009/11/02  17:32    <DIR>          ..
2009/09/29  09:53    <DIR>          7-Zip
2009/10/30  16:35    <DIR>          Adobe
2009/10/30  16:11    <DIR>          Advanced System Optimizer
2009/09/19  19:10    <DIR>          Alawar
2009/09/19  19:10    <DIR>          Alive! Jigsaw Producer
2009/10/21  17:58    <DIR>          Apple Software Update
2009/09/19  19:10    <DIR>          Aquadelic
2009/09/19  19:10    <DIR>          Astra Jigsaw Art Edition
2009/09/19  19:10    <DIR>          Astra Jigsaw Europe Tour
2009/09/19  19:10    <DIR>          Astra Jigsaw France and UK
2009/09/19  19:11    <DIR>          Astra Jigsaw USA Edition
2009/09/19  19:11    <DIR>          Astro Gemini Software
2009/09/19  16:46    <DIR>          ASUS
2009/09/19  19:11    <DIR>          Axialis
2009/09/19  19:11    <DIR>          BigJig50
2009/10/21  17:59    <DIR>          Bonjour
2009/09/19  19:11    <DIR>          Boxer Text Editor
Press any key to continue . . .


C:\Program Files>dir/p
 Volume in drive C is Philip Inc
 Volume Serial Number is 0410-3207

Directory of C:\Program Files

[.]                          [..]
[7-Zip]                                                        [Adobe]
[Advanced System Optimizer]        [Alawar]
[Alive! Jigsaw Producer]                         [Apple Software Update]
[Aquadelic]                                                                              [Astra Jigsaw Art Edition]
[Astra Jigsaw Europe Tour]                 [Astra Jigsaw France and UK]
[Astra Jigsaw USA Edition]         [Astro Gemini Software]
[ASUS]                                    [Axialis]
[BigJig50]                                [Bonjour]
[Boxer Text Editor]                           [BreakPoint Software]
[ClocX]                                                         [Common Files]
[ComPlus Applications]                   [Cool Bananas Software]

               1 File(s)         40,960 bytes
              96 Dir(s)  28,408,242,176 bytes free

C:\Program Files>

Regards
Philip

---

### Post by Aubergines on 2009-11-17
dir /w = ls
dir /p = ls | less

or 

ls -l | less

if you want it to be listed as well as paused per screen to look like your above output

---

### Post by Philip Gray on 2009-11-17
Hi DeMus thanks a lot for yr help I really appreciate it.

Regards
Philip

---

### Post by Philip Gray on 2009-11-17
Hi Aubergines tks for yr reply. I tried ls -less and I got an error response concerning the e after the ls. I am new to linux did not know about using the | key.

Regards
Philip

---

### Post by Nostoc on 2009-11-17
ls | less      and    ls | more   will seem to do the same thing, but with "less" is a better choice.

it will be faster with large files, since it does not require the entire input stream to be read in order to work. Plus, you can rewind with less.

---

### Post by Nostoc on 2009-11-17
> **Philip Gray said:**
> Hi Aubergines tks for yr reply. I tried ls -less and I got an error response concerning the e after the ls. I am new to linux did not know about using the | key.

Regards
Philip

the | is a pipe, it basically takes the output of "ls" and send it as input into "less"

you could use less for other thing, such as reading a file. "cat" reads a file, so : 
*cat filename | less.*

The possibilities are endless!


[LIST]
[*]*ls | sort -r | less *
[LIST]
[*]will print page by page in reverse alphabetical order
[/LIST]
 
[*]*ls | wc -l*
[LIST]
[*] will give you the number of files (wc counts words, or lines with the -l flag)
[/LIST]
 
[/LIST]

---

### Post by Philip Gray on 2009-11-17
Hi Nostoc thanks for yr reply

Regards
Philip

---

### Post by Jerry N on 2009-11-17
I learn something every day!  I have been using DOS and Windows since DOS 2.0 and have never used DIR /W or DIR /P.  I have used pipes and re-direction (misdirection?) many many times though.

Jerry

---

