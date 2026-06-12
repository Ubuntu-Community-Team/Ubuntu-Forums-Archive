---
title: "Gaining premission for a hard drive"
date: 2010-03-12
forum: General Help
---

### Post by avanrens on 2010-03-12
I have used Storage device manager to mount a newly in stalled drive but don't have permission to write to the drive. how can I change the permission using the above program

---

### Post by a cup of tea on 2010-03-12
in terminal:

```
sudo chown -hR $USER disk
```

replacing "disk" with what your disk shows as. I think that'll work if it's ext3/ext4. Not sure about Windows filesystems, they're a bit of a pain with permissions. I'm kinda guessing here that your drive is "owned" by root or something and that's why you can't write to it.

---

### Post by scouser73 on 2010-03-12
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by avanrens on 2010-03-13
Thank you

---

