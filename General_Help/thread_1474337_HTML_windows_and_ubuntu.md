---
title: "HTML windows and ubuntu"
date: 2010-05-06
forum: General Help
---

### Post by sxmaxchine on 2010-05-06
hello as you probably know that in ubuntu you use / in the explorer (nautilus) and in windows you use \.

When you make web pages in html you need to link to pages in folders using either \ in windows and / in Linux. My program is made on windows and needs to run on windows but when i try to open it on my Ubuntu pc i need to change the \ to /.

Is there a simple way to do this without having to edit the code.

Thanks in advance for the help.

---

### Post by WorMzy on 2010-05-06
I don't understand. You don't use back slashes in webpages, regardless of whether you're on Windows or Linux, or whatever..

```
<html>
  <head>
  </head>
  <body>
    <a href="folder/page.html">A link</a>
  </body>
</html>
```

Will work the same on any browser, on any OS.

---

### Post by sxmaxchine on 2010-05-06
thanks for the tip, i have been using backslashes on the pages i creat in windows.

---

### Post by John Bean on 2010-05-06
> **sxmaxchine said:**
> thanks for the tip, i have been using backslashes on the pages i creat in windows.

That's completely wrong. The only reason it works is that Windows browsers automatically substitute the slash for a backslash by default because it's a common user error due to its use inside Windows for that purpose.

---

