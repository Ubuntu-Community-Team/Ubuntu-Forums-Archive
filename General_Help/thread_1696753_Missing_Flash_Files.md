---
title: "Missing Flash Files"
date: 2011-02-27
forum: General Help
---

### Post by macoklein on 2011-02-27
Hi Everyone,
For years now I have been able to download youtube files by moving them from the /tmp directory. However, after upgrading to 10.10 the signature Flash* files no longer show up in the /tmp directory. 

Could this be something wrong with my flash settings?
Is this a problem with Chrome?

Thanks for the help.

---

### Post by Verbeck on 2011-02-27
see if it's in the browser's cache directory
~/.cache/chromium/Default/Cache/
~/.cache/chrome/Default/Cache/
~/.mozilla/firefox/xxxxxxx.default/Cache/

---

### Post by macoklein on 2011-02-27
They dont seem to be there either. 
Also I dont have a .chromium/ or .chrome/ directory. Only a .google-chrome/ directory. In those directories, I found quite a few files in the Default/Cache or Default/Media Cache directories but none of the files seemed to change with opening Flash videos.

---

### Post by steve161 on 2011-02-27
It was the most recent adobe flash upgrade that changed what directory it is in.  Not really familiar with chrome but, as Verbeck stated, it should be in your browser cache.

---

### Post by Verbeck on 2011-02-27
also, the files are not  named like FLASHXXXX so you'll need to look for the 'flash vedio' file type

---

### Post by macoklein on 2011-02-27
How would I search for a specific file type?

---

### Post by Verbeck on 2011-02-27
something like
```

find /path/to/cache/directory/ -type f -exec file -i {} \; | grep 'video/x-flv'

```

---

