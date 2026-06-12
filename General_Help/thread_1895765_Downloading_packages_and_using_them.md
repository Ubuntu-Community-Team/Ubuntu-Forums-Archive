---
title: "Downloading packages and using them"
date: 2011-12-15
forum: General Help
---

### Post by rng on 2011-12-15
If I choose 'download package files only' in synaptic package manager, firstly where will it download to (or can I choose); secondly, will it download different deb files including dependencies; and thirdly, how can I now install the application?

Thanks for your help.

---

### Post by seawolf167 on 2011-12-15
If you use the following command

```
sudo apt-get --download-only install somepackagenamehere
```then the package along with all its dependencies will be downloaded and saved in the following directory

```
/var/cache/apt/archives
```

to install the resulting file, you should be able to simply double-click it

---

