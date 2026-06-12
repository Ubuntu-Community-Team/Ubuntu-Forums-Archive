---
title: "Ubuntu server php Problem"
date: 2009-08-02
forum: General Help
---

### Post by Thought_Crime on 2009-08-02
I have a problem I am using ubuntu 8.10 server edition with it configured to be a LAMP server but for some reason the server is not processing the php files and just displaying the files to the browser when requested

Any ideas?

Please ask if you need more information

---

### Post by credobyte on 2009-08-02
Try:
```
sudo apt-get install php5 libapache2-mod-php5 && sudo /etc/init.d/apache2 restart

```

Nothing have changed ? Try:
```
sudo apt-get remove --purge php5 && sudo apt-get install php5 && sudo /etc/init.d/apache2 restart
```

---

