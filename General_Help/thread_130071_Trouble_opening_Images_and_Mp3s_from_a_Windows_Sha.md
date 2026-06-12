---
title: "Trouble opening Images and Mp3s from a Windows Share"
date: 2006-02-15
forum: General Help
---

### Post by macjohn on 2006-02-15
I just installed Ubuntu Gnome this past weekend and have found solutions to many of my issues in this forum.  I thank everyone for this excellent source for information... it's almost too good... I find myself cutting and pasting from this forum into a terminal window and fixing my problem without ever really knowing what I did... but I'm sure eventually I'll catch on.  

I was able to get a printer hooked up to my Ubuntu PC shared with my Windows computers on my network with the help of this forum configuring samba (I think).  I am able to print from my other PC's anyway (all running XP pro).  I'm able to browse to my Windows PC and surf around in various directories, etc and I'm also able to surf my Linux box from my Windows PC's.  I'm able to VNC to and from each as well.  It looks like my connection is solid but the one thing I'm having trouble with is being able to open up either an image file or any mp3 file from my windows PC's.  

I can't open an image with any program I've tried (Gimp was the default but I right clicked and tried every other option there was and even installed a afew more to try).  Gimp gave some error about not being able to access the file or something (If I was typing this from home, I'd give you the exact message).  The other programs either don't open or just blink at me.

I can open MP3's with the media player that loads as the default player (totem I think).  But I'm a Winamp user and would like to use XMMS but it won't open any of my shared MP3's on my windows PC.  I can copy them to my desktop and play them (just like I can copy images to my desktop and view them).  I just can't do it from the network.

It's as if I don't have security so I have played with security settings on the windows XP box.  My linux user is the same as the user ID on the windows box... I also created an account in windows with the same name as my linux PC name.  I've done everything except give security to 'everyone' to read and write (I hope that's not the solution but I'll try it later just to see if it fixes things).

Has anyone else had problems like this?  Is there some setting I need to tweak in either linux or windows to resolve this?

Assuming this is an easy fix, feel free to offer suggestions on my other action items that I haven't resolved since installing:

Accessing my webcam (Intel CS330) without crashing
Learning the simple (hopefully) steps to downloading and compiling and installing a program (if there are any).
Installing a web server

If I can get access to my webcam from work, get a web server running, get a proxy server running, and resolve this network access issue I'm having, I might be able to convert another PC to linux within a few weeks (my windows web/proxy server).

Thanks in advance for any help

John

---

### Post by Ramses de Norre on 2006-02-15
For the webcam: I'd check for drivers for it (spca5xx maybe?). I don't know which fits your model, just google for it:)
For compiling programs: download the source and check the read me files, they have always explained me how to do it perfectely.
Don't really know the solution for now for the other issues.

---

### Post by sbassett on 2006-02-15
MacJohn -

This might be an easy fix. Did you use the nautilus, right click, Connect to server approach to connect to your windows boxen? If so, this could be the issue. If not, stop reading here as the rest is a waste of time.

First things first, right click on the remote folders located on your desktop and select Disconnect...
It appears as though you can connect to your windows shares easily enough, it's just that many programs don't handle the gnoe-vfs method of connecting to other servers very well. The other option is to have these mounted at boot-up via /etc/fstab.

2 ways of accomplishing this:

1.
Add an entry to /etc/fstab as follows:
//servername/sharename /mnt/localsharename cifs username=windowsname,password=windowspass 0 0

2.
This method hides the windows logon info.
gedit /home/username/.smbinfo
in this document place the following
username=windowsname
password=windowspassword

save and close, then 
chmod 600 /home/username/.smbinfo
You would then add the following to /etc/fstab:

//servername/sharename /mnt/localdir cifs credentials=/home/username/.smbinfo 0 0

This method is recomended as it hides the info a little better. 

I have replaced the traditional smbfs with cifs, as there have been reports of significant speed gains with the new method. If this does not work:
sudo apt-get install smbfs

After all is said and done:
sudo mount -a

should have you up and running.

Let me know if there are any problems.

---

### Post by macjohn on 2006-02-15
I have been opening through Nautilus and tried the first step of your instructions:
adding a line to /etc/fstab, but I can't seem to open fstab except in read only mode.  What might I be doing wrong?  I've tried entering that from a terminal window and receive 'permission denied' and I can open it in read only if I browse to it.

John

---

### Post by sbassett on 2006-02-15
My humblest apologies. It should be
sudo gedit /etc/fstab

Don't know what I was thinking.

---

### Post by macjohn on 2006-02-15
thanks for the info... I tried the first option because it seemed simpler with less room for error with the intention of trying the second if the first worked... it didn't.  Here's what I typed in:
//192.168.1.100/f /mnt/macjohn_F cifs username=windowsusersname,password=windowspassword 0 0

192.168.1.100 was the server, f is the drive, macjohn is the pc's name and I assumed it would be ok to name the mount that.

I restarted and tried to reconnect and received the same errors.  Here's what the Gimp is telling me specifically:
Could not open '/home/administrator/smb://macjohn/f/directory/filename.jpg' for reading: No such file or directory

and

Opening '/home/administrator/smb://macjohn/f/directory/filename.jpg' failed: Plug-In could not open image

when I right click and choose 'open with image viewer', the image viewer shows on the task bar for about 15 seconds and then vanishes.

When I try this command:
sudo mount -a

it complains about whatever I have in the mnt section of my fstab line.  So I think that might be where I went wrong... but I don't really know what that mnt is asking for.

---

### Post by sbassett on 2006-02-16
What is the error that mount spits out at you? Does /mnt/macjohn_F exist? Also,  windowsname and windowspassword is not what you put in the /etc/fstab file, correct? You put in the username and userpassword that you would normally access the windows pc with.

Let me know about the error.

---

### Post by macjohn on 2006-02-16
it tells me mount:  mount point /mnt/macjohn_f does not exist

I have no idea really what it's talking about.  I've tried to create a folder on my desktop that shares the name as what is in this section to no avail.  I also did replace the windows usersname and password with the username and password that is valid on every pc on my network... I just replaced it before I posted.

---

### Post by sbassett on 2006-02-16
then the only step left is:
sudo mkdir /mnt/macjohn_F

Notice the uppercase F, as this is how it is listed within your /etc/fstab entry. This should be the final piece of the puzzle. execute mount -a again and you should be able to open the files from /mnt/macjohn_F from this point on.

---

### Post by macjohn on 2006-02-16
wow, amazing how easy it is when it's all said and done... works like a champ!  thanks a bunch!

---

### Post by nianhbg on 2006-03-02
Thanks for the tips :)

I got my connections working perfect \\:D/

---

