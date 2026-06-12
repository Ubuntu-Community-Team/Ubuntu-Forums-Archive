---
title: "~ Files"
date: 2010-11-05
forum: General Help
---

### Post by kmac on 2010-11-05
For the record, "~" is not Googlable. 

So, I'm designing some PHP files and uploading with Filezilla via FTP. Awesome. However, whenever I upload an entire directory, Filezilla sends the *.php~ temp files right along with it. Now, this may seem innocent, but let's say I have a php contact form with email addresses in it that I don't want shared. Should someone be witty enough to navigate to myurl.com/contact.php~, they would then be prompted to download the file as text. Now my php is available for all to see. I get that I could just go through and delete these files from the server or local machine, but I'd like to figure out a nice way to keep these files from being generated in a SINGLE recursive directory, or use a regular expression to tell Filezilla to weed them out. 

Any help would be greatly appreciated :biggrin:

---

### Post by Cope57 on 2010-11-05
The symbol for the *tilde* does not work for searching, but you may understand why when you search for **[tilde]("http://lmgtfy.com/?q=tilde")** instead.  I will not go into any detail as to why, I am sure can search it yourself.

---

### Post by kmac on 2010-11-05
Thank you kindly, sir, but even searching with the text, "tilde" led to irrelevant results.

---

