---
title: "WOW...Ubuntu and XP"
date: 2009-11-24
forum: General Help
---

### Post by robertcoulson on 2009-11-24
Hello, I just got Ubuntu and XP running on the same machine....No one seemed to be able to help me, but I did it myself (not that I am that smart with Ubuntu)..But, I have a couple of silly questions for some one to help me with.

1 - Do I need an antivirus...??

2 - How come when I installed Ubuntu and it asked if I wanted my bookmarks from XP to be installed, they did not...???

3 - Is it possible to un-install Ubuntu (not that I ever will) and will the grub flash screen disappear...???

Thanks for maybe helping a ( 61 year old ) computer lover.
Bob

---

### Post by Vadi on 2009-11-24
Hiya,

1) Nay

2) I think that is for the Firefox web browser. Are you sure it doesnt have your bookmarks?

3) Grub will still be there, you'd need to use a Windows tool to replace it.

---

### Post by Chunz0r on 2009-11-24
You will need an antivirus on xp, naturally that goes without saying.

---

### Post by robertcoulson on 2009-11-24
Thanks guys...I do have an antivirus running on XP...NO, my bookmarks didn't come over, no big deal thou....Probably get rid of XP before I get rid of Ubuntu...QUESTION..If I dump XP, will the grub program still be there...??
Bob

---

### Post by t0p on 2009-11-24
You do not *need* AV software for Ubuntu.  Some people like to run antivirus so they can scan files in Ubuntu to see if they are infected with Windows malware.  As you are dual-booting XP, you might want to do that.  But it's a matter of personal preference, and depends on how paranoid/"careful" you feel.

---

### Post by robertcoulson on 2009-11-24
OK...Well, I guess it won't hurt to run an antivirus...Can you suggest a small, free decent one...I use AVG on XP
Bob

---

### Post by fancypiper on 2009-11-24
All Linux programs are free! Unless you are serving mail to Windows machines, the viruses found can't hurt your Linux, so an antivirus program for Linux is actually worthless.

It is rather hard to write a virus for Linux. See the [Virus Writing HOWTO]("http://virus.bartolich.at/virus-writing-HOWTO/_html/index.html").

I would suggest installing and running chkrootkit instead.

---

### Post by ramjet_1953 on 2009-11-24
Hi, there!

Regarding your bookmarks:

If you are using Firefox in Windows, just install the 'FEBE' add-on and then run it after first setting it up for a full profile backup.

Of course, you will then need to also install FEBE in your Linux Firefox also.

Use the Restore profile feature in FEBE to set up all of your setting in the Linux Firefox.

Note: You cannot do this in the default profile, you will need to create a new profile in your Linux Firefox first.

Regards,
Roger :)

---

### Post by fluffman86 on 2009-11-24
1) Antivirus is pointless, but if you want to manually scan a few files here and there you can install clamwin-gtk from the Ubuntu Software Center.

2) The account settings importer is kind of hit-or-miss.  If you were using IE in Windows, you'll need to install firefox and let it import the IE bookmarks.  Then backup your bookmarks with Bookmarks > Organize > Backup.  Most other browsers have a similar feature to Export as HTML.  Save the resulting file in your email or a thumbdrive or a folder on XP that you access from Ubuntu, then reverse the procedure and import into Firefox in Ubuntu.

3) If you decide you no longer want Ubuntu on your XP hard drive, you can reclaim the space with the Ubuntu live cd.  Use Gparted (System > Administration > Partition Editor) from the live cd to delete your Ubuntu / and swap partitions, then grow the XP partition to reclaim the empty space.

After doing this, you computer will no longer boot, because Grub overwrote the MBR and Windows boot loader, and then you removed Grub along with the Ubuntu partition.  (Grub is in /boot, which is part of /, the root directory in Ubuntu.  Every single folder, drive, USB port, CPU...EVERYTHING...is a folder or file under /)  

To get windows booting on this drive again, insert your XP cd, boot to command prompt or recovery console, log in (default password is blank), and type "fixmbr" (no quotes) to fix the master boot record and get Windows booting again.

Use a similar process for removing Windows.  Boot the Live CD, open gparted as before, and this time delete the NTFS windows partition and grow your Ubuntu partition.  You haven't changed grub or the MBR this time, so no need to try and fix things.  It should just work, although Windows may still show up in grub for a while.

---

### Post by robertcoulson on 2009-11-25
Thanks [fancypiper, ]("http://ubuntuforums.org/member.php?u=533072")[ramjet_1953 and ]("http://ubuntuforums.org/member.php?u=160725")[fluffman86]("http://ubuntuforums.org/member.php?u=275993")
  []("http://ubuntuforums.org/member.php?u=533072") That is a LOT of good info....You guys are great (and a great forum to )...I will try to use all this material you have sent me...
P.S> I don't think I will be removing Ubuntu any time soon....Spend 2 years with Live Cd's and finally got it on my computer.

Thanks again Bob

---

### Post by Desert Sailor on 2009-11-25
*IF* you are running the new Grub-2 (Ubuntu 9.10 boot-strap) you can easialy update the menu listing after you remove the Redmond Virus.  Just run update-grub from a terminal window and if windows is missing it will take it off the menu options.

---

### Post by robertcoulson on 2009-11-25
Desert Sailor...I have NO idea what you are talking about....???...But it sounds good.
Bob

---

### Post by ikacer on 2009-11-25
> **Desert Sailor said:**
> *IF* you are running the new Grub-2 (Ubuntu 9.10 boot-strap) you can easialy update the menu listing after you remove the Redmond Virus.  Just run update-grub from a terminal window and if windows is missing it will take it off the menu options.

.... huh?

---

### Post by audiomick on 2009-11-25
> **Desert Sailor said:**
> *IF* you are running the new Grub-2 (Ubuntu 9.10 boot-strap)  the thing that lets you chose between windows and ubuntu. 9.04 used the "old" grub, 9.10 has  grub2 as standard. Some people are changing back because of problems.
> you can easialy update the menu listing after you remove the Redmond Virus.  

as every good citizen should be striving to do...
> Just run update-grub
a command to (you guessed it.. ) update grub
> from a terminal window
there is a terminal in accessories in the applications menu. It is a window for entering command line commands.
 
> and if windows is missing it will take it off the menu options.

because linux is just better...:p

---

### Post by robertcoulson on 2009-11-25
Thanks audiomick...A little clearer now..(I think)
Thanks Bob

---

### Post by Sin@Sin-Sacrifice on 2009-11-25
Don't mean to butt in but I had to ask OP... Is that your real name or is it a "Fight Club" spoof?

---

