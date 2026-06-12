---
title: "Update Manager unable to check repositories"
date: 2010-10-01
forum: General Help
---

### Post by Ahava591 on 2010-10-01
I have just re-installed Ubuntu 10.04.
-The installation went smoothly, completing in approximately 25-30 minutes.
All of my hardware, including keyboard, mouse, monitor and network interface has been detected and works properly. I am currently using the machine to type this. I can browse the web using Mozilla Firefox.

My network connection does not start and stop; the machine remains connected with no indication that there is a fault with the NIC, and so on. I am able to download files at 150-170kB/s as is normal for me with Firefox.

I have not yet installed a graphical user interface to configure the firewall. I have not in any way worked with any system files. I am using the same hardware that I have used for approximately one year before this with no incident.


I first encountered this with my previous install at approximately 3:00 AM (local time,) when I manually started Update Manager and attempted to check for updates in the default repositories. I have not altered the repository list in either the previous install or this new install. The Update Manager is entirely default.


Upon checking for updates, the list of repositories hangs after I believe at least ten lists have been checked. All of the lists checked before this hangup read "0 B" in the downloaded section of the window. It appears that upon checking for updates, no actual data is transferred to my computer. Again, after going through several of the default repo lists, the entire process halts. A wait of approximately ten minutes still reads that the process has not continued.
-During this time I am able to browse the web using Firefox, and the OS seems to be responsive and otherwise functional. There is not a slow response from the keyboard or mouse, there are also no graphics glitches.


Again, this problem first occurred with my previous install of Ubuntu 10.04, which was up-to-date as of approximately midnight last night.
I have reinstalled the OS and the problem persists. The symptoms of this problem are consistent between my previous install and the reinstall. 


Any ideas?

---

### Post by Ewingo401 on 2010-10-01
Mine is doing the same thing this morning.  I'm thinking that one of the repos is having some trouble.

---

### Post by gotsanity on 2010-10-01
yeah Im having the same issue with one of the repos

seems it is us.archive.ubuntu.com 139.239.18.173 that is not responding

---

### Post by Ahava591 on 2010-10-01
Are your repository lists downloading except for the one list which apparently you are both unable to get new information from?

Or is the entire "check," process halting for you as well?

---

### Post by gotsanity on 2010-10-01
> **gotsanity said:**
> yeah Im having the same issue with one of the repos

seems it is us.archive.ubuntu.com 139.239.18.173 that is not responding

switching to the non-us server fixed the issue for me

---

### Post by sikander3786 on 2010-10-01
Did you try changing the update servers from System > Administration > Software Sources?

---

### Post by Ahava591 on 2010-10-01
Here is a screenshot I have taken a minute ago of what is happening.

---

### Post by Ahava591 on 2010-10-01
Navigating to System>Administration>Software Sources, and then staying on the first tab, which is labeled "Ubuntu Software," and then changing the tab option "Download from: " from "Server for United States," to "Main server," has allowed me to find the updates again.


However, when checking for updates from the default repositories the process takes much longer than has been usual. I was formerly able to check for updates in approximately fifteen to thirty seconds. Now it has taken nearly one minute to complete the check of default repositories.

Is this simply because the main server is far away from the U.S.? If not, should I be concerned? 
Also, any word on what has caused the apparent failure of U.S. server(s)?

---

### Post by sikander3786 on 2010-10-01
You should be concerned about speed this moment. Use it 1-2 days and then revert to your local servers.

Don't know why U.S servers went down. There might be a discussion later on in the Community Cafe.

---

### Post by Ahava591 on 2010-10-01
Thank you guys for the help, it means a lot to me.

Although my problem seems to be solved for the moment, I will post more information to this thread as the situation develops.

---

### Post by Ewingo401 on 2010-10-01
Issue seems to be resolved from here.

---

