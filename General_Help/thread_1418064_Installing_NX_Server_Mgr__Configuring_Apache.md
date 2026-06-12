---
title: "Installing NX Server Mgr / Configuring Apache"
date: 2010-02-28
forum: General Help
---

### Post by TehKivin on 2010-02-28
I'm following this guide: [http://www.nomachine.com/documents/manager/install.html](http://www.nomachine.com/documents/manager/install.html)

However, there are a few things which are over my head.
[B]
_Section 6.1 - Configuring the Web Server to Run NX Server Manager_[/B]
"... adding the following directive before the *Global Environment* section"

What I've done is:
* **sudo gedit /etc/apache2/apache2.conf**
* Inserted ***Include /usr/NX/etc/manager.conf***just before ***### Section 1: Global Environment***


**_Section 6.2 - Configuring NX Server Manager_**"... you should ensure that the following keys are set according to the configuration of the Web Server on your system"

It wants me to correct the **ApacheUname** and **ApacheGname** in [B]/usr/NX/etc/manager.cfg
[/B]However, I haven't the faintest idea what these are.

Thanks for looking.  Thanks +1 for assisting if you can clarify this.

---

