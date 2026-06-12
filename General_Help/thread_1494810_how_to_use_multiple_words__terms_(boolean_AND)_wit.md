---
title: "how to use multiple words / terms (boolean AND) with gnome search tool"
date: 2010-05-27
forum: General Help
---

### Post by cedardoc on 2010-05-27
I just want to search file names, not their content.  

Using gnome-search-tool, if I search for "word1 word3" I can't find "word1 word2 word3.txt" but I do find it (and too many others) if I just search for "word1"

I would have thought a boolean AND search would just be automatic, but I guess not.  I've already come across searchmonkey, but I'm not smart enough to figure out how to set it up to do this - i.e. I don't want to have to use regular expressions or be typing "*" all over the place.

Have I missed something here?  Please help...

Dave

P.S. I do use google desktop search, but I hate using it as the results are way too narrow to be of any use and haven't been able to figure out how to widen it.

P.P.S. I also found this:
In terminal type gconf-editor and find gnome-search-tool in the Apps. Then look for the field quick_search_second_scan_excluded_paths and change the slash to nothing, i.e. delete the "/".

It worked for my ubuntu 10.04 pc, but not this one (ubuntu 9.1) - so I thought maybe there's another way...

---

### Post by cedardoc on 2010-05-27
I take that back - that last "fix" didn't work on 10.04 after all.

Any ideas?

---

### Post by kaibob on 2010-05-28
I don't believe that the gnome-search-tool will do exactly what you want. The following does work as a regular search term, but you apparently already knew that. 

```
word1*word3*
```

You can also use the regex option and search on the following, but once again you appear to have ruled that out.

```
word1.*word2
```

Perhaps another forum member will have a solution.

---

### Post by cedardoc on 2010-05-28
maybe regex wouldn't be a bad idea - it seems so arcane I thought it was out of reach for  me.  

How would you search for the words out of order though?  i.e. "word3 word1" (I have all these wordy descriptive files but don't always remember the right order)

Thanks,
Dave

---

### Post by kaibob on 2010-05-28
> **cedardoc said:**
> How would you search for the words out of order though?  i.e. "word3 word1" (I have all these wordy descriptive files but don't always remember the right order)

My knowledge of regex is extremely limited, but the only way I know to do this is:

```
word1.*word3|word3.*word1
```

---

### Post by cedardoc on 2010-05-28
that's it!  Thank you.  :)


Now my next step is to make a little Autokey script to take "word3 word1" and spit out what you just provided, and then send it to searchmonkey.

I'll post that here if I ever get it working.

---

