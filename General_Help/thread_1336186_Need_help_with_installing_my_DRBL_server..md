---
title: "Need help with installing my DRBL server."
date: 2009-11-24
forum: General Help
---

### Post by Pascal11110 on 2009-11-24
I am trying to install a DRBL server on my schools network, but only need the DRBL so that I can use clonezilla. I have 2 network cards. Basically I have gone through the steps here: [Clonezilla.org (then hit SE edition and installation doc)]("http://clonezilla.org") and it fails every time. I have my network cards set up on separate subnets.

The first part where I install the GPG-KEY works fine. Then I click on the sources list and add the two sites for my distro (8.1 desktop). Then I execute apt-get update and then apt-get install drbl. These both seem to work fine. Then I try to do the impatient install, because I only need the defaults for the DRBL environment since I am only using it for clonezilla. It seems to work, but at the end of the install it only shows a blank screen in the terminal. I continued because I figured it finished anyway. Then I run the drblpush -i and at the end it gives me this error: 

"linux-image-2.6.25-2-386 can NOT be downloaded!!! Something went wrong!
Maybe you should check /etc/apt/sources.list or remove the unnecessary kernel block in /var/lib/dpkg/status so that apt-cache pkgnames linux-image can get the downloadable kernel! Then try to run this program again.
Program terminated!!!"

Also, if I run the command after this to start clonezilla (/opt/drbl/sbin/dcs) it says:

"[root] You should run this program /opt/drbl/sbin/dcs in DRBL server, NOT in DRBL client or other machine."

Even though it is run on the server and with sudo, it still gives me this message.

If you need any more info, or if I have been unclear, just leave and a post and I will answer quickly. Any help is GREATLY appreciated as I have been wasting hours and hours on this for weeks.

---

### Post by Cheesemill on 2009-11-24
I'm afraid I've got no experience with CloneZilla but I'd like to suggest an alternative.

If it's a machine imaging solution that your after then take a look at [FOG]("http://www.fogproject.org/").
It installs in minutes with a simple script and I do believe it has more features than CloneZilla.
I've installed it at several sites without a hitch, the documention and support community are very active as well.

I managed to have my first installation up and running just minutes after discovering the project.

---

### Post by Pascal11110 on 2009-11-24
Hmmm... sounds good I'll look into it. But for anybody else I'd still like to get this working as well.

---

### Post by tasmaniasedado on 2009-12-09
hey pascal, im trying to install clonezilla on a school to, i just found this guide, maybe it helps:
[http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/](http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/)

---

### Post by Pascal11110 on 2009-12-28
Well actually I solved my issue, I just completely forgot to post finish up this thread, sorry. My problems were actually two-fold. When configured the network manually, for some reason it decided not to detect the dns servers on the network and that was part of the reason it failed. My other problem I got around but it is still perplexing. Basically I had always tried the impatient installer before I tried doing it manually, and because that would fail it would destroy my package manager. I fixed this by doing the manual install and it worked fine. But the odd thing is that I later made a new server at work and that kept failing on the manual install, but the impatiant worked great, so I don't know.

P.S. If anyone that had anything to do with clonezilla is reading this, I love the software and I wasn't trying to badmouth you guys through any of this. Thanks for an awesome free product and keep up the good work!

---

### Post by Pascal11110 on 2009-12-28
Also, can someone tell me how to mark this thread as solved? I can't find a button anywhere that will let me edit that.

---

### Post by Sef on 2009-12-28
>  		Also, can someone tell me how to mark this thread as solved? I can't find a button anywhere that will let me edit that. 	

It's under Thread Tools: top left.  (I set it as solved.)

---

### Post by Pascal11110 on 2009-12-29
ooooooook, thanks a lot!

---

