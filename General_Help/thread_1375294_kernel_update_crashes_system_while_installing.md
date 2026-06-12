---
title: "kernel update crashes system while installing"
date: 2010-01-07
forum: General Help
---

### Post by charonred on 2010-01-07
Well, that takes the cake; I've just spent the past week plus migrating from Hardy to Karmic (to support my new graphics card), and today update manager informs me a Kernel update 2.6.31.17-generic-pae

So I give the permission, it downloads relevant files, and then halfway through the install process, the system crashes and reboots - only thing is it won't boot to OS, so I have to reboot using existing Kernel 2.6.31.16-generic-pae

So now I've installed Startup Manager, but only after having to repair Synaptic Package Manager (sudo dpkg blah blah blah)- and have now set system to use 2.6.31.16-generic-pae

So, how do I get the latest kernel 2.6.31.17-generic-pae to install correctly, or do I wait till 2.6.31.18-generic-pae is released?

---

### Post by charonred on 2010-01-07
bump

---

### Post by HiImTye on 2010-01-08
load synaptic and mark all relevant updates for reinstallation

:)

---

### Post by charonred on 2010-01-08
that's a bit of a problem, I have no idea what files were included in the 2.6.31.17-generic-pae update, all I know is there were lots listed in update manager, and I just entered the password and let it do it's thing.

---

### Post by HiImTye on 2010-01-08
[LIST=1]
[*]administration>log file viewer
[*]select 'dpkg.log' on the left pane
[*]scroll down to the bottom and look for any fails (or better yet, just mark down all relevant updates and reinstall them)
[/LIST]

---

### Post by charonred on 2010-01-08
thanks, I'll give that a shot later when the PC has finished work for the day.

update; just had a quick look at 'dpkg.log' ... agh big long list that I can't make head nor tail of; think I'll wait till next kernel update and see if they get that one right.

---

### Post by HiImTye on 2010-01-08
no problem :)

---

