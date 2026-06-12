---
title: "How to transfer settings from one install to another"
date: 2010-09-29
forum: General Help
---

### Post by KatsumeBlisk on 2010-09-29
I have no idea what to do to copy settings for programs, etc. to a new install of Ubuntu so that I don't have to do it all over again. When 10.10 releases, I would like to upgrade with a fresh install because upgrades sometimes bug out. Which folders do I copy/What is the best method of doing this?

---

### Post by e24ohm on 2010-09-29
I might be wrong, but if you install most of your software in /opt, you should only need to backup that location.

I have been giving this idea some thought myself recently. My laptop runs Fedora Core 13, and I'm witing for release 14 to come out; however, I have a good number of apps installed in the /opt location, and my hope is - the need to only move/backup/restore the /opt location.

Can anyone offer insight on this, and help both of us out?

---

### Post by cj.surrusco on 2010-09-29
You want to copy your home folder to keep all of the settings. Most of your config files are in hidden folders in your home directory. But, you also need to install the programs that you had in your old installation. 

This is a good link to follow:

[http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/)

---

### Post by Quackers on 2010-09-29
Is there any way to keep the programs too?

---

### Post by KatsumeBlisk on 2010-09-29
> **cj.surrusco said:**
> You want to copy your home folder to keep all of the settings. Most of your config files are in hidden folders in your home directory. But, you also need to install the programs that you had in your old installation. 

This is a good link to follow:

[http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/)

Thanks, that's exactly what I was looking for. Thanks for the quick reply.

---

### Post by KatsumeBlisk on 2010-09-29
> **Quackers said:**
> Is there any way to keep the programs too?

If you make the list of programs programs like the link said, you can add the repos and then 'sudo apt-get install program-1 program-2' That's what I think.

---

### Post by Quackers on 2010-09-29
Ok, I'll do some mooching about :-)

---

### Post by cj.surrusco on 2010-09-29
> **KatsumeBlisk said:**
> If you make the list of programs programs like the link said, you can add the repos and then 'sudo apt-get install program-1 program-2' That's what I think.

It's even easier than that. Read the "Restore" section:

> Once your done with the fresh install, copy the file package.selections into your home. Then copy your sources.list file into /etc/apt/ and update it to match your current distro (e.g Gutsy –> Intrepid) you can use CTRL + H in gedit for that. Then do a “sudo apt-get update” ,and finally invoke:

sudo dpkg --set-selections /home/package.selections && apt-get dselect-upgrade

apt-get will now start downloading all your apps, this will take some time depending on the number of apps you have installed.

---

### Post by KatsumeBlisk on 2010-09-29
> **cj.surrusco said:**
> It's even easier than that. Read the "Restore" section:

Sweet. I didn't realize that. Even better.

---

### Post by Quackers on 2010-09-29
Ooh nice, thanks. Bookmarked!

---

