---
title: "&quot;not authenticated sources&quot;"
date: 2012-03-29
forum: General Help
---

### Post by veggiefish on 2012-03-29
None of the options have worked for me. I am just trying to update, not installed anything in particular like opera.

The action would require the installation of packages from not authenticated sources.

apport-hooks-medibuntu libavcodec-extra-53 libavutil-extra-51

---

### Post by oldos2er on 2012-03-29
Post moved to its own thread.

---

### Post by kazztan0325 on 2012-03-29
> **veggiefish said:**
> The action would require the installation of packages from not authenticated sources.

apport-hooks-medibuntu libavcodec-extra-53 libavutil-extra-51

Hi veggiefish,

Have you installed a package 'medibuntu-keyring'?
If you have not done it yet, try following code with Terminal.

```
sudo apt-get install medibuntu-keyring
```

And then,

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by raja.genupula on 2012-03-29
> The action would require the installation of packages from not authenticated sources.

means you're trying to install some third party software , if you dont want to get warning like this means in the update manager settings at other software TAB enable Canonical checkbox . then try again .

---

