---
title: "Share file between windos 7 and Ubuntu"
date: 2010-07-30
forum: General Help
---

### Post by João Oliveira on 2010-07-30
Can anyone tell me, how to create a wireless network to share files between a desktop ubuntu 10.04 and a laptop with windows 7??

---

### Post by Segofam on 2010-07-30
System>Preferences>Personal File Sharing

---

### Post by sikander3786 on 2010-07-30
> **João Oliveira said:**
> Can anyone tell me, how to create a wireless network to share files between a desktop ubuntu 10.04 and a laptop with windows 7??

Hi.

Just right click on the folder you want to share, Go to Sharing Options and tick Share This Folder. It will ask you to install Sharing Services. Click Install.

After the installation is complete, log out and then back in again. Now share the desired folder, select permissions whatever you want to grant.

Hope you know how to access the files in Windows. Anyway in Windows go to run and give your pc name or ip address in this format //pcname or //ipaddress.

Username and password will be the same as on your Ubuntu Box unless you have created specific Samba Accounts.

Regards.

---

### Post by João Oliveira on 2010-07-30
> **Segofam said:**
> System>Preferences>Personal File Sharing

In personal file sharing, it says that i can't share on the network because i do'nt have the necessary programs installed!

---

### Post by sikander3786 on 2010-07-30
> **João Oliveira said:**
> In personal file sharing, it says that i can't share on the network because i do'nt have the necessary programs installed!

Thats what I told you in my post above.

Either install samba this way

```

sudo apt-get install samba

```

Or follow the steps mentioned above.

---

### Post by Segofam on 2010-07-30
Have a read through this...[http://ubuntuforums.org/showthread.php?t=1532916](http://ubuntuforums.org/showthread.php?t=1532916)

I had to search through the forum for those two files...I will have a quick search again...I should have marked it...BBS

---

### Post by João Oliveira on 2010-07-30
> **sikander3786 said:**
> Thats what I told you in my post above.

Either install samba this way

```

sudo apt-get install samba

```

Or follow the steps mentioned above.

Already did that it still apears the message [http://img225.imageshack.us/img225/5316/capturaecra.png]("http://img225.imageshack.us/img225/5316/capturaecra.png")

---

### Post by Segofam on 2010-07-30
[http://ubuntuforums.org/showthread.php?t=1473760](http://ubuntuforums.org/showthread.php?t=1473760)
I had one of the extra files that are needed.
Good luck.
Kind regards,
Scott

---

### Post by João Oliveira on 2010-07-30
> **Segofam said:**
> [http://ubuntuforums.org/showthread.php?t=1473760](http://ubuntuforums.org/showthread.php?t=1473760)
I had one of the extra files that are needed.
Good luck.
Kind regards,
Scott

Thanks a lot!!!this is working at 100%!!!

---

### Post by Segofam on 2010-07-30
We should thank the people who offered the threads!

I have also used Samba too as [sikander3786]("http://ubuntuforums.org/member.php?u=806649") suggested, it works well also.
Like you I am a newbie and the Personal File Sharing worked to a T with Win7 and XP.

We have lots to learn, but it is fun...and good for the brain too :)

---

### Post by Segofam on 2010-07-30
I am just chucking this one in because as a newbie, and possibly someone who is going to use Grub to boot into what ever OS you wish to, you are going to get sick of the build up of resigned headers for previous Kernals. This program will save you heaps of time having to learn how to edit grub etc...

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Run Ubuntu Tweak > Package cleaner > Clean Kernals
...and then select what is not being used...which I have found out is all of them, or at least, it is on my machine :)

This beats the heck out of opening up command line and doing 'sudo gedit /boot/grub/grub.cfg and then editing stuff that you don't want to stuff up :))

Kind regards,
Scott

---

