---
title: "unusal running process"
date: 2010-02-26
forum: General Help
---

### Post by VinyMac on 2010-02-26
I have pdfinfo & pdftotext that keeps running in my process. I don't even use pdf files or such. 

When i kill them in console they keep reopening back, and i don't know why.

It automatically loads around 1min after start up.
It takes around 25% resources of my Quad Core, and it is pretty annoying.

Anybody know why this is happening, or how i can kill / delete them for good... or see what is triggering them ?

[IMG]http://ubuntuforums.org/picture.php?albumid=1687&pictureid=5671[/IMG]

---

### Post by Enigmapond on 2010-02-26
Try to uninstall the package [poppler-utils ]("http://packages.ubuntu.com/karmic/poppler-utils")this is the package that is associated with both those programmes.

---

### Post by VinyMac on 2010-02-26
> **Enigmapond said:**
> Try to uninstall the package [poppler-utils ]("http://packages.ubuntu.com/karmic/poppler-utils")this is the package that is associated with both those programmes.

thanks for the quick reply 

when i go to synaptic-package manager, (i'm using ubuntu 9.10) & click to remove [poppler-utils]("http://packages.ubuntu.com/karmic/poppler-utils"), it requires to delete ubuntu-desktop ... i don't think this would be a good idea. Is there a workaround other than synaptic package manager ?

---

### Post by Enigmapond on 2010-02-26
not that I'm aware of but that ubunu-desktop is just a few apps and all you would need to do is just re-install it. It's not as drastic as it sounds and I have had that uninstalled and then re-installed it without any adverse effects. At least you would be rid of the offensive apps. It would probably be quicker in the terminal..

```
sudo apt-get purge poppler-utils
``````
sudo apt-get install ubuntu-desktop
```

---

### Post by VinyMac on 2010-02-26
> **Enigmapond said:**
> not that I'm aware of but that ubunu-desktop is just a few apps and all you would need to do is just re-install it. It's not as drastic as it sounds and I have had that uninstalled and then re-installed it without any adverse effects. At least you would be rid of the offensive apps. It would probably be quicker in the terminal..

```
sudo apt-get purge poppler-utils
``````
sudo apt-get install ubuntu-desktop
```

I followed those two steps, and everything is working fine. :)
Thanks, i really appreciate.

---

### Post by Enigmapond on 2010-02-27
Glad to be of service..:D You should mark the thread as solved in the thread tools.

Cheers!

---

### Post by gmargo on 2010-02-27
Removing the tool is merely masking the problem.  Who invoked that tool?  What PDF file was it working on?  What if you want to legitimately use that tool at the command line? It's probably the fault of clamtk, the virus scanner.

---

### Post by Enigmapond on 2010-02-27
> **gmargo said:**
> Removing the tool is merely masking the problem.  Who invoked that tool?  What PDF file was it working on?  What if you want to legitimately use that tool at the command line? It's probably the fault of clamtk, the virus scanner.

The OP stated he doesn't use PDF files. Why that tool was invoked? I have no idea but the end result was that it was gone and not using the CPU as it was for no apparent reason.

---

### Post by VinyMac on 2010-02-27
> **gmargo said:**
> Removing the tool is merely masking the problem.  Who invoked that tool?  What PDF file was it working on?  What if you want to legitimately use that tool at the command line? It's probably the fault of clamtk, the virus scanner.

i started using clam virus scanner after the problem occur... i was searching for a virus. :)

But indeed is there a way to see what triggers a process ?

---

### Post by VinyMac on 2010-02-27
.pdf files are still working... i have no use of them right now, but it might be useful some day... so this is a win win situation !!

I just want to say that i love the Ubuntu / Linux community. I moved on from MS Windows a few months ago, and was a little bit scared at first sight. But the spirit, the help, and kindness (witch isn't MS trademark) made me stayed on Ubuntu... 
I wouldn't go back now :), i love my OS, and the community, cheers to *yall*

---

