---
title: "How to delete &quot;Synaptic Package Manager&quot; config files?"
date: 2012-05-08
forum: General Help
---

### Post by purgeinator on 2012-05-08
There is a bug in synaptic " [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/779756](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/779756) 
" which prevents deleting custom filter created. How can I remove config files for synaptic, since 'apt-get purge'  didn't work. I want to remove synaptic config files, so that on  reinstall there is no custom filter created by me.

---

### Post by Enigmapond on 2012-05-08
The easy way is to install ubuntu-tweak which has a package cleaner that also purges config files.

---

### Post by purgeinator on 2012-05-08
> **Enigmapond said:**
> The easy way is to install ubuntu-tweak which has a package cleaner that also purges config files.
How to do that manually since I don't like installing many software? Also why "apt-get purge" is not working?

---

### Post by Enigmapond on 2012-05-08
apt-get purge <file name> will delete the programme and all config files from the original file. If there are dependencies they would need to be listed separately..

---

### Post by Enigmapond on 2012-05-08
OR

```
dpkg -l | awk '/^rc/{ print $2}' | sudo xargs dpkg --purge
```

This will purge all orphaned configs....just found it.

SOURCE - [http://tuxtweaks.com/2011/09/remove-old-package-configuration-files-in-ubuntu/](http://tuxtweaks.com/2011/09/remove-old-package-configuration-files-in-ubuntu/)

---

### Post by purgeinator on 2012-05-08
> **Enigmapond said:**
> apt-get purge <file name> will delete the programme and all config files from the original file. If there are dependencies they would need to be listed separately..
Tried this but didn't work.

---

### Post by drs305 on 2012-05-08
I created a custom filter and found it in /root/.synaptic/filters.  Remove that file and it appears to remove any custom filters. To be on the safe side, you could also try moving it out of that folder rather than delete it.

---

### Post by purgeinator on 2012-05-09
> **drs305 said:**
> I created a custom filter and found it in /root/.synaptic/filters.  Remove that file and it appears to remove any custom filters. To be on the safe side, you could also try moving it out of that folder rather than delete it.
Thanks! This is what I was looking for. Any idea why "sudo apt-get purge synaptic" didn't remove these files?

---

### Post by drs305 on 2012-05-09
> **purgeinator said:**
> Thanks! This is what I was looking for. Any idea why "sudo apt-get purge synaptic" didn't remove these files?

Not really. The filter file is in root's .synaptic folder, which seems like a normal location for configuration files to me.

Perhaps someone else might know, or maybe the Launchpad bug thread will provide some insight.

Once you have found the answer, no longer care, or give up, please mark the thread SOLVED via the thread tools link at the upper right of the right post.

Happy Ubuntu-ing !

---

### Post by CatKiller on 2012-05-09
Purge doesn't remove files from any Home directory. It really isn't a good thing to do, no matter what bad habits people have picked up from using Windows.

---

