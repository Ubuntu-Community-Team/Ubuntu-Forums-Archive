---
title: "Login screen defaults to secondary monitor"
date: 2010-01-11
forum: General Help
---

### Post by protargol on 2010-01-11
I have a dual monitor setup with the primary on the left and the secondary on the right.  When the login screen comes up after a reboot for instance, the login options such as user selection are on the secondary (right) monitor.  How can I change this?  Thanks.

---

### Post by miniyak on 2010-01-11
I've seen the same thing happen with my friends laptop. His solution is to plug in after login.

That might not make sense with a desktop set-up though

---

### Post by scouser73 on 2010-01-11
> **protargol said:**
> I have a dual monitor setup with the primary on the left and the secondary on the right.  When the login screen comes up after a reboot for instance, the login options such as user selection are on the secondary (right) monitor.  How can I change this?  Thanks.

You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

---

### Post by miniyak on 2010-01-11
> **scouser73 said:**
> 
**1** - Paste this command into terminal: **gksudo nvidia-settings**



Would that only be if you are using the nvidia driver?

---

### Post by shiwen1984 on 2010-01-11
Hi [scouser73]("http://ubuntuforums.org/member.php?u=536148").
Actually I have the same problem.
And the other problem is  **6** - Click **Save To X Configuration File**. When I did this, the system informs me that failed to parse existing X config files..........
Could you help me with this?
Thanks a lot

---

### Post by scouser73 on 2010-01-12
> **shiwen1984 said:**
> Hi [scouser73]("http://ubuntuforums.org/member.php?u=536148").
Actually I have the same problem.
And the other problem is  **6** - Click **Save To X Configuration File**. When I did this, the system informs me that failed to parse existing X config files..........
Could you help me with this?
Thanks a lot

Paste these commands into Terminal to create a new Xorg.conf, that should now have created a new xconfig file.

The first step creates a backup of your currently working xorg.conf file.
**> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak**

Step 2 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.
**> sudo nvidia-xconfig**

Step 3 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.
**> sudo nvidia-settings**

If this does not work then after step 1, do **sudo rm /etc/X11/xorg.conf** to delete your current xorg.conf file. Then run **sudo nvidia-xconfig** and **sudo nvidia-settings**.

---

### Post by scouser73 on 2010-01-12
> **miniyak said:**
> Would that only be if you are using the nvidia driver?

Yes, that command is for use with nVidia graphics cards only.

---

### Post by xstnc on 2010-01-12
Is there any fixes for Intel onboard cards? 
Trying to run multiple monitors on a HP6930p and it's giving me the same problem.

---

### Post by miniyak on 2010-01-12
scouser73's suggestion may work well for me and my panp5 (her nvidia card doest want to properly do dual screens either) but where ive seen this exact problem was on a dell laptop w/ onboard intel stuff

seems that ubuntu prioritizes the monitor of the highest vertical resolution as the main monitor for some odd reason, some how changing all the settings you wanted on start-up.

---

### Post by protargol on 2010-01-15
I'm not sure what's not working, but it treats the left monitor as the default (shows all Ubuntu boot images and text), then switches to the right monitor for login, and then back to left monitor for further Ubuntu initialization.  I'm thinking it's not an xorg.conf issue.  I could post what my xorg.conf file looks like, but I think the issue is elsewhere

---

### Post by jeroenst on 2013-04-12
> **scouser73 said:**
> You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

Tested this with Ubuntu 12.10 with no luck, login screen still appears on the wrong monitor... :-(

---

### Post by wildmanne39 on 2013-04-12
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

