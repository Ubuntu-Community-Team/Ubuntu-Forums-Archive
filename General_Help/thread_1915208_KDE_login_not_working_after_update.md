---
title: "KDE login not working after update"
date: 2012-01-25
forum: General Help
---

### Post by davidsrsb on 2012-01-25
This laptop was running Kubuntu 11.10 just fine.
After recent updates the login dialog triggers a terminal window very briefly and then retrurns to the login. If I crash out of X back to the command promp I can login, so I know the password store is OK.

---

### Post by davidsrsb on 2012-01-26
Solved
Having read of others with this a year ago when KDE 4.6 came out, I ran

sudo apt-get install kubuntu-desktop

and found 60 packages to install. The update had managed to delete several packages and fail to reinstall

---

