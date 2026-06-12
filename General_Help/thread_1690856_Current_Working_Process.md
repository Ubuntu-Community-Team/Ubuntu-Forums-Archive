---
title: "Current Working Process"
date: 2011-02-19
forum: General Help
---

### Post by phanie on 2011-02-19
I'm sorry about my last thread. I guess it offended some of the higher ups here. LOL.

Is there a way that a current working process be viewed in Ubuntu? Such that when an application is open, say Mozilla Firefox, it can be viewed and used in a conditional script such that MozillaFirefoxOpen=yes or MozillaFirefoxOpen=No? I guess this is the second to the last thread I am going to post so bear with me guys.

The project I am working on, which I am planning to post here, will hopefully benefit all us guys.

---

### Post by 3rdalbum on 2011-02-19
firefox-bin appears in the output of the 'ps aux' command, which can be searched with 'grep':

```
ps aux | grep "firefox-bin"
```

This will return one line ('grep "firefox-bin"') if Firefox is not open, or two lines if Firefox is running. You just have to count the lines. Pretty sure there's a command to count the number of lines in stdin, but I don't know what it is.

---

### Post by TeoBigusGeekus on 2011-02-19
```
#!/bin/bash
if test $(pidof firefox-bin)
then echo Firefox running
else echo Move along - nothing to see here...
fi
```

---

### Post by phanie on 2011-02-19
Thank you 3rdalbum and TeoBigusGeekus. You guys are of great help.:KS

---

