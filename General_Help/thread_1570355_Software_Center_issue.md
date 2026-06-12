---
title: "Software Center issue"
date: 2010-09-08
forum: General Help
---

### Post by PRC1014 on 2010-09-08
I just moved to China from the US, and before it worked and now it doesn't. Whenever I attempt to install a new application is sends me a message saying: The action would require the installation of packages from not authenticated sources. I uninstalled the alarm clock app and tried to reinstall to try and download a program I knew worked and received the same message. Update Manager works, but gave me a similar message but I was still able to download. My more tech savvy friend had used this box previously while we tried to set up a server back in the States so I am unsure what if any changes had been made to my connection, and he has been unavailable for me to ask. Ideas?

---

### Post by sikander3786 on 2010-09-08
Try changing the download server from System >>> Administration >>> Software Sources. Set it to Main preferably, then update.

```

sudo apt-get update

```

And then try to install some software from terminal and post back the errors if any. e.g,

```

sudo apt-get install vlc

```

Regards.

---

### Post by PRC1014 on 2010-09-08
spot on solution there, I'm very appreciative. turns out the server was set to Mexico.

---

