---
title: "Arabic text not visible in pdf - evince."
date: 2009-12-22
forum: General Help
---

### Post by emigrant on 2009-12-22
hi all,
i have a pdf which have arabic and english text.
the arabic texts are not visible in evince, while the english is clear.
and both text are visisble in windows.


how to solve this problem

thank you all :)

---

### Post by sanderd17 on 2009-12-22
Have you tried Okular? Or Document Viewer? Maybe it works with one of those.

---

### Post by schmolch on 2009-12-22
Ask on the Evince Mailing-List and dont forget to mention the Version of Evince you are using.

---

### Post by emigrant on 2009-12-23
thank you very much all for replying.
> **sanderd17 said:**
> Have you tried Okular? Or Document Viewer? Maybe it works with one of those.

Is there a way to get a .deb because, im having a problem with apt-get and its not working at all.
Docuemtn Viewer=Evince right?

> **schmolch said:**
> Ask on the Evince Mailing-List and dont forget to mention the Version of Evince you are using.
thanks for the tip.
i did that.
(currently im using evince 2.26.1)

---

### Post by emigrant on 2009-12-23
also it seems i should have KDE4 installed to build or install okular. but im in gnome :(

---

### Post by StuartN on 2009-12-23
> **emigrant said:**
> i have a pdf which have arabic and english text.
the arabic texts are not visible in evince, while the english is clear.

Perhaps the arabic font is not embedded in the PDF or installed in your system, and is being substituted for a system font that does not contain arabic glyphs. You can check the document fonts by opening the file in evince and looking under File->Properties->Fonts.

As a last resort (if you need access) select all the text in evince and paste it into a document editor in which you are able to view arabic, then set the font on the newly pasted text, if it is not already visible.

---

### Post by emigrant on 2009-12-23
> **StuartN said:**
> Perhaps the arabic font is not embedded in the PDF or installed in your system, and is being substituted for a system font that does not contain arabic glyphs. You can check the document fonts by opening the file in evince and looking under File->Properties->Fonts.

As a last resort (if you need access) select all the text in evince and paste it into a document editor in which you are able to view arabic, then set the font on the newly pasted text, if it is not already visible.

thanks for your reply.
now i think the problem is with arabic fonts in the system. i can't view the arabic fonts even if opened with gimp. but the fonts are clearly visible in MS windows vista.

i opened the documetns fonts dialog. and coudlnt figure out what to do with the listed fonts. and copy pasting 'seleact all' in a doc did't help either :(

---

### Post by StuartN on 2009-12-23
> **emigrant said:**
> i can't view the arabic fonts even if opened with gimp. but the fonts are clearly visible in MS windows vista.

Do you mean that you can not see or type arabic in any application, even Open Office Write? I feel sure that arabic glyphs exist in the default installation - dejavusans is working fine for me with arabic glyphs, so any arabic text copied from a PDF file will display in this font. ttf-arabeyes is also a default font set and ttf-sil-scheherezade is also available.

Here are a couple of guides to installing a font (which means putting the font file in ~/.fonts or in /usr/share/fonts and rebuilding some index) - [http://www.wikihow.com/Install-True-Type-Fonts-on-Ubuntu](http://www.wikihow.com/Install-True-Type-Fonts-on-Ubuntu) [http://www.zolved.com/synapse/view_content/28550/How_to_Install_Fonts_on_Ubuntu](http://www.zolved.com/synapse/view_content/28550/How_to_Install_Fonts_on_Ubuntu).

You can find the fonts in your other OS by searching for *.ttf if they are truetype.

---

### Post by emigrant on 2009-12-23
hi, thank you very much for your reply,
what i mean is, some Arabic texts are visible and in some pdf files the arabic texts are not visible. i have attached two different screenshots from different pdf to demonstrate what i mean.

thank you.

---

### Post by deebocean on 2010-01-06
it may be the fonts problem! try reading this discussion at google groups:
[http://groups.google.com/group/Jolug/browse_thread/thread/b8f4e751c08c1d84?pli=1](http://groups.google.com/group/Jolug/browse_thread/thread/b8f4e751c08c1d84?pli=1)

---

### Post by IsraeliHawk on 2010-02-19
> **emigrant said:**
> what i mean is, some Arabic texts are visible and in some pdf files the arabic texts are not visible. i have attached two different screenshots from different pdf to demonstrate what i mean.

as a Hebrew, English and Arabic user, i think you should try going to System-->Admin.-->Language Support and install (by clicking 'Install/Remove languages' button) the Arabic language. it will install some helpful integration tools and might help.

also, if you have some issues with Apt-get, try installing Okular through the Ubuntu Software Center (if you have 9.10)/Add/Remove (if you have 9.04) -- even though it's for KDE. Remember - we're all still Linux -- it'll work (hey, i use gnome and it works fine for me) :popcorn:

good luck

---

### Post by sajiz on 2010-10-15
I used to have this problem, however i compiled a package of fonts that solved the problem for me!

here is the link to the package

[http://www.4shared.com/file/06-tp8Y9/Addional-arabic-fonts.html](http://www.4shared.com/file/06-tp8Y9/Addional-arabic-fonts.html)

---

### Post by Bagustrix on 2012-11-27
Hi, 
you can install the traditional Arabic font. 

Download here: [URL="http://www.ahya.org/amm/modules.php?name=Downloads&d_op=getit&lid=40"]
[/URL]
[http://www.ahya.org/amm/modules.php?name=Downloads&d_op=getit&lid=40](http://www.ahya.org/amm/modules.php?name=Downloads&d_op=getit&lid=40)
  and double click to install the font.


it works for me for the same problem.

---

### Post by wildmanne39 on 2012-11-27
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

