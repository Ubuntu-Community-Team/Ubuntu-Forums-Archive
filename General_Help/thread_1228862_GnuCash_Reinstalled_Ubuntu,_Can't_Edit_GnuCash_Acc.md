---
title: "GnuCash: Reinstalled Ubuntu, Can't Edit GnuCash Accounts"
date: 2009-08-01
forum: General Help
---

### Post by Steve00 on 2009-08-01
Running Ubuntu 8.10, Gnucash 2.2.6 on a HP Tablet 1100.

I installed Ubuntu after several months of using Wubi. I did backup all of my data to an external hard drive. The backup included my complete Gnucash data folder.  My system now dual boots with WinXP. After reinstalling Gnucash, everything has been working as advertised with the exception of GnuCash. I had several extensive gnucash accounts to track both my and my parents checking accounts. Gnucash had worked fine under Wubi.

Once I had my full version of Ubuntu up and running and satisfied it was stable, I copied my old gnucash data folder back over to my home directory. When I tried to open my checking account folder, the file loaded, but I was unable to enter any new entries and I was unable to view any of my old entries. The only thing showing in any of the accounts (assets, expenses, etc.) when was a blank line showing today's date (8/1/09). The main account page does indicate proper balances. 

I did go into Edit | Edit Account and unchecked 'placeholder'. However, each account still appears to be locked or in read-only mode and I am unable to see any transactions that occurred prior to 8/1/09. Account preferences start and end dates are set relative to the start and end of this year. I also tried different start dates and that had no effect.

I did do a search here as well as a general google search and did not find any obvious answers.

Suggestions on how to get full access to my account?

Also, if this area is not the proper forum, anyone know of a good gnucash help forum that is active? Didn't find much out there in Cyberspace.

Thanks!

--Steve

---

### Post by zacktu on 2009-08-01
I use gnucash 2.2.6 also.  The only difference I can see between what you and I did is that when I reinstalled the os I kept the old /home partition.  There's also a ~/.gnucash directory, but that should be placed there by the installer.  

You might check permissions for your gnucash directory.  Mine are 755.

---

### Post by michy99 on 2009-08-01
Yes, check permissions and also make sure you are the owner of the files.```
ls -lad ~/.gnucash
ls -la ~/.gnucash
```

---

### Post by Steve00 on 2009-08-01
Thanks for help.

I ran permissions with the commands indicated and the output is shown below. I must admit to more than a little bewilderment at this point:confused: any guidance will be greatly appreciated.

d7r@d7r-laptop:~$ ls -lad ~/.gnucash
drwx------ 4 d7r d7r 4096 2009-08-01 09:41 /home/d7r/.gnucash
d7r@d7r-laptop:~$ ls -la ~/.gnucash
total 40
drwx------  4 d7r d7r  4096 2009-08-01 09:41 .
drwxr-xr-x 75 d7r d7r  4096 2009-08-01 10:31 ..
-rw-r--r--  1 d7r d7r 17945 2009-08-01 09:41 accelerator-map
drwx------  2 d7r d7r  4096 2009-08-01 09:41 books
drwx------  2 d7r d7r  4096 2009-08-01 09:36 checks
-rw-r--r--  1 d7r d7r     0 2009-08-01 09:41 expressions-2.0
-rw-r--r--  1 d7r d7r   871 2009-08-01 09:41 stylesheets-2.0

--Steve

---

### Post by HermanAB on 2009-08-01
It sounds like a permissions problem.  When you re-installed, the IDs assinged to the users may be different from what they used to be.  The way to fix it is with a recursive chown:

$ sudo -R yourusername:yourusername /wherever/the/fsck/gnucash/data/is

That will reset all the old user and group IDs to the new user and group IDs and the problems should go away.

Hope that helps!

---

### Post by michy99 on 2009-08-01
The ownership looks ok, but the permissions are different from what I have on mine. See if this fixes it:```
chmod 755 -R ~/.gnucash
```

---

### Post by Steve00 on 2009-08-01
Thank you for your assistance. Running the following command:

d7r@d7r-laptop:~$ sudo -R d7r:d7r /home/d7r/GnuCash

resulted in the following response:

sudo: illegal option `-R'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

---

### Post by michy99 on 2009-08-01
I think what HermanAB meant was```
sudo chown -R yourusername:yourusername ~/.gnucash
``` but I think you already own the files anyway. Have you tried the command I gave above?

---

### Post by Steve00 on 2009-08-01
> **michy99 said:**
> The ownership looks ok, but the permissions are different from what I have on mine. See if this fixes it:```
chmod 755 -R ~/.gnucash
```

Thanks, but this had no effect.

---

### Post by michy99 on 2009-08-01
I noticed in one of the command you put /home/d7r/GnuCash. Do you have a folder named GnuCash in your home directory? Is this something that was created by the program or something you put there yourself?

---

### Post by Steve00 on 2009-08-01
To summarize, I tried in order the following with no effect:

sudo -R d7r:d7r /home/d7r/GnuCash

chmod 755 -R ~/.gnucash

sudo chown -R d7r:d7r ~/.gnucash

Thanks!

--Steve

---

### Post by Steve00 on 2009-08-01
> **michy99 said:**
> I noticed in one of the command you put /home/d7r/GnuCash. Do you have a folder named GnuCash in your home directory? Is this something that was created by the program or something you put there yourself?


That is the subdirectory in which I keep by GnuCash data, it is under my home directory. Now that you ask this, when I decided to transition from WUBI to a full Ubuntu install, I manually backed up all of my data. I do not recall if this was a folder I created in order to move the GnuCash data or if it was created by GnuCash when I first set up the accounts.

---

### Post by michy99 on 2009-08-01
> **Steve00 said:**
> That is the subdirectory in which I keep by GnuCash data, it is under my home directory. Now that you ask this, when I decided to transition from WUBI to a full Ubuntu install, I manually backed up all of my data. I do not recall if this was a folder I created in order to move the GnuCash data or if it was created by GnuCash when I first set up the accounts.
Okay, I get it now. Let's see this then:```
ls -ld ~/GnuCash
ls -l ~/GnuCash
```

---

### Post by Steve00 on 2009-08-01
> **michy99 said:**
> Okay, I get it now. Let's see this then:```
ls -ld ~/GnuCash
ls -l ~/GnuCash
```

d7r@d7r-laptop:~$ ls -ld ~/GnuCash
drwxrwxrwx 7 d7r d7r 4096 2009-08-01 13:22 /home/d7r/GnuCash
d7r@d7r-laptop:~$ ls -l ~/GnuCash
total 408
drwxrwxrwx 3 d7r d7r   4096 2009-08-01 13:22 Dad
drwxrwxrwx 3 d7r d7r   4096 2009-08-01 13:39 Mom
drwxrwxrwx 2 d7r d7r   4096 2009-08-01 09:35 Mine

Thanks!

---

### Post by michy99 on 2009-08-01
That all looks as it should. Have you had a look at this page?

[http://www.gnucash.org/docs/v1.8/C/gnucash-guide/basics_backup1.html](http://www.gnucash.org/docs/v1.8/C/gnucash-guide/basics_backup1.html)

---

### Post by Steve00 on 2009-08-01
> **michy99 said:**
> That all looks as it should. Have you had a look at this page?

[http://www.gnucash.org/docs/v1.8/C/gnucash-guide/basics_backup1.html](http://www.gnucash.org/docs/v1.8/C/gnucash-guide/basics_backup1.html)

Yes, tried both the .xac and the .log files. Same problem: "This account register is read only" with the further instruction to uncheck the placeholder. Once unchecked, still can't edit or add to the register.

---

### Post by Steve00 on 2009-08-01
Thanks to all for your very prompt and detailed assistance. The problem was, not surprisingly, a nut loose on my keyboard :redface: Otherwise known as "operator error". 

I was trying to open the wrong accounts. Instead of going thru the default account for the checkbook register, I was dropping into the expense and income accounts and trying to edit there.

Sorry to have wasted your time, but I do appreciate the prompt and willing help y'all provided.

--Steve

---

### Post by mike555 on 2009-08-01
you might install " nautilus-gksu " then you should be able to rt. click on the folder and open as admin.

---

### Post by michy99 on 2009-08-01
I have to admit I'm running out of ideas, but let's look at this:```
ls -la ~/GnuCash/Dad
ls -la ~/GnuCash/Mom
ls -la ~/GnuCash/Mine
```

---

