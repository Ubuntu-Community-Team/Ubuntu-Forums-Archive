---
title: "Problem performing updates"
date: 2012-01-02
forum: General Help
---

### Post by juanvi on 2012-01-02
Hello,

From 8 days ago my system is not capable of performing updates. This is the output I get:

```
sudo apt-get update
Ign http://softlibre.unizar.es oneiric InRelease
Ign http://dl.google.com stable InRelease 
....
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
```


I have attempted to fix it by removing the trusted software provider authentications from the update manager, and then pressing 'Restore defaults'. But doesn't work.

I'm using ubuntu 11.10 

Thank you in advance,

---

### Post by yugnip on 2012-01-02
Ah, gpg key issues. No worries, it's fixable. Install Y PPA Manager and use it to fix the key issue.

```
sudo add-apt-repository ppa:webupd8team/y-ppa-manager
sudo apt-get update
sudo apt-get install y-ppa-manager
```

Choose 'advanced settings' and then choose 'fix keys'.

You can read more about Y PPA Manager here:

[http://www.webupd8.org/2011/11/y-ppa-manager-0084-released-finally.html]("http://www.webupd8.org/2011/11/y-ppa-manager-0084-released-finally.html")

Now you could just run a script or terminal command to do the same thing (google gpg key issue). But having Y PPA Manager is pretty useful for more than just this problem, so it's worth an install.

Hope this helps.

---

### Post by juanvi on 2012-01-02
Thanks so much, yugnip. It worked like a charm.

I installed Y PPA Manager and then chose:
Try to fix all GPG BADSIG errors
Try to import all missing GPG keys

After that I updated the system without any problem!

---

### Post by audiomick on 2012-01-02
Thank you yugnip. That solved the problem I was having too.
[http://ubuntuforums.org/showthread.php?t=1898926](http://ubuntuforums.org/showthread.php?t=1898926)

---

