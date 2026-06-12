---
title: "searching within a pdf from the command line"
date: 2011-07-02
forum: General Help
---

### Post by craq on 2011-07-02
I want to search through a large number of pdf files for a specific phrase. From the command line, I get nothing. Specifically, I use:
find ./ -maxdepth 3 -name *.pdf |xargs grep phraseToSearchFor

If I open the pdfs in a text editor, everything is scrambled (binary) and I can't search for anything meaningful.

But if I open the pdf in DocumentViewer, or Acrobat, I can search for text and find it no problems.

Does anybody know how to search for internal text without opening the pdf? Otherwise I can't batch it.

I didn't make the pdfs, and I can't change how the originals are formatted, but I would alternatively settle for a program which converts them to a searchable format.

---

### Post by Gryllida on 2011-07-02
Under both Linux and Windows, you can use **Acrobat Reader**, which has a command to search multiple files.

Under Linux, there is Recoll ("**recoll** - Personal full text search package with a Qt GUI"), which builds an index of your pdf files on first run. To install it, run: " sudo apt-get install recoll " - or find it in the Software Center.

You also can convert the files to text using the "**pdftotext**" utility directly. Iit's also available via apt-get or Software Center. Then use grep on the text files.

```

find -name '*.pdf' -exec pdftotext {} \;
grep -r --include '*.txt' -l -F "exact phrase to search"
grep -r --include '*.txt' -l -E "regular expression to search"

```

More details: [Command line tool to search phrases in large number of pdf files](http://superuser.com/questions/163182/command-line-tool-to-search-phrases-in-large-number-of-pdf-files)

---

