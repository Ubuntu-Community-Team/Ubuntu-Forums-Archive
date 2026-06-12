---
title: "create zip files in ubuntu command line"
date: 2011-12-04
forum: General Help
---

### Post by coffeecake on 2011-12-04
i want to zip a entire folder of files. So i entered the following command

zip *.* *.zip

But zip gives me a error. 


[PHP]zip warning: missing end signature--probably not a zip file (did you
	zip warning: remember to use binary mode when you transferred it?)

zip error: Zip file structure invalid (fc.pdf)

pdftotext# zip *.* *.zip
	zip warning: missing end signature--probably not a zip file (did you
	zip warning: remember to use binary mode when you transferred it?)
[/PHP]

How do i resolve this ? Could someone please help me ?

---

### Post by mutley89 on 2011-12-04
```
zip -r name_of_output_archive.zip directory_to_archive/
```Have a look at man zip for more info

---

### Post by noah++ on 2011-12-04
Hi,

Note that ***.* **is the DOS way of globbing. To pick all (non-hidden) files in a directory in Linux, use ***** instead. You also use the wrong argument order for the *zip* command. The name of the zip file comes first, the stuff you want in the file comes second. That's why you got the weird error.

Now if you wanted to zip the directory into one compressed file, follow **mutley89**'s advice. But if you are trying to compress each file into a self-named zip file, then that's not what you want, and I think just correcting your syntax will not help. I say that because you seem to be imagining that both wildcards in your command will be expanded to the same filename, resulting in a series of commands like *zip file1.zip file1*, *zip file2.zip file2*, and so on, with *n *commands for *n *files in the directory. But I don't think that is what will happen.

When I want to do a "for each" kind of operation, I use a short script, which can be entered at the command line. For you, something like this will work if your (reordered) original command doesn't work.

```
for file in `ls -1`; do zip "$file".zip "$file"; done
```

---

