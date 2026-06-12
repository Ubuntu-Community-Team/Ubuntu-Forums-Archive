---
title: "Not able to update"
date: 2010-09-10
forum: General Help
---

### Post by FahadMKS on 2010-09-10
Hi

I have installed the ubuntu Studio to my computer and now have installed the Klam AV to it so as to check for Viruses.

Now the issue is that, I am not able to update the Virus Database of the Klam Av anti Virus software.
The message I get there is that it cannot create a File.
What do I do to solve this issue.
If the Klam AV is not the best, can anyone suggest me a better Antivirus software to install on the computer I have installed the Ubuntu.

---

### Post by FahadMKS on 2010-09-12
So long have I been waiting for an answer for the issue I had given.

If anyone does know what is the exact cause, please do help me with that.

---

### Post by Lukas666 on 2010-09-12
I really don't think you need an antivirus on Ubuntu. And if you had more popular edition (I don't even know what "Studio" is) you might increase your chances for getting a response.

---

### Post by FahadMKS on 2010-09-12
Is that so?

But what is the difference between the normal Ubuntu and the Ubuntu Studio OS except for the graphical changes.

---

### Post by Lukas666 on 2010-09-12
> **FahadMKS said:**
> Is that so?

But what is the difference between the normal Ubuntu and the Ubuntu Studio OS except for the graphical changes.

I don't know (and I don't care), also I bet over 90% of users installs the standard version. I wish I could help you but my OS is different :)

So... unless you're an expert use what others use if you're going to ask them for help.

---

### Post by Lateralis on 2010-09-12
I would echo what Lukas said, in that AV software for Ubuntu really isn't necessary.  There are so few viruses for Linux that AV software is really quite redundant.  

But of course it is your choice. =)  And I will fight for you right to choose to have AV software if you want it!  

As for why you can't update, it looks like it is trying to write a file to a directory which is protected, namely /var.  To write files to any directory other than you home directory (/home/<uyour login name>) you need root/superuser privileges.  So, you can either start the programme with root privileges, or change the directory that KlamAV uses for its virus definition database to a directory in your home partition, perhaps ~/KlamAV.  Whether you can do the latter... I'm not sure.  I'm totally unfamiliar with AV software in Ubuntu/Linux generally so you'll have to look at the KlamAV manual for that sort of information. 

@ Lukas 

His problem clearly isn't Distro specific.  

Moreover Ubuntu Studio is also an officially recognised version of Ubuntu.  It is designed for the audio and video editing enthusiast/professional. 

See [this Ubuntu Wiki page]("https://help.ubuntu.com/community/What%20Is%20Ubuntu%20Studio") for more info.

---

### Post by llamabr on 2010-09-12
I'm not sure about Lucas' point, since your OS and his are probably the same, except for some meta packages that you installed for some graphics, or whatever.

It looks like you're trying to write to /var, but don't have permission.  I don't know how that program works, though I think it's supposed to be useful for people who dual boot with windows, so you can use your ubuntu partition to do antivirus on the windows version.  In any case, can't you install from the repos?:

```
brock@hops:~$ apt-cache search klam
klamav - KDE frontend for ClamAV
brock@hops:~$ 
```


I don't think you need antivirus software.  I've been running one form or another of linux at home for 15 years, and never had antivirus software, or a virus.  But it's your box.

To install it in /var, you either need to use sudo, or else put it somewhere in your home, like ~/virus/

But again, I don't have any idea how that program works.

---

### Post by FahadMKS on 2010-09-12
Thanks for the response.

I use the Klam AV o get rid of the Virus on my external HDD so that I can use that in my other computers which has the windows installed.
None of the AV softwares for the windows seems to have get rid of the Virus in that where as Klam AV with Linux has done the job in less than a minute or so.

Anyway, Thanks for the responses.

---

### Post by FahadMKS on 2010-10-06
The issue seems to have solved with the new version of the Ubuntu.
Now I get the updates of Clam AV along with the normal updates.

---

