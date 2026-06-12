---
title: "Script to find zips containing xml"
date: 2011-10-05
forum: General Help
---

### Post by bakegoodz on 2011-10-05
Can someone come up with a a script to search within all zip files within a directory? (1000s) and then find which ones have .xml files archive in them. Thank You!

Back Story:
I used Photorec to try to recover a much needed docx file. The problem is that Photorec only identifies them as zip file. So does other recovery software because docx files are zip files. The 2007+ Office files are zip files that contain a bunch of .xml files.

---

### Post by Vaphell on 2011-10-05
```
#!/bin/bash

mkdir -p potential_docx_files
mkdir -p potential_xlsx_files

for file in *.zip
do
  filelist=$( unzip -l "$file" )
  if echo "$filelist" | grep -q 'word.*xml'
  then
    echo "$file" looks like .docx file
    **echo** mv -v "$file" potential_docx_files/"${file%.zip}".docx
  elif echo "$filelist" | grep -q 'xl.*xml'
  then
    echo "$file" looks like .xlsx file
    **echo** mv -v "$file" potential_xlsx_files/"${file%.zip}".xlsx
  else
    echo "$file" is not MSO file
  fi
done

```

i hope there are no base name collisions, i didn't bother to test it, i just move stuff to subdir and change extension to docx/xlsx. Currently it merely prints the move command out, if you like the dry run results, remove echo in bold font.

---

### Post by bakegoodz on 2011-10-06
Your Awesome! Thank You! The script did what I asked plus more when you had it recognize the different between docx and xlsx files.
 I haven't found the file yet, most of the files are unopenable with both OpenOffice and Microsoft Office. Maybe I can find a program that extract the data out of corrupt office files.

BTW I did find that PhotoRec does detect docx and xlsx files, and I had a couple recovered. Though this script does find a few more in the zip files, apparently Photorec only recognizes the ones in pristine condition.

---

### Post by Vaphell on 2011-10-06
you may want to tweak the script
**unzip -l "$file"** returns a list of contents. You may add the following line:
```
"echo "$filelist"
``` just above the if block to have the list of contents printed out for each archive.

I created empty xlsx and docx in open office, checked their structure and set the testing expression accordingly. Check your legit office files if they follow the pattern i assumed (run unzip -l filename manually), if not then modify the script to suit your needs.

---

