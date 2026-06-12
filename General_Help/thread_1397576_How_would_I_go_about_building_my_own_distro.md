---
title: "How would I go about building my own distro??"
date: 2010-02-03
forum: General Help
---

### Post by switch10 on 2010-02-03
Is there a way to make my own custom ubuntu iso image with only the packages that I want to install?  I know I can do a minimal install and install only the packages I want, but it would be nice to have these applications on a cd so I wouldn't need an Internet connection. 

Thanks

Dave

---

### Post by fr3ak.m3 on 2010-02-03
Tyo remastering the ubuntu using remastersys.

Add the following lines to your sources.list
```
deb http://www.geekconnection.org/remastersys/repository ubuntu/
```

```

sudo apt-get update
sudo apt-get install remastersys

```

After you have successfully installed remastersys. You can use remastersys to create a backup or install/live CD of the current system you are using.

Have fun.

Regards
fr3ak

---

### Post by switch10 on 2010-02-03
Perfect!  Thanks a lot!

I also found this [http://susestudio.com](http://susestudio.com) to build your own SUSE based distro using your web browser!!  pretty cool as well.

---

### Post by grndslm on 2010-02-23
You'd use Remastersys, of course...

And here's THE Guide to Remastersys:

[http://ubuntuforums.org/showthread.php?t=1073838](http://ubuntuforums.org/showthread.php?t=1073838)
-OR-
[http://geekconnection.org/remastersys/forums/index.php?topic=406.0](http://geekconnection.org/remastersys/forums/index.php?topic=406.0)

Same one. :)

---

