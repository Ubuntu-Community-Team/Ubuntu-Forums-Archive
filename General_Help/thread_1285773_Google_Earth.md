---
title: "Google Earth"
date: 2009-10-08
forum: General Help
---

### Post by windowsfree on 2009-10-08
I downloaded and installed the latest stable version of Google Earth.  The program worked fine for about 7 times, now when starting it, the programs terminates after about 8 seconds.  I am using Ubuntu 9.04.  Has anyone had this occur and is there a fix for it?
Thank you.

---

### Post by sedawk on 2009-10-08
Google stores user settings and temp-stuff at some directory
("cd; ls .googl*")
You can try to rename or remove that folder and then retry.

You might also check if you are out of disk space.

Another test would be to create a new user and try
again with the fresh desktop of that new user.

---

### Post by x C0MMAND0 x on 2009-10-08
1. Go to [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin) to download the newest version.

2. Open terminal

3. Go to directory where file is located
```
cd /path/to/.binfile
```

4. Make file executable
```
chmod +x GoogleEarthLinux.bin
```

5. Execute program
```
 ./GoogleEarthLinux.bin
```

That will prompt the install.  Then, it tells you how to run it.  It double listed Google Earth for me in Applications > Internet, but you can remove that from System > Administration > Main Menu > Internet

---

### Post by windowsfree on 2009-10-08
Thanks, tried it and it seems to be working as of now.

---

