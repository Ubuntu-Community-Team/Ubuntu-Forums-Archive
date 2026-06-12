---
title: "team viewer/how to restart computer"
date: 2010-09-30
forum: General Help
---

### Post by elephant99 on 2010-09-30
i am having trouble connecting on teamviewer to my home computer. i can do file transfer but remote access is not working. is there a way i can transfer a file that can restart my home computer or any way i can restart my home computer through the internet?

---

### Post by HermanAB on 2010-09-30
Well, you discovered one more reason why you should use SSH and not Teamviewer...

You could try uploading a bash script containing the command 'reboot' and placing it in the /etc/cron.hourly directory, but you need to make it executable.

---

