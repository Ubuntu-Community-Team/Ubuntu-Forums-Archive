---
title: "Help - Can not share any folder with Samba"
date: 2010-04-11
forum: General Help
---

### Post by Kalma on 2010-04-11
Hi there,

I am not able to share any folder on my Ubuntu 8.10. From Nautilus, I received the following message:

The «shared Network» returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Logon failure.

I added "usershare owner only = False" to my smb.conf, as well as some other parameters I saw on some forums. I have downloaded all samba packages including system-config-samba and tried from there with no success. I have also added the read-write permissions to /var/lib/samba/usershares and created a file with the sharing details. Using shares-admin, the folders I want to share are there, but they are not visible from other PCs neither from Places -> Network Places... Nothing of this seems to work.

Any help will be very welcome...

---

### Post by Kalma on 2010-04-14
Please, help.

I'm totally lost... Any idea or help will be really welcome.

Thanx in advance.

---

### Post by Kalma on 2010-04-18
I finally got it.

I'm not sure how it was, but it's working now. It seems there is some sort of incompatibility between some samba packages I installed when looking for a solution. What really solved the problem was starting with a new smb.conf, then erasing all shares in system-config-samba, and then starting Nautilus using sudo... After that, it worked.

---

### Post by maverick280857 on 2011-01-04
How exactly did you get this to work?

I also tried the remedy mentioned on

[http://ubuntuforums.org/showthread.php?t=1140216](http://ubuntuforums.org/showthread.php?t=1140216)

but it didn't work either.

---

