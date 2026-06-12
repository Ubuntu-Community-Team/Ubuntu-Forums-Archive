---
title: "nfs client mount on server boot"
date: 2009-08-28
forum: General Help
---

### Post by Karloman on 2009-08-28
Hello,

I'm running a mythbuntu 9.04 backend/frontend server and an ubuntu 9.04 client. I can share using sftp/samba/nfs and I have spent a lot of time on getting everything to work just the way I wanted. Well everything except this: I was wondering if it's possible to make client mount the nfs share automatically once the server boots. The client is on mostly from 11am till 6pm and the server is on from 4pm till 11pm. I was thinking about automatically making the server ssh the command to the client as well as making it ssh the umount command on a shutdown. Would this work? And if so: how do I go about to do that? If not, any suggestions about how to make the client mount the share on boot of the server.
Also, cron is not an option, because the times can and will change.
If this is totally incomprehensible please tell me, I'll try to explain it better.

Thanks,

---

### Post by Karloman on 2009-08-29
bump

---

### Post by mal on 2009-08-29
I'm not really sure what you are trying to do here.  Your mythbuntu client will not be much use when the server is not running.

Anyway, if you are looking for a way to automatically mount nfs shares, you could have a look at autofs ([https://help.ubuntu.com/community/Autofs]("https://help.ubuntu.com/community/Autofs"))

Hope this helps.

Mal

---

### Post by mal on 2009-08-29
By the way, I should add that there is a problem with autofs that could make it unsuitable for your application.  It can cause lengthy delays when the server is not running.  This is discussed at this thread: [http://ubuntuforums.org/showthread.php?t=1117131]("http://ubuntuforums.org/showthread.php?t=1117131").  There is also some advice here on setting up autofs if you decide to give it a go.

Mal

---

