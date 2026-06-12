---
title: "How to update Opera 10.01 to 10.10?"
date: 2009-11-24
forum: General Help
---

### Post by Razmear on 2009-11-24
Howdy,
In Opera 10.01 I do a check for updates and it tells me about 10.10 and says: 
We recommend that you update Opera thru your systems update mechanism. 
with no manual method to launch the update. 

Will this hit in update manager in a few days or should I just install the newest version by downloading the package from Opera? 

Thanks,
eb

---

### Post by Arup on 2009-11-24
Don't wait for it in the repos, download the .deb, remove previous opera by doing a sudo apt-get --purge remove opera and install the new one.

---

### Post by 3rdalbum on 2009-11-24
I've already had the update pushed out to me through the Opera repository (that was enabled when I installed the 10.01 Deb package).

If you don't seem to have this repository, you can always just download the current 10.10 package from Opera.com.

---

### Post by Razmear on 2009-11-24
Thanks 3rd. 
I added : 
```

deb http://deb.opera.com/opera/ stable non-free

```
to my software sources in update manager and the update now shows. 

eb

---

### Post by DeMus on 2009-11-24
> **Razmear said:**
> Thanks 3rd. 
I added : 
```

deb http://deb.opera.com/opera/ stable non-free

```
to my software sources in update manager and the update now shows. 

eb

I just did the same but get a message about a missing key. Where can I find that key. I searched on the Opera site for "Ubuntu repo" but no luck.

Never mind, found it and added it to Synaptic. Don't get opera yet btw.

---

### Post by Razmear on 2009-11-24
I got the error about an unverified application when installing, so I guess I don't have the key either. 
Other than the error the upgrade went fine. 

Where did you find and how did you install the key? 

Thanks,
eb

---

### Post by DeMus on 2009-11-24
> **Razmear said:**
> I got the error about an unverified application when installing, so I guess I don't have the key either. 
Other than the error the upgrade went fine. 

Where did you find and how did you install the key? 

Thanks,
eb

You can find the key [_here_]("http://deb.opera.com/")
Just add it as you normally do:
copy the long text file and save it as a file on your desktop, then add the file in the sources list.

---

### Post by ghetto2ivy on 2009-12-28
> **Razmear said:**
> I got the error about an unverified application when installing, so I guess I don't have the key either. 
Other than the error the upgrade went fine. 

Where did you find and how did you install the key? 

Thanks,
eb

From: 
[http://www.opera.com/support/kb/view/841/](http://www.opera.com/support/kb/view/841/)

To install the repository GPG key, issue the following commands:

gpg --keyserver subkeys.pgp.net --recv-key 6A423791
gpg --fingerprint 6A423791
gpg --armor --export 6A423791| apt-key add -

---

### Post by mkvnmtr on 2009-12-28
I have been using Ubuntu tweek for awhile and added the app and the repositories through there. There is a lot of other interesting things I found there also.

---

