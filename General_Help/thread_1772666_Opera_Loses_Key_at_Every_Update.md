---
title: "Opera Loses Key at Every Update"
date: 2011-05-31
forum: General Help
---

### Post by jamesisin on 2011-05-31
I install and update Opera using this method:

[http://jamesisin.com/a_high-tech_blech/index.php/2008/09/add-opera-to-ubuntus-update-manager-synaptic/](http://jamesisin.com/a_high-tech_blech/index.php/2008/09/add-opera-to-ubuntus-update-manager-synaptic/)

Works great.  I am notified of updates and everything.

Problem is that lately when I run an update to Opera the key is deleted from Software Sources.  This happens on several systems (10.04 and 9.10 at least) and happens each time I update Opera.

I install the key again, of course, and the next update deletes the key.

Any suggestions?

---

### Post by linuxinstalledfromhdd on 2011-05-31
Go into synaptic and remove the repository, and reload synaptic to save the changes.

In synaptic goto Settings, and then Repositories. Look for the repository you originally installed and uncheck it and then click on 'reload' synaptic to refresh everything.

Now we are going to reinstall it so the key will always be there from now on:

Cut and paste into your terminal:
```
sudo sh -c 'echo "deb http://deb.opera.com/opera/ stable non-free" >> /etc/apt/sources.list.d/opera.list' sudo sh -c 'wget -O - http://deb.opera.com/archive.key | apt-key add -' sudo apt-get update sudo apt-get install opera
```If you are looking for more guides to get your system configured check out:

11.04
[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

10.10
[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by jamesisin on 2011-06-01
Your first paragraph tells me to remove the repo.  Your second tells me to uncheck it.  I can't uncheck it if I've removed it.  Please clarify your instructions.

Can you offer some insight into why the key is vanishing?

---

### Post by jamesisin on 2011-06-04
Hello?

---

