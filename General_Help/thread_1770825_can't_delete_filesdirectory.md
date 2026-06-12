---
title: "can't delete files/directory"
date: 2011-05-29
forum: General Help
---

### Post by mistertransistor on 2011-05-29
I have managed to create a directory /media/SEISMICDATA that should be a removable device. But somehow it's a directory with files in it. I want to get rid of it.

If I do 
  sudo rmdir SEISMICDATA
it naturally complains that the directory is not empty, which I think is true. However
  ls SEISMICDATA 
returns Permission denied, but
  sudo ls SEISMICDATA
shows four files in there.

Now the problem:
  cd SEISMICDATA
gives Permission denied, and
  sudo cd SEISMICDATA 
gives 
sudo: cd: command not found

Catch-22 I'd say. ls -l shows
drwx------ 2 root root 4096 2011-05-29 18:17 SEISMICDATA

Please tell me how to delete these files and directory.
Thanks
Andrew

---

### Post by szabouk on 2011-05-29
> **mistertransistor said:**
> I have managed to create a directory /media/SEISMICDATA that should be a removable device. But somehow it's a directory with files in it. I want to get rid of it.

If I do 
  sudo rmdir SEISMICDATA
it naturally complains that the directory is not empty, which I think is true. However
  ls SEISMICDATA 
returns Permission denied, but
  sudo ls SEISMICDATA
shows four files in there.

Now the problem:
  cd SEISMICDATA
gives Permission denied, and
  sudo cd SEISMICDATA 
gives 
sudo: cd: command not found

Catch-22 I'd say. ls -l shows
drwx------ 2 root root 4096 2011-05-29 18:17 SEISMICDATA

Please tell me how to delete these files and directory.
Thanks
Andrew


man rm

---

### Post by wojox on 2011-05-29
You need to use the -rf switches.

---

### Post by iclestu on 2011-05-29
> **mistertransistor said:**
> I have managed to create a directory /media/SEISMICDATA that should be a removable device. But somehow it's a directory with files in it. I want to get rid of it.

If I do 
  sudo rmdir SEISMICDATA
it naturally complains that the directory is not empty, which I think is true. However
  ls SEISMICDATA 
returns Permission denied, but
  sudo ls SEISMICDATA
shows four files in there.

Now the problem:
  cd SEISMICDATA
gives Permission denied, and
  sudo cd SEISMICDATA 
gives 
sudo: cd: command not found

Catch-22 I'd say. ls -l shows
drwx------ 2 root root 4096 2011-05-29 18:17 SEISMICDATA

Please tell me how to delete these files and directory.
Thanks
Andrew

you are sure that it is not ACTUALLY a removable drive? try

```
sudo umount /media/SEISMICDATA
```

---

### Post by mistertransistor on 2011-05-29
wojox
thanks very much. That solved it. You probably guessed that I'm a relative newbie.

iclestu
yes I was sure - the device has been physically removed. I did try a umount and got

andrew@andrew-Seismo:~$ sudo umount /media/SEISMICDATA
[sudo] password for andrew: 
umount: /media/SEISMICDATA: not mounted

but thanks anyway.

Andrew

---

