---
title: "Can't burn CD in Jaunty"
date: 2009-10-10
forum: General Help
---

### Post by erop on 2009-10-10
Hi there!
A couple of days ago I wanted to burn Fedora 12 live-cd iso to just have a look at it. Brasero worked for about 10 minutes, it even showed some progess of  “Burning image to disc" (see Screenshot01.png) and successfully finished burning (see Screenshot02.png). But CD remained blank.

Here [http://ubuntuguide.org/wiki/Ubuntu:Jaunty#CD-ROM_Troubleshooting](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#CD-ROM_Troubleshooting) I read about permissions issue for /dev/scd0. I looked at that /dev/scd0 and here is `ls -l` output for these files:
```

$ ls -l /dev/ | grep cd
lrwxrwxrwx  1 root   root             3 2009-10-11 01:29 cdrom -> sr0
lrwxrwxrwx  1 root   root             3 2009-10-11 01:29 cdrw -> sr0
drwxr-xr-x  2 root   root            60 2009-10-11 01:29 pktcdvd
lrwxrwxrwx  1 root   root             3 2009-10-11 01:29 scd0 -> sr0
crw-rw----+ 1 root   cdrom      21,   0 2009-10-11 01:29 sg0
brw-rw----+ 1 root   cdrom      11,   0 2009-10-11 01:29 sr0
```


As you can see /dev/scd0 already has 777 permissions and is the symlink of /dev/sr0 that in its turn has a 660 permissions. It seems but one should to chmod 777 /dev/sr0 but I'm already in 'cdrom' group 
```
$ id
uid=1000(erop) gid=1000(erop) groups=4(adm),20(dialout),24(cdrom),46(plugdev),106(lpadmin),121(admin),122(sambashare),1000(erop)
```

and should have full r/w access to /dev/sr0. So as I think there is no need to neither chmod 777 /dev/scd0 nor /dev/sr0. Am I right?

Any other suggestions on how to fix the problem and get my ISO burned?

---

### Post by TheStroj on 2009-10-10
Same thing happened to me when I was burning a corrupted file to a CD. It was burning without effect. 
Can happen also if the CD is in a bad condition.

But if it is a OS related thing, you can try some other CD burner.
Don't know what else could it be.

---

