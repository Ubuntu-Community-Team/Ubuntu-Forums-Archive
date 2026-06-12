---
title: "Locked out ssh"
date: 2010-03-26
forum: General Help
---

### Post by ronan.l.n on 2010-03-26
Hi all,
Here is my problem. I am using a machine I SSH into to do some processing over very large files, but I am now unable to access it through ssh.
The shell I had opened is not responsive, and when I try to connect again, it hangs even before asking for the password.
I suspect this to be a memory problem as a couple of processes need to load a lot of the data to process it.

Is there an emergency way of going back into this machine, or killing some processes to free the memory up ? I tried ssh ... 'kill -9 pid' but it is not even able to do this.

Do you reckon the processing is still happening or is the machine completely idle ? How would you advise me to go back to it ? It's for my final year project, and I'm starting to stress !

Thanks,
R.

---

### Post by joe.beard on 2010-03-26
Do you only have remote ssh access to this box or can you get local access?

---

### Post by ronan.l.n on 2010-03-26
No, I can only access it remotely

---

