---
title: "Mounting a nas server under ubuntu 10.10"
date: 2011-06-22
forum: General Help
---

### Post by phampson on 2011-06-22
Hello Ime having a problem

When I run smbtree i get the following out (abridged)
WORKGROUP
      \\LG-NAS
              \\LG-NAS\IPC$
              \\LG-NAS\service
              \\LG-NAS\Home

I want to mount LG-NAS\Home automatically onto /lgnas to use in a backup script.

Im using  

mount -F cifs -orw,user=,password=.soft /LG-NAS/Home /lg-nas

It fails , ive tried every combination of the sharename i can think of and always get the same message. When i get it to work ill put it into /etc/fstab.

It can be mounted using kde. But when i tried to use this moint point in my scripts it failed. Plus i would rather have a moint point in fstab for ease of admin

Any ideas what im doing wrong.

Paul 

What is the sharename i should use.

---

### Post by alexthunder on 2011-12-02
When I try to mount using the following command:
```
sudo mount //lg-nas/Share /media/LGNAS -t cifs -o username=USER,password=PASSWORD,uid=1000,gid=1000
```
or
```
sudo mount //LG-NAS/Share /media/LGNAS -t cifs -o username=USER,password=PASSWORD,uid=1000,gid=1000
```
I get the following error:
```
mount error: could not resolve address for LG-NAS: Unknown error
```

But I can mount using IP address of the NAS instead:
```
sudo mount //192.168.1.5/Share /media/LGNAS -t cifs -o username=USER,password=PASSWORD,uid=1000,gid=1000
```

I had problem mounting before until I installed cifs-utils. Make sure samba is installed as well.
```
sudo apt-get install cifs-utils samba
```

---

