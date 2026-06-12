---
title: "Ubuntu 11.04 won't boot"
date: 2012-01-21
forum: General Help
---

### Post by dorlow on 2012-01-21
Ok, I've been an Ubuntu user as my only os for years and haven't had trouble until the last few weeks.  My computer wouldn't boot up a few weeks ago so I reloaded it.  I have a ton of personal files I back up (about 500 gb of pics and videos).  So I reloaded the pc and it takes about 4 days to redownload all my files.  Twice now I've redownloaded all my files and then rebooted and the computer won't boot.  I see the little dots showing Ubuntu is booting but then it just goes to a black screen.  I can go to Ctrl + alt + 1 and get to a command line.  I uninstalled the software that I used to restore my files via the uninstall script to see if that was causing the boot issue.

One weird thing I've found in the last 3 reloads in the last few weeks is sudo doesn't work anymore.  I get the error 

Sudo: can't open /etc/sudoers: permission denied

Don't know if this has anything to do with why the pc won't boot.  I was planning on researching this once I got all my files restored and the pc operational.

---

### Post by dorlow on 2012-01-22
Oh well, I just reloaded my computer's OS again.  Sudo seems to work now.  I think my problem is I was restoring my files and I think it was overwriting my home directory.  I'm restoring to an alternate location now and I'll just move the files back manually.

---

### Post by 2F4U on 2012-01-22
How do you restore the files? Do you keep the user and group id's or do you overwrite them?

---

### Post by dorlow on 2012-01-22
> **2F4U said:**
> How do you restore the files? Do you keep the user and group id's or do you overwrite them?

Not 100% sure what you mean.  I use Crashplan to backup my files.  I then have to restore them from the web.

---

