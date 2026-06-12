---
title: "Mediatomb - how do I nuke it and get the config file back?"
date: 2011-02-21
forum: General Help
---

### Post by cackles on 2011-02-21
For some reason the directories on medatomb are messed up and it wont stream to PS3. It did work fine but, ummm, less said the better. But at least I know it works with the setup.

Ive tried reinstalling mediatomb but it wont download the config file with it. Is there anyway to completely remove everything that mediatomb installed and then reinstall it as if it was first time?

---

### Post by seawolf167 on 2011-02-21
Assuming you want to completely remove the program and all config files, use

```
sudo apt-get purge package_name
```

*remove* will remove the binaries
*purge* will remove the binaries + config files

---

### Post by cackles on 2011-02-21
> **seawolf167 said:**
> Assuming you want to completely remove the program and all config files, use

```
sudo apt-get purge package_name
```

*remove* will remove the binaries
*purge* will remove the binaries + config files

Thanks. Config is now nuked and replaced ... but the directories it is showing are still messed up. The tree is all wrong. I dunno what is making them look how they are.

---

