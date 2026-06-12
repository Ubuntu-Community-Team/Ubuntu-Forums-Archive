---
title: "Synaptic Package Manager not installed"
date: 2009-08-08
forum: General Help
---

### Post by applefox on 2009-08-08
Hello. I just installed kubuntu on my laptop and Synaptic is not installed. Can you please direct me on how to do this? I just directly installed kubuntu. Gnome is not and has not been installed on here. Thanks in advance.......
                                                                                                                                                                                                      ~applefox

---

### Post by michy99 on 2009-08-08
Kubuntu uses Adept instead of Synaptic. If you want Synaptic, open a terminal (I think Kubunutu calls it a konsole) and enter```
sudo apt-get install synaptic
```

---

### Post by applefox on 2009-08-08
Thank you but I get this. 

"Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate"

---

### Post by harry2006 on 2009-08-08
the error means its not available in the repo configured in your repo list, 
are you sure all the basic repos are added properly in /etc/apt/sources.list ?

---

### Post by MickS on 2009-08-08
When I had this problem I used Kpackagekit to download and install synaptic, try that it worked for me, been using Synaptic ever since.


Mick

---

### Post by applefox on 2009-08-15
Ok I will try this thank you.

---

