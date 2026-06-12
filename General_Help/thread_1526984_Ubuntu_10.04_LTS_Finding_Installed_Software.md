---
title: "Ubuntu 10.04 LTS Finding Installed Software"
date: 2010-07-08
forum: General Help
---

### Post by 55 62 75 6E 74 75 6D 65 on 2010-07-08
Why is it that some software isn't in the Ubuntu Software Center's installed software list and must be searched for. Is the presented list a comprehensive list for applications only, or does it categorize software some other way. I am a bit uncertain about this since both image magick (a command line "application) and xvfb needed to be searched for in order to appear. Is their a way to get a complete listing of different types (and if necessary all) of the software installed on your system. Please help.

Thank you

---

### Post by nothingspecial on 2010-07-09
```
dpkg --get-selections | grep install
```

or

```
dpkg-query -l
```

---

### Post by 55 62 75 6E 74 75 6D 65 on 2010-07-09
Thank you! -> [SOLVED]

---

### Post by nysnsweet on 2011-06-27
Hi i did this, but the list went to fast that I couldn't read it and when I move the cursor button up, it does not go to the top of the page...how can I view the beginning list of installed software from this command?

---

### Post by Karlchen on 2011-06-27
Hello, nysnsweet.

Try ```
dpkg --get-selections | grep install | more
dpkg-query -l | more
``` please.

Kind regards,
Karl

---

### Post by nysnsweet on 2011-06-27
This definately helps!  Thank you.

:)

---

