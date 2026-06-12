---
title: "New user. Issues with local file permissions, Samba, etc..."
date: 2010-05-20
forum: General Help
---

### Post by Oberon Prime on 2010-05-20
Hello,

I just recently installed 10.04. On first boot an icon was placed on my desktop for my external USB hard drive which is formated NTFS and it right out of the gate worked with both read and write. All was good.

I've managed to get everything else I want setup without too much hassle including sharing of media on that drive to my Xbox via uShare.

My remaining hassles concern Samba. I've found so many guides that all give different steps make different recommendations using different assumptions.

What I want is to Share a folder with full read/write access to my wifes notebook so that when she clicks on the folder it just simply displays the contents without any prompts for a password.

But everytime I do it I see my computer on the Windows machine from there it shows the share names but when i try to click in I get this error every single time.

Network Error
Windows cannot access \\VALYRIA\Backups
Check the spelling... 

I setup the shares using the Samba Server Configuration tool. In the properties of the share under Basic both Writable and Visible are checked. Under Access it says to allow access to everyone.

This is what shows in /etc/samba/smb.conf

[Backups]
	path = /media/Essos/Backup
	writeable = yes
;	browseable = yes
	guest ok = yes

[Unsorted]
	path = /media/Essos/Video/Unsorted
	writeable = yes
;	browseable = yes
	guest ok = yes

I've tried editing it a dozen different ways adding lines for things like guest account settings. Though many sources would suggest how I have it set in tool is correct.

I came across a guide that appeared to explain how to do it the way that I wanted but it assumed I hadn't mucked with anything so i removed samba and scrubbed the config file. Began again from Nautilus selecting the setup sharing options from the context menu of the folder. It installed samba again. And I used the options in that dialog. Checked all 3 boxes and picked a a name. It showed the folder in Windows but nothing was in the smb.conf file when I did that.

Got the same result.

Most recently I came across suggestion that the file persmissions locally for that folder had to be set appropriately as well.

As it stands now the permissions are as follows.

drwx------ 1 matthew matthew  4096 2010-01-27 23:33 Backup

I've ran chmod 777 /media/Essos/Backup  many different ways from a root terminal and so on and it gives no error and with a -v switch I get this result.


mode of `/media/Essos/Backup' changed to 0777 (rwxrwxrwx)


When I do ls -l I get the same result so it did nothing.

I have no idea if the local permissions are relevant to the samba issue. Or if the fact that its an external  auto mounted that is the reason for the permissions issues. I could badly use some help.

---

### Post by dino99 on 2010-05-20
basicly when you want to share a device or partition or file, you only need to right click on and set the user rights (case sensitive)

into synaptic you can install mountmanager, then set your prefs with it (system admin mountmanager)

---

### Post by Oberon Prime on 2010-05-21
Okay played around some more. And what I've discovered is this.

If I use the Sharing options available from the Nautilus context menu on a folder within my home folder and check to allow Guest access then it works perfectly. It opens that folder with no errors shows the files and allows them to be read. If I go back into Sharing Options and check "Allow others to ..." it asks to apply changes to permissions and those changes actually take. Now it won't allow the changes to be saved. But it does allow files to be viewed at least.

Clearly their is some difference in how external USB drives are mounted that is at the hart of why I can't get the shares to work.

I would be greatly appreciate it if somebody could tell me what this difference is and how to correct it so I can get this resolved.

---

