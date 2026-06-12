---
title: "trying to open document of unknown format, I think is a mac word processing type"
date: 2010-03-10
forum: General Help
---

### Post by rhythmiccycle on 2010-03-10
i working with a partner on a school project, she sent me a document, with no extension

i'm using ubuntu desktop karmic, and it see the file as a archive, 

when I open it is full of xml files, and directories

when i first open the file the "archive" contains

3 folders , "_rels" "docProps" "word"
and an xml file "[content_Types].xml"

when i open that file i get this

```

<Types>
<Override PartName="/word/styles.xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.styles+xml"/>
<Override PartName="/word/webSettings.xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.webSettings+xml"/>
<Override PartName="/docProps/core.xml" ContentType="application/vnd.openxmlformats-package.core-properties+xml"/>
<Override PartName="/word/settings.xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.settings+xml"/>
<Default Extension="xml" ContentType="application/xml"/>
<Override PartName="/word/theme/theme1.xml" ContentType="application/vnd.openxmlformats-officedocument.theme+xml"/>
<Default Extension="jpeg" ContentType="image/jpeg"/>
<Override PartName="/word/document.xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.document.main+xml"/>
<Override PartName="/docProps/app.xml" ContentType="application/vnd.openxmlformats-officedocument.extended-properties+xml"/>
<Override PartName="/word/fontTable.xml" ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.fontTable+xml"/>
<Default Extension="rels" ContentType="application/vnd.openxmlformats-package.relationships+xml"/>
</Types>

```


I think this is some type of mac word processing file, I think word for mac, but i really don't know. 

I found the main content of the document in "word/document.xml" but all the text is surrounded in xml tags. I want to see the document with the formating not the tags.

Does anyone know the correct way to open this file?

---

### Post by BenAshton24 on 2010-03-10
Looks like it might be an office 2007 document based on this from microsofts website:
> The Office Open XML Formats are based on XML and ZIP archive technologies. The new file format in Microsoft Office Word 2007 divides the file into document parts, each of which defines a part of the overall contents of the file. You can easily create, change, add, or delete data in a Word 2007 file programmatically or manually.

Have you tried opening it with OpenOffice writer, maybe try renaming it to a .docx?

---

### Post by rhythmiccycle on 2010-03-10
adding docx worked!!!!

thanks alot!

I tried adding doc before i made the thread, but that didn't work. I never thought of using docx

---

