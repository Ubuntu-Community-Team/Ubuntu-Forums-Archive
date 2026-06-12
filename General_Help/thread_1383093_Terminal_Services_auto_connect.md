---
title: "Terminal Services auto connect"
date: 2010-01-16
forum: General Help
---

### Post by nmyrick on 2010-01-16
I currently have a startup application that automatically runs the Terminal Server Client at startup.  

Can anyone help me out by telling me what command I need to enter into the startup app that would make it automatically connect?

---

### Post by AlexDBall on 2010-01-16
Hi, I think that what you need is rdekstop (installed by default as far as i know)

rdesktop is a command line app which i think is the backend for tsclient. (correct me if i'm wrong)

To connect to a remote host automatically run the following command:
```
rdesktop *hostname* or *IP_Address *of server
```

Hope this helps!

---

