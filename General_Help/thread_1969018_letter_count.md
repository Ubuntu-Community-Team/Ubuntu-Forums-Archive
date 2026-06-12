---
title: "letter count ??"
date: 2012-04-29
forum: General Help
---

### Post by jas2mine on 2012-04-29
how can i count the number of  letters(capital and small )in the file ??

and 
how can i count the number of paragraph in the file

---

### Post by matt_symes on 2012-04-29
Hi

For the number of characters

```
cat <filename> | tr -cd '[:alpha:]' | wc -c
```It will count a-z and A-Z but no numbers.

```

matthew@matthew-Aspire-7540 ~ % cat tt                             
acd5     


xq34
matthew@matthew-Aspire-7540 ~ % cat tt | tr -cd '[:alpha:]' | wc -c
5
matthew@matthew-Aspire-7540 ~ % 
```

How are you defining your paragraphs ? With a tab at the start ?

Kind regards

---

### Post by audiomick on 2012-04-29
If it is an Open Office text file, there is a thing in the "extras" menu that will give you a word count and a character count. I assume this is also in Libre Office.

If you are looking at a text file in Gedit, there is a thing in the tools menu to get statistics on the Document. It will show you lines, words and characters.

Don't know about counting paragraphs.

---

### Post by jas2mine on 2012-04-30
[COLOR="Red"]matt_symes [/COLOR]

yes ,,  With a tab at the start  :| !??

---

### Post by matt_symes on 2012-05-01
Hi

> yes ,,  With a tab at the start  :neutral: !??If your using tabs to identify the start of a paragraph then you can grep the file looking for tabs as the first characters on a line.

```
grep -cP '^\t' <filename>
```Above, the -P switch identifies a perl regex and the -c switch counts the number of instances it finds in the file.

Take a look at this file called ttt below.

```

matthew@matthew-Aspire-7540 ~ % cat -T ttt
^IThis is paragraph one

^IThis is paragraph two.
^IThis is paragraph three.
This is not a paragraph.

and neither is this
matthew@matthew-Aspire-7540 ~ % 
```The -T switch for cat will display <tab> characters as ^I characters (read the man page for cat). 

As you can see, the file has three paragraphs in it and some other text.

```
matthew@matthew-Aspire-7540 ~ % grep -cP '^\t' ttt
3
matthew@matthew-Aspire-7540 ~ %
```Kind regards

---

