---
title: "OpenOffice won't export HTML ??"
date: 2010-05-08
forum: General Help
---

### Post by marksmarks on 2010-05-08
Lucid clean install
Removed Open Java
Installed  Sun JRE 1.6.0-20
------------------
Happened to notice that OpenOffice 3.2 in Lucid won't export writer document as HTML.

I was able to export to HTML in the previous UBUNTU version.
--------------------

OpenOffice fails with error message;

“Error saving the document
 Write error
 The file could not be written”
-------------

 Permission problem in Lucid?
 Do I need to install more Java (SDK or something?)

  Thanks,

Not a deal breaker at this point.

---

### Post by WorMzy on 2010-05-08
It works fine for me. Where are you trying to save to?

---

### Post by marksmarks on 2010-05-08
Tried to save to my home directory.  Then tried to save to my desktop. 

Since I now know it should work (thanks), I'll keep playing around here.  

Must be something I'm doing or I've configured wrong.

(It exports to PDF OK, just not to HTML)

---

### Post by ramjet_1953 on 2010-05-08
Having exactly the same problem here

Regards,
Roger

---

### Post by WorMzy on 2010-05-08
Here's a list of packages I have installed that relate (in some way or another) to Java. Maybe it can help you guys see if you're missing something vital

[[img]http://www.ubuntu-pics.de/thumb/58971/synaptic_package_manager__012_vdERn6.png[/img]](http://www.ubuntu-pics.de/bild/58971/synaptic_package_manager__012_vdERn6.png)

---

### Post by marksmarks on 2010-05-08
Solved...


I can save as HTML!!


(I guess that's what I had done in the previous Ubuntu version)

--> File - Save As - File Type - HTML

That's all I need.



I was overlooking that pesky "X" in front of the HTML on the Export option. (Obviously I don't know what "X"html is.)



I'll ignore the &#8220;Export...&#8221; function for now.

--> File &#8211; Export... - File Type &#8211; XHTML; HTML, XHTML






.

---

### Post by Dave Mallisk on 2010-08-21
Hi all! ):P You need to overwrite the existing OpenOffice.org suite. This affects no existing documents. In Ubuntu 10.4, do the following:

[LIST=1]
[*]Go to the **Ubuntu Software Center**.
[*]Type **office** in the search field.
[*]Scroll to and select **OpenOffice.org Office Suite**.
[*]Click **Install** to display the *Authenticate* window.
[*]Type your password, and then click **Authenticate** to close its window.
[*]Click **Install** to overwrite the original Office Suite.
[/LIST]
In addition to letting you export XHTML files, your newly-installed Office Suite also lets  you check grammar after you have installed the LanguageTool extension.

For more information, please see my Associated Content document, [How to Repair OpenOffice.org On Ubuntu 10.4]("http://www.associatedcontent.com/article/5715910/how_to_repair_openofficeorg_on_ubuntu.html?cat=15").

---

### Post by deserthowler on 2010-08-21
> **marksmarks said:**
> Solved...


I was overlooking that pesky "X" in front of the HTML on the Export option. (Obviously I don't know what "X"html is.)


I'll ignore the “Export...” function for now.

--> File – Export... - File Type – XHTML; HTML, XHTML

.

It is just a more structured form of HTML for all practical purposes.

Earl

---

### Post by calvinwels on 2011-02-20
I too was having the same problem with exporting the more structured html from an open office word document but installed the "office suite" as Dave Mallisk noted.  Worked like a charm.  Who knew we had to have another layer of offcie installed?  Great advice.  Thanks.

---

