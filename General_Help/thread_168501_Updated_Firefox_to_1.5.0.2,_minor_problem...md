---
title: "Updated Firefox to 1.5.0.2, minor problem.."
date: 2006-04-30
forum: General Help
---

### Post by Poka64 on 2006-04-30
Well, I updated Firefox 1.5.0.1 to 1.5.0.2 and everthing works fine, except that I can't get rid of the sucessful update page, the one that tells you that you sucessfully updated to the latest version. 

How do I fix this so I don't have to see this every time I have to use Firefox, I want to see my "homepage" when I start Firefox.

---

### Post by towsonu2003 on 2006-04-30
which method did you use to update? sudo, ksudo, or chown?

---

### Post by Poka64 on 2006-04-30
I used chown, I used this guide: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

"The first way is to close Firefox and give your user (yourself) file ownership: sudo chown -R ${USER}:${USER} /opt/firefox Start Firefox normally and update (Help -> Check for updates...) Once the update is completed, close Firefox and then restore ownership to root: sudo chown -R root:root /opt/firefox Do NOT browse other sites while firefox has these elevated permissions, that is without changing back the ownership of /opt/firefox over to root. Such a practice is not safe."

---

