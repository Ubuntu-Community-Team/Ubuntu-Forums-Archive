---
title: "file access denied monitoring"
date: 2011-06-25
forum: General Help
---

### Post by goosecrossing on 2011-06-25
I am looking for a file monitor to tell me when a file was attempted to be accessed, but was denied.

A windows equivalent could be the auditing feature in server 2k3.

I don't know which account or which file is attempting to access or be accessed, but I was hoping something built into Linux would support some sort of file auditing for security purposes.

Any ideas???
Thank you,
Goose

---

### Post by Abir Valg on 2011-06-25
The feature you are after is called "inotify". You may want to look that up with
[http://startpage.com]("http://startpage.com")

---

### Post by goosecrossing on 2011-06-25
Thanks. Is there a GUI for this? I don't mind trying to do C programming to make this work, but it seems a bit advanced just to troubleshoot a permission issue on a file.

Again, thanks for the advice!

-Goose

---

