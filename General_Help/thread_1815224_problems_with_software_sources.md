---
title: "problems with software sources"
date: 2011-07-30
forum: General Help
---

### Post by Cpierce on 2011-07-30
My software sources some how got screwed up. Now when I try to install from software manager or Synaptic, I get error messages. Here is the error messages at the bottom of "sudo apt-get update" :

 W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5


How do I fix this ?

---

### Post by cjack2964 on 2011-07-30
I have read about this error in other posts, and the fix appears to be this command

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys

Followed by the hex numbers that come in the errors

I have never had this issue myself, but this appears to have worked for others....

---

### Post by 73ckn797 on 2011-07-30
Try using a back-up sources list such as: "/etc/apt/sources.list.save" if it is an earlier enough document before your problem began. Use: ```
sudo nautilus
``` to be able to rename to "sources.list" after deleting or renaming the current "sources.list" file.

---

### Post by Cpierce on 2011-07-31
I tried to rename  source.list.save first, but it didn't work. I thought since this was a new install the file should be new enough but I guess it had changed.

However,the suggestion from Cjack worked like a charm. 

Thanks to both of you for trying to help me out.

---

