---
title: "find files with an extension, then mail the results"
date: 2011-07-02
forum: General Help
---

### Post by Kissell on 2011-07-02
Is there an easy way to do a recursive command line search on a path for a particular type of file extension?  

I want to build a script that will check for the existence of any .xxx files in a recursive path, if they exist, I would like to run the "mail" command to send me a message.  I already have mail running on the server.

My thoughts were to try
> 
ls -R |grep .ini


or
> 
find . |grep .ini


but neither of those return only the .ini files, they also return files that are named such as .ini.bak, .ini.original, .ini.old, ect...

---

### Post by sam_delta on 2011-07-02
try ```
find . -name *.ini
``` 

Note that if you would like to search the entire filesystem, replace the first dot with a '/'

sam

---

### Post by Kissell on 2011-07-02
Thanks a lot!  That works much better!

---

