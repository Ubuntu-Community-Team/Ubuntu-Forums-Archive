---
title: "Searching WITHIN doc, xls, ppt files"
date: 2011-08-15
forum: General Help
---

### Post by anjaanaadmi on 2011-08-15
Hello.

I am on Ubuntu 11.04 and using Libre Office 3.3.2 to compose new documents and am saving them using .doc, .ppt and .xls files. (due to having to share them with others who are on Windows systems)

I have a lot of doc files and I need to search for text INSIDE these files. I am perplexed with the fact that no search tool is able to search for text INSIDE these file types. "cat" can display them of course, but grep is not able to locate text INSIDE these file types. I even tried to save a .doc file as an .odt file, but no luck. The Applications>Accessories>Search for Files does not search INSIDE doc, xls or ppt with the option "Contains the text".

Does anyone know how to resolve this?

Many Thanks.

---

### Post by dino99 on 2011-08-15
Sometimes watching the man page can help ;)

[http://askubuntu.com/questions/51315/how-do-i-search-for-binary-openoffice-files-which-contain-specific-text](http://askubuntu.com/questions/51315/how-do-i-search-for-binary-openoffice-files-which-contain-specific-text)

---

### Post by anjaanaadmi on 2011-08-15
Sorry, but this command returns nothing. :(

grep -Rian leader *.doc

And I know that the word "leader" is in at least 5 of the several .doc files I have.

I downloaded SearchMonkey and it fails to search in .doc files as well. It When I use it to search in ALL files, it lists one .csv file which is a text file - go figure. It does not even lis PDF files which grep does.

---

### Post by Wim Sturkenboom on 2011-08-15
If you specify *.doc, the -R option is useless as the directories must be called *_something.doc_*.

The below searched for the word 'remotely' in doc files. Startpoint was my home directory and the doc file is in Documents
```

wim@ubuntu-desktop01:~$ grep -iran remotely *.doc
grep: *.doc: No such file or directory
wim@ubuntu-desktop01:~$ find . -iname "*.doc" -exec grep -i remotely {} \;
Binary file ./Documents/ILS server setup on HP DL380.v0.3.doc matches
wim@ubuntu-desktop01:~$ 

```And for binary files, the -n option is quite sueless as well ;) It might be one massive long line ;)

---

### Post by scorp123 on 2011-08-15
> **anjaanaadmi said:**
>  I have a lot of doc files and I need to search for text INSIDE these files. 

Read this ... maybe it will help:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=1808&start=0](http://forums.linuxmint.com/viewtopic.php?f=42&t=1808&start=0)

Long story short: You need the package **wv**.
```
sudo apt-get install wv
```

In that package there is this program: **wvSummary** ... and you can use it to spit out infos about *.doc files. In my case (see thread above) I used it to rename ca. 1100 Word files with cryptic names (KB040303.doc, KB2323244.doc, KB8277181.doc, etc.) into files with more useful names. Very handy.

There are other tools in that package too, e.g. **wvText** which will convert *.doc files into plain *.txt files ... and thus make their content searchable for tools such as **grep**.

Credits go to Microsoft for making their closed-source format obscure and hard to process by automatic means ...

---

### Post by anjaanaadmi on 2011-08-15
I would rather have something which will search directly within MS Office files - the option of first converting them into txt and then searching in that seems too much to me.

Thanks anyway for the suggestion.

---

### Post by scorp123 on 2011-08-15
> **anjaanaadmi said:**
> I would rather have something which will search directly within MS Office files You'll have to convince Microsoft then to open up their obscure closed-source file formats ...

> **anjaanaadmi said:**
>  the option of first converting them into txt and then searching in that seems too much to me.  There are other tools you maybe should play with, e.g. **antiword** and **catdoc** ... Those tools can read a Word document and output plain text "on the fly" without having to convert the file first.

---

