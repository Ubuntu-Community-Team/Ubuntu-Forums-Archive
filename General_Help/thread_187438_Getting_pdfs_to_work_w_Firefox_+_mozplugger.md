---
title: "Getting pdfs to work w/ Firefox + mozplugger"
date: 2006-06-03
forum: General Help
---

### Post by drewyates on 2006-06-03
This took me forever to solve, but here is the problem and the solution for others:

In Dapper Drake, I used apt-get to install acroread and thefirefox plugin. BUT firefox didn't seem to recognize the plugin and would still ask how to handle pdfs.

I tried installing mozplugger, but then pdf files would open in a tab but wouldn't display. The window would be blank and there would be no error message.

To fix this, I complete uninstalled mozplugger, acrobat, and the acrobat plugin. Then, I manually installed Acrobat from the Adobe website. In the adobe install script, I was prompted to install / reinstall the pdf firefox plugin (which I did).

pdfs now correctly displayed in firefox tabs.

I then re-apt-get'ed mozplugger, and both plugins now work.

I hope this helps!

---

### Post by bluevoodoo1 on 2006-06-03
Great, I was just thinking about this today. I'll test it later on and see if I can get it working here.

EDIT: So far so good. It's working well. Thank you!

---

