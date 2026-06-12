---
title: "Uninstall Shiretoko? (firefox Build)"
date: 2009-07-08
forum: General Help
---

### Post by risknothin on 2009-07-08
I have shiretoko - which is listed as minefield 3.5 still installed

I have upgraded to the final version of Firefox 3.5

how to i uninstall shiretoko without messing up the final build of firefox?

Thanks!

---

### Post by t4thfavor on 2009-07-08
I built it from source, and couldn't get it to uninstall. I just looked at the output from which firefox. and then deleted it. Make sure your getting the right one. I believe the 3.5 one will be called firefox-3.5 while the other will be called just firefox.

---

### Post by lovinglinux on 2009-07-08
> **risknothin said:**
> I have shiretoko - which is listed as minefield 3.5 still installed

I have upgraded to the final version of Firefox 3.5

how to i uninstall shiretoko without messing up the final build of firefox?

Thanks!

That depends on how you installed MInefield in the first place and how you installed the version you want to keep. Did you installed them from the repositories? If yes, then run this:

```
sudo apt-get remove firefox-3.1
sudo apt-get remove firefox-3.2
sudo apt-get remove firefox-3.6
```

Don't follow the instructions below if you didn't compile it.

> **t4thfavor said:**
> I built it from source, and couldn't get it to uninstall. I just looked at the output from which firefox. and then deleted it. Make sure your getting the right one. I believe the 3.5 one will be called firefox-3.5 while the other will be called just firefox.

Check the "Manual Installation & Removal" item from de "Compiling Firefox" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). It has the list of files and folders you need to remove after compiling it. BTW, you should try compiling it with those instructions. It works great for me and boost Firefox performance by 30%.

---

### Post by risknothin on 2009-07-09
i used - sudo apt-get remove firefox-3.5 - it worked

i was worried it would remove the wrong one.


Thanks!

---

### Post by lovinglinux on 2009-07-09
> **risknothin said:**
> i used - sudo apt-get remove firefox-3.5 - it worked

i was worried it would remove the wrong one.


Thanks!

Since you removed firefox-3.5, I'm wondering which method did you used to install the version that it is still on your system?

---

### Post by risknothin on 2009-07-09
i cant remember, i used help off a website.

but 3.5 final is still installed.

---

### Post by ssdt on 2009-07-10
Thanks for the information. I had done the same and installed 3.5 and uninstalled it right now with your method.

---

### Post by FeTTo on 2009-10-22
> **lovinglinux said:**
> That depends on how you installed MInefield in the first place and how you installed the version you want to keep. Did you installed them from the repositories? If yes, then run this:

```
sudo apt-get remove firefox-3.1
sudo apt-get remove firefox-3.2
sudo apt-get remove firefox-3.6
```Don't follow the instructions below if you didn't compile it.



Check the "Manual Installation & Removal" item from de "Compiling Firefox" section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567"). It has the list of files and folders you need to remove after compiling it. BTW, you should try compiling it with those instructions. It works great for me and boost Firefox performance by 30%.

This process did not work for me.  get the error message "E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

i had 3.1 and a friend had me upgrade to Shiretoko to get quakelive working. Then i upgraded to firefox 3.5 because shiretoko was out of date build. I just got an update message from ubuntu so i updated my system, restarted my machiine and now my firefox icons all appear as a big black square and all i have left is shiretoko...any idea wtf is going on here? i will be upgrading to 9.10 tomorrow when the final release goes live..maybe that will fix things.

---

### Post by lovinglinux on 2009-10-22
> **FeTTo said:**
> This process did not work for me.  get the error message "E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

Close Synaptic or any other package manager before running the command. That error message usually happens to avoid running two package managers at the same time.

---

