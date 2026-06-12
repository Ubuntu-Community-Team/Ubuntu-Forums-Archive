---
title: "Need help opening Writer file"
date: 2012-02-14
forum: General Help
---

### Post by DaveFlurry on 2012-02-14
I have been adding to an OpenOffice Writer file for three months without any problem, until yesterday 

when it would not come up on the screen, using the usual procedure of Places > Documents > file. The 

operating system is Ubuntu 10.04.1, and the machine is Dell INSP DT 620S. 

As an experiment, I created a new file in Writer, and this opened without any problem; only the older files 

refuse to open. 

I'd be very grateful if anyone could help me unstick this file. I'm like an Ancient Mariner stuck in the ice, 

can't go forward, or backward, or anywhere.

thanks,

DaveFlurry

---

### Post by dragonfly41 on 2012-02-14
Do you have a *.bak file? 

...

This article gives one possible cause .. is the file in ext4 formatted partition in ubuntu?

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=36027](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=36027)

A trial of these (Windows only .. do you have access to Windows) recovery programs might tell you if the file can be recovered

[http://www.systoolsgroup.com/open-office-writer-recovery.html](http://www.systoolsgroup.com/open-office-writer-recovery.html)

[http://www.nucleustechnologies.com/writer-recovery.html](http://www.nucleustechnologies.com/writer-recovery.html)


If you do recover your file I would create a script to keep date stamped backup files.


[EDIT]

I found this thread which might help you (and avoid paying out for a recovery utility) ..

[http://ubuntuforums.org/showthread.php?p=9814022](http://ubuntuforums.org/showthread.php?p=9814022)

this suggests trying scalpel for forensic analysis of corrupt odt file
```

sudo apt-get install scalpel

```

scalpel then needs to be setup to find odt files

add odt files to end of /etc/scalpel/scalpel.conf

you might find earlier deleted odt files.

---

### Post by dragonfly41 on 2012-02-15
Here is a simple test I've tried ..

Firstly to view XML files ..

sudo apt-get install xmlcopyeditor

(or install via Synaptics Package Manager)

set xmlcopyeditor options to wrap text for easier viewing

....

in your *,odt file

right click your corrupt *.odt file in Nautilus and open with Archive Manager

Now .. do you see several folders and files?   Or is it still corrupt?

```

Configurations2
META-INF
Thumbnails

    content.xml
    manifest.rdf
    meta.xml
    mimetype
    settings.xml
    styles.xml
```Your rawtext should be found in a tag in content.xml .. near the end of the xml file.

Save a simple test.odt file .. with content one word "test" .. and repeat to compare internal structure. 

Right click on content.xml and open with xmlcopyeditor.

You can see the single word [COLOR=Red]"test"[/COLOR] in content.xml below ...

```

<?xml version="1.0" encoding="UTF-8"?>
<office:document-content xmlns:office="urn:oasis:names:tc:opendocument:xmlns:office:1.0" xmlns:style="urn:oasis:names:tc:opendocument:xmlns:style:1.0" xmlns:text="urn:oasis:names:tc:opendocument:xmlns:text:1.0" xmlns:table="urn:oasis:names:tc:opendocument:xmlns:table:1.0" xmlns:draw="urn:oasis:names:tc:opendocument:xmlns:drawing:1.0" xmlns:fo="urn:oasis:names:tc:opendocument:xmlns:xsl-fo-compatible:1.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:meta="urn:oasis:names:tc:opendocument:xmlns:meta:1.0" xmlns:number="urn:oasis:names:tc:opendocument:xmlns:datastyle:1.0" xmlns:svg="urn:oasis:names:tc:opendocument:xmlns:svg-compatible:1.0" xmlns:chart="urn:oasis:names:tc:opendocument:xmlns:chart:1.0" xmlns:dr3d="urn:oasis:names:tc:opendocument:xmlns:dr3d:1.0" xmlns:math="http://www.w3.org/1998/Math/MathML" xmlns:form="urn:oasis:names:tc:opendocument:xmlns:form:1.0" xmlns:script="urn:oasis:names:tc:opendocument:xmlns:script:1.0" xmlns:ooo="http://openoffice.org/2004/office" xmlns:ooow="http://openoffice.org/2004/writer" xmlns:oooc="http://openoffice.org/2004/calc" xmlns:dom="http://www.w3.org/2001/xml-events" xmlns:xforms="http://www.w3.org/2002/xforms" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:rpt="http://openoffice.org/2005/report" xmlns:of="urn:oasis:names:tc:opendocument:xmlns:of:1.2" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:grddl="http://www.w3.org/2003/g/data-view#" xmlns:officeooo="http://openoffice.org/2009/office" xmlns:tableooo="http://openoffice.org/2009/table" xmlns:field="urn:openoffice:names:experimental:ooo-ms-interop:xmlns:field:1.0" xmlns:formx="urn:openoffice:names:experimental:ooxml-odf-interop:xmlns:form:1.0" xmlns:css3t="http://www.w3.org/TR/css3-text/" office:version="1.2" grddl:transformation="http://docs.oasis-open.org/office/1.2/xslt/odf2rdf.xsl"><office:scripts/><office:font-face-decls><style:font-face style:name="Lohit Hindi1" svg:font-family="&apos;Lohit Hindi&apos;"/><style:font-face style:name="Ubuntu" svg:font-family="Ubuntu"/><style:font-face style:name="DejaVu Sans" svg:font-family="&apos;DejaVu Sans&apos;" style:font-family-generic="system" style:font-pitch="variable"/><style:font-face style:name="Lohit Hindi" svg:font-family="&apos;Lohit Hindi&apos;" style:font-family-generic="system" style:font-pitch="variable"/></office:font-face-decls><office:automatic-styles><style:style style:name="P1" style:family="paragraph" style:parent-style-name="Standard"><style:text-properties officeooo:paragraph-rsid="0001b5cf"/></style:style><style:style style:name="T1" style:family="text"><style:text-properties officeooo:rsid="0001b5cf"/></style:style></office:automatic-styles><office:body><office:text><text:sequence-decls><text:sequence-decl text:display-outline-level="0" text:name="Illustration"/><text:sequence-decl text:display-outline-level="0" text:name="Table"/><text:sequence-decl text:display-outline-level="0" text:name="Text"/><text:sequence-decl text:display-outline-level="0" text:name="Drawing"/></text:sequence-decls><text:p text:style-name="P1"><text:span text:style-name="T1">[COLOR=Red]test[/COLOR]</text:span></text:p></office:text></office:body></office:document-content>


```

---

