---
title: "Help me,please"
date: 2010-10-09
forum: General Help
---

### Post by ujjal on 2010-10-09
Hi everyone,This is my first post here.I was a xp user.Recently I have diverted to Ubuntu 10.04LTS.When I have upgrades all packages,I was asked  to restart system.I did the same.But After pressing restart button,there is something like....

```

Boot from cd
No such device found.......
grub rescue>

```

Now I can not run my PC.There is XP on C drive,and Ubuntu in D drive installed in my harddisks.Now what should I do now.......
Thanks in advance........

---

### Post by 0N3 on 2010-10-09
Is your PC setup in the bios to boot from CD or HDD?

---

### Post by 0N3 on 2010-10-09
What exactly is your problem?

---

### Post by Rubi1200 on 2010-10-09
I am going to assume that this is a Wubi install.

The fix depends on the symptoms.

The 2 possibilities are:

[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

and

> **[COLOR=DarkRed][SIZE=3]Important Note to Wubi (Windows Ubuntu) Users: Grub Update results in "No Such Disk":[/SIZE][/COLOR] **
A late July 2010 Grub 2 update is causing a "**[COLOR=DarkRed]no such disk[/COLOR]**"  error for some users of WUBI, resulting in an unbootable system. If the  system doesn't display the original Windows menu, the most likely cause  of the failure is that Grub 2 was installed in the MBR and/or on the  Windows partition. To correct this, restore the Windows bootloader using  this link:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

Whether the failure is due to improper user selections or Grub 2's  failure to recognize a Wubi install, it has been reported in the  following bug and users can review it for status updates and recovery  options when they become available:
[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

Also see here:
[http://ubuntuforums.org/showpost.php?p=9932481&postcount=7](http://ubuntuforums.org/showpost.php?p=9932481&postcount=7)

---

### Post by ujjal on 2010-10-09
Yes,my PC setup in the bios to boot from CD or HDD.
```

grub rescue>

```

when I am trying to start PC,a boot window is appeared and wants a command for grub resque.PC is not running.

---

### Post by ujjal on 2010-10-09
Please help me,that what will be the command for "grub rescue"?
My PC is not running.I tried writin "help" or "tab".it shows..
```

grub rescue>help
unknown command "help"
grub rescue>

```


what should I write now to startup my PC.

---

### Post by sendblink23 on 2010-10-09
Can you try the comment posted by garvinrick4: [http://ubuntuforums.org/showthread.php?t=1591300](http://ubuntuforums.org/showthread.php?t=1591300)

maybe that could help... you will need to boot from the LiveCD

---

### Post by Rubi1200 on 2010-10-09
If you installed Ubuntu via Wubi then attempting to reinstall GRUB will amount to...nothing!

Please read the information in the links I posted.

If you get a GRUB rescue prompt after installing Ubuntu via Wubi or after an upgrade and are unable to boot either Ubuntu or Windows, fix it by reinstalling the Windows bootloader.

If you can boot Windows, but get a blank screen or the computer restarts when attempting to boot Ubuntu, then use the other fix I linked to.

---

### Post by ujjal on 2010-10-09
[@sendblink23]("http://ubuntu-virginia.ubuntuforums.org/member.php?u=639398"),
I have seen that page.And reinstalled as the commands are given there.
After executing 
```

sudo shutdown r

```

PC is restarted and now there is a command list and it is requiring A command for GRUB.

```

GRUB>


```

typing help,there appeared a commandlist.Which command I must type to run my pc.

[Now I am using ubuntu[keeping no change] 

Please help.

---

### Post by Rubi1200 on 2010-10-09
Can you please answer the question of whether you installed Ubuntu on the hard-drive or **within** Windows using Wubi?

_Your answer_ will determine the kind of help we can offer.

If you used Wubi, see what I posted above.

If not, then use the LiveCD and post the results of the boot-script which you can find linked at the bottom of my post.

Thanks in advance.

---

### Post by ujjal on 2010-10-09
Please read this.....
I am going to tell you clearly..

1.I was a xp user.(xp is installed on C drive)
2.Then I installed UBUNTU on D drive(not booting,using wubi.exe)
3.I used ubuntu about 2 days.
4.Then I upgrade all packges.when completing it,there was a question whether I want to install grub.I pressed "NO".
5.After completing upgrading,pc restarted.
5.Now here is the problem.It requiring GRUB command.

```

GRUB>

```

PC is stable here.If I press enter,it does the same.So ,I can't PC to run.
Please tell me specifically,what should I do now.
Thanks in advance..

---

### Post by Rubi1200 on 2010-10-09
Thanks for the explanation. If you had read my previous posts, you would know that I already gave you the solution.

If you are unable to boot (get in) to Windows XP OR Ubuntu (which you installed using Wubi), then you need to restore the Windows XP bootloader.

This link will explain how to do this:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Playing around with the commands at the GRUB prompt you see will not help you in this situation.

If you do not have the Windows XP installation CD, then tell us and we can offer another solution to get Windows working again (and hopefully the Wubi install as well).

---

### Post by ujjal on 2010-10-09
Finally I got it.Now I have to install Xp again and.then I will install UBUNTU again.Ok then.

Thanks for your help.

---

### Post by Rubi1200 on 2010-10-09
> **ujjal said:**
> Finally I got it.Now I have to install Xp again and.then I will install UBUNTU again.Ok then.

Thanks for your help.
NO!!!!

You need to reinstall the Windows bootloader. Just as Ubuntu uses a bootloader called GRUB, Windows also has one.

Did you read the information in the link I provided?

You need to use the information in the section that starts with:

> [SIZE=5][COLOR=red]How to restore the Windows XP bootloader[/COLOR][/SIZE]

Once you do this, you will be able to use Windows again and should also be able to use Ubuntu. 

If not, then we can help you get Ubuntu sorted out.

There is no need, I repeat, no need to install the whole operating system again to make things work.

I hope this is just a language misunderstanding, but please tell me if anything was not clear to you. I am more than happy to explain and answer any questions you have.

---

### Post by ujjal on 2010-10-09
@Rubi1200,


Off ****,I have set up whole operating system.It means I didnt understand your words.Sorry for that.I gonna read the document you advised.But here is one problem .In ubuntu software center,there is no option to "install" now.I reset all.But why is this problem?I am sorry to disturbing too much.Please explain what you know.....

---

### Post by Rubi1200 on 2010-10-09
> **ujjal said:**
> @Rubi1200,


Off ****,I have set up whole operating system.It means I didnt understand your words.Sorry for that.I gonna read the document you advised.But here is one problem .In ubuntu software center,there is no option to "install" now.I reset all.But why is this problem?I am sorry to disturbing too much.Please explain what you know.....
I do not understand what you mean; sorry.

If you use the Ubuntu Software Center, installing software is very easy. Just click "Install" and wait for things to finish. I don't know what you mean by resetting something?

But, I understood you cannot boot into Windows or Ubuntu? Did I miss something?

If you don't mind me asking; what is your native language?

---

### Post by ujjal on 2010-10-09
This is my fault,I am sorry for that.
My native language is Bangla But I know English.I am student of B.S.C Engineering studing Computer Science & Engineering.
You have no lack.It was of mine.
I missed something.
Let's see again.

```

If you are unable to boot (get in) to Windows XP OR Ubuntu (which you  installed using Wubi), then you need to restore the Windows XP  bootloader.

```
It was not clear to me.So,I reinstalled XP and then UBUNTU using wubi.Now,pc is running.After doing such,I am facing a new problem.

<UBUNTU SOFTWARE CENTER>
You have seen that,from developer tool we can install software directly using INTERNET.
But,there is no "install" button in softwares....

If I am not clear,then please let me know.And help me,how could I install softwares...

---

### Post by Rubi1200 on 2010-10-09
> **ujjal said:**
> This is my fault,I am sorry for that.
My native language is Bangla But I know English.I am student of B.S.C Engineering studing Computer Science & Engineering.
You have no lack.It was of mine.
I missed something.
Let's see again.

```

If you are unable to boot (get in) to Windows XP OR Ubuntu (which you  installed using Wubi), then you need to restore the Windows XP  bootloader.

```It was not clear to me.So,I reinstalled XP and then UBUNTU using wubi.Now,pc is running.After doing such,I am facing a new problem.

<UBUNTU SOFTWARE CENTER>
You have seen that,from developer tool we can install software directly using INTERNET.
But,there is no "install" button in softwares....

If I am not clear,then please let me know.And help me,how could I install softwares...
First of all, no need to apologize. I am really glad that Windows and Ubuntu (via Wubi) is working again for you :)

To the next question: I don't use the Wubi version of Ubuntu, but if I remember correctly some software is not available for installation immediately after a new install because the system needs to update itself first. Is this for all software you want to install or only some things?

Also, if this does not help, then the next time you want to try and install something take a screenshot and post it here so someone can try and help.

I wish you the best of luck with your studies and using Ubuntu!

---

### Post by ujjal on 2010-10-09
OH brother,It is okay now."install" button is visible now.Actually you said,is right.It takes time after installing.I have just learnt from net that,I can't run more than one at same time.It was upgrading media player,when I amtrying developer tool.This was the problem.

Thanks a lot for your kind help.Would you mind remaining contact with me?Actually I am very much interested about ubuntu.So,Can I disturbe you?

---

### Post by Rubi1200 on 2010-10-09
You are more than welcome ujjal :)

Please mark this thread Solved using the Thread Tools near the top of the page.

Anytime you need to ask questions, come to the forum and post here. There will always be someone willing to take the time to try and help. This is one of the fantastic things about this community.

I will keep an eye open for your posts in the future and try to help when I can.

---

### Post by ujjal on 2010-10-09
Hey brother,thanks a lot.I am going to mark it solved.And I will visit this forum regularly.
Again thanks to you for the receiption.........
See you again........

---

