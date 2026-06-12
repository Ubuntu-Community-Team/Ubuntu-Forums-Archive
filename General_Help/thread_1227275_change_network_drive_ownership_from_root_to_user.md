---
title: "change network drive ownership from root to user"
date: 2009-07-30
forum: General Help
---

### Post by zippyties on 2009-07-30
I just followed the [_[COLOR="RoyalBlue"]tutorial[/COLOR]_]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") on how to edit fstab to mount a network drive.  I have succeeded in mounting the drive however it says that it is owned by root and does not allow me to even view the folder contents.  I tried running using
```
sudo nautilus /media/Mdrive
```
I got an "access denied" dialog

I also tried to change the ownership using "sudo chown" but I got access denied here also

How do I change the ownership of the drive?

---

### Post by Het Irv on 2009-07-30
Did you do the chmod stuff?

---

### Post by zippyties on 2009-07-30
> **Het Irv said:**
> Did you do the chmod stuff?
Do you mean; sudo chmod 600 ~/.smbcredentials?

If so then yes.

---

### Post by Het Irv on 2009-07-30
Hmm, I have used that Tut a few times, and actually wrote a part of it. I never had that problem.  Can you post your fstab file?

---

### Post by zippyties on 2009-07-30
> **Het Irv said:**
> Hmm, I have used that Tut a few times, and actually wrote a part of it. I never had that problem.  Can you post your fstab file?
I can yes, but I would like to avoid a public post.  Is there a way to send it privately?

Thanks,

---

### Post by synapsys on 2009-07-30
Try un-mounting the drive first then change permissions on the folder it mounts to.

---

### Post by Het Irv on 2009-07-30
You send me a PM with it or a link to the pastebin

---

### Post by Het Irv on 2009-07-30
Look at #6 on that Tut, seting the UID may help

---

### Post by zippyties on 2009-07-30
@Het Irv  That did it!  Thanks for the help,  I used windows for years and because of that, I have this sort of dependency on GUI's.  Linux commands make sense, but the fact that the changes take place on the CLI or in a .conf file, tends to mess me up.

@Synapsys Thank you also your advice. I couldn't make the "umount" command work so I restarted the computer, (after implementing line 6 in the tut) and incredibly it worked.

Now I can use this knowledge to map the company ftp site as a drive:D.

Thanks again!

---

### Post by Het Irv on 2009-07-30
For anyone that finds this post later, When the OP sent me his fstab, I saw that the UDI=1000 part was missing.

---

