---
title: "Wubi 10.10 will not install"
date: 2011-03-01
forum: General Help
---

### Post by Amber2011 on 2011-03-01
Hello,
I just reinstalled XP and now I am trying to reinstall Wubi. I want to  use Ubuntu as my main operating system. I had it  on this PC already but  now can't get it back.  I am trying to install 10.10 version, the one I used to have.
Every time I get this message.

windows - No disk

Exception Processing Message

c0000013  Parameters - 75b6bf7c   4   75b6bf7c   75b6bf7c


I tried it many times with and without anti virus and firewall. Nothing   is working. In fact now all I have on my PC is avast and a firewall.  Please help I can't stand XP any more. Thanks in advance


Maybe I should post in the Installation area instead. Thanks

---

### Post by bcbc on 2011-03-01
If you intend to use Ubuntu more than windows, why not do a proper dual boot install?

That message is likely because you have a cellphone, ipod, or some other sort of device that wubi/python doesn't like. Unplug them and it should work.

---

### Post by temman on 2011-03-02
Hi Amber2011,
                       I had  the same problem with xp at one stage the problem was by default windows installs with some hidden folders you need to unhide such folders so the installation of ubuntu can find them.
                       What you need to do is go to C/drive folders section and click on tools tab at the top of your screen,click on  Folder Options hit View tab scroll down and activate "Show hidden files and folders" and apply. Try your installation again!
                       I also run Avast and firewall had no problem with neither of them.Hope I have been of some help to you.

---

### Post by Amber2011 on 2011-03-02
bcbc,
I am not ready yet to get rid of windows completely. I am new to Ubuntu, just tried it for about a week. My computer was not running well prior to that so I thought I would get a fresh start with a XP reinstall, then put Ubuntu back in and get serious with it. 


Temman,
I tried that but it is not working. The first time I had Ubuntu it installed fine. I can't imagine the problem now. I updated drivers and that still did not work. I have been working on it for a day and a half now, I am sooo mad.

Thanks I appreciate the help.

---

### Post by bcbc on 2011-03-02
This describes the problem you are having:
[https://bugs.launchpad.net/wubi/+bug/346521](https://bugs.launchpad.net/wubi/+bug/346521)
[http://sylefeb.blogspot.com/2009/07/linux-wubi-and-no-disk-issue.html](http://sylefeb.blogspot.com/2009/07/linux-wubi-and-no-disk-issue.html)

What I meant was - Wubi is great to try out Ubuntu without worrying about partitioning. But if you intend to use is predominantly then you can also install - still as a dual boot with windows - but to a separate partition. This is more stable than wubi although it is more complicated to install.

But if you choose to install Wubi I have no issue with that. Just wanted to make it clear that there is another option.

Just be careful if you do decide to do a traditional dual boot install with 10.10 - it's installer has been known to 'trick' users to wipe windows. Select "install alongside" and then avoid clicking "use whole disk" or "use whole partition" after that: [http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by Amber2011 on 2011-03-02
I have a live cd, 10.4 version. I am just afraid of messing with a partition. But I will do it one way or another. I don't know why computers have to be so annoying, I am ready to throw this one out the window. I think I just need a break, I can't think anymore.
Thanks

---

### Post by Rubi1200 on 2011-03-02
Here is what I recommend:

For a dual-boot install, see the following links:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

Before you start, however, I suggest you do the following:

1. post the specifications for the computer

2. download the Ubuntu iso: [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

3. check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

4. burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

5. try as a LiveCD first to see that everything works as it should (don't forget to set BIOS to boot from the CD drive first)

6. from the LiveCD, go to Applications > Accessories > Terminal and post the output of the following command so we can check the state of your drive to make sure there is enough space etc. to do what you want

```
 sudo parted -l
```

(lowercase L not 1)

7. backup all important data

8. install

With all this done, you should be ready for a safe and happy dual-booting experience.

If you have any questions, feel free to ask.

---

### Post by Amber2011 on 2011-03-02
Rubil 200 and everyone,

I really appreciate all your help. I guess I will do it from the live CD I burned about a year ago. I makes me mad though not being able to figure out the Wubi thing. 

bcbc,
I went to those web sites and I guess the way it is worded is too advanced for me. I got as far as putting USBDLM on my cdrive and lost it after that. After that a new Wubi icon was on my desktop and I was feeling good, but as I said I could not understand it after that. 

Again thanks, take care

---

### Post by bcbc on 2011-03-02
> **Amber2011 said:**
> Rubil 200 and everyone,

I really appreciate all your help. I guess I will do it from the live CD I burned about a year ago. I makes me mad though not being able to figure out the Wubi thing. 

bcbc,
I went to those web sites and I guess the way it is worded is too advanced for me. I got as far as putting USBDLM on my cdrive and lost it after that. After that a new Wubi icon was on my desktop and I was feeling good, but as I said I could not understand it after that. 

Again thanks, take care

Sorry I didn't intend for you to install that program. Just try and disable those drives (look in the notification area of your taskbar and see if there is a 'removable devices' icon - left click on it and 'safely remove the drives').

---

### Post by Amber2011 on 2011-03-02
bcbc,
You do not need to apologize, you guys really helped me out.

Guess where I am now? Inside of Ubuntu. I installed it from a live CD, man was I scared. When it first shut down after it installed I got a whole page of errors,then when it started back up I got a black page. Seems to be alright now, though it would not let me install updates, I used my password and all but it is not recognizing me. I will work the bugs out!

You guys gave me the nerve to do this.....many thanks.:p:p:p

---

### Post by temman on 2011-03-09
[SIZE=2]Hi Amber2011,
                   I have had that problem where it would not let me install updates,this is how I got around it.

Open Terminal and copy and paste the following Code:

sudo apt-get clean ; sudo apt-get update && sudo apt-get upgrade

See how you go!
                                    Regards temman

[/SIZE]

---

