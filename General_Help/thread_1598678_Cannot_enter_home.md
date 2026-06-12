---
title: "Cannot enter /home"
date: 2010-10-16
forum: General Help
---

### Post by sabersong on 2010-10-16
I tried to change the permissions on my /home the other day, which failed. After trying to make the changes, I could no longer access my /home folder. I tried restarting, but the restart would only get so far, then I'd get an error saying "cannot enter /home" and the restart would fail.

I wrote this off to user stupidity and reinstalled kubuntu, this time going to 10.04 (I had been using 9.04.) After installation completed, I restarted the computer, and everything seemed to be fine. I installed a couple applications, copied over my old fstab (I back it up every month, along with a few other configuration files), and told the computer to do the recommended updates. It did them and said a restart was required. I restarted, but the restart process failed again with the same error -- "cannot enter /home, using /" I can't log in to my computer.

Does anyone have any idea how to fix this problem?

---

### Post by dcstar on 2010-10-16
> **sabersong said:**
> I tried to change the permissions on my /home the other day, which failed. After trying to make the changes, I could no longer access my /home folder. I tried restarting, but the restart would only get so far, then I'd get an error saying "cannot enter /home" and the restart would fail.

I wrote this off to user stupidity and reinstalled kubuntu, this time going to 10.04 (I had been using 9.04.) After installation completed, I restarted the computer, and everything seemed to be fine. I installed a couple applications, copied over my old fstab (I back it up every month, along with a few other configuration files), and told the computer to do the recommended updates. It did them and said a restart was required. I restarted, but the restart process failed again with the same error -- "cannot enter /home, using /" I can't log in to my computer.

Does anyone have any idea how to fix this problem?

Don't blindly copy old configuration files to working systems.

Post the contents of this fstab file you refer to and some actual details of the "configuration files" you replaced.

---

### Post by sabersong on 2010-10-17
I read your reply, and in reading it I realized that the problem WAS my fstab. I'd been using the same fstab through the past three incarnations of Kubuntu, but when I reinstalled this time, I partitioned the drive differently, which rendered my old fstab useless. The problem is fixed now. Thank you for your help.

---

