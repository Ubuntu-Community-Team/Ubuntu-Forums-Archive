---
title: "Convert from html to text"
date: 2010-07-09
forum: General Help
---

### Post by roshanjose on 2010-07-09
I have 2 GB of html files and i need to convert all of them at once to text files. Is there any way that I can do it. Converting each of them manually is really a pain and I want to convert all of them with a single command to text files.

Can anyone help

---

### Post by techunit on 2010-07-09
Um you could open them in say firefox and copy the text? I don't know I am understanding you.

---

### Post by Muscovy on 2010-07-09
You could find or write a script, perhapse. Do you just need plain text?

---

### Post by fragos on 2010-07-09
You can open any html file with OpenOffice and then save as Text which strips all the markup and images. There may be some editing since it will save the text but not the URL of any navigation link on the HTML page.

---

### Post by jonobr on 2010-07-09
I used to have to convert a lot of xml raw billing data to CSV format.
I used an excellent program called xml2csv. There was a linux and a windows version of that software.
Becuase the xml tags were somewhat unique I could filter what I wanted to see and how I wanted to see it.

I believe that program also contained a html2csv
(im not sure about text, however, a simple vi would remove any commas.)
sorting was hard as the html had repetative tags which meant sorting data was difficult.

Anyway Im babbling, if you look around for html2csv and maybe even to txt you may find something,.
Heres [is a python script i found from a quick google]("http://www.aaronsw.com/2002/html2text/")
note its 2002, and not the ine I think I used.

Failing all that, and if your feeling lazy
you could put up your data on a webserver and use something like w3m to only see the data without the formatting?

---

### Post by cbraxton on 2010-07-09
> **roshanjose said:**
> I have 2 GB of html files and i need to convert all of them at once to text files. Is there any way that I can do it. Converting each of them manually is really a pain and I want to convert all of them with a single command to text files.

Can anyone help

You might try running lynx inside a shell script, maybe something like:

```

#!/bin/sh

if [ ! -d text ]; then
  echo "Creating text subdir."
  mkdir text
fi

for file in *.html
do
  FNAME=`echo $file | cut -d . -f 1`
  lynx -dump $file >text/$FNAME.txt
done

```

(This would dump the converted files into a "text" subdirectory.)

---

