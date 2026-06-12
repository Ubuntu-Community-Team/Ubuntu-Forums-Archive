---
title: "How-To: XSLT 2.0 xsl:result-document"
date: 2009-08-12
forum: General Help
---

### Post by jjalocha on 2009-08-12
In this post, I will show how to get XSLT 2.0 to work under Ubuntu. In particular, I will show the useful and often required [xsl:result-document]("http://www.w3.org/TR/xslt20/#element-result-document") instruction.

I am posting this as an answer to another thread in this forum ([thread #356214]("http://ubuntuforums.org/showthread.php?t=356214")), that showed up constantly first on all my Google searches. But that thread is now closed, incomplete, and sometimes wrong.

The instructions here are the results of many days of struggle with different software. I hope, this may be of help to someone else. Any comments or corrections are really appreciated.


[SIZE="3"]Saxon (from Ubuntu repository)[/SIZE]
====================

[Saxon]("http://saxon.sourceforge.net/") is the only free XSLT 2.0 processor that I am aware of. It was written by Michael Kay, the editor of the XSLT 2.0 specification. Thus, you can expect it to be very truthful to the specification.

Ubuntu ships two different versions of Saxon. The older 'libsaxon-java', provides [XSLT 1.0]("http://www.w3.org/TR/xslt") and [XPath 1.0]("http://www.w3.org/TR/xpath"). We will install the newer 'libsaxonb-java' package, which provides [basic conformance]("http://www.w3.org/TR/xslt20/#basic-conformance") to [XSLT 2.0]("http://www.w3.org/TR/xslt20/"), [XPath 2.0]("http://www.w3.org/TR/xpath20/"), and [XQuery 1.0]("http://www.w3.org/TR/xquery/").

The installation is straightforward. This might automatically install a lot of required dependencies, because it is written in Java:
```

$ sudo aptitude update
$ sudo aptitude install libsaxonb-java

```

Now, you can process an XML file with XSLT 2.0 from the command line:
```

$ saxonb-xslt -ext:on -o:out/dummy.xml -xsl:example.xsl -s:example.xml

```

**saxonb-xslt**
This handy script (/usr/bin/saxonb-xslt) provided by the debian packagers invokes the Java class file behind the scenes.

**-ext:on**
The Debian (thus Ubuntu) version of Saxon comes with the [extension functions disabled by default]("https://bugs.launchpad.net/ubuntu/+source/saxonb/+bug/412517"). In order to process xsl:result-document, we need to enable these extension functions.

**-o:out/dummy.xml**
Even if we are using the xsl:result-document to generate output, the processor requires an output file. In our case, It will output an empty XML file. In this example, 'out' is the directory where all the other files will be written by xsl:result-document.

**-xsl:example.xsl**
```

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="2.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
   <xsl:template match="value">
      <xsl:result-document href="{.}">
         <test>
            <xsl:value-of select="."/>
         </test>
      </xsl:result-document>
   </xsl:template>
</xsl:stylesheet>

```

**-s:example.xml**
```

<?xml version='1.0' encoding='UTF-8'?>
<data>
   <value>A1</value>
   <value>B1</value>
   <value>C1</value>
   <value>A2</value>
   <value>B2</value>
   <value>C2</value>
</data>

```

[SIZE="3"]Saxon (from sourceforge)[/SIZE]
====================

You might also want to use one of the [other versions]("http://saxon.sourceforge.net/") of Saxon provided by Saxonica that are more complete but commercial, or the official [sourceforge version]("https://sourceforge.net/projects/saxon/files/"), which is usually more up-to-date than the versions in the Ubuntu repositories.

After unpacking the archive, you should put the '.jar' file in some meaningful place. In our example, we'll use '/usr/local/share/java/saxon9he.jar'

Since the official versions don't distribute a script, you must invoke Saxon through the Java runtime:

```

$ java -classpath /usr/local/share/java/saxon9he.jar net.sf.saxon.Transform -o:out/dummy.xml -xsl:example.xsl -s:example.xml

```


[SIZE="3"]xsltproc[/SIZE]
====================

If you don't want or can't use Saxon for some reason, you still can use [xsltproc]("http://xmlsoft.org/XSLT/xsltproc2.html"), which is probably installed in Ubuntu and Xubuntu by default. This processor supports XSLT 1.0 only, but since it is written in C, it is much faster than Saxon, in my experience.

In this case, you will need a special XSLT stylesheet. Instead of using the XSLT 2.0 only xsl:result-document instruction, you can use the [saxon:output]("http://saxon.sourceforge.net/saxon6.5.3/extensions.html#saxon:output") instruction, which is implemented by xsltproc.

```

$ xsltproc --output out/dummy.xml example-sax.xsl example.xml

```

Note, that this extension only works for XML output, as xsltproc [can't handle text output]("http://bugzilla.gnome.org/show_bug.cgi?id=591449") in this mode.

Note: You could use the [xsl:fallback]("http://www.w3.org/TR/xslt#fallback") instruction to create one single stylesheet that [implements both methods]("http://books.google.com/books?id=ioeNfpAj58IC&pg=PA217&dq=xslt+fallback+saxon:output&ei=_uiCSuCgLIXiywStmLW4Cg").

**example-sax.xsl**
```

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
      xmlns:saxon="http://icl.com/saxon"
      extension-element-prefixes="saxon">
   <xsl:template match="value">
      <saxon:output file="{.}">
         <test>
            <xsl:value-of select="."/>
         </test>
      </saxon:output>
   </xsl:template>
</xsl:stylesheet>

```

---

### Post by mlissner on 2009-08-21
Haven't tried this yet, but thanks for the detailed instructions. They look great.

---

### Post by jjalocha on 2009-08-22
Thanks! Good luck with your tests, and tell me if I need to change/improve something.

---

