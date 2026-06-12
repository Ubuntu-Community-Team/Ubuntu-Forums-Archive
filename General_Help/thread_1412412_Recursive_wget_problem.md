---
title: "Recursive wget problem"
date: 2010-02-21
forum: General Help
---

### Post by oygle on 2010-02-21
I'm trying to download a set of files with wget, and I only want the files and paths "downwards" from a URL, that is, no other files or paths.

Here is the comand I have been using

```

wget -r -np --directory-prefix=Publisher http://xuups.googlecode.com/svn/trunk/modules/publisher

```

There is a local path called 'Publisher'. The wget works okay, downloads all the files I need into the /Publisher path, and then it starts loading files from other paths.

If you see [http://xuups.googlecode.com/svn/trunk/modules/publisher](http://xuups.googlecode.com/svn/trunk/modules/publisher) , I only want those files, plus the paths and files beneath that URL.

Thanks,

Oygle

---

### Post by dwhitney67 on 2010-02-21
This is not really a programming question, so I'm not quite sure why you chose this forum.

Anyhow, to resolve the issue you are having, add a / character to the end of your command statement:
```

wget -r -np --directory-prefix=Publisher http://xuups.googlecode.com/svn/trunk/modules/publisher**/**

```

---

### Post by oygle on 2010-02-22
Thanks, that did the trick.

---

