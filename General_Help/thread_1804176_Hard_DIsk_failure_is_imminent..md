---
title: "Hard DIsk failure is imminent."
date: 2011-07-14
forum: General Help
---

### Post by Asalwayshappy on 2011-07-14
I am using a DEll Inspiron 15r laptop, with 500gb ata wdc-****, i am using ubuntu11.04 only,when i am into my desktop it gives me a window, that hardisk has detected some problem click to examine, when i examine it says hardisk failure is imminent, here is screenshot of smartdata and runselftests

[http://img20.imageshack.us/img20/3924/screenshot1ttg.png](http://img20.imageshack.us/img20/3924/screenshot1ttg.png)

its the second time i am facing this problem, laptop is a month old now still under warranty, but i dont want to give it now, i want to give it for replacement on monday, so i want to temporiraly fix bad sectors so that hardisk succesfully last till monday easily, what can i do to fix it, i am only using ubuntu 11.04.

---

### Post by psusi on 2011-07-14
Back up your data and hope it doesn't die by then.

---

### Post by Asalwayshappy on 2011-07-14
i just got that error today? would my hard disk last upto monday? and what if it dies? would i still be able to get it replaced on warranty?

---

### Post by dino99 on 2011-07-14
run fsck first, then ask for exchange guaranty

[http://manpages.ubuntu.com/manpages/oneiric/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/fsck.8.html)

sudo shutdown -R now  (fsck on next boot)

---

### Post by Asalwayshappy on 2011-07-14
what is the command to run fsck? please post it again, couldnt understand from your post is it
or 
sudo shutdown -R 
sudo shutdown -R now

and do i have to run this command running into my system or boot from a cD?
i dont know what is live cd, is it the cd on which ubuntu iso image is present?

---

### Post by ruffEdgz on 2011-07-14
Lets try this way to force a fsck on next reboot.
--- Need to make a file called 'forcefsck' ---
```

sudo touch /forcefsck

```

--- Reboot the system now ---
```

sudo shutdown -r now

```

After these two commands, this should make your file system complete a fsck on the root partition.

Cheers!

---

### Post by Asalwayshappy on 2011-07-14
can i use those commands normally running a system, or do i have to insert a livecd etc to do?

---

### Post by yungballla6 on 2011-07-14
I have had two dell inspirons. Both of them had hard disk failure. Have no idea why they fail with dells.

---

### Post by Mark Phelps on 2011-07-14
> **Asalwayshappy said:**
> i just got that error today? 
Then, I would use the option in the panel to run the self-test and see what you get.  There were lots of reports in older Ubuntu versions about "false positives" with the hard disk health app. Folks would get that error on brand new drives!  Don't know if that is still the case with 11.04, though.
> would my hard disk last upto monday? 
No one knows.  If the warning is bogus, it could last for YEARS.  On the other hand, it could die in the next five minutes. 
>  and what if it dies? would i still be able to get it replaced on warranty?
That depends on the warranty terms.  Typically, a drive manufacturer will require you to run a utility they provide to produce some failure stats on the drive.

You can head that off by going to the website of the manufacturer of your drive, seeing if they have a drive health utility, downloading and running that.

If THAT still shows serious drive problems, then your drive IS failing -- and the sooner you back off the important stuff, the better.

If THAT does not show drive problems, then it's the old "false positive" problem -- that still has not been fixed (apparently).

---

### Post by psusi on 2011-07-14
There were one or two drives that incorrectly reported millions of bad sectors when there was really only one or two.  In this case, the bad sector count is reasonable, and the overall self health assessment says it is failing, so there is no doubt that the drive is toast.

---

