---
title: "Ubuntu Not Showing Up On Boot Menu. Can't Uninstall Either."
date: 2011-06-22
forum: General Help
---

### Post by No0bzZ on 2011-06-22
Hello. 

I was messing with my msconfig trying to free up some memory then I realize when I restarted my PC it just boot directly to Windows 7 without prompting anything, although it should because of Ubuntu.

Then, I tried uninstalling Ubuntu and installing it again (hoping to fix the problem). *It's alright for me to just reinstall Ubuntu anytime, I was just exploring it.* This error pop up when uninstalling Ubuntu
```
An error occurred:

Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete
[730c4202-f42c-11df-b452-d3bb323c0ea9]/f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.
The system cannot find the file specified.

>>stdout=

For more information, please see the log file:
c:\users\ej\appdata\local\temp\wubi-11.04-rev211.log
```

I searched the "file that was not specified" and it was there!!!


So, I can't boot to Ubuntu and I can't uninstall it either. What should I do?

[COLOR="Red"]HELP!!!!![/COLOR]

---

### Post by FormatSeize on 2011-06-22
> **No0bzZ said:**
> So, I can't boot to Ubuntu and I can't uninstall it either. What should I do?
 
[COLOR=red]HELP!!!!![/COLOR]
You can always uninstall something. 
 
If you want to uninstall it, first get [Hiren's Boot CD]("http://www.hirensbootcd.org/download/"). Boot from the CD. A very drab looking menu will be presented to you. Select "DOS Programs" and then select "Partitioning Tools" from the next drab menu you are presented with. Then go to GParted, and you will be presented with a GUI which allows you to alter your partitioning of the hard disk.
 
Delete the partition that Ubuntu lives on. Delete the Linux swap space created as well.
 
Now if you don't want to uninstall Ubuntu, or would like to do something else, then wait around for someone with more knowledge on how to fix boot problems. I'm not that knowledgeable in that area (I'm still trying to get Fedora to recognize other Linux systems at boot time).

---

### Post by No0bzZ on 2011-06-22
> **FormatSeize said:**
> You can always uninstall something. 
 
If you want to uninstall it, first get [Hiren's Boot CD]("http://www.hirensbootcd.org/download/"). Boot from the CD. A very drab looking menu will be presented to you. Select "DOS Programs" and then select "Partitioning Tools" from the next drab menu you are presented with. Then go to GParted, and you will be presented with a GUI which allows you to alter your partitioning of the hard disk.
 
Delete the partition that Ubuntu lives on. Delete the Linux swap space created as well.
I dont think that I can do that :(

---

### Post by ptminh20 on 2011-06-22
oh men, u should be composed. in my opinon, your GRUB was broken down. 
i think u can use a live CD try to fix grub before reinstall ubuntu.
this is tutorial that help you restore ur grub:
[http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/](http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/)
  whatever, u can use an hirrent CD or another bood CD to try to DEL partion that you installed ubuntu OS.

---

### Post by ptminh20 on 2011-06-22
> **No0bzZ said:**
> I dont think that I can do that :(

oh men, you can search on google with key: "how to use....", " how to restore ....", etc
try to get it before giving up men ..
good luck

---

### Post by No0bzZ on 2011-06-22
What I meant by *"I dont think I can do that"* is I cant do it because I dont have a CD. I installed Ubuntu using Wubi.

---

### Post by Mark Phelps on 2011-06-22
> **No0bzZ said:**
> ... I installed Ubuntu using Wubi.

Which SHOULD have been obvious by your references to BCD -- a point easily missed in THESE forums.

Since this is basically an MS Windows question, the solution you need is to clean out the post-install stuff that was left behind when the Wubi uninstall failed.

My suggestion is that you go to sevenforums.com (a Windows 7 forum) and ask the folks there about recommending Uninstaller apps.  There may be something you can download for free that will then clean out the stuff from the Windows registry.

---

### Post by No0bzZ on 2011-06-22
> **Mark Phelps said:**
> Which SHOULD have been obvious by your references to BCD -- a point easily missed in THESE forums.

Since this is basically an MS Windows question, the solution you need is to clean out the post-install stuff that was left behind when the Wubi uninstall failed.

My suggestion is that you go to sevenforums.com (a Windows 7 forum) and ask the folks there about recommending Uninstaller apps.  There may be something you can download for free that will then clean out the stuff from the Windows registry.

I was intrigued on what you said Uninstaller apps so I downloaded (and installed) one from Download.com. Which is Revo Uninstaller.

I used it to Ubuntu. Unfortunately, it still uses the (default) built-in uninstaller and prompted me with the same error I was initially getting. But somehow, it manage to uninstall Ubuntu.

Now, I'm going to install Ubuntu again (using Wubi). I hope it really did fixed my problems.

Thank you!!!

---

### Post by No0bzZ on 2011-06-22
I have successfully reinstalled Ubuntu!!!! Im currently using it!!! Thank you all for your help, I should be fine from here (for now)

---

