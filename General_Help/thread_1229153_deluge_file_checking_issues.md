---
title: "deluge file checking issues"
date: 2009-08-01
forum: General Help
---

### Post by ffxigotenks on 2009-08-01
I've been using deluge for a while and it seems like a perfect client for me, the only problem I'm having with it is that sometimes when I start it up, it will say that it's checking the files, but none of them are progressing in the check, even if I shut down the client and daemon when it starts up it'll have the same problem, the only thing I can see that fixes it is a complete reboot, any ideas on why this is? I' using 1.1.9

---

### Post by hibliss on 2009-08-01
> **ffxigotenks said:**
> I've been using deluge for a while and it seems like a perfect client for me, the only problem I'm having with it is that sometimes when I start it up, it will say that it's checking the files, but none of them are progressing in the check, even if I shut down the client and daemon when it starts up it'll have the same problem, the only thing I can see that fixes it is a complete reboot, any ideas on why this is? I' using 1.1.9

I do not use deluge, I use rtorrent, but do you stop the torrents before shutting down the client?

I googled a bit and this seems like a common problem, but with the previous version, where you say you are using the latest.

---

### Post by ffxigotenks on 2009-08-01
yeah, I've had this problem for weeks, and been googling solutions with little to no success, so I'm stuck

---

### Post by hibliss on 2009-08-01
> **ffxigotenks said:**
> yeah, I've had this problem for weeks, and been googling solutions with little to no success, so I'm stuck

Out of curiosity, what reason do you have to shut down the client when you are not shutting down? You could always just stop them and keep the client open if the problem is only after closing and reopening.

I say this as a workaround and not a solution.

---

### Post by ffxigotenks on 2009-08-01
sorry, I forgot to mention that restarting it doesn't always work, it may have to do with the fact that the drive that the torrents save to isn't always mounted on startup, and sometimes restarting doesn't even help, I have to remove the torrent, add it again, and verify local data for it to resume

---

### Post by hibliss on 2009-08-01
You will have to wait for someone who knows more about Deluge. In rtorrent there is an option to save_session, which will make it so the client will open in it's previous state as long as it is properly shutdown. This means no checking ever.

---

### Post by michy99 on 2009-08-01
I think your problems will be solved if you set up your drive to mount automatically at boot. What filesystem is the drive?

---

### Post by ffxigotenks on 2009-08-01
> **michy99 said:**
> I think your problems will be solved if you set up your drive to mount automatically at boot. What filesystem is the drive?

it's an ext3 partition, I know how to set it up to mount at boot, I just have been a bit lazy about it... I'll try fixing that and seeing what happens

---

### Post by haafmaad on 2010-10-01
Here's the solution:

First find out from deluge that in which drive are you downloadind the  torrents.
When you reboot or start your machine at first mount that drive then  start deluge.
You can mount the drives at startup too editig the fstab file

---

