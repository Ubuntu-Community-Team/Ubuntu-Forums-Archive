---
title: "replace multiple lines in multiple files"
date: 2011-08-20
forum: General Help
---

### Post by matt434 on 2011-08-20
Hi there. I often use the rpl command to make changes to multiple html files at once. For example:

rpl -R '<br />' '<br /><br />' mydirectory

However, I haven't been able to figure out how to change multiple lines. For example, let's say I want to change all occurrences of :

<br />
<br />

to:

<br />

I've tried

rpl -R '<br />\n<br />' '<br />' mydirectory

but that didn't work. Does anyone know how to do this with rpl or some other way?

---

### Post by sanderd17 on 2011-08-20
I never heard of the 'rpl' program, I always used sed to find and replace.

But about your rpl, what line endings do you use? If you have mac or windows line endings, \n won't work.

[http://en.wikipedia.org/wiki/Newline](http://en.wikipedia.org/wiki/Newline)

---

### Post by matt434 on 2011-08-20
How do I find out what line endings I'm using? I'm running Ubuntu 11.04 and use Text Editor to create all my HTML files.

---

### Post by sanderd17 on 2011-08-20
You can try with one file in a text editor like gedit. Look at what it responds.

---

### Post by matt434 on 2011-08-20
Text Editor = gedit. When I open it in gedit, I see don't see line endings. ie. it renders the file as:

1
2
3

not

1\n2\n3

---

### Post by sanderd17 on 2011-08-20
yes, and now try out the find dialog to see if you can find "<BR />\n<BR />" or if it works with any other line endings.

---

### Post by matt434 on 2011-08-20
Ah, I understand now. Yes, in gedit \n seems to work. But not in rpl. Will it work in sed?

---

### Post by darkdragn on 2011-08-20
```
 
ls |while read line; do sed -e 's/<\/br>\n<\/br>/<\/br>/g' -i "$line"; done
 

```
Give it a try

---

### Post by sanderd17 on 2011-08-20
it should work in sed, but sed is a bit more difficult it seems.

sed can't work on multiple files at once, so you would need to write a for loop, and the sed command should look like

```

sed 's|<BR />\n<BR />|<BR />|g' <inputfile >outputfile

```

You can read about sed here: [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

### Post by matt434 on 2011-08-20
Ah, I don't think sed is what I'm looking for then. The neat thing about rpl is that it does multiple files at once and even does subdirectories. It seems to be limited to single lines though. Pity.

---

### Post by sanderd17 on 2011-08-20
if you write your own loop (as darkdragn has done), than you also can search-replace in multiple files. If you want to search in subdirectories, replace the "ls" by "ls -r"

---

### Post by AlphaLexman on 2011-08-20
> **matt434 said:**
> rpl -R '<br />\n<br />' '<br />' mydirectory
According to the man page 'rpl' needs the '**-e**' option to escape the newline code.
```
     -e, --escape
             Expand escape sequences in old_string and new_string.  Examples
             of escape sequences are &#8216;\n&#8217; (new-line), &#8216;\t&#8217; (tab), &#8216;\x42&#8217;
             (hexadecimal number 42), &#8216;\033&#8217; (octal number 033).

```

---

### Post by matt434 on 2011-08-20
That's done it! All I needed was -e!

Thanks for all the help.

rpl rocks!

---

