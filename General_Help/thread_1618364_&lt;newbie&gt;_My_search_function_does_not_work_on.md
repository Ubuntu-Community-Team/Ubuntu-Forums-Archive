---
title: "&lt;newbie&gt; My search function does not work on 9.10"
date: 2010-11-10
forum: General Help
---

### Post by Cypress Tech on 2010-11-10
I have a few thousand .doc and .odt files (Word & OpenOffice documents)  in a folder. Under 9.04, I was able to run a query search for keywords  by using; Places - search for files - contains the text. It would find  files with the text that I requested every time. 

Now that I have 9.10, that search function does not work any more. 

Has anyone had a similar problem? How can I fix that?

Thanks 
Jesse

---

### Post by TeoBigusGeekus on 2010-11-10
```
find /path/to/the/folder/ -name string_you're_looking_for
```

---

### Post by Cypress Tech on 2010-11-10
Hi Teo, that points to file name searches. I'm looking to text within file searches. Do you have something for that?

---

### Post by TeoBigusGeekus on 2010-11-10
Oh, I see...
Then go with grep
```
grep "string to search" *.doc *.odt
```

---

