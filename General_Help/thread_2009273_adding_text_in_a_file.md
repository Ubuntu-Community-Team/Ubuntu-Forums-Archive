---
title: "adding text in a file"
date: 2012-06-24
forum: General Help
---

### Post by inashdeen on 2012-06-24
Hi, this is a bash question.

I am building a new keyboard layout. and so, i need to have an automated script which add :

> <layout>
         <configItem>
           <name> jw </name>
           <shortDescription> jw </shortDescription>
           <description> Jawi </description>
           <languageList>
              <iso639Id> jw </iso639Id>
           </languageList>
         </configItem>
         <variantList/>
       </layout>

on top of the line 


> </layoutList>

can someone give a tip on how can i do that?

---

### Post by codemaniac on 2012-06-24
With a few escapes and added newlines , you can manage to replace 
"</layoutList>" with the xml content posted by you above.

Please refer the below .

```
cat FileA
<layoutList>
</layoutList>
```

```

awk '{sub("</layoutList>","\n<layout>\n\
<configItem>\n\
<name> jw </name>\n\
<shortDescription> jw </shortDescription>\n\
<description> Jawi </description>\n\
<languageList>\n\
<iso639Id> jw </iso639Id>\n\
</languageList>\n\
</configItem>\n\
<variantList/>\n\
</layout>\n\
</layoutList>\n\
"); printf"%s",$0}' FileA
```

---

### Post by inashdeen on 2012-06-24
Hi i tried to use your code to do this:

> awk '{sub("</layoutList>","\n<layout>\n\
<configItem>\n\
<name> jw </name>\n\
<shortDescription> jw </shortDescription>\n\
<description> Jawi </description>\n\
<languageList>\n\
<iso639Id> jw </iso639Id>\n\
</languageList>\n\
</configItem>\n\
<variantList/>\n\
</layout>\n\
</layoutList>\n\
"); printf"%s",$0}' /home/ihsan/evdev.xml > temp 
mv temp /home/ihsan/evdev/xml

but apparently, the output is not the same as the original.

---

### Post by codemaniac on 2012-06-24
> **inashdeen said:**
> Hi i tried to use your code to do this:


but apparently, the output is not the same as the original.

The above awklet is meant to substitute "</layoutList>" of FileA with the xml snippet contents posted by you .

Is there anything else in your requirement ?

---

### Post by inashdeen on 2012-06-25
> The above awklet is meant to substitute "</layoutList>" of FileA with the xml snippet contents posted by you .

I know, but when i copy changes to temp file then rename temp file to my file name, the output does not look the same. all other original setting for other text ( spaces, bla2) ,were misplaced

---

### Post by codemaniac on 2012-06-25
> **inashdeen said:**
> I know, but when i copy changes to temp file then rename temp file to my file name, the output does not look the same. all other original setting for other text ( spaces, bla2) ,were misplaced

Can you please post how your output looks like ?

---

### Post by markbl on 2012-06-25
If you want to read, and particularly write, xml from a bash script then you are **far** better off using xmlstarlet. Just "apt-get install xmlstarlet" and then read the online docs. Sure, there is a tiny learning investment but ultimately you will produce a better more reliable script which is shorter and easier to extend and maintain.

---

### Post by inashdeen on 2012-06-26
Technically i don't want to install the xmlstarlet not because i don't want to learn but because this bash script is in a postinst file of a deb. i don't feel is worth it to let user install xmlstarlet just to edit the file

---

### Post by steeldriver on 2012-06-26
well I guess you could try sed:

```
sed 's|^</layoutList>|<layout>\
<configItem>\
<name> jw </name>\
<shortDescription> jw </shortDescription>\
<description> Jawi </description>\
<languageList>\
<iso639Id> jw </iso639Id>\
</languageList>\
</configItem>\
<variantList/>\
</layout>\
&|' *yourfile*
```

---

### Post by codemaniac on 2012-06-26
> **inashdeen said:**
> Technically i don't want to install the xmlstarlet not because i don't want to learn but because this bash script is in a postinst file of a deb. i don't feel is worth it to let user install xmlstarlet just to edit the file

There are ample of native filters available in Unix in order to do any text manipulation jobs .Instead of toiling hard to learn external tools , you will be better off learning native Unix utilities like perl , awk ,sed etc.. 

The above posted awklet gives me the desired output , it would be helpful if you can post what exactly mischievous you are getting in your output .

---

### Post by inashdeen on 2012-06-26
I am not getting all mischivious with my output. In fact I all I want to do is to install a jawi (traditional malay - ms )keyboard to users system. here is my project hosted :
[https://launchpad.net/jawi]("https://launchpad.net/jawi")

there is an installer file if you like to try. It works well as far as I know. 

There is technically no source code since most of the stuff runs in bash (zenity) . just extract the .deb file and see its content

---

