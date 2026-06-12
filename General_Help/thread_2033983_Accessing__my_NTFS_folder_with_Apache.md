---
title: "Accessing  my NTFS folder with Apache"
date: 2012-07-27
forum: General Help
---

### Post by aqk on 2012-07-27
I  have a Windows NTFS partition in which I have a folder "www".  It is the Windows WAMP user folder.

When I boot into Ubuntu,  I can mount this partition **and I CAN edit the html files in the NTFS www folder.** with Gedit or Bluefish. No problem!

However, Apache in my LAMP system cannot access them. 
When I browse "Localhost" I get the following message: 
[B][COLOR="DarkRed"]Forbidden
You don't have permission to access / on this server.
  Apache/2.2.22 (Ubuntu) Server at localhost Port 80[/COLOR][/B]

How can I give Apache (or LAMP) the necessary permission to access this NTFS www folder? 
I think the Apache user-id is "www-data".  

And yes, I have changed my Apache sites-enabled to 
**DocumentRoot /media/DATA-175gig/www/ ** 
  and 
**<Directory /media/DATA-175gig/www/>**

Don't ask me to post the Apache error log here; it's basically the same as the 403 error message above.

---

### Post by galvatron408 on 2012-07-28
That means that you don't have permission to / on that server.

Make your configuration look like the below

```

DocumentRoot "/media/DATA-175gig/www/"  
  
<Directory />
    Options FollowSymLinks +Indexes
    AllowOverride None
</Directory>

<Directory "/media/DATA-175gig/www/">
    Options FollowSymLinks +Indexes
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

```

---

### Post by aqk on 2012-07-28
Didn't you read my message?  I have already done this.
I.E. -
[I][B][COLOR="SeaGreen"] And yes, I have changed my Apache sites-enabled to
DocumentRoot /media/DATA-175gig/www/
and
<Directory /media/DATA-175gig/www/>[/COLOR][/B][/I]

In any event, I have solved the problem quite simply.
See my next message below.

---

### Post by aqk on 2012-07-28
For the record, if anyone wishes both their LAMP (Ubuntu) and WAMP (windows) servers in a dual boot system to use the same NTFS www folder, proceed as follows:

The following assumes that the www repository is in a folder named "www" on a Windows' NTFS partition named "DATA-175gig"
As well, my editor of choice here is Gedit. Yours may vary.

***Step-1.***  Modify your Apache config file:
[INDENT]   **[COLOR="Red"]sudo gedit /etc/apache2/sites-enabled/000-default[/COLOR]** 
    to use the NTFS partition and folder name.
E.G.  **DATA-175gig/www/** where DATA-175gig is the name of the NTFS partition, and www is the folder in it. (see an example in above previous message.)
BTW, quotes are not necessary![/INDENT]

***Step-2.***  Restart Apache:
  [INDENT] **[COLOR="Red"]sudo /etc/init.d/apache2 restart[/COLOR]**[/INDENT]

***Step-3.*** Find your NTFS partition id, as used by Linux:
[INDENT]Issue a **[COLOR="Red"]sudo blkid[/COLOR]** to find out the NTFS device ID.
  In my case, the output from this shows a line
    [COLOR="Navy"]/dev/sda5: LABEL="DATA-175gig" UUID="588A35268A350254" TYPE="ntfs"[/COLOR][/INDENT]

***Step-4.*** Mount the NTFS drive with the correct permissions: [INDENT]Using the device ID (in the above case it is "/dev/sda5"), plug this value into  the following **udisks --mount** command:
  **[COLOR="Red"]sudo udisks --mount /dev/sda5 --mount-options umask=022[/COLOR]**

 This should mount the NTFS drive and allow Apache to access it.[/INDENT]
 
***Step-5.***  Check the address "localhost" with your browser. It should work now, in both LAMP and WAMP.

***Step-6.*** Add the above device id entry to your FS table:
[INDENT]**[COLOR="Red"]sudo gedit /etc/fstab[/COLOR]** 
  Otherwise you will have to issue the above Udisks mount command every time you boot into Ubuntu. 
[/INDENT]
**[CENTER]- PLEASE SEE NEXT REPLY ON HOW TO ADD THE NTFS DISK TO YOUR FSTAB -[/CENTER]**

---

### Post by aqk on 2012-07-28
The previous comment showed how to mount an NTFS partition in Ubuntu using a terminal command.
So you do not have to issue the command every time you boot into Ubuntu, an entry for it should be placed in the FSTAB.

  Step-1.  First mount the NTFS device:
[INDENT]**[COLOR="Red"]sudo mkdir /media/DATA-175gig[/COLOR]**
This  gives it a "mount point" - effectively this is just a fancy way of saying "give the device a Linux name".
The simplest name to use would be the very same name as the partition name in Windows- DATA-175gig as used previously above. But it does not have to be.
It can be any name you want i.e.  "wwwcrap".
But remember that this name **must be used** in the Apache conguration file:
  E.G.  ***<Directory /media/wwwcrap/www/>*** [/INDENT]

Step-2. Add the entry to FSTAB:
[INDENT]  **[COLOR="Red"]sudo gedit /etc/fstab[/COLOR]**   
and add a line such as
**/dev/sda5  /media/wwwcrap ntfs uid=1000,gid=1000,nls=utf8,umask=002 0 0 **
  where sda5 is your device id shown in **blkid**, and wwwcrap is the Ubuntu partition name (OK then, the "mount point"!) that you have chosen.[/INDENT]

Step-3.  Restart Apache:
[INDENT]  **[COLOR="Red"]sudo /etc/init.d/apache2 restart[/COLOR]**[/INDENT]

If Apache still cannot detect the added NTFS device, you may have to reboot Ubuntu.  Check "Computer" - you should see the Ubuntu device mounted there. 
Note that you cannot unmount it anymore- only root can.
E.G. **[COLOR="Red"]sudo umount /dev/sda5[/COLOR]**  

Now, you should be able to reboot back and forth at will between Windows and Ubuntu, and all HTML and PHP files can be edited and browsed in either system using the single www repository folder.

Windows Apache Version: 	**Apache/2.2.22 (Win64) PHP/5.3.13**
Ubuntu  Apache Version: 	**Apache/2.2.22 (Ubuntu) PHP: 5.3.10-1ubuntu3.2**

---

