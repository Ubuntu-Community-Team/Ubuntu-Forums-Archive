---
title: "Unable to write to drive"
date: 2009-09-13
forum: General Help
---

### Post by rmcellig on 2009-09-13
Looks like my problem deals with permissions. When I drag and drop a file to my external USB HD, I get the error enclosed in this post. What can I do to solve this?

Is there a GUI way I can view/change permissions rather than going to the command line?

---

### Post by scouser73 on 2009-09-13
Go to **Terminal**, copy & paste this command: **gksudo nautilus**

That will open Terminal as root, navigate to your new drive, **Right Click**, select the **Permissions** tab change the **Owner** drop-down menu to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write**, **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by rmcellig on 2009-09-13
Thanks that worked. I have one question. I use a Live CD of Clonezilla to make backup images to the same drive. Does Clonezilla automatically use root when backing up or does it use my user account? Do I need to be concerned here?

Thanks again!!

---

### Post by tivoboy on 2009-10-08
@scouser73

I signed up for this forum JUST to THANK YOU for this information. I have been scouring the threads trying to find a way to get WRITE ACCESS to an external drive.  Tried all SORTS of commands, fdisk, mount, etc.  Nothing worked.  

This ONE COMMAND instantly enabled access and allowed me to write and to DELETE some data from an external drive that I needed to get repaired.

I GUESS that this command is a scary one in that it opens up a lot of access locally, and especially for someone using the UBUNTU CD just for doing some admin work, it could prove to be fatal for another hda or other OS local drive.  

But, if one tip toes around and watched what they are doing, it seems to JUST WORK which is all I needed.

Again, thanks for being here and helping so pragmatically!

---

