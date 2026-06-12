---
title: "Archiving many(&gt;100000) files into a single file via cli"
date: 2011-03-04
forum: General Help
---

### Post by kafka201 on 2011-03-04
I'm trying to zip or rar >100000 files into a single file so that I can upload it to my server much faster than ftp downloaded it.  Total they're all only 4gb, but because of the number of files Nautilus freezes just opening the folder they're in.  They're all .jpgs and all in the same folder and I've tried a few commands but I keep getting error messages.  

Anyone have a command that will archive all the files from a folder into a single zip (or rar, tar etc)?  I can't just archive the folder because then I would have to move all the files out of that folder and just opening the folder to move them would crash it, and I don't have ssh into that server.

Thanks

---

### Post by turtle153 on 2011-03-04
There is the **zip** command that creates *.zip files
```

cd folder_with_files
zip name_of_archive.zip *

```
(The * adds all files)

---

### Post by gmargo on 2011-03-04
> **turtle153 said:**
> (The * adds all files)
Likely to fail on such a large directory, because there is a limit on the length of a command line.  But you could use the -r option for recursion.
```

cd folder_with_files
zip -r /tmp/name_of_archive.zip .

```Since tar was one of your options, why not use that?   Since they're .JPG files, you won't significantly benefit from zip's compression.
```

cd folder_with_files
tar cf /tmp/name_of_archive.tar .

```

---

### Post by kafka201 on 2011-03-04
Thanks for the help, turtle153's command did the trick, they're nicely zipped up and it's being uploaded to the server now.  Gmargo I used zip because I knew for sure it would work on my server, I'm not completely sure what capabilities my hosting company's software had and I can't really install server software onto it, so I played it safe with something I knew worked.

Thanks again

---

