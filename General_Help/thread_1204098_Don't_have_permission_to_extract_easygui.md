---
title: "Don't have permission to extract easygui"
date: 2009-07-04
forum: General Help
---

### Post by Nubi505 on 2009-07-04
I'm using Ubuntu 9.04 and working with Python 2.6. I'm the only user on my Ubuntu OS and I need to be able to extract the easygui files into the usr/local/lib/python2.6/dist-packages. However, when I tell the extractor to extract the files to that folder it says: "You don't have the right permissions to extract archives in the folder "file:///usr/local/lib/python2.6/dist-packages" " Which is rather frustrating. 

I followed the instructions from [ [easygui on sourceforge] ]("http://easygui.sourceforge.net/current_version/index.html") with the whole "sudo chmod 755 /usr/local/lib/python2.6/dist-packages" but it didn't do anything :/ 

So how do I get permission to extract easygui into the dist-packages folder? Even if I need to *temporarily* give myself permissions. I read on the forums that owning certain directories is dangerous?

I'd really appreciate the help!

Thanks.

---

### Post by blueridgedog on 2009-07-04
If you are trying to extract the files via nautilus, perhaps starting it as root may carry the user privileged to the extraction:

sudo nautilus

Otherwise, you can extract them from the terminal with sudo:
```
sudo cp myfile.tgz /usr/local/lib/python2.6/dist-packages
sudo cd /usr/local/lib/python2.6/dist-packages
sudo tar xvfz ./myfile.tgz
```

---

### Post by Nubi505 on 2009-07-04
To be honest, I'm  not sure what nautilus is. So I dunno about that. I'm using the default extractor that comes with Ubuntu, if that is any help. 

I tried to follow your instructions, but I can't get past the first line. What is "myfile.tgz" supposed to be? The name of the downloaded easygui file? Either way, it comes up saying no such directory. I replaced myfile with the name of downloaded file/folder/archive and same error. Btw, I'm a total terminal noob.

---

### Post by michy99 on 2009-07-04
If you want to use the default extractor with root permissions, open a terminal and enter```
gksudo file-roller
```You can then open the archive and extract it wherever you want.

---

### Post by Nubi505 on 2009-07-04
Thanks michy99! It extracted and easygui is working in python. <3 Appreciate the help.

And thank you blueridgedog for your help too.

---

