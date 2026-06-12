---
title: "Problem with wubi Ubuntu 10.10"
date: 2010-12-18
forum: General Help
---

### Post by jimmys_ on 2010-12-18
Hi

I recently installed Ubuntu 10.10 inside Windows with wubi. A few days ago all of a sudden I wasn't able to boot Ubuntu. I tried booting both kernels with recovery modes too but nothing. Now I tried to uninstall wubi since I couldn't find a solution and I got the following message "Permission denied removing C:\ubuntu\disks\root.disk". What is going on? Any help?

Thanks

---

### Post by sikander3786 on 2010-12-18
Are you able to boot Windows successfully? Depending on this query, either problem # 1 or problem # 2 from following thread would apply.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

And once fixed, don't forget to apply the 'Permanent Fix' from that page to avoid future troubles ;-)

---

### Post by Rubi1200 on 2010-12-18
Just to add to the great advice posted by sikander3786, if you are unsure of the current state of your setup then post the results of the boot info script mentioned in the section on things you may need for troubleshooting.

---

### Post by jimmys_ on 2010-12-18
Yes I can boot Windows normally. I'll give a look at the thread. Thanks.

@Rubi1200 I haven't understand where I can find that boot info screen. If you mean the boot screen I see when I try to boot Ubuntu, it gives hundreds of error (or info) lines

My bad.. I just understood what you are talking about.. Thanks

---

### Post by theozzlives on 2010-12-18
It's a Boot Info Script! The Link is in Ruby1200's signature.

---

### Post by jimmys_ on 2010-12-18
My problem seems to be problem#2 but the solutions are for cases which there was un upgrade to 10.10. In my case, it was a clean install of 10.10.

Is there a way I can just uninstall it to get over with it?

---

### Post by theozzlives on 2010-12-18
> **jimmys_ said:**
> My problem seems to be problem#2 but the solutions are for cases which there was un upgrade to 10.10. In my case, it was a clean install of 10.10.

Is there a way I can just uninstall it to get over with it?

What Windows you using? If Vista or 7, you may have to be Administrator.

---

### Post by Rubi1200 on 2010-12-18
I would post the results of the script anyway so we can make sure what is going on before moving ahead with solutions.

To uninstall, if you are sure that is what you want to do, see here:
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by theasprint on 2010-12-18
I was just wondering if this would work.

Boot Windows and run your command prompt as administrator.

Then follow the steps in this link:

[http://www.tech-recipes.com/rx/2947/windows_uninstall_application_command_line/]("http://www.tech-recipes.com/rx/2947/windows_uninstall_application_command_line/")

and uninstall Ubuntu.

Good luck! :D

---

### Post by jimmys_ on 2010-12-18
> **theozzlives said:**
> What Windows you using? If Vista or 7, you may have to be Administrator.

Win 7 64bit.. I already tried to run the uninstall program as administrator but I got the same problem

---

### Post by jimmys_ on 2010-12-18
Ok something goes really wrong.. I tried to boot my computer with two different version Ubuntu Live CDs (to run the script) but I wasn't able to boot it with either. When I restarted my PC I noticed that the boot screen where there was the option for Ubuntu 10.10 is now gone and it boots automatically into Windows.

Another weird thing, now it uninstalls..

Thanks everyone for your help

---

### Post by Rubi1200 on 2010-12-18
If the problem is resolved, please mark this thread solved.

Thread Tools > Mark as Solved

Thanks.

---

