---
title: "Chromium browser fails to start up"
date: 2009-09-08
forum: General Help
---

### Post by MountainX on 2009-09-08
Chromium fails to start up on Ubuntu Jaunty amd64. I installed for the first time today. The browser never opens. Anyone else seeing this?

```
~$ chromium-browser
[20532:20535:23098451160:FATAL:/build/buildd/chromium-browser-4.0.207.0~svn20090907r25598/build-tree/src/chrome/browser/renderer_host/async_resource_handler.cc(145)] Check failed: read_buffer_->data(). 
Trace/breakpoint trap
~$ [3:4:23098474330:ERROR:/build/buildd/chromium-browser-4.0.207.0~svn20090907r25598/build-tree/src/ipc/ipc_channel_posix.cc(451)] pipe error (9): Connection reset by peer

$ ident /usr/lib/libnss3.so.1d
/usr/lib/libnss3.so.1d:
     $Header: NSS 3.12.3.1 Basic ECC  Aug 25 2009 00:27:14
```


solved. see [http://ubuntuforums.org/showpost.php?p=7917536&postcount=12](http://ubuntuforums.org/showpost.php?p=7917536&postcount=12)

---

### Post by darco on 2009-09-08
I upgraded to the same build earlier today and all seems well.....have you tried uninstalling then reinstalling?

darco

---

### Post by MountainX on 2009-09-08
> **darco said:**
> I upgraded to the same build earlier today and all seems well.....have you tried uninstalling then reinstalling?

darco

yes, tried that. 

Is there a settings for config file from Chromium? I can't find one. I'd like to make sure it is deleted when I uninstall and reinstall.

---

### Post by darco on 2009-09-08
Chromium installs in the usr/lib/chromium-browser folder if thats what you are asking..

darco

---

### Post by MountainX on 2009-09-08
> **darco said:**
> Chromium installs in the usr/lib/chromium-browser folder if thats what you are asking..

darco

Thanks but , no, I was asking where it keeps its settings (like ~/.mozilla or any other application).

[]("http://code.google.com/p/chromium/issues/detail?id=21244")

---

### Post by MountainX on 2009-09-08
when i installed the first time, chromium asked me if I wanted to import my settings from Firefox. After using Synaptic to do a "complete removal" and then installing again, Chromium does not ask this. It is "remembering" that it was installed before. I need to find where it stores this info so I can delete everything.

Anyone know where the chromium settings are stored? thanks.

---

### Post by oldos2er on 2009-09-08
I'd start by looking in /home/<user>/.chromium

---

### Post by philinux on 2009-09-08
~/.config/chromium

---

### Post by MountainX on 2009-09-08
> **oldos2er said:**
> I'd start by looking in /home/<user>/.chromium

Sorry to be sarcastic, but you'd be looking in a folder that doesn't exist -- at least on my system. Do you have that folder? Maybe it gets created after Chromium starts the first time (which it has never done for me). 

However, that is not the location where chromium keeps the info that allows it to "remember" that it was installed before.  Where else could I look?

---

### Post by MountainX on 2009-09-08
> **philinux said:**
> ~/.config/chromium

ah, that's it! Thanks. :)

---

### Post by MountainX on 2009-09-08
I deleted ~/.config/chromium and reinstalled again. This time I got the initial dialog about importing firefox settings and I declined. However, the result is that chromium still fails to start.

```
$ chromium-browser
[26974:26977:76624146016:FATAL:/build/buildd/chromium-browser-4.0.207.0~svn20090907r25598/build-tree/src/chrome/browser/renderer_host/async_resource_handler.cc(145)] Check failed: read_buffer_->data(). 
Trace/breakpoint trap
```

---

### Post by MountainX on 2009-09-08
SOLVED

```
sudo nano /etc/fstab
```

```
#for security of shared memory
#the next line seems to have created a problem for Google Chromium browser
 #tmpfs /dev/shm tmpfs defaults,ro 0 0 
#using this instead solves the Chromium problem
tmpfs /dev/shm tmpfs defaults,nosuid,noexec,rw 0 0
```

```
sudo mount -o remount /dev/shm/
```

---

### Post by oldos2er on 2009-09-11
> **MountainX said:**
> Sorry to be sarcastic, but you'd be looking in a folder that doesn't exist -- at least on my system. Do you have that folder? 

 Sorry, I should've checked more closely. .chromium is a file, not a directory.

---

