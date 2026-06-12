---
title: "NTFS mount problem - odd behaviour"
date: 2011-06-24
forum: General Help
---

### Post by robfromdublin on 2011-06-24
Hi all,

I want to automount an NTFS partition, which I do with this line in fstab:

UUID=884846EF4846DB96 /data ntfs-3g defaults,user,exec,locale=en_AU.utf8   0       0

However, only some of the directories appear in Nautilus.  I thought it might be a permissions thing but it doesn't appear to be.  Here is the ls -a output.  'music' appears in Nautilus but 'downloads' doesn't:

```
-????????? ? ?    ?             ?                ? install.res.1033.dll
-????????? ? ?    ?             ?                ? install.res.1036.dll
-????????? ? ?    ?             ?                ? install.res.1040.dll
-rwxrwxrwx 1 root root 1173029545 2011-06-19 21:11 install.res.1041.dll
-rwxrwxrwx 1 root root 1173017053 2011-06-19 20:52 install.res.1042.dll
-rwxrwxrwx 1 root root 1380683776 2011-06-04 19:58 install.res.2052.dll
-????????? ? ?    ?             ?                ? install.res.3082.dll
drwxrwxrwx 1 root root      20480 2011-04-25 12:36 music
drwxrwxrwx 1 root root      24576 2011-04-26 21:38 My Films
drwxrwxrwx 1 root root      49152 2009-08-26 20:05 My Music
drwxrwxrwx 1 root root          0 2011-04-27 07:35 Photos
drwxrwxrwx 1 root root          0 2011-04-25 17:06 $RECYCLE.BIN
drwxrwxrwx 1 root root          0 2011-04-25 12:06 System Volume Information
drwxrwxrwx 1 root root      16384 2011-06-13 17:27 downloads
-rwxrwxrwx 1 root root 1172431422 2011-06-19 21:13 VC_RED.cab
-rwxrwxrwx 1 root root 1172692424 2011-06-19 21:11 vcredist.bmp
-rwxrwxrwx 1 root root 1173321473 2011-06-19 21:03 VC_RED.MSI
drwxrwxrwx 1 root root       4096 2011-06-10 11:59 VS_EXPBSLN_x64_enu.CAB
-rwxrwxrwx 1 root root  733280256 2011-06-10 13:20 VS_EXPBSLN_x64_enu.MSI
```

I want to tidy it up but can't delete the 'install*' or 'V*' stuff either (despite having rw access):

```
rob@robs-laptop:/data$ sudo rm install*
rm: cannot remove `install.res.1033.dll': Input/output error
rm: cannot remove `install.res.1036.dll': Input/output error
rm: cannot remove `install.res.1040.dll': Input/output error
rm: cannot remove `install.res.1041.dll': No such file or directory
rm: cannot remove `install.res.1042.dll': No such file or directory
rm: cannot remove `install.res.2052.dll': No such file or directory
rm: cannot remove `install.res.3082.dll': Input/output error
```

Any ideas on what I can do here?  I'm very close to just reformatting the partition but it'll take a while to move the data around.

---

