---
title: "Citrix ICA Client &quot;The Package is of Bad Quality&quot;"
date: 2011-09-05
forum: General Help
---

### Post by evilsoup on 2011-09-05
My dad needs to use the Citrix client to connect to a remote desktop at his work. I had previously set this up aaages ago, under 10.10, but today I've upgraded to 11.04 (nuked the HD, so I need to install the client again).  So, I grabbed the .deb from [here]("https://www.citrix.com/English/ss/downloads/details.asp?downloadId=2309164&productId=1689163&ntref=clientcenter#top") and chucked it into the software center, only to get the following error:
[IMG]http://i.imgur.com/K16PD.png[/IMG]

The details are below:
> 
Lintian check results for /home/almonds/Downloads/icaclient_11.100_i386.patched.deb:
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/config/All_Regions.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/config/canonicalization.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/config/regions.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/config/Trusted_Region.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/config/Unknown_Region.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/config/Untrusted_Region.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/config/usertemplate/All_Regions.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/config/usertemplate/Trusted_Region.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/config/usertemplate/Unknown_Region.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/config/usertemplate/Untrusted_Region.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/nls/en/appsrv.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/nls/de/appsrv.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/nls/ja/appsrv.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/nls/en/module.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/nls/de/module.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/nls/ja/module.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/nls/en/wfclient.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/nls/de/wfclient.ini
E: icaclient: file-in-usr-marked-as-conffile usr/lib/ICAClient/nls/ja/wfclient.ini
Use of uninitialized value in hash element at /usr/share/lintian/lib/Lintian/Collect/Binary.pm line 283, <$idx> line 14309.
Obviously, I'm going to forward this to Citrix, but I would like to know if these are genuinely dangerous problems, or if Ubuntu is just being whingy. So, what say you, mighty space-ghosts of ubuntuforums.org? Steer clear or push ahead?


EDIT: for anyone reading this off of google, it seems that [this](http://lintian.debian.org/tags/file-in-usr-marked-as-conffile.html) is the responsible problem: the ICAclient creates config files under "/usr", which on some systems is set to read-only. The .tar.gz version of the program has the same issue. This doesn't seem to be a problem for me, but I'm no expert and YMMV. Write to Citrix, that's the best bet of this getting fixed.

---

### Post by bayan.r on 2011-09-05
The DEB packaging of the Citrix Package is known to be faulty I recommend you install it using the .run file instead.

---

### Post by Toz on 2011-09-05
Interesting. I have the same version Citrix Receiver running well on my Xubuntu 11.04 install. I downloaded I believe the same deb file about 3 months ago and installed it via:
```
sudo dpkg -i icaclient_11.100_i386.patched.deb
```
(IIRC, I needed to install libmotif4 first)

and didn't see any sort of message like the one you're seeing.

---

### Post by evilsoup on 2011-09-05
Oh, okay, but the Citrix downloads page only has a .rpm, a .deb and a .tar.gz - do you recommend that I use the .tar.gz?

EDIT: Toz, I'm using the Ubuntu Software Center. I'm inclined to assume that the Software Center's just playing it safe, but I wanted to cast the error under more experienced eyes in case there is anything genuinely wrong.

---

### Post by bayan.r on 2011-09-05
I really prefer you use the tar.gz one because the deb file could really screw up your apt, and when an error like this is seen I would take it very seriously.

---

### Post by evilsoup on 2011-09-05
Yeah, I decided that it wasn't that much effort, so I erred on the side of caution and used the .tar.gz

Should I mark this as 'solved'? Not sure if it really is...

---

### Post by Toz on 2011-09-05
I believe this is the reason for the messages: [http://lintian.debian.org/tags/file-in-usr-marked-as-conffile.html]("http://lintian.debian.org/tags/file-in-usr-marked-as-conffile.html")

---

### Post by evilsoup on 2011-09-05
I just checked in  "/usr/lib/ICAClient/nls/en", and all the .ini files listed in the OP error are present ... so it seems that the .tar.gz isn't any better than the .deb, it just doesn't set off the idiot alarms (because I used the command line instead of the Software Center). Toz, if I'm reading your link properly, then 'all' this would do would is prevent me from altering the configuration for the Citrix client - is that correct? So, not a system-threatening issue, just a case of untidyness?

EDIT: and even that wouldn't apply to me, as my /usr is set to be readable and writable by root, so if I *really* needed to ... still, I'll bring this to Citrix's attention.

---

