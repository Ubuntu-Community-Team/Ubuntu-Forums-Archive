---
title: "Cant mount Ipod Touch"
date: 2011-02-04
forum: General Help
---

### Post by HooKTroniC on 2011-02-04
When I plug the ipod in I get the following error message 
"DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"

Amarok sees the ipod but cant access it. Gtkpod doesnt see it at all. 
 Its an Ipod Touch 8GB, 2nd or 3rd gen, not sure, it was given to me.
Any help would be greatly appreciated.

---

### Post by I&#9829;HTML5 on 2011-02-06
Open up your terminal and run```
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```
(from [http://ubuntuforums.org/showpost.php?p=10415969&postcount=131](http://ubuntuforums.org/showpost.php?p=10415969&postcount=131))

---

### Post by |{urse on 2011-03-02
will this work with the ipt4g on 4.2.1?

---

### Post by I&#9829;HTML5 on 2011-03-06
It should. I suppose the best way to find out is to try it.

---

