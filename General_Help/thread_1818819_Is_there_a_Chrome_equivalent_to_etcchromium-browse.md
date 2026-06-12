---
title: "Is there a Chrome equivalent to /etc/chromium-browser/default?"
date: 2011-08-05
forum: General Help
---

### Post by nrundy on 2011-08-05
chromium has a file at /etc/chromium-browser called "default" where users can set flags for chromium. 

Is there any equivalent for the Google Chrome browser? Is there a place to set flags that affect every running instance of the Chrome browser?

---

### Post by nrundy on 2011-08-06
bump

---

### Post by AlphaLexman on 2011-08-06
I have a file at '/etc/default/google-chrome'
```
 $ cat /etc/default/google-chrome

repo_add_once="false"
repo_reenable_on_distupgrade="true"

```
Using Chrome 13.0.782.107

---

### Post by nrundy on 2011-08-06
This doesn't appear to be the same thing, though.

Would any harm come if I added this line to the file, I wonder?: CHROME_FLAGS="--disable-webgl"

The problem though is I don't even know what to call chrome. "GOOGLE-CHROME_FLAGS"  "CHROME_FLAGS"

---

### Post by AlphaLexman on 2011-08-06
I found [this]("http://www.google.com/support/forum/p/Chrome/thread?tid=2383fa32b4c65fa9&hl=en").
And, fwiw, the actual binary is '/usr/bin/google-chrome'

I executed the binary with the '--disable-webgl' option and didnot get any errors, although I don't know what it was supposed to do!

---

### Post by nrundy on 2011-08-06
hmm. Thanks for this. I thought of doing this but was wondering why Chromium has a file specifically for adding flags. Why doesn't Chrome has such a file?

I'll try the --incognito flag on the binary and see if it works. It's a flag that I can see the result of :)

> **AlphaLexman said:**
> 
I executed the binary with the '--disable-webgl' option and didnot get any errors, although I don't know what it was supposed to do!

How exactly did you attach the flag to the binary? the file at /usr/bin links to /opt/google/chrome/google-chrome. But I don't see any flag language in the file like I saw in the chromium file.

---

