---
title: "Network pritner install problem"
date: 2011-02-21
forum: General Help
---

### Post by nbo10 on 2011-02-21
Hi all,
I have set up a local server running 10.04. I have cups installed and running. I can access the server via 192.168.28.200:631 webapoge. I can print test pages from that site. But when I try installing the networked printer on a client, the printer will install but I can't get the test page to print. Any ideas on what I should check.

---

### Post by wt8008 on 2011-02-26
Your next step would be to take a look at the log files for cups, they are located in:
  /var/log/cups
look in access_log, error_log, and page_log and see if you find any error messages or access denied messages. If you do you can try to search on how to configure cups for network access. 

If you don't see the other computer accessing the CUPS server, then the problem is from the client end. If you can see the client sending print jobs over, then it is most likely that there is an issue with the CUPS server. 

If you see an error message then that is easier to Google the message to fix the issue.

---

