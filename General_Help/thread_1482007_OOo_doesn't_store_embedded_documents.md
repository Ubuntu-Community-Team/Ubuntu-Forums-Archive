---
title: "OOo doesn't store embedded documents"
date: 2010-05-13
forum: General Help
---

### Post by pallart on 2010-05-13
I don't know if the bug comes from Ubuntu or from the upstream. I've already posted it in
the bug tracker of OpenOffice.org.

Insert a Calc SpreadSheet inside a Writer document
Choose "existing file" and select an existing spreadsheet.
Keep unchecked the "link" box

You get the spreadsheet inserted.
Save the document.
Open it again: the spreadsheet is no more available.

Here the unzip output of the document:
```

Archive:  ../DocumentsInseres.odt
 extracting: mimetype                
   creating: Configurations2/statusbar/
  inflating: Configurations2/accelerator/current.xml  
   creating: Configurations2/floater/
   creating: Configurations2/popupmenu/
   creating: Configurations2/progressbar/
   creating: Configurations2/menubar/
   creating: Configurations2/toolbar/
   creating: Configurations2/images/Bitmaps/
 extracting: Pictures/1000000000000C68000009B9C57718CA.jpg  
  inflating: content.xml             
  inflating: manifest.rdf            
  inflating: styles.xml              
 extracting: meta.xml                
  inflating: Thumbnails/thumbnail.png  
  inflating: settings.xml            
  inflating: META-INF/manifest.xml

```Here is the relevant part in content.xml:

```

<text:p text:style-name="Standard">
   <draw:frame draw:style-name="fr2"
              draw:name="Objet1" 
              text:anchor-type="paragraph" 
              svg:width="13.998cm"
              svg:height="4.658cm" 
              draw:z-index="1">
         <draw:object xlink:href="./Object 2"
              xlink:type="simple" 
              xlink:show="embed" 
              xlink:actuate="onLoad"/>
          <draw:image
              xlink:href="./ObjectReplacements/Object 2" 
              xlink:type="simple"
              xlink:show="embed" 
              xlink:actuate="onLoad"/>
    </draw:frame>
</text:p>

```If you choose to insert a new object insteed of an existing file, all works fine.

I'm using OOo 3.2.0m12 (build: 9483) coming from the Ubuntu 10.04 main repository.

---

### Post by Hagar Delest on 2010-05-13
Indeed: [Issue 108978 - WW8. exported OOo Spreadsheet disappears when re-imported in writer](http://www.openoffice.org/issues/show_bug.cgi?id=108978).

Fixed in 3.2.1 (RC1 has been released so it should be there in a few weeks).

---

