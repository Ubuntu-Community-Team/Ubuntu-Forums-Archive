---
title: "Adobe install with Wine help please"
date: 2011-07-06
forum: General Help
---

### Post by CDWells on 2011-07-06
I am new-ish to Ubuntu and have dualbooted XP Pro with Ubuntu 11.04, trying to do full install, but anyway back to my problem is there a way to install the newest adobe flash player on Ubuntu I tried using Wine and it didn't work at all
can somebody please help
thanks in advance

---

### Post by pqwoerituytrueiwoq on 2011-07-07
google "flash aid"

---

### Post by lovinglinux on 2011-07-07
As mentioned above...

Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance and fix common issues. 

BTW, although Wine allows you to install and run Windows applications, you should avoid doing so, when there is a native application for Linux. Flash is available for Linux as well.

Unlike Windows, most of the time you don't need to hunt for applications on the web and install them manually. Although you can install applications that way, Ubuntu provides a repository where all supported applications are stored. All you need is to search for the application on Ubuntu Software Center, which is already installed on your machine. 

For advanced installation methods: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

So why should you install Flash-Aid then? Well, flash is a particular case. You can install flash from the Software Center as well. In fact, Flash-Aid make use the repository to install flash (depending on selected options), but it does more than that. It fixes common issues and apply some performance tweaks. After replying to hundreds of posts asking for help with flash issues, I decided to create Flash-Aid to do the job automatically.

---

