---
title: "File names in my ntfs partiotions have &quot;invalid encoding&quot;"
date: 2011-10-14
forum: General Help
---

### Post by glaubersm on 2011-10-14
Hello
I want automatically mount my ntfs partitions on every boot, I have use ntfs-config and file names with accented characters have "(invalid encoding)" message. Any easy way to mount my ntfs partitions with write support?

Oneiric x32
pt-br language

---

### Post by prodigy_ on 2011-10-14
For best experience simply avoid using filenames with non-English characters in them.

---

### Post by glaubersm on 2011-10-14
> **prodigy_ said:**
> For best experience simply avoid using filenames with non-English characters in them.

I can not do it.
Some programs on my win 7 will lose correct path to my files.

---

### Post by linuxwin2 on 2011-10-14
Look this link 
[http://linuxconfig.org/How_to_mount_partition_with_ntfs_file_system_and_read_write_access]("http://linuxconfig.org/How_to_mount_partition_with_ntfs_file_system_and_read_write_access")
To automatically mount  ntfs partitions add this line in /etc/fstab
```

**/dev/sda1**  /media/windows  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

```

---

### Post by WasMeHere on 2011-10-14
You can also try to add [COLOR="Red"],windows_names[/COLOR] to the line in /etc/fstab for example

```
/dev/sda1  /media/windows  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8[COLOR="Red"],windows_names[/COLOR]  0  0
```
and reboot your computer. [COLOR="Red"]windows_names[/COLOR] will make sure that Ubuntu does not allow you to enter file names that cannot be read by Windows.

Good luck
Olle

---

### Post by glaubersm on 2011-10-14
> **linuxwin2 said:**
> Look this link 
[http://linuxconfig.org/How_to_mount_partition_with_ntfs_file_system_and_read_write_access]("http://linuxconfig.org/How_to_mount_partition_with_ntfs_file_system_and_read_write_access")
To automatically mount  ntfs partitions add this line in /etc/fstab
```

**/dev/sda1**  /media/windows  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

```

Nautilus crashed some times but is working now.
Thnak you very much, friend. :)

---

### Post by MarjaE on 2011-10-14
> **prodigy_ said:**
> For best experience simply avoid using filenames with non-English characters in them.

WHAT?

And let me guess, this won't like transliterations either, if the transliterations require uncommon English letters such as the thorn.

---

### Post by Vaphell on 2011-10-14
is thorn english? i haven't seen it on sesame street ;-)

it's an encoding issue, that ntfs most likely uses some crap windows cp12xx encoding and ubuntu goes with utf8. I guess that you need to explicitly define what charset should be used to read the partition or something.

---

### Post by oldfred on 2011-10-14
As mentioned above windows_names solves many issues.

Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,uid=1000,windows_names,umask=000 0 0

---

