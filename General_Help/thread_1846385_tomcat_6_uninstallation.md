---
title: "tomcat 6 uninstallation"
date: 2011-09-18
forum: General Help
---

### Post by mdt90 on 2011-09-18
hi,

i had  downloaded tomcat6.0.33.tar.gz file from the apache site.then i executed the
tar xvzf ....to extract that file.

now,i want to uninstall it completely because the older version of tomcat which i am using is unable to acquire the database.i have the following error-
java.sql exception:socket creation error

can somebody explain me the reason of this error?how can i delete 6.0.33  completely.

my application worked well with older tomcat version before extracting this newer one

---

### Post by Dangertux on 2011-09-18
You will likely have to fully uninstall the newer version of Tomcat and reinstall the old version that worked for you. I don't think you can just roll back.

However, about that error can you show the full trace? If you can it might tell you what the issue is.

---

### Post by mdt90 on 2011-09-19
hey ,

i Just figured  out the reason of the error. database exception error was thrown because i was not privileged to do that task. i logged in as superuser and then i could run the application without any  problem.

now,i just have to uninstall the latest version of tomcat.thanks!

---

