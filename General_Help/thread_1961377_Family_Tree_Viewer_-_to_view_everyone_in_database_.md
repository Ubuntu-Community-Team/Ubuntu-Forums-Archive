---
title: "Family Tree Viewer - to view everyone in database on 1 image"
date: 2012-04-19
forum: General Help
---

### Post by Rytron on 2012-04-19
Hi.

I use the excellent GRAMPS to build my family tree. Does anyone know of a program native/wine to view everyone in database on 1 image?

Examples:
[http://upload.wikimedia.org/wikipedia/commons/3/3e/Gens_Caecilia_Metella_family_tree.png](http://upload.wikimedia.org/wikipedia/commons/3/3e/Gens_Caecilia_Metella_family_tree.png)
[http://www.trinity-bris.ac.uk/assets/images/history/cann_family_tree_large.gif](http://www.trinity-bris.ac.uk/assets/images/history/cann_family_tree_large.gif)

Thanks.

---

### Post by dragonfly41 on 2012-04-19
I'm testing [www.thejit.org](www.thejit.org) for visualising large tree structures (not genealogy) ..

but thejit framework is also used in genealogy applications ..

[http://blog.thejit.org/2009/05/11/interactive-visualization-of-genealogical-graphs/](http://blog.thejit.org/2009/05/11/interactive-visualization-of-genealogical-graphs/)

---

### Post by Rytron on 2012-04-19
> **dragonfly41 said:**
> I'm testing [www.thejit.org](www.thejit.org) for visualising large tree structures (not genealogy) ..

but thejit framework is also used in genealogy applications ..

[http://blog.thejit.org/2009/05/11/interactive-visualization-of-genealogical-graphs/](http://blog.thejit.org/2009/05/11/interactive-visualization-of-genealogical-graphs/)

Hi dragonfly41. I downloaded the file - how is it run?

---

### Post by dragonfly41 on 2012-04-19
View the source of one of thejit demos to see how the scripts are added to an html page.

You would need to export your GRAMPS data to be converted into json.

---

### Post by Rytron on 2012-04-19
> **dragonfly41 said:**
> View the source of one of thejit demos to see how the scripts are added to an html page.

You would need to export your GRAMPS data to be converted into json.

I am baffled. Is there an easier way/alternative?

---

### Post by dragonfly41 on 2012-04-19
I haven't done this .. but this is how I guess it would go ..

generate XML from your gramps family tree

[http://www.gramps-project.org/wiki/index.php?title=Generate_XML](http://www.gramps-project.org/wiki/index.php?title=Generate_XML)

> Generating XML

The easiest way to generate an XML file is to export the data. This can be done from the menu: Family Trees->Export or Family Trees->Backup.... This will generate a file with a .gramps extension. This file is usually a gzip'd XML file (depending on some system settings, sometimes this will be an uncompressed XML file). 
...

This command worked for me .. gramps exported to /home/myusername/gramps_export/data.gramps

**[COLOR=Blue]$ gunzip < /home/myusername/gramps_export/data.gramps > /home/myusername/gramps_export/data.xml[/COLOR]**


Now the next step would be to convert data.xml using XML to JSON (javascript used in thejit).

search "XML2JSON" in google


[http://stackoverflow.com/questions/6465256/how-can-i-convert-an-xml-file-into-json-using-python](http://stackoverflow.com/questions/6465256/how-can-i-convert-an-xml-file-into-json-using-python)

...

Once you have your gramps xml data in json format you can apply thejit to visualise.

...

[EDIT]

I remembered there is an online XML2JSON service you can try out first.

[http://extjs.org.cn/xml2json/xml2json_online.php](http://extjs.org.cn/xml2json/xml2json_online.php)


...

[FURTHER EDIT]

Perhaps this is an alternative to above approach ...

[http://www.graphviz.org/Home.php](http://www.graphviz.org/Home.php)

---

### Post by Rytron on 2012-04-20
I found 'Simple Family Tree 1.32'. It works fine in Wine.

Any additional viewers would be appreciated.

---

