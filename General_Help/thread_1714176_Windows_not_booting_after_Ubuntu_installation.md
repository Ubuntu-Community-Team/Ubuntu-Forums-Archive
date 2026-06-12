---
title: "Windows not booting after Ubuntu installation"
date: 2011-03-25
forum: General Help
---

### Post by sivakumarj on 2011-03-25
Hi,

I'm new to Ubuntu, yesterday i installed Ubuntu 10 and the installation was successful. When I rebooted my system to access my other OS which is Windows 7  from the drop down menu (see the attachment) available on the boot screen i'm unable to go to Windows 7 and it restarts again, goes to the same menu where i have to choose the OS. Even after several trials i'm still unsuccessful to boot my windows. 

Please help. 

regards
Siva

---

### Post by spirit.986 on 2011-03-25
There is very little info about your problem in your question :(

Did you followed any guide or tutorial about dual booting win and ubuntu or you have just installed ubuntu on top of the windows by yourself folowing the default setings?

If you were installing from an online guide please can you post the link from the tutorial in order to determine the steps which you were using during the install..

---

### Post by Rubi1200 on 2011-03-25
I cannot see what it says for the entry which is highlighted in the screenshot.

Try booting from the next entry (on sda1) and see if that works.

If not, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by zaminur143 on 2011-03-25
Well I was facing a similar type of problem, but now I know the solution of it and I have solved my problem a few moments ago. Thanks buddy.

---

### Post by Script Warlock on 2011-03-25
@zaminur143, would you care to share your solution so others that has a similar problem can benefit too...

---

### Post by sivakumarj on 2011-06-29
zaminur143 could you please share with us the solution.

---

### Post by sivakumarj on 2011-06-29
Dear All,
  I am sending the issues that I have been facing using Ubuntu especially for Windows to boot.


  I installed Ubuntu 10 and the installation was successful. When I rebooted my system to access my other OS which is Windows 7 from the drop down menu (see the attachment Ubu 1) available on the boot screen i'm unable to go to Windows 7 and it restarts again, goes to the same menu where I have to choose the OS. Even after several trials i'm still unsuccessful to boot my windows. 



  But when I insert the Ubuntu live CD and reboot and when my system restarts I keep pressing the down arrow key and I reach the screen (see the attachment Ubu4) then I press the esc key and it take me to another screen (see the attachment Ubu5) then I choose the last option “boot from first hard disk” it take me to a another screen (see the attachment Ubu6) which is very much similar to the first boot screen (ubu1) but this time when I choose the last option from the Ubu6.JPG screen which is “windows 7 loader on /dev/sda1 it take me to another screen (see the attachment Ubu7). Ubu7.JPG has two options Windows and Ubuntu, when I choose Windows it loads Windows and takes me to Windows login screen.


  Also attached the edit command screen Ubu2.JPG and Ubu3.JPG. 
  Please help me in getting out of this issue.


  Cheers
  Siva

---

### Post by sivakumarj on 2011-06-29
Sending the other two attachments.

> **sivakumarj said:**
> Dear All,
  I am sending the issues that I have been facing using Ubuntu especially for Windows to boot.


  I installed Ubuntu 10 and the installation was successful. When I rebooted my system to access my other OS which is Windows 7 from the drop down menu (see the attachment Ubu 1) available on the boot screen i'm unable to go to Windows 7 and it restarts again, goes to the same menu where I have to choose the OS. Even after several trials i'm still unsuccessful to boot my windows. 



  But when I insert the Ubuntu live CD and reboot and when my system restarts I keep pressing the down arrow key and I reach the screen (see the attachment Ubu4) then I press the esc key and it take me to another screen (see the attachment Ubu5) then I choose the last option “boot from first hard disk” it take me to a another screen (see the attachment Ubu6) which is very much similar to the first boot screen (ubu1) but this time when I choose the last option from the Ubu6.JPG screen which is “windows 7 loader on /dev/sda1 it take me to another screen (see the attachment Ubu7). Ubu7.JPG has two options Windows and Ubuntu, when I choose Windows it loads Windows and takes me to Windows login screen.


  Also attached the edit command screen Ubu2.JPG and Ubu3.JPG. 
  Please help me in getting out of this issue.


  Cheers
  Siva

---

