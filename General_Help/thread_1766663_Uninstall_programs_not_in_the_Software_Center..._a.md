---
title: "Uninstall programs not in the Software Center... and a couple other questions"
date: 2011-05-24
forum: General Help
---

### Post by Kruger2147 on 2011-05-24
There are a few applications that I have installed via ppa, Terminal and .deb files that are not in the Software Center when I look for them. i don't want them anymore, how do I uninstall them?

Also, in Thunderbird, when I reply to an email the cursor goes to the bottom of the message and I have to manually put it to the top and press enter a few times to get some space. How/ can I change it so it automatically does this? 

Last thing, In thunderbird, I have several emails set up as well as RSS feeds, I wanna reorganise the order, I've looked around in settings and tried to drag them, but it doesn't work. How can I reorganise my accounts and RSS feeds? 

I'm running Natty 32bit.

---

### Post by Frogs Hair on 2011-05-24
You can remove the applications from the Synaptic Package Manager . Locate them with the search , right click an the line they appear , mark for complete removal and select apply . From the same application go to settings > repositories > other software and remove the PPA sources from the list.

---

### Post by linuxinstalledfromhdd on 2011-05-24
If you are going to remove a PPA, make sure to use PPA purge from the command line.

---

### Post by Kruger2147 on 2011-05-24
ppa purge from command line... how?

---

### Post by akand074 on 2011-05-24
> **Kruger2147 said:**
> ppa purge from command line... how?

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:whatever/whatever
```

Where 'ppa:whatever/whatever' is replaced with the ppa name. This will remove the ppa from your software sources as well as uninstall all applications associated with it I believe.

---

### Post by nickleboyblue on 2011-05-24
One more thing: if you compiled the program yourself, i.e. downloaded a .tar file, uncompressed it, and ran "make" and "make install,"  you'll have to look up where the files got sent and delete them manually.  I had to do this to get rid of a build of Asterisk that wasn't working properly.

---

### Post by akand074 on 2011-05-24
> **nickleboyblue said:**
> One more thing: if you compiled the program yourself, i.e. downloaded a .tar file, uncompressed it, and ran "make" and "make install,"  you'll have to look up where the files got sent and delete them manually.  I had to do this to get rid of a build of Asterisk that wasn't working properly.

Not true actually. If you still have the folder you can run "make uninstall" and it'll uninstall automatically (maybe not in all cases?). Also those packages made from "make install" also come up in Synaptic Package Manager if I'm not mistaken.

---

