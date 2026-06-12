---
title: "Pidgin 2.10.0 on Ubuntu 10.10 Help"
date: 2011-10-25
forum: General Help
---

### Post by A4orce84 on 2011-10-25
Hello Everyone,

I recently upgraded to Pidgin 2.10.0 on my Ubuntu 10.10 install and libnotify is no longer an option on the plugin's page.

Has anyone done this and got libnotify to work after upgrading to Pidgin 2.10.0 while REMAINING on Ubuntu 10.10?

Thanks in advance!  =)

--Asif

---

### Post by oldtimer7777 on 2011-10-25
> **A4orce84 said:**
> Hello Everyone,

I recently upgraded to Pidgin 2.10.0 on my Ubuntu 10.10 install and libnotify is no longer an option on the plugin's page.

Has anyone done this and got libnotify to work after upgrading to Pidgin 2.10.0 while REMAINING on Ubuntu 10.10?

Thanks in advance!  =)

--Asif

Have you installed the latest version through the PPA?

```

sudo add-apt-repository ppa:pidgin-developers/ppa && sudo apt-get update
sudo apt-get upgrade
sudo apt-get update sudo apt-get install pidgin pidgin-data pidgin-lastfm pidgin-guifications msn-pecan pidgin-musictracker pidgin-plugin-pack pidgin-themes
```

---

### Post by A4orce84 on 2011-10-25
Yup, that's what I did to perform the upgrade from Pidgin 2.7 to Pidgin 2.10.0 and then libnotifiy stopped working.

I checked my plugins inside Pidgin, and it's not even an option anymore:

[IMG]http://img.photobucket.com/albums/v405/A4orce84/Plugins_001.jpg[/IMG]

Maybe because Pidgin is expecting a newer version of Ubuntu and it's dependencies, Version 10.10 of Ubuntu no longer satisfies the libnotify constraints that the new pidgin requires? 

Thoughts?

Also, when I ran your last command, I got the following message:

```

aahmad@aahmad-hdesktop:~$ sudo apt-get install pidgin pidgin-data pidgin-lastfm pidgin-guifications msn-pecan pidgin-musictracker pidgin-plugin-pack pidgin-themes
[sudo] password for aahmad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pidgin is already the newest version.
pidgin-data is already the newest version.
pidgin-data set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 pidgin-guifications : Depends: pidgin (< 1:3.0) but 3:2.10.0-1~unixmen~maverick~ppa is to be installed
                       Conflicts: pidgin (>= 1:3.0) but 3:2.10.0-1~unixmen~maverick~ppa is to be installed
E: Broken packages
aahmad@aahmad-hdesktop:~$ 

```



Thanks!

---

### Post by A4orce84 on 2011-10-25
anyone?

As a reference, I have another machine running Ubuntu with the older version of Pidgin (2.7.11) and it DOES have the libnotify option:

[IMG]http://img.photobucket.com/albums/v405/A4orce84/Plugins_001-1.jpg[/IMG]

---

### Post by A4orce84 on 2011-10-25
Or would it be easier to just downgrade?

---

### Post by A4orce84 on 2011-10-25
Ttt

---

### Post by A4orce84 on 2011-10-25
Ttt

---

### Post by A4orce84 on 2011-10-26
Ttt

---

### Post by A4orce84 on 2011-10-29
Anyone?

Thanks

---

### Post by A4orce84 on 2011-11-05
Anyone?

---

