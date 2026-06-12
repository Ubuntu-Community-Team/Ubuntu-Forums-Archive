---
title: "Help with SED to replace random charaters"
date: 2010-03-04
forum: General Help
---

### Post by Funkey Monkey on 2010-03-04
Hello Guys,

Need some more help with SED please.

In my [prev post]("http://ubuntuforums.org/showthread.php?p=8876382") I learned how to replace "known" characters with:
```
 sed -i.old -e 's/<HTML>/<html>/g' -e 's/<\/HTML>/<\/html>/g' *.htm
```

I now need help to replace "strings" of characters of various lengths.

Example - Problem:
scr="oldPATHtoREPLACE/Pic1.jpg"
scr="ANOTHERPathTOreplace/Pic2.jpg"

Example - Required:
scr="UpdatedPath/Pic1.jpg"
scr="UpdatedPath/Pic2.jpg"

My proposed command to get from Problem to the Required:
```
sed -i.old -e 's/scr\=\"*\//scr\=\"UpdatedPath\//g' *.html
```

**[COLOR="RoyalBlue"]Q: Please check my command above as it is not giving me the required output.[/COLOR]**

Thanks.

---

### Post by djurny on 2010-03-04
```

sed -i.old -e 's/scr\=\"*\//scr\=\"UpdatedPath\//g' *.html

```

trouble is the '*', that makes sed never find the pattern you're actually searching for:

try this one:
```

sed -ne 's|scr=".*\/|src="UpdatedPath\/|p'

```


or this one:
```

sed -i.old -e 's/scr=".*\//scr="UpdatedPath\//g' *.html

```

the only difference is actually the '.*' instead of the '\"*', in the old version it only replaced the path in sentences with zero or more double quotes '"' followed by a '/' :)

hth

---

### Post by Funkey Monkey on 2010-03-04
Thanks for your response djurny.

I tried both the commands above but neither worked

I tried the modify the code (adding \ were I thought needed).
```
sed -i.old -e 's/scr\=\".*\//scr\=\"UpdatedPath\//g' *.html
```

That did not work either.

Googled .* and found [http://www.regular-expressions.info/quickstart.html](http://www.regular-expressions.info/quickstart.html)

Read through the guide, but now I am more confused.

I need to replace the OLDPATH with NEWPATH:

<img height=86 src="[COLOR="Red"]**OLDPATH**[/COLOR]/Pic1.jpg" width=78 />

<img height=86 src="[COLOR="Navy"]**NEWPATH**[/COLOR]/Pic1.jpg" width=78 />

a further problem is that my JavaScript in the html file also starts with src=" (although its been updated to ./Style_Sheets) and I do not wish to change them.

I am thinking the code should be something like:
```
sed -i.old -e 's/scr\=\"[^\.\/Style\_Sheets][.*]\//scr\=\"\./Pictures\//g' *.html
```

but I am getting the following error:
[FONT="Courier New"]UsrName$ sed -i.old -e 's/scr\=\"[^\.\/Style\_Sheets][.*]\//scr\=\"\./Pictures\//g' *.html
sed: -e expression #1, char 47: unknown option to `s'[/FONT]

---

### Post by djurny on 2010-03-04
> **Funkey Monkey said:**
> Thanks for your response djurny.

I tried both the commands above but neither worked

I tried the modify the code (adding \ were I thought needed).
```
sed -i.old -e 's/scr\=\".*\//scr\=\"UpdatedPath\//g' *.html
```

That did not work either.

Googled .* and found [http://www.regular-expressions.info/quickstart.html](http://www.regular-expressions.info/quickstart.html)

Read through the guide, but now I am more confused.

I need to replace the OLDPATH with NEWPATH:

<img height=86 src="[COLOR="Red"]**OLDPATH**[/COLOR]/Pic1.jpg" width=78 />

<img height=86 src="[COLOR="Navy"]**NEWPATH**[/COLOR]/Pic1.jpg" width=78 />

a further problem is that my JavaScript in the html file also starts with src=" (although its been updated to ./Style_Sheets) and I do not wish to change them.

I am thinking the code should be something like:
```
sed -i.old -e 's/scr\=\"[^\.\/Style\_Sheets][.*]\//scr\=\"\./Pictures\//g' *.html
```

but I am getting the following error:
[FONT="Courier New"]UsrName$ sed -i.old -e 's/scr\=\"[^\.\/Style\_Sheets][.*]\//scr\=\"\./Pictures\//g' *.html
sed: -e expression #1, char 47: unknown option to `s'[/FONT]

```
sed -i.old -e 's/scr\=\".*\//scr\=\"UpdatedPath\//g' *.html
```

looks like i made a typo there.. shouldn't that read 'src' instead of 'scr' ??

```
sed -i.old -e 's/src\=\".*\//src\=\"UpdatedPath\//g' *.html
```


tested with the following snippet:
```

#!/bin/bash

echo "old method"
{
  echo '<img height=86 src="OLDPATH/Pic1.jpg" width=78 />'
  echo '<img height=86 src="NEWPATH/Pic1.jpg" width=78 />'
} | sed -e 's/src\=\".*\//src\=\"UpdatedPath\//g'


echo "alt method 1"
{
  echo '<img height=86 src="OLDPATH/Pic1.jpg" width=78 />'
  echo '<img height=86 src="NEWPATH/Pic1.jpg" width=78 />'
} | sed -e 's|src=".*\/|src="UpdatedPath\/|g'

# EOF

```

```

./ubuntuforums2 
old method
<img height=86 src="UpdatedPath/>
<img height=86 src="UpdatedPath/>
alt method 1
<img height=86 src="UpdatedPath/>
<img height=86 src="UpdatedPath/>
alt method 2
<img height=86 src="UpdatedPath/>
<img height=86 src="UpdatedPath/>

```

---

### Post by Funkey Monkey on 2010-03-04
Thanks for fixin' the typo.

Tested it myself and its working.

Thanks for all your assistance, much appreciated.

---

