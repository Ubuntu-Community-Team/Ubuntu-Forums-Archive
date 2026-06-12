---
title: "Webserver setup"
date: 2010-03-30
forum: General Help
---

### Post by Datamac on 2010-03-30
I am stuck at the ending point of setting up a web server to do virtual hosting for 3 sites.  I have created the individual virtual host files and think that they are stored in the correct directories.  I am unable to run a2ensite to finish this step of the process.  Can anyone here help me understand the last two steps in the process.  I am following the tutorial at: [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

### Post by rudy.b on 2010-03-31
a2ensite requires root permissions.  Did you precede the command with sudo?  i.e. ```
sudo a2ensite www.example.com
```  If that's not the issue, please describe what the system response is when you issue the command.  Is there an error message?

---

