---
title: "edit fstab in recovery shell"
date: 2011-04-21
forum: General Help
---

### Post by Bolinga on 2011-04-21
Hey,
I am stuck in recovery shell because I mistyped one line in the fstab file. I know what I did wrong but now I cant edit my fstab anymore. I can only enter recovery shell and thats it.
sudo nano doesent work because it's a read only file / disk.
So any idea is worth trying :)

---

### Post by mikewhatever on 2011-04-21
You get full root access in the recovery mode, so that 
```
nano /etc/fstab
```

should open the file for editing. No need for sudo because you are superuser in recovery already.

---

### Post by Bolinga on 2011-04-21
I know, I have tried several times but when I exit it again its asks if I want to save, is say yes. But then it says cant safe, it is a read only file.
I've tried to change any other file from the same disk but it says the same thing.

---

### Post by FoobyZeeky on 2011-04-21
Try using chmod (will it run in recovery shell properly?):

```

cd etc
chmod a+w fstab

```

Then try editing it. Just a thought.

---

### Post by mikewhatever on 2011-04-21
If every file is read only, it strongly implies that the file system is mounted as read only. If that is becasue of the change to fstab, you might be able to correct it by editing fstab from a live cd/usb. Another reason may be filesystem errors, in which case you should also use the cd/usb and run fsck.

---

### Post by Bolinga on 2011-04-22
thanks for the reply's :)
to bad it dident have any result :(
Same problem over and over

I even already tried with kernel, but then it puts me back into recovery shell :/

---

### Post by erind on 2011-04-22
> **Bolinga said:**
> I know, I have tried several times but when I exit it again its asks if I want to save, is say yes. But then it says cant safe, it is a read only file.
I've tried to change any other file from the same disk but it says the same thing.     

 When you boot in recovery mode, at the prompt (as root) type:
      
  ```
# mount -w -o  remount  /
```
This will remount the file system in write mode, so you can edit the fstab file.

---

### Post by Bolinga on 2011-04-22
HMmm...
All of the above dident work :/
But I managed to change my fstab bij starting ubuntu from the OS install cd.

Rather weird that it is possible then :/
soo thnxs :)

---

### Post by erind on 2011-04-23
Glad you got it working. The previous and the following commands worked fine for me, anyway assuming that */dev/sda1* is your main OS partition, you could have also tried:

    ```
# mount -w -o remount /dev/sda1 /
```Or the same thing, but written a bit differently:

```
# mount -o remount,rw /dev/sda1 /
```If your OS is on a different partition, then replace */dev/sda1* with the proper */dev/device_name*. Check your */etc/fstab* file.

---

