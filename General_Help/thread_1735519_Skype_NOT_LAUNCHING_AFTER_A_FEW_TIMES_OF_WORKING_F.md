---
title: "Skype NOT LAUNCHING AFTER A FEW TIMES OF WORKING FINE"
date: 2011-04-21
forum: General Help
---

### Post by sgb77 on 2011-04-21
Hello,
skype does not start when I try to launch it, when I unistall it and  reinstall it, it starts working again for a couple of times but then it  stops again. I have deleted all my settings in the ~/.Skype folder and  have purge removed my skype and reinstall it from synaptic and from the  download in the skype website.

when I launch it from the command prompt I get the following at the prompt:
Segmentation fault

an I get the following in the various logs:

==> kern.log <==
Apr 21 12:34:29 my-laptop kernel: [ 2730.775856] skype[9265] general  protection ip:8078173 sp:bfbac720 error:0 in skype[8048000+13d2000]

==> messages <==
Apr 21 12:34:29 my-laptop kernel: [ 2730.775856] skype[9265] general  protection ip:8078173 sp:bfbac720 error:0 in skype[8048000+13d2000]

==> syslog <==
Apr 21 12:34:29 my-laptop kernel: [ 2730.775856] skype[9265] general  protection ip:8078173 sp:bfbac720 error:0 in skype[8048000+13d2000]

I am using ubuntu 10.10
skype 2.2

Thanks for any help

---

### Post by oODeanOo on 2011-04-23
My segmentation fault errors with Skype 2.2.0.25 were caused by Prelink corrupting the binary when the cron job run so it would work fine for a day and then fail with a Segmentation Fault.

So if you have prelinking enabled the solution is to exclude the Skype binary from being prelinked.

To fix is to edit the prelink configuration file by entering

sudo gedit /etc/prelink.conf

insert the following line to exclude skype and save.

-b /lib/modules
-b /usr/lib/locale
[COLOR=DarkRed]**-b /usr/bin/skype**[/COLOR]
-l /usr/local/sbin
-l /sbin
-l /usr/sbin

Then to reinstall Skype type

sudo apt-get install --reinstall skype

Hope this helps 

Dean

---

### Post by sgb77 on 2011-04-23
Thanks Dean,
I know I had enabled prelink a few months back, and skype was working fine until recently. I didn't have the /etc/prelink.conf file not sure if adding it manually will do anything.
I did however found /etc/default/prelink file, it looks like some sort of configuration file, I'll add your suggestions here and let you know if that worked or not.

---

### Post by oODeanOo on 2011-04-23
It's only started following the 2.2 Skype update, all was ok with 2.1.

I'm on 10.04 so maybe location of the prelink.conf file has moved in 10.10.

Dean

---

