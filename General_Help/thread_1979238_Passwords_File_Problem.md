---
title: "Passwords File Problem"
date: 2012-05-13
forum: General Help
---

### Post by prashanth1991 on 2012-05-13
Hello everyone, I have a problem, this might be a minor prob to you but its a major problem for me.
I'v learnd that ubuntu stores the administrative password in a file(dint remember the name of file). If I authenticate that file for a download, like we type password for downloading a file. Until  that file gets downloaded, I can't authenticate another application. Is this correct? Well, I think so.

So, whenever I authenticate an application, the passwords file gets locked, the lock is released only when the specific action is completed.

Now, my problem is, I use desktop. I dont have UPS, lost its backup recently. I authenticate an application for downloading files by entering the password. After a while, when the file was still downloading, Power went off. So PC just got powered out at once. Now, after a while when I tried to login into that specific account, I can't log into it anymore. The account gets logs in and automatically logs out. Can anyone please help me with this problem. I will be very thank full to you guys...

---

### Post by papibe on 2012-05-13
Hi prashanth1991. Welcome to the forums!

> **prashanth1991 said:**
> So, whenever I authenticate an application, the passwords file gets locked, the lock is released only when the specific action is completed.

Unfortunately, no. It doesn't work that way.

My guess is that the disk suffered some sort of data corruption. I would check the console right after you got kick out of the session. There, you should be able to see any important error message.

To go to the text mode console press Ctrl+Alt+F1
To go back to the graphic mode Ctrl+Alt+F7

Report back if you get more clues about what is happening.
Regards.

---

