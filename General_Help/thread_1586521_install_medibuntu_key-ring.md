---
title: "install medibuntu key-ring"
date: 2010-10-02
forum: General Help
---

### Post by ki4jgt on 2010-10-02
I upgraded to 10.10. Now I want to install medibuntu. I have the repos added, but when I try to add the key-ring with the terminal it won't add. Can someone give me the command for that again?

---

### Post by gandaran on 2010-10-02
> **ki4jgt said:**
> I upgraded to 10.10. Now I want to install medibuntu. I have the repos added, but when I try to add the key-ring with the terminal it won't add. Can someone give me the command for that again?
you can also use synaptic package manager if the repo is already added, open synaptic find medibuntu-keyring from the list and mark for install, click the apply button.
or CLI
```
sudo apt-get install medibuntu-keyring
```

---

### Post by ki4jgt on 2010-10-02
The repos are add I checked software sources. but no such package exists

---

### Post by gandaran on 2010-10-02
> **ki4jgt said:**
> The repos are add I checked software sources. but no such package exists
refresh package list
```
sudo apt-get update
```

---

### Post by ki4jgt on 2010-10-02
did that! I even tried removing them and following the same instructions I do for every release of Ubuntu. I think !0.10 RC may either have a problem or extra security measures have been added.

---

### Post by gandaran on 2010-10-02
> **ki4jgt said:**
> did that! I even tried removing them and following the same instructions I do for every release of Ubuntu. I think !0.10 RC may either have a problem or extra security measures have been added.
or maybe medibuntu will work only when 10.10 is finally released, I really don't know, I will only install 10.10 when the final release comes out, was this the code you ran to install medibuntu?
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by wojox on 2010-10-02
> **ki4jgt said:**
> did that! I even tried removing them and following the same instructions I do for every release of Ubuntu. I think !0.10 RC may either have a problem or extra security measures have been added.

You can install

```
sudo apt-get update; sudo apt-get install ubuntu-restricted=extras
```

I couldn't get medibuntu to work for 10.10 either. Restricted-extras has a lot of what you need for codecs except windows.

---

### Post by QIII on 2010-10-02
Medibuntu is not slated to be available until the final release.  Debian has things like the deb for libdvdcss2 if you check out their site.

---

