---
title: "deleting empty mount points"
date: 2011-12-17
forum: General Help
---

### Post by carlbelmonte on 2011-12-17
Hello,

1. In a previous thread, I had installed ntfs-config which added all my ntfs volumes to fstab, and automatically mounted them (against my will!) After deleting those lines in fstab, and removing ntfs-config, I thought all was back to normal.

But, on checking the media directory, I find that there are still the mount points in there for those volumes, although they are completely empty. From what I have searched on the forum, mount points are not automatically deleted and the user must do this himself.

I have tried sudo rmdir /media/"mountpoint" where "mountpoint" is the name of the volume, but all I get back is "file or directory unknown" or something of the sort. I also tried rm -r, but that gave the same error.

Please, what am I missing? Even if these empty mount points don't seem to create any particular problem, is there some way to remove them?

2. I have an external hard disk that is partitioned in 2 volumes. It is not listed in fstab, but is automatically mounted at launch, I assume because it is on a USB bus. When I click on the icon in the launch bar, I get Nautilus with the contents of the volume - the name of the volume is correctly listed.

But, if I open the volume from within an application (such as LibreOffice, Transmission, or anything else), the volume name has an underscore appended. For example, in Nautilus, the volume will appear as "Backup", while when opened from an application, its name is "Backup_".

And the Media directory contains mount points for both variants. But, the volume name without the underscore is owned by root, whereas the variant with the underscore is owned by the user. Is there some reason for this or is it just a mistake? And should I remove the duplicate mount points and how can I do that?


Just for information, here is the contents of my fstab file:
```
#Entry for /dev/sda8 :
UUID=1eaf11d9-194d-4eac-981d-291d89e50926    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda9 :
UUID=afe9af1c-3b18-49b8-8ff1-08b292b96f9f    none    swap    sw    0    0

```Many thanks for all tips.

Best regards.
Carlos

---

### Post by mikewhatever on 2011-12-17
Can you post the output of 'ls /media', followed by the output of the 'rmdir' command you use. It seems you may have mistyped something.

PS: Just thought I'd mention, it's not a crime to have an empty directory or two in /media.

---

### Post by carlbelmonte on 2011-12-17
Thanks.

I have the following:

on the external hard disk, all NTFS volumes:

Backup     ---> owned by root
Backup_   ---> empty
Backup__ ---> owned by user

Image Drive     ---> owned by root
Image_Drive    ---> empty
Image Drive_   ---> owned by user


on the internal hard disk, all NTFS volumes

Local Disk     ---> owned by root
Local_Disk     ---> empty
Windows_XP  ---> empty
Downloads     ---> empty
M:                 ---> empty


Thanks to your tip, I just realized that it is all case-sensitive, so I tried again to remove the empty mount points, but with the capital letters, and everything worked fine. Typical beginner error. Thanks.

Now, I have the problem of the external hard disk and double mount point, one without underscore and one with. Can I safely remove the latter? Does it matter? And what is the reason for that double mount point, since it is a little confusing?

I read in this post:
[http://ubuntuforums.org/showthread.php?t=1887113](http://ubuntuforums.org/showthread.php?t=1887113)

that this could be due to the [COLOR=#000000][FONT=Verdana]"Disk Utility" a.k.a. gnome-disk-utility a.k.a. Palimpsest not using UUIDs. But, I would appreciate confirmation before making changes that could render Ubuntu unstable.

Best regards.
Carlos
[/FONT][/COLOR]

---

### Post by mikewhatever on 2011-12-17
> **carlbelmonte said:**
>  ...

Now, I have the problem of the external hard disk and double mount point, one without underscore and one with. Can I safely remove the latter? Does it matter? And what is the reason for that double mount point, since it is a little confusing?

...

Not sure, but I also don't see why that is a problem. Does it cause malfunctioning? Why do you have to remove it?

Generally, since nothing but / and swap are mounted by fstab, it should be safe to delete all mount points in /media, as they'll get re-created next time the partitions are mounted. Hopefully, not against your will. 
:~)

---

### Post by carlbelmonte on 2011-12-17
No, everything is working fine, but since I am very new at this, I just wondered if it was normal. If everybody with an external USB hard drive has 2 mount points for their volumes, one owned by root and the other by the user, then I would not bother about this. But, if most people only have one mount point, then I would like to understand what is different about my installation. Thanks for your suggestions.

Best regards.
Carlos

---

### Post by dcstar on 2011-12-17
> **carlbelmonte said:**
> Thanks.

I have the following:
........

You were asked to provide the output of the /media folder, please do this and provide what you were asked:

```
ls -al /media
```

---

### Post by carlbelmonte on 2011-12-17
Uhm, excuse me, David, Mike kindly requested that I post the result of ls /media, and not what you write. And that is what I did. You will find this information above in post #3.

Thanks.
Carlos

---

### Post by JKyleOKC on 2011-12-17
> **carlbelmonte said:**
> Uhm, excuse me, David, Mike kindly requested that I post the result of ls /media, and not what you write. And that is what I did. You will find this information above in post #3.Actually the preferred way to provide such information is to copy the result directly from the screen, and paste it into your message between CODE tags, like this: 
```
[COLOR="Red"]jk@mehitabel:~$ [/COLOR]ls /media
cdrom  usb

```To create the code tags, click the "#" icon at the top of the message editor. You can then paste the clipboard content between them. The part of my example in red is simply my terminal's prompt; I usually leave it in, to show the whole terminal action.

The eliminates the possibility of typos in transcribing the output, and also the possibility of having a wrong-case situation.

And welcome to the forums!

By the way, both of those mount points in my example are currently empty, but I leave them there so that they are ready for use any time I need them.

---

### Post by mikewhatever on 2011-12-18
Actually, I'd much rather have had the output itself, but since that was intended to troubleshoot the 'rmdir' error, and that is solved, it is now irrelevant.

Generally, when asking for an output, we expect to see it as is without being edited in any way.

---

### Post by carlbelmonte on 2011-12-18
Thank you, Jim, for the welcome, and thanks to all for your comments, particularly Mike who helped me further my understanding of this issue.

I have deleted all the mount points in /media whether they are owned by root or user, re-booted, and lo-and-behold, everything is fine. New mount points for the 2 volumes on the external USB hard drive are present in the directory, and I have all user permissions for them. There is no mount point for these volumes owned by root anymore.

So, I shall now mark this thread as solved, and add some comments for any beginners who have this same problem and search the forum for a solution.

From what I have understood, mount points are simply directories created to display the contents of volumes. The user can create them as can the system. Generally, user will receive all permissions and does not have to worry about this issue.

However, in some cases, perhaps because I installed outdated tools (although I do not blame ntfs-config, since I lack sufficient knowledge for that), there will be different mount points for the same volume, one owned by root without permissions for the user, and another owned by the user with all permissions.

The solution for me was to remove the offending tool(s), edit the fstab file (sudo gedit /etc/fstab) to remove any extraneous lines and only leave the Ubuntu root and swap volumes, and then simply delete all mount points from the media directory (sudo rmdir /media/"mountpoint" and be sure to place quotes around volume names that contain a space.)

This solved the problem for me completely, I now have what I wanted, and have a somewhat better understanding of the file system and volume mounting.

Thanks again to all. And on to the next problem.

Best regards.
Carlos

---

