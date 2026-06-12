---
title: "Access denied on download"
date: 2010-12-14
forum: General Help
---

### Post by xerces8 on 2010-12-14
After starting Wubi (rev 190, for Ubuntu 10.04.1), I just set a password and clicked Install.
After about a minute I got an error dialog:

```

---------------------------
Ubuntu Installer
---------------------------
An error occurred:

Permission denied

For more information, please see the log file: c:\docume~1\stein\locals~1\temp\wubi-10.04.1-rev190.log
---------------------------
OK   
---------------------------

```

I'll attach the log file.

Regards,
David

PS: Note I changed the attached file. The first version had some additional logs, not relevant to this issue.

---

### Post by bcbc on 2010-12-14
The thing stalled trying to download the Ubuntu CD image.

Wubi's bittorrent thing isn't very efficient. I recommend downloading the .iso and wubi.exe and saving them in the same folder, then running wubi.exe from there. It will use the .iso it finds in that folder (provided it matches the 'flavour' you select in the Wubi drop down box.

So it's quicker. Also, you can burn the downloaded .iso to a CD (see [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) , step 2, show me how). This is useful for 2 reasons - a) you can try out Ubuntu in 'live CD' mode ('Try without installing') and see if it's compatible with your hardware, and b) you now have a 'rescue CD' in case you have problems later.

You can also install Wubi from the CD - insert while running windows and follow the prompts.

Final note: there are grub-pc and grub-common updates that will be applied to the 10.04.1 install that are known to break Wubi Ubuntu. Do not update these packages. For details see this thread [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198))

---

