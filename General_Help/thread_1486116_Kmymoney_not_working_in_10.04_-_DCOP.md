---
title: "Kmymoney not working in 10.04 - DCOP?"
date: 2010-05-17
forum: General Help
---

### Post by Marsonis on 2010-05-17
I have been using Kmymoney for several years now and I really like it.  Unfortunately, I can't seem to get it working in 10.04.  

Whenever I start the program I get an error box that says "There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not read network connection list.
/home/name/.DCOPserver_comuptername_0

Please check that the "dcopserver" program is running!"

After I click the OK button, the program loads and I get another error box:

"Could not find mime type

application/octet-stream"


I did not have this problem in 9.10.  In 9.10 I used 32bit and in 10.04 I installed 64bit.

Any ideas?

---

### Post by Hei Ku on 2010-05-22
You don't have KDE3 installed, that's why it can't find the DCOP services.

In your case, you might want to try version 3.98.1, which is a Release Candidate for KDE4.

Here is a PPA you can install it from: [https://edge.launchpad.net/~claydoh/+archive](https://edge.launchpad.net/~claydoh/+archive)

You have to uninstall your current version first.

---

### Post by Marsonis on 2010-05-24
Thanks for the reply.  I have installed the 3.98.1 version, but it crashes before it loads.  Here is the error it throws:

Application: KMyMoney (kmymoney), signal: Segmentation fault

Any thoughts?

Also, would it be difficult for me to install KDE 3?

Thanks!

---

### Post by Hei Ku on 2010-05-25
Start it from console and let me know if it throws any other error message.

Did you install it from the PPA?

For Ubuntu, installing KDE3 is kind of hard, and really unsupported. Or at least, that's the way it was last time I used it.

---

### Post by Marsonis on 2010-05-26
I installed it from this PPA:  [https://edge.launchpad.net/~claydoh/+archive/kmymoney2-kde4](https://edge.launchpad.net/~claydoh/+archive/kmymoney2-kde4)

When I started it from the console, it threw a lot of errors like this:

trying to create local folder /home/name/.kde/share: Permission denied

So, I tried running the program with sudo and it loaded just fine.  Using sudo to launch is a workaround, but is there a way to change the permissions so that it does not need to be run as a superuser?

Thanks for your help!

---

### Post by Hei Ku on 2010-05-26
So, the problem seems to in the .kde/share folder of your home. If you can get to it using Nautilius, double click and make sure you are the owner and you have write permissions to it.
Running an application with sudo is never a good thing, other than for troubleshooting like in this case.

---

### Post by Marsonis on 2010-05-29
You're right - the owner of all of the folders and files within the .kde folder is root.  I used sudo nautilus to launch a root version of nautilus to change the permissions, but it looks like I have to change each file individually.  Nautilus has a button that says apply permissions to all files, but it does not seem to work.  Is there any way for me to change all of the permissions at once or do I need to go through each one?

Thanks again.

---

### Post by pfnorris on 2010-05-29
If you don't mind using the command line, a simple command will change ownership recursively (i.e. on all sub-folders and files). The command is:

sudo chown -R <username> /home/username

Change <username> for your own username on the system. This will change ownership on all files and subfolders in your home directory. This should correct any anomalies that might have crept in.

---

### Post by Hei Ku on 2010-05-29
I'd do:

sudo chown -R <username>:<username> /home/username/.kde

Just in case, you know.

---

### Post by Marsonis on 2010-05-30
That worked!  The program loads fine without sudo and I can use it now!

Thanks for your help!!

---

### Post by egwest on 2010-07-09
Thank you for this thread! I was having the same problem, just got a new notebook computer and installed Ubuntu 10.04. Installed all my favorite programs and digikam and kmymoney would not work.

But thanks to this thread, both are working properly now!

---

### Post by 73ckn797 on 2010-11-25
> **Hei Ku said:**
> I'd do:

sudo chown -R <username>:<username> /home/username/.kde

Just in case, you know.


This works.

---

