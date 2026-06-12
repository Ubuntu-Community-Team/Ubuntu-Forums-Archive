---
title: "more documents in recent documents list"
date: 2010-04-04
forum: General Help
---

### Post by neiljansons on 2010-04-04
I would like to know how I can increase the number of documents that are displayed in the recent documents list (Ubuntu 9.10).

One suggestion was to add an entry in ~/.gtkrc-2.0 of
[INDENT]gtk-recent-files-limit = xx[/INDENT]
where xx is the number of documents to display
That didn't appear to work even after a reboot.

I don't know what the limit is to how many files are listed in ~/.recently-used.xbel
but there were many hundreds in there.

Surely there is a way to display more of them in the list?

---

### Post by hal-u on 2010-06-24
I'd also like this facility, but haven't found a way so far.

I explored using XSLT as a workaround, but when you click on the links in the resulting html page, the file is opened within the browser, rather than with your default program for that file type:

_**~/translate.xsl**_
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

<xsl:template match="xbel">
    <html lang="en">
    <head>
    <title>Recently Used List</title>
    </head>
  <body>
  <h2>Recently Used List</h2>
    <table border="1">
      <tr bgcolor="#9acd32">
        <th>Recently used</th>
      </tr>
      <xsl:for-each select="bookmark">
      <tr>
        <td><a href="{@href}"><xsl:value-of select="@href"/></a></td>
      </tr>
      </xsl:for-each>
    </table>
  </body>
  </html>
</xsl:template>
</xsl:stylesheet>
``````

xsltproc translate.xsl ~/.recently-used.xbel > ~/recentlyused.htm

firefox ~/recentlyused.htm

```Note that you will need to install xsltproc if you don't have it already.

I hope someone finds this useful, but any contributions of further improvements to this approach are very much appreciated.

Cheers
Hal

---

### Post by Sepiraph on 2010-10-06
Bumping this, I can't (refused to anyway) believe that there is no workaround to increase this to beyond 10.

---

