---
title: "intra and inter file searching?"
date: 2011-08-28
forum: General Help
---

### Post by princeofnam on 2011-08-28
I have a directory filled with powerpoint files that I'd like to perform searches on both within the filenames and the powerpoint's content.  I assume the grep function might be used but if anyone has more specific instructions I'd be very grateful.

---

### Post by kartabosh on 2011-08-28
> **princeofnam said:**
> I have a directory filled with powerpoint files that I'd like to perform searches on both within the filenames and the powerpoint's content.  I assume the grep function might be used but if anyone has more specific instructions I'd be very grateful.

geany can search within files, i'm not sure if it can within powerpoint files but it can with text files, you might want to give that a try 

for the file names you can use the find command

find /path/where/to/search -name *insert here*
you could also grep that by going to the folder you're interested in and typing 
ls | grep keyword

---

### Post by princeofnam on 2011-08-28
I'm not sure how it works.  Can it search a whole directory and its files' contents?

---

### Post by SeijiSensei on 2011-08-29
The simplest option is 

```

cd /path/to/ppt/directory
grep 'some string to search for' *

```

That will list all the files and occurrences of 'some string to search for'.

For finding files, I much prefer locate:

```

locate string

```

That returns a list of all filenames containing that string.  If you've made a lot of changes to the files before you run locate, I'd run "sudo updatedb" first to force the locate function to update its database of file names.

---

### Post by princeofnam on 2011-08-29
does grep search within the file though?

---

### Post by SeijiSensei on 2011-08-29
> **princeofnam said:**
> does grep search within the file though?

Yes, give it a try and see for yourself.

---

