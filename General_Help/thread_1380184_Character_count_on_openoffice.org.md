---
title: "Character count on openoffice.org"
date: 2010-01-13
forum: General Help
---

### Post by Legendário on 2010-01-13
I need a way to count characters without taking into account spaces, on OpenOffice Writer, and a way to do same, plus counting words on OpenOffice Calc.

On Calc, it seems impossible to count words, just cels. I need that to help a friend who is a translator and receives per characters like that (without spaces).

She wants to migrate to free software, but she (and I too) couldn't find this tool on OpenOffice. She tells me it's possible to do that on MS Office.

Any help would be appreciated.

Thanks.

---

### Post by ttoilleb on 2010-01-13
On OO 3.0.1 you can get a word and character count in Writer in File-Properties then select the Statistics tab.

---

### Post by Legendário on 2010-01-13
> **ttoilleb said:**
> On OO 3.0.1 you can get a word and character count in Writer in File-Properties then select the Statistics tab.

Yes, I know. But it shows me only the characters, WITH the spaces. And _as I described_, in Calc, it only shows the number of cels.

---

### Post by falconindy on 2010-01-13
Not an avid OO.o user, but it seems as though you could save an OO-Writer doc as a simple text file and do the following:
```
tr -d ' \n' < /path/to/file | wc -c
```
This deletes all white space and newline characters and return the true number of characters. If anyone knows of a way to read the raw text from an OO.o writer doc on the command line....

Not sure what to do about OO-calc sheets.

---

### Post by Legendário on 2010-01-13
> **falconindy said:**
> Not an avid OO.o user, but it seems as though you could save an OO-Writer doc as a simple text file and do the following:
```
tr -d ' \n' < /path/to/file | wc -c
```
This deletes all white space and newline characters and return the true number of characters. If anyone knows of a way to read the raw text from an OO.o writer doc on the command line....

Not sure what to do about OO-calc sheets.

Thanks a lot for your help, but I really need a way to do that on the OO.org.

You see, I'm trying to help a friend migrate to linux and that's something important to her. Besides that, she needs to send the resulting work as MS Office files.

Thanks again

---

### Post by blueridgedog on 2010-01-13
Here is a macro that will count words and characters.  I do not know if it omits spaces, but it is a start:

[http://www.necco.ca/dv/oo_html_tmx.htm#word_count](http://www.necco.ca/dv/oo_html_tmx.htm#word_count)

It appears that you could edit the separator section to remove the counting of spaces:

      'Add your own separators here
      'chr(9) is a tab
      Case " ", "(", ")", chr(9)
        bLastWasseparator = true
        nSelChars = nSelChars + 1

---

