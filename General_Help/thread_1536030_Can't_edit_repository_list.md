---
title: "Can't edit repository list"
date: 2010-07-21
forum: General Help
---

### Post by Strag0 on 2010-07-21
Hi,

I can't seem to figure this out. I've searched Google and these forums to see if I can find the answer, but I've turned up empty handed on both.

My issue is this, I'm trying to add a PPA to my repository on Karmic. When I go to "Software Sources" in the menu bar (preferences?) I get a password prompt and then nothing else. If I go to Synaptic and try to edit the repositories from there it tells me that they have changed and to 'reload' them. So, I do so and when I go back to edit them it tells me the same thing. Now, in the command prompt I can run apt-get update and upgrade without any issues. I've checked the list in nano for any irregularities but have noticed none. AND, if I try to add the PPA via the command line I get an error (don't have it offhand) within a python script. 

Any clue as to what could be causing this?

Thanks.

---

### Post by bodhi.zazen on 2010-07-21
Post the error message you are getting.

Otherwise I see no reason why you can not open the file with nano or gedit and edit away.

```
sudo nano /etc/apt/sources.list

gksu gedit /etc/apt/sources.list
```

---

### Post by Strag0 on 2010-07-21
> **bodhi.zazen said:**
> Post the error message you are getting.

Otherwise I see no reason why you can not open the file with nano or gedit and edit away.

```
sudo nano /etc/apt/sources.list

gksu gedit /etc/apt/sources.list
```

I can edit it via the command line, however I don't know how to go about adding PPAs that way. I'll post the error shortly.

---

### Post by bodhi.zazen on 2010-07-21
> **Strag0 said:**
> I can edit it via the command line, however I don't know how to go about adding PPAs that way. I'll post the error shortly.

See :

[https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20Launchpad%20PPA%20Repositories](https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20Launchpad%20PPA%20Repositories)

The ppa should list the line you need to add and the key.

---

### Post by Strag0 on 2010-07-21
> **bodhi.zazen said:**
> Post the error message you are getting.

Otherwise I see no reason why you can not open the file with nano or gedit and edit away.

```
sudo nano /etc/apt/sources.list

gksu gedit /etc/apt/sources.list
```

Here's the error I keep getting:

```
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 40, in <module>
    sp = SoftwareProperties(options)	
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
```

---

