---
title: "Delete files on flash drive &quot;locked&quot;"
date: 2010-06-06
forum: General Help
---

### Post by IWC316 on 2010-06-06
I got a free flash drive from Columbia College that has some files I want to remove.  I did the right click thing and they are read only.  I tried to change to read and write but I got...


Sorry, could not change the permissions of "ColumbiaCollegeViewbook.pdf": Error setting permissions: Read-only file system

Now this thing only shows up as 5.4 MB  Yea that is right Megabytes!  But I have a plan for it.  So is there any way to get the files off so I can put mine on it?

---

### Post by marcoftheknight on 2010-06-06
Applications-->Accesories-->Terminal-->

Use the following code WITH the correct directory Read everything below before you input code:

sudo nautilus /home/youcomputername/music

("sudo launchs with admin rights nautilus lauchs the GUI for document management and the last part is for the directory you want to launch this way


 /home/youcomputername/music = replace my example directory with the one you want

to get the directory right click on it and go to properties then copy the directory into the terminal

I think that will work then you can delete with sudo permissions

Thanks

---

### Post by IWC316 on 2010-06-06
OK I tried it but with no luck, I got...

jason@jason-desktop:~$ sudo nautilus /computer:///
[sudo] password for jason: 
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I got the "computer:///" when I right clicked and it was listed as the "Location"

BUT there has been a new development. When I went to "computer" my eyes were drawn right to the "CD drive: Columbia" and I did not notice the USB 2.0 Flash Disk icon.  Maybe I did the wrong thing but I right clicked it and formated it.  Now I have 2.1 GB of space showing.  I took it to my PC and it showed up there too.  So I copied a pic to it and took it back to the Ubuntu computer and it worked.  But how ever the Columbia files are still on the other partition.  Now to get rid of them!

---

### Post by MedianMajik on 2010-06-06
> **IWC316 said:**
> OK I tried it but with no luck, I got...

jason@jason-desktop:~$ sudo nautilus /computer:///
[sudo] password for jason: 
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I got the "computer:///" when I right clicked and it was listed as the "Location"


Another way to run your filemanager as admin is by running ```
gksudo nautilus
``` and browsing to the directory.  The reason to not do it is in order to prevent destroying data, which it sounds like you might have problems with.  Running admin is the same as smashing a flower with a sledgehammer rather than using pruning shears.

Samba is not configured correctly so use ```
whereis smb.conf
``` to locate and post your config file so we can solve the problem.  [Here]("http://ubuntuforums.org/showthread.php?t=1026668") a link to this same question and the solution for Error 255.  Enjoy

---

### Post by elliotn on 2010-06-06
Right click on the file and go to properties and the permission

---

### Post by elliotn on 2010-06-06
> **elliotn said:**
> Right click on the file and go to properties and the permission

Meant change the permission to Read and Write

---

### Post by IWC316 on 2010-06-06
> **elliotn said:**
> Meant change the permission to Read and Write

I tried that before and I get a pop up box...


Sorry, could not change the permissions of "ColumbiaCollegeViewbook.pdf": Error setting permissions: Read-only file system

---

### Post by wojox on 2010-06-06
Do you have access to a Windows machine? That will wipe it out. :P  

Seriously

---

### Post by IWC316 on 2010-06-06
> **wojox said:**
> Do you have access to a Windows machine? That will wipe it out. :P  

Seriously

Yep!  Which one and how?

Windows 7 home premium 64bit
Windows 7 starter
Windows Vista
or Windows XP

---

### Post by wojox on 2010-06-06
> **IWC316 said:**
> Yep!  Which one and how?

Windows 7 home premium 64bit
Windows 7 starter
Windows Vista
or Windows XP

Vista. You said before that it's a sanDISK right? Just plug it in and it should give you the option.

Someone on these forums helped me out with this same problem before.

---

### Post by IWC316 on 2010-06-06
I have the vista/xp comp on the TV.  I will try it when the Wii is at idle!;)

As for the FD it does not have a brand name on it!

---

### Post by Oakfen on 2012-09-22
> **wojox said:**
> Do you have access to a Windows machine? That will wipe it out. :P  

Seriously

I love you, have been trying everything but to no avail.

 Then I saw your post and plugged it into my windows machine. Everything has become right with the universe.:KS

---

