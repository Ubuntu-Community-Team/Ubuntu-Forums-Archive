---
title: "password problems after 6.06 ugrade"
date: 2006-06-30
forum: General Help
---

### Post by em0maha on 2006-06-30
Ever since I installed 5.10 my computer has frozen up after about 15-30 minutes of idle time, and I was never able to find the cause. So I tried upgrading to 6.10 last night, and of course, my computer froze in the middle of the upgrade. 
The computer is working okay now. I can not log in to the one user account that did not have admin privilages, but all of the other accounts work well. When I log on to one of my other two user accounts that do have admin privilages, I can open up the terminal and run any sudo command with my user password. However, when I try and open the package manager or the user accounts program, I get the following error:
Failed to run /usr/sbin/synaptic as user root:
 Wrong password.
I know the password that I type in is the same password that I use to log on and run sudo commands. I have tried changing the password with the "sudo passwd" command, but still no luck.
Any Ideas?
Thank you very much for your time.

---

### Post by thingy on 2006-06-30
> Ever since I installed 5.10 my computer has frozen up after about 15-30 minutes of idle time,

Hmm you say the words "idle time". Could it be that your computer's power management features are kicking in and causing the freeze?

Is this a laptop?

Can you turn off all power management features (such as hdd power down, sleep mode etC) in the bios?

The rest of your post is confusing but it could be this problem:

[http://ubuntuforums.org/showthread.php?t=180206&highlight=Failed+run+%2Fusr%2Fsbin%2Fsynaptic+user+root](http://ubuntuforums.org/showthread.php?t=180206&highlight=Failed+run+%2Fusr%2Fsbin%2Fsynaptic+user+root)

Please read the FULL thread before carrying out the appropriate isntructions in that thread.

regards

jin

---

### Post by em0maha on 2006-06-30
Nevermind, I got everything to work by going through and installing all of my updates that had been missed when the computer froze the first time. Thanks for your help though.

Oh, and btw, the computer is a desktop, and I don't relaly think it was a power management issue. Ill write another post if it starts happening in 6.06.

Thanks!

---

