---
title: "thank you, tasksel -_-; phpmyadmin not found"
date: 2011-05-31
forum: General Help
---

### Post by LiteDrive on 2011-05-31
Yup. 

When I type "apt-get install ubuntu-desktop", it just reports the following: 

```

ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

Does this mean that I was lucky, and DIDN'T fall victim to the Tasksel Uninstall desktop --purge bug? 

This is the only thing which makes me think that I could have screwed up my lampsserver install. I ended up having problems after my first install of tasksel LAMP (I couldn't access phpmyadmin for some reason). So, I uninstalled it using tasksel, and tried to reinstall the packages separately via command line. 

Seemed to work fine, until I loaded phpmyadmin and I receive just another 404. 

Is there any idea what could be wrong here? I've been searching the net for the past 30 minutes here to no avail. I've tried numerous tutorials, and am somewhat paranoid to wonder IF for some reason (one way or another) I may have fell victim to this tasksel bug which I only just read about *after* I uninstalled it. Go figure, right?

---

### Post by wildmanne39 on 2011-05-31
> **LiteDrive said:**
> Yup. 

When I type "apt-get install ubuntu-desktop", it just reports the following: 

```

ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

Does this mean that I was lucky, and DIDN'T fall victim to the Tasksel Uninstall desktop --purge bug? 

This is the only thing which makes me think that I could have screwed up my lampsserver install. I ended up having problems after my first install of tasksel LAMP (I couldn't access phpmyadmin for some reason). So, I uninstalled it using tasksel, and tried to reinstall the packages separately via command line. 

Seemed to work fine, until I loaded phpmyadmin and I receive just another 404. 

Is there any idea what could be wrong here? I've been searching the net for the past 30 minutes here to no avail. I've tried numerous tutorials, and am somewhat paranoid to wonder IF for some reason (one way or another) I may have fell victim to this tasksel bug which I only just read about *after* I uninstalled it. Go figure, right?
Hi, that usually means what you were trying to view on the web is not there anymore or on the server.

---

### Post by LiteDrive on 2011-05-31
Hi, thanks for your reply. While that would naturally be the first thing to consider, I am well aware of that and have been trying many different methods to get this up and running, one being editing my apache2.conf file and including the phpmyadmin directory to it. Multiple attempts at installing and reinstalling not only phpmyadmin but the entire web server have been made as well. 

So, despite all of this, I'm very stumped.

---

### Post by LiteDrive on 2011-05-31
Hmm, I kind of feel like I'm being ignored here. If that's the case, it'd be nice to at least know why.

---

