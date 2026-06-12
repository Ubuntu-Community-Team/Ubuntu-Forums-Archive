---
title: "Define runelevel 2 as runlevel 2"
date: 2011-09-01
forum: General Help
---

### Post by djlucas on 2011-09-01
Hello, attempting to learn how to use upstart and  having a little bit of difficulty understanding the docu located here: [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html). I'd like to define a proper runlevel 2 since it has been omitted in the default installation. How would I go about this? I realize that I'll have to edit about half of the scripts in /etc/init. My problem stems from the existing 'start on' parameters, and almost complete lack of 'stop on' params. Is it as simple as adding 'stop on runlevel [0126]' to all network scripts and all scripts that depend on something in /usr? Will adding the stop on [0126] cause the scripts to restart when switching from RL2 to RL3 or will I have to add to the existing 'start on' parameters a runlevel argument for [345]? Also in the case of say this:

```

start on (local-filesystems
             and stopped udevtrigger)

```Just add another and? I plan to transfer /usr to an NFS mount as a test once the proper edits have been completed.

Thanks in advance.

-- DJ Lucas

---

