---
title: "Terminal-Free Python"
date: 2010-03-04
forum: General Help
---

### Post by SoulMazer on 2010-03-04
Hi, I've made a Python script that I would like to add a shortcut to in my quick-launch panel. Except, I'm having a little trouble. I assume this is because it does not like it when I launch my program without a controlling terminal (even though the script has a full GUI). I know that on Windows I can simply run my script with "pythonw" or change the extension to ".pyw", but since GUN/Linux doesn't care for extensions, how can I do this without running it via a terminal?

Thanks in advance.

---

### Post by tgalati4 on 2010-03-04
What's the first line of your script?

---

### Post by zine92 on 2010-03-04
i think you just need to make the file name as .py and add this to the first line of your script.
```
#!/usr/bin/python
``` and make sure to make your file permission as executable. right click on the script then properties and under permission tick the Allow executing files as a program.

---

### Post by SoulMazer on 2010-03-05
Haha wow! Sorry, but I just made a boneheaded mistake. I do have the correct shebang and permissions, but I had a different problem. My script imports some of my other local scripts and since I usually run my script from a certain directory, I forgot to change the working directory from within my script.

I apologize for the inconvenience, however thanks for the fast responses.

Problem solved.

---

