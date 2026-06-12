---
title: "Booted from flash drive, data lost"
date: 2011-11-24
forum: General Help
---

### Post by gregoryclark on 2011-11-24
Help! I was trying out ubuntu using the boot from a flash drive method and all of the files, data and program files on my XP desktop disappeared. I ran an undelete program and nothing that went missing showed up in the search. Any help any of you can provide me would be greatly appreciated.
Greg

---

### Post by MrSpike16 on 2011-11-24
In XP, the user's desktop files are located in a "Desktop" folder.  Hopefully all you did was accidentally drag this folder into another while trying out Ubuntu's file manager.

For example: If Greg is the username then the Desktop files are located in: C:\Documents and Settings\Greg\Desktop 

If you weren't in your XP partition while trying Ubuntu,  then I can't think of anything that you could have done in Ubuntu to cause the XP problem.

---

### Post by gregoryclark on 2011-11-24
MrSpike, thanks for the response. I've checked all folders and nothing still shows up. Here is what I did before the folders and files on my desktop disappeared:
Downloaded, unzipped and saved to my flash drive
I changed my order of the start up to the flash drive first
I rebooted and just played around in ubuntu
      I was able to open some of my documents from my hard drive (I use OOo 3.3)
I shut down using the shutdown menu item in ubuntu
I removed the flash drive
I rebooted, signed in, and all file folders and files (including a program installed in the hard drive but not in the windows installer). Also all the back up files for the program were gone. The other things that were gone were documents on the desktop.

It sure looks like something happened in the trial set-up and first use that sucked all that stuff into oblivion.

I have done searches, system restores, an undelete, Pandora, as well as looking through each folder manually. Can't find anything.

Additional information: I just booted from the flash drive and when I try to view existing documents (OOo) I get error messages (Unable to mount 160 GB Filestem: Eror mounting : mount exited with exit code 21) and then with Libre Office I got the following message: Libre Office 3.4 0 Fatal Error; An internal error occurred.

Anything else I can try? Thanks

---

### Post by MrSpike16 on 2011-11-25
Late here, but one quick advice.  Always unmount the XP partition before shutting down to help prevent damage.  This also includes any USB drives.

Don't know your experience level with Linux and Ubuntu, but unmount is like Windows "Safely Remove Hardware".  When mounted an icon should be created that you can right click on and then click unmount.

You didn't mention it but I assume you ran a file system check in Windows.

---

### Post by gregoryclark on 2011-11-25
I have no experience using ubuntu, just followed the written directions. I'm guessing that the files etc. that are missing are gone for good given your description of 'unmounting'. Do you think that there is anyway to recover the data?  Thanks for your help.

---

### Post by cryptotheslow on 2011-11-25
You could try using PhotoRec (despite it's name it can recover all manner of file types).

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Step by step:
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Ideally you will have a spare drive (e.g. an external drive) to recover the files too rather than recovering them somewhere on the XP partition which could easily overwrite the location of the files you need to recover.

It can be a pain as the recovered files will not have their original names.

Read up on how to use PhotoRec before blindly diving in.

Good luck

---

### Post by gregoryclark on 2011-11-25
Thanks for the suggestion. Your warning about blindly jumping in was well received as that is how I have come to be in the mess I find myself in. I am such a pre-novice I may need the help of a professional to do this for me. Thanks again.

---

### Post by MrSpike16 on 2011-11-25
Your best chance for recovery was if Windows file system checker (chdsk) found a problem with the Master File Table and successfully repaired that.

After that your only hope is what [cryptotheslow]("http://ubuntuforums.org/member.php?u=1017128") suggested, but you needed to shutdown and not run XP again immediately after you discovered the problem. With System  Restores and using XP, any of the lost  files has a high probability of being over written by now.

With what you were doing in Ubuntu, you would think the worse case would be a lost file that you opened.  All I can think of is perhaps the drive is starting to fail.

You can use a Windows program to check drive health or Disk Utility in Ubuntu  (S.M.A.R.T.).    [http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

---

