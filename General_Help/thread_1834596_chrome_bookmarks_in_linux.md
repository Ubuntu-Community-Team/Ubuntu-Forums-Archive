---
title: "chrome bookmarks in linux"
date: 2011-08-27
forum: General Help
---

### Post by rajohns08 on 2011-08-27
how do i change where chrome pulls it's bookmark info from in linux? i changed it on my laptop and desktop in windows by both pulling from a dropbox folder so every time bookmarks are changed on one computer it changes them on all. how do i do this on ubuntu with chrome?

---

### Post by SavageWolf on 2011-08-27
Chrome has a synchronisation service which you can use, [http://www.google.com/support/chrome/bin/answer.py?hl=en-GB&answer=165139&from=165140&rd=1](http://www.google.com/support/chrome/bin/answer.py?hl=en-GB&answer=165139&from=165140&rd=1)

---

### Post by captain_171 on 2011-08-27
The info after the --user-data-dir= is where your profile will go.

```
/opt/google/chrome/google-chrome --enable-udd-profiles --user-data-dir=/home/dude/Dropbox/profiles/googlechrome
```

Make sure your google chrome is in the /opt/google/chrome/google-chrome if not change that to the other location. If you don't know where it is type in the command line. 
```
whereis
```

My google-chrome is in /usr/bin/google-chrome

---

### Post by rajohns08 on 2011-08-27
> **SavageWolf said:**
> Chrome has a synchronisation service which you can use, [http://www.google.com/support/chrome/bin/answer.py?hl=en-GB&answer=165139&from=165140&rd=1](http://www.google.com/support/chrome/bin/answer.py?hl=en-GB&answer=165139&from=165140&rd=1)

thanks i guess i can just use this. i normally use ie9 on my windows machines but swapping across to chrome won't be much of a difference.

---

