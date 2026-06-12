---
title: "How to Migrate Data from a Raid 1 setup in ubuntu to Win7 or External Drive"
date: 2011-06-13
forum: General Help
---

### Post by ZcRaider on 2011-06-13
Hello everyone. This is my first time posting on the forums. Im somewhat of a newbie when it comes to linux. Slowly starting to learn it. However i have a very critical issue that must be resolved.
 
We have a computer that was formerly being used as a Fileserver via Ubuntu. However the former adminstrator had left us high and dry with a passworded O/S. So we are trying to recover the data using the Ubuntu Live Cd. Here are the Issues.
 
1.) We cant backup data to an External Drive (we have 133gigs worth) because of file permissions. Im a noob to linux. Not sure how to "release" these files. The files are mostly windows based because this fileserver was mainly shared with windows pcs on the network. 
 
2.) We considered just porting the data directly from the HDD's via USB Sata transfer cable with powersupply. I downloaded a program called Disk Internals Linux Reader and i can see the drives, but i cant access them because there configured to be Raid 1 software formated. My transfer sata kit isnt equiped for a Raid 1 setup.
 
3.) We were considering some how reverting the Raid 1 setup to just one single HDD. Then we can back it up to the windows O/S bypassing the locked files. But im not 100% sure how to do this without losing our percious data....
 
4.) We finally considered just overiding the server with a fresh install of Linux. Maybe we can access the files with immunity on a new O/S.
 
We want to setup the server to dual boot both Ubuntu and Win7. And be able to share files between the two. But before we start that endeaver...we want to back up the data for it is very valuable to the company.
 
I know the sauce is a little thick........but any help as to the best way to backup this data and or remove these stuiped file access permissions would be very very much appreciated. The former Network Administrator really screwed us over...and we really need that data. The server is Passworded and we are only able to administer it via Live CD.
 
*update: If i could just..some how reset the permissions and ownership of a each folder that has an "X" on it and says "Data unreadable", i could back it up while booted to live cd. These folders are acutal accounts that used to be networked, and they need there data... 
 
Thanks again
 
ZcRaider

---

### Post by ZcRaider on 2011-06-13
Man this is frustrating....there must be a way.

---

### Post by psusi on 2011-06-13
You don't dual boot a server.  Servers are kept running constantly; you don't want users to be unable to access their files because you decided to reboot it into another OS for a while.

Recovering a lost password is easy and will save you from disrupting the existing service and all the aggravation and expense that installing Windows will cause.  To backup files, you will want to have super user permissions.  See these:

[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ZcRaider on 2011-06-14
> **psusi said:**
> You don't dual boot a server. Servers are kept running constantly; you don't want users to be unable to access their files because you decided to reboot it into another OS for a while.
 
Recovering a lost password is easy and will save you from disrupting the existing service and all the aggravation and expense that installing Windows will cause. To backup files, you will want to have super user permissions. See these:
 
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
 
I apprieciate the advise, even tho it sounded more like a rebuking.....:-/ I am a Windows user so im not very experienced with Ubuntu. However im slowly learning it. 
 
This "server" is really just a NAS using a dell computer as a slave. Nothing really fancy about it. Mountable drives etc etc. Something that can easly be acomplished in a Windows 7 enviornment.
 
The problem is that attempts to reset this password have failed. And we need to backup our files, which is not possible because of the absurd permissions that our previous admin setup. Not to mention it is setup on a Raid 1. And since he has jumped ship, we are up the creek without a paddle.
 
1.) The first suggestion does not work. Pressing "enter" or "Esc" after Post does not load Grub or whatever its called. Even when we where able to login as part of the administrator group, we still had these Ownership and permission problems. We need to reset all the files so we can access the data.
 
2.) Im a complete noob when it comes to ubuntu. Its mostly a command line system with a simple GUI windows style shell. Ive tried to use the advise in that article but nothing seems to work.
 
The only way for us to even see our files is to Boot to Live CD and use the O/S on that medium.
 
If someone could show what commands are needed to enable "Super Permissions" so that we can recover our data on an external drive without getting "unable to view file, or You dont have permission prompts, this nightmare will be over. And we ill start the fresh install of Windows 7, followed by Ubuntu.
 
Also if i could figure out how to disable the Raid 1 Software created by Ubuntu, and revert it back to a normal drive again, that would could possibly lead to another work around.
 
We are in a transition phase right now. We want to have a dual boot server to be flexable. Yes it will be running all the time. But we want the ablity to switch Platforms if we need to revisit Ubuntu for future uses.
 
Data backup is our top priority right now.
 
Thanks for the suggestions. Hopefully someone out there has a solution.
 
*Update: I have fully reviewed the link for the "root and sudo" commands.  When i go in tommorrow, i try to login as Root.  Maybe that will give me the full access i need for the backup.  Again thanks for the sugguestions.  Still gonna need some help tho.

---

### Post by psusi on 2011-06-14
> **ZcRaider said:**
> 
*Update: I have fully reviewed the link for the "root and sudo" commands.  When i go in tommorrow, i try to login as Root.  Maybe that will give me the full access i need for the backup.  Again thanks for the sugguestions.  Still gonna need some help tho.

Bingo.  You don't even need to recover a password since you said you already have an admin logon.  Just because you are an admin does not mean you have permission to trash the system; you have to ask for it first.  Microsoft finally started doing this with Windows 7.  Hopefully it will help curtail the spread of windows worms/trojans.  It only took them 20 years to catch up.

---

### Post by ZcRaider on 2011-06-15
First i would like to say thank you for your information.  Even tho it sounds like you have a bone to pick, why your choosing me to vent i dont know.  However i respect your opinions.  But i do not agree.
 
Im not here to argue how much "Power" an admin should have.  Bottom line is im trying to fix the mess our former admin created.  He basically gave us the finger because we sighted him for repeatedly not showing up for work and not doing his job.
 
So now we have a locked server with company files on an a raid 1 setup.
 
I personally believe that admins should have the power to adjust there own systems.  That is why i love windows 7, and i had no problems at all with this type of thing.
 
*update: 
Over the past 24 hours we have been able to install ubuntu on a usb drive.  We are now running the server of that.  Now we have full access to the files on the raid.
 
The problem is even with the new install, i still can change anything as the only admin on this server.  I have only read only access.  I need to have FULL ACCESS so i can recreate the file share enviornment with windows desktops on the network.  I cant even change the network name on my pc....
 
I try:  
gksudo gedit /etc/hostname
 
I get:
 
 WARNING: attempting to store changes into /root/.local/share/recently-used.xbel, but failed no such file in directory

or
 
 WARNING: attempting to set permissions of /root/.local/share/recently-used.xbel, but failed no such file in directory
 
This is very frustrating...i have full access, the sole admin on the server, and i still can do anything.  
 
What must i do to get full control of my box?
 
Thank you.

---

### Post by ZcRaider on 2011-06-15
Ok... i might have solved my access problems.  I have found a way to login as root.  Hopefully that will give me the power i need to get this server back on the network.  I keep posting updates...

---

### Post by psusi on 2011-06-15
You keep conflating unrelated/incompatible statements.  If you have an admin logon, then you are not locked out.  When you get an error saying a file does not exist, you are not having a permissions problem.

Note also that those were WARNINGs, which you can happily ignore.

---

