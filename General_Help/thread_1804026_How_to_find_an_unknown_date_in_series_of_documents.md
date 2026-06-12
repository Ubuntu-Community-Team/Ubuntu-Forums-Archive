---
title: "How to find an unknown date in series of documents and add this date to document name"
date: 2011-07-14
forum: General Help
---

### Post by Jan Sloep on 2011-07-14
Hello,

I'm working on an inventory of a few hundred paper documents I ever received in the past. 

First I scanned these documents to text-searchable PDF files in the format Document0001.pdf 002.pdf 003.pdf ... etc.

Now I want to be able to sort these documents on the date specified in the document itself by adding this date to the file name. This (unknown) date is almost always in the format 01-01-99 or 01-01-1999

The grep command *-*-* *. pdf neatly displays all files in which a date in this format is available.

What I do not know is how I can add the date in the found files to the file name. I don't even know if grep actually can display the found date as a result or just sets a flag that something is found that meets the search criteria (*-*-*).

Is there anyone who can help me?
:confused:

---

### Post by dethorpe on 2011-07-14
Grep will output the matched line, so you can get the date from it. You would need to pipe it through something else (e.g. awk, perl) to split the line and get the date, then rename the file.
 
I would suggest a shell of perl script, perfoming something like this algorithum
```
 
 
FOR each file
  Search file for date line (e.g. grep, perl IO loop with match)
  IF line found
    split line to get date (e.g. awk, perl split command)
    rename file
    skip to next file
  ENDIF
ENDFOR

```
 
If you post a sample file and and script or shell commands you've tried may be able to look at it and work outsomething more specific.

---

### Post by Jan Sloep on 2011-07-14
Hi,

Thanks for your reaction. 

How to do this with a shell script for all the files is not the problem. 

The problem is that the date can be anywhere in the document. I should be able to find the line where the date is in with grep, but I don't know how to extract the date value from the line. I don't know what split syntax should be able to do that. So I have to find that first.

Thanks

---

### Post by Vaphell on 2011-07-14
you want to extract creation date from pdf metadata? i don't think grep will work here as pdf is not a plain text format.

sudo apt-get install pdftk

```

for pdf in *.pdf
do
  crdate=$( pdftk "$pdf" dump_data | grep -A 1 'CreationDate' | grep -oE '[0-9]{14}' | sed -r 's/([0-9]{4})([0-9]{2})([0-9]{2}).*/\1-\2-\3/' )
  echo $crdate
  echo mv "$pdf" $crdate-"$pdf"
done

```

---

### Post by Jan Sloep on 2011-07-14
Hi Vaphell,

No the date is not in the metadata. I received the documents as printed documents so I scanned them to PDF files and OCR'ed them. The text is inserted "behind" the PDF file so the PDF files are text searchable now. 

I need to know the date from the original printed document, but as the PDF file is generated at a much later date than the original printed document, I need to find a way to extract the date from the OCR'ed data which now is in the text searchable PDF file.

Unfortunately the date can be at in different postion in every PDF file. Grep finds the dates, but I don't know how to get those dates out of grep.

---

### Post by Jan Sloep on 2011-07-14
This is what I am trying to do, but I get no output

for f in *.pdf
do
      grep -o "-*-*-*" *.pdf | dates
      echo $dates
done

---

### Post by Vaphell on 2011-07-14
i get it now
does grep on a single file work and return anything?

your code is wrong because:
- you iterate files one at a time (for f in *.pdf), yet inside the loop you use *.pdf again (all pdfs at once), instead of current $f
- you don't capture the output but pass it via pipe to dates.

```
for f in *.pdf
do
  dates=$( grep -oE '[0-9]+-[0-9]+-[0-9]+' "$f" )
  echo "$dates"
done
```

---

### Post by Jan Sloep on 2011-07-14
No, no output at all.

If you want I can post one of those file, but I have to make it anonymus first

---

### Post by Vaphell on 2011-07-14
that would be nice

---

### Post by Jan Sloep on 2011-07-14
Sorry I thought I could upload a file here. But not!

---

### Post by dethorpe on 2011-07-14
You could just insert the line of the file containing the date into a post, with a few lines each side for context, that would be enough to work on.

---

### Post by Jan Sloep on 2011-07-14
You are right, it could also be done with a normal text file.

Here is some example (In Dutch) The date is 13-05-11

 Debiteurennr.            Tijd              Medewerker                        Factuurdatum           Factuurnummer

 251001234                 15:23             PATTUK                            13-05-11               251023347
 Aantal    Artikelnummer         Omschrijving                                                      Prijs           Totaal

       1   20005053              HI 3.5" SATAN 1TB/7200RPM/32MB SAMSUNG                    &#8364;      49,95    &#8364;        49,95
                                 Serienr.:    S246J8BZG00301

---

### Post by dethorpe on 2011-07-14
Ok, something like this then:
 
```
 
for file in *.pdf
do
        datestamp=$(grep -E "[0-9]+-[0-9]+-[0-9]+" $file | awk '{print $4}')
        cp $file "${datestamp}_$file"
done
 

```
 
 
(i'm using a UNIX box at work to try this and its grep dosn't have the -o option, if you use that then don't need the pipe to awk bit.)

---

### Post by Jan Sloep on 2011-07-14
Hello Dethorpe,

Thanks very much. This indeed works on the txt output I also made from the scanned files. The strange thing is that it does not work on the PDF files. 

Anyway, your solution shows how to get the date out of a file, now I can see what goes wrong with the pdf files.

Thanks very much

---

