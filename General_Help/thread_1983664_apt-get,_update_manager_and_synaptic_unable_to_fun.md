---
title: "apt-get, update manager and synaptic unable to function"
date: 2012-05-20
forum: General Help
---

### Post by oxman on 2012-05-20
System fubar:

Quote:
```

E: Encountered a selection with no Package: header
 E: Problem with MergeList /var/lib/apt/lists/
 extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
 E: The package lists or status file could not be parsed or opened.
 E:_cache->open() failed, please report.                      

```

The system would not let me file a report either. Neither through apt-get, update-manager or synaptic. Seems like a serious bug. I followed Rubi1200 suggestion and all is well.

Rubi1200 in a previous thread proffered clearing and updating the lists with terminal apt-get :

> 

Hi,
you can try this and see if it helps:

```

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```


the first command removes corrupted package lists, the second refreshes them.



Thank you Rubi1200 very much. I am posting this as not solved since it is a serious bug.

---

### Post by Old_Grey_Wolf on 2012-05-20
ubuntuforums.org is not the place to report bugs. The developers don't look here for bug reports. If you think you found a bug, report it on [http://launchpad.net](http://launchpad.net).

Edit: I like the Homestead website. :)

---

### Post by rai4shu2 on 2012-05-20
Is there a bug report on launchpad.net about this? I don't suppose you know a sure-fire way to reproduce this bug.

---

### Post by oxman on 2012-05-20
> **rai4shu2 said:**
> Is there a bug report on launchpad.net about this? I don't suppose you know a sure-fire way to reproduce this bug.

Once I manually deleted the list and manually refreshed the list from a terminal the problem went away. Others have had a similar problem and similar solution. Many are not comfortable with cli, hence the designation of the problem as a serious bug. 
I purposefully started the thread so that others with similar problems could find a workaround. 
Since the solution fixed the problem it can not be replicated. Unless it happens again of course.

Thanks for responding though.

Busy installing 12.04 on an old computer with graphics issues but I should see if there's a bug or not. Thanks for the feed back.

---

### Post by oxman on 2012-05-20
> **Old_Gray_Wolf said:**
> ubuntuforums.org is not the place to report bugs. The developers don't look here for bug reports. If you think you found a bug, report it on [http://launchpad.net](http://launchpad.net).

Edit: I like the Homestead website. :)

Thanks! Old Nam vet likes Homestead too.:)

---

