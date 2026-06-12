---
title: "System Restore Point LOL!"
date: 2011-01-08
forum: General Help
---

### Post by micha8l on 2011-01-08
Hey,

I'm new to Ubuntu, hence the title, and I'm wondering if there's any feature like Microsoft's System Restore Point, which is like a system that'll allow me to restore my computers setting to earlier date in time.
I'm intrested in such a thing because I know I'm bound to screw my Ubuntu instillation up at some point and it would be nice to have this "safety net."

Kind Regards,
Mike

---

### Post by mike555 on 2011-01-08
probably best thing is to backup your /home folder ,then if you mess up , simply reinstall ...

---

### Post by zsazso on 2011-01-08
Ubuntu tweak has a recovery options section. Used it once. worked flawlessly.

---

### Post by Vaphell on 2011-01-08
if you don't want to hose your system, don't play with privileges of anything that is not in your home folder, don't use sudo for everything and don't hack anything to have permanent admin rights to save few seconds of typing passwords, don't use terminal commands you don't understand, use standard repositories and use other installation methods (from ppa, from .deb, from source) only as a last resort.

backing up home dir and optionally exporting installed packages (there is an option in the package manager) to a text file to import it when necessary should be enough to have everything under control.
Having a separate partition for /home is very nice because you can wipe your system clean with no side effects. When you reinstall, all your user data/settings are left untouched and are picked up by the fresh system right off the bat. If you don't have separate home, consider setting it up.

---

### Post by micha8l on 2011-01-08
Hey guys thanks for reply, I appreciate it.


@vaphell I hear you and couldn't agree more with what you say. But sometimes I must, as I'm hosting a web server for development purposes so most of my important data is outside of my home directory: /var/www, /usr/local/zend, /etc/apache2 and god knows what else :(

I used to have an app on Windows named Commodo Backup it took directorys paths as input and backed them up at scheduled times to .bak format and optionally uploaded via ftp to a remote location. Is there anything similar to this app in Ubuntu?

Thanks again guys,
Mike

---

### Post by JOHNNYG713 on 2011-01-08
As much as I hate to say it System restore is one of the functions that sould be incorparated in to linux! micha8l has a more than valid inquiry !  I can envision a Snapshot recovery point, set by the user, or an "auto set"  and a line set in recovery mode like "fix broken packages" or "update grub" "restore to last snapshot of system" then reboot ! Yeaaaa Back in B Booty Bidneez ! This should be relatively easy, Given all of the great people, developers and input  we have in our community ! :D

---

### Post by micha8l on 2011-01-08
@johnnyg713 I suppose its one of them things people look for when they come from Windows, but I can overlook this due to everything else Ubuntu offers. I opted for Simple Backup which is a program that has all the feature of Commodo Backup (mentioned above) plus allows me to specify which extensions to exclude and specify a max file size etc, - really nice program although it doesn't stick a launcher in the Applications menu so I find I have to ALT+F2 and run gksudo nautilus to run it from /usr/share/sbackup.

---

