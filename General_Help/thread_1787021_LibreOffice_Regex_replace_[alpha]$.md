---
title: "LibreOffice Regex: replace [:alpha:]$"
date: 2011-06-20
forum: General Help
---

### Post by jesuisbenjamin on 2011-06-20
Hi there,

My friend lost her dissertation and she had only a pdf copy of it. I am trying to convert the pdf into an odt format. After copy-pasting the content into an odt, i need to replace all paragraph breaks which are not following a dot with a space. For which i thought of using the regular expression feature of Libre Office. I've not succeeded so far.

I tried: to replace [:alpha:]$ or [a-z]$ or [a-z]\>$ with space, but none of them worked.
Finding [a-z] seems to work, finding [a-z]\> too. So did finding $ (end of paragraph) but if i combine any regex with $ then it doesn't find anything.

Can anyone help? Thanks.

---

### Post by bodhi.zazen on 2011-06-20
[s]Two[/s] Three steps might work (try it on a copy first).

1. Remove all Paragraph marks 

Find $ replace with  ' ' (a space)
Find ```
$
```
Use a single space in the Replace box 

2. Find all '.' and replace with a ".new line".

Find ```
([:alpha:])\.
```Replace  ```
$1.\n
```3. To remove excess white space at the front of the lines

Find ```
^ *([:alpha:])
```Replace ```
$1
```That should get you close

---

### Post by jesuisbenjamin on 2011-06-20
It's not perfect because it adds a paragraph break at each dot, while it should rather remove paragraph breaks where there are no dots. 
But it did 50% of the job, i just have to remake paragraphs out of few thousands of lines 8-[

Thanks :D

---

### Post by jesuisbenjamin on 2011-06-20
Ok i worked on an alternative by replacing the first replace $ by [:space:] into replace $ by @ for instance. Then i logically can find (non-regex) instances of .@ and replace them by .\n (new paragraph), and eventually replace all remaining @ by [:space:].
But for some strange reason open office can't find .@ in my document. But if i do type "something.@somethingelse" in another document and search for .@ it _does_ find it. Pretty weird huh?

Do you have some idea as to what's happening here?

Thanks.
B.

---

### Post by jesuisbenjamin on 2011-06-20
Haaa good ol'Gedit did the trick. By copy-pasting the text to gedit i discovered some invisible character had been added before each @. Gedit was much more cleaner. Hurray for Gedit and +1 for simplicity.

Thanks for all the help.

---

### Post by bodhi.zazen on 2011-06-20
Glad you got it sorted out, as you found, it is hard to write a search pattern for a document you can not work with directly.

---

### Post by GregorDS on 2011-07-09
I have the same issue but my search for $ finds nothing.
I want to find all paragraph marks in selected text and replace them with either 
case 1: a space
or
case 2: nothing (eliminate the paragraph mark)

---

### Post by jesuisbenjamin on 2011-07-09
It should not be a problem, did you try to search for $ (don't forget to enable the regular expression option)?

---

