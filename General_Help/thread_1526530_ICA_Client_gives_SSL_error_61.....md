---
title: "ICA Client gives SSL error 61...."
date: 2010-07-08
forum: General Help
---

### Post by tonwib on 2010-07-08
[FONT=Arial][SIZE=2]**_Problem logging into Citrix._**[/SIZE][/FONT][SIZE=2]
[/SIZE]   [FONT=Arial][SIZE=2]
I have downloaded the file "_**icaclient_11.100_i386.patched.deb**_" from the Citrix website and installed it on my Ubuntu laptop. Everything seems to work fine. I can login to the secured website and even can click on the application.[/SIZE][/FONT][SIZE=2]

[/SIZE]    [FONT=Arial][SIZE=2]After a while I get this error message:
"*You have not chosen to trust Thawte Server CA, the issuer of the server's security certificate (SSL error 61)*"
](*,)  ](*,) ](*,) ](*,) ](*,) ](*,)[/SIZE][/FONT][SIZE=2]
[/SIZE] [FONT=Arial][SIZE=2]
Of course, I deinstalled the ICA Client (Citrix Receiver) and re-installed it again, but nothing seems to help. I keep receiving this "Thawte Server CA" error!  :'-([/SIZE][/FONT][SIZE=2]

I have checked everything in FireFox (Thawte is there) and also tried to load the certificate, but FF tells me the certificate is already known to it.
[/SIZE] [FONT=Arial][SIZE=2]
So, why am I getting the error that I didn’t choose to trust “Thawte Server CA”?[/SIZE][/FONT][FONT=Arial][SIZE=2]Anyone out there who can help me?[/SIZE][/FONT][SIZE=2]
[/SIZE]   [FONT=Arial][SIZE=2]
Thanks![/SIZE][/FONT]

---

### Post by R Smit on 2010-07-11
Same here. Used Citrix long time without problems.
Now, 'suddenly', it says: You have not chosen to trust [www.valicert.com;](www.valicert.com;) ssl 61.

Ubuntu 10.04

---

### Post by R Smit on 2010-07-12
sudo cp /usr/share/ca-certificates/mozilla/* /usr/lib/ICAClient/keystore/cacerts/

This managed the problem, although I still do not understand how the error suddenly appeared. Maybe because of an update of FF?

I found it here:

[http://ubuntuforums.org/showthread.php?t=912886&highlight=citrix](http://ubuntuforums.org/showthread.php?t=912886&highlight=citrix)

Message# 8

---

### Post by Remuzzz on 2011-10-19
In case someone runs into this problem again (just like I did). The directory of the keys has been changed in version 12 to:

/opt/Citrix/ICAClient/keystore/cacerts

so use this:

sudo cp /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts

---

### Post by jonnymd on 2012-07-11
Beautiful. This is why I LOVE the linux community. Such a niche problem and simple Googling provides a solution. Thanks guys. Same problem here but solved with the updated path for 12.

---

