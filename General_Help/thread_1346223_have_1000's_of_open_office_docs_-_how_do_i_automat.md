---
title: "have 1000's of open office docs - how do i automatically change font for all?"
date: 2009-12-04
forum: General Help
---

### Post by daaussie on 2009-12-04
I have 1000's of open office docs - how do i automatically change font for all?

I don't want to have to go through each document and change the font manually.....

Thanks

---

### Post by jegerjensen on 2009-12-04
The odt files are actually zipfiles, containing xml-files with the document data.  So by unzipping, and studying the xml-files you may be able to locate the setting for the font.  Or you could check the specification:

[http://standards.iso.org/ittf/PubliclyAvailableStandards/c043485_ISO_IEC_26300_2006(E).zip]("http://standards.iso.org/ittf/PubliclyAvailableStandards/c043485_ISO_IEC_26300_2006(E).zip")

If you find out which setting you need to change, it should be fairly easy to create a script for processing your files... 

This is a cool project :)

---

### Post by LuisGMarine on 2009-12-04
I know this is going to be a cool project.  The funniest thing is that when I saw it I went around looking and came across the xml files that the .odt files have within them.  I was able to at least locate the line that could contain the settings for the font.  If you open up your content.xml file, line 4 of the code should be the following.

```
<style:font-face style:name="Nimbus Roman No9 L" svg:font-family="'Nimbus Roman No9 L'" style:font-family-generic="roman" style:font-pitch="variable"/>
```

That says my text is pretty much "New Times Roman."  My first step would be to find out the same output of this code using the font you want to use on all my documents.  

Then I would copy that line of code and learn some scripting or something to auto replace that line of code with your "modified" line to every file in a folder.  That would be the hardest part, but I'm sure it is doable. 

Good Luck =):KS

---

### Post by daaussie on 2009-12-04
thanks, but some of my docs are** .odt**, and some are **.doc**

i am also looking for a standard easy to read font that comes from Open Office, 

**Anyone use one?**

Liberation Serif is the best ..& FreeSerif is a little blurier when PDFing

i also noticed that when I PDF, these fonts drastically reduce CUPS-PDF size from 480kb to about 60-70kb. 
**Why is that?**

---

### Post by jegerjensen on 2009-12-04
These guys are discussing how to turn lots of .doc files into .odt

[http://www.linuxquestions.org/questions/linux-software-2/automatic-conversion-.doc-to-.odt-several-files-410157/]("http://www.linuxquestions.org/questions/linux-software-2/automatic-conversion-.doc-to-.odt-several-files-410157/")

---

