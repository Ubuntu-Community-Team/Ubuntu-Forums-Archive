---
title: "help creating a very basic XML syntax highlighting file for Kate"
date: 2010-09-27
forum: General Help
---

### Post by begtognen on 2010-09-27
I know how to create an XML file for Kate, to make my own specific syntax highlighting. I know how to make it appear in the menu, I know how to fiddle with the Fonts and Colors of my custom XML file.

The sticking point is how to get the XML file to do what I want - to get the three options below to appear under Fonts and Colors when I have my own custom XML syntax highlighting file selected. I'm after something *very* simple. I want it to do just three very basic things:

1) Highlight keywords.

2) Highlight words inside  brackets, like: [elephant]

3) Highlight comments (I'm not fussy what kind, I'd just like the highlighting)

Would really appreciate any help you can offer.

---

### Post by begtognen on 2010-10-01
I was able to edit the css.xml file in order to get the brackets highlighted. 

```
      <!-- finds comments -->
      <context attribute="Normal Text" lineEndContext="#stay" name="FindComments">
        <RegExpr attribute="Region Marker" context="#stay" String="[" beginRegion="UserDefined" />
        <RegExpr attribute="Region Marker" context="#stay" String="]" endRegion="UserDefined" />
        <Detect2Chars attribute="Comment" context="Comment" char="/" char1="*" beginRegion="comment" />
      </context>
```It was the String="[" and the String="]" bits that I changed. Now anything inside brackets is highlighted.

(I don't know if it's important, but I did use the codes for the brackets, apologies, I can't type them in because the forum just turns them into real brackets)

---

