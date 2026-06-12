---
title: "sharing windows printer to ubuntu"
date: 2010-03-03
forum: General Help
---

### Post by nothpeople on 2010-03-03
Hello! (my english is not very good but i'm going to try to work it out)
I have a Samsung printer connected to a windows xp computer. I want to share the printer with my ubuntu 9.10 laptop. Some months ago, I managed to do it. However, now, without any previous notice, my ubuntu says that it can't find the printer. 

I've tried to change the windows computer for another one (windows too), and the sharing system works ok.

The problems I have with the first set of computers are the following: I make System>Administration>Printers>Add printer>windows printer via samba. If I choose the option 'explore', ubuntu finds my windows computer, but it can't show the printer. If I type the uri, ubuntu says that the printer is not accesible.

I don't know how to solve it: in my windows computer, the printer is shared and has the option 'bidirectional compatibility' disabled.

Thank you all very much.

---

### Post by SteveHillier on 2010-03-03
Hi there,
If you have the windows sharename for your printer can you specify that when you add the printer.
Also have you looked in the Samba configuration file - try opening a terminal and typing
```
sudo gedit /etc/samba/smb.conf
```
The printer configuration settings are towards the bottom of the file

---

### Post by plucky on 2010-03-03
Go to **System > Administration > Printing > Server > Settings** and make sure the box "Show Printers shared by other systems" is checked,and then see if it finds the printer.

Good Luck

---

### Post by nothpeople on 2010-03-07
i'm sorry, but none of the two options given by plucky and SteveHillier have worked. 

maybe could it be a problem  of the windows xp computer (this is the one with the printer)? i have installed ubuntu 9.10 in another computer (now ubuntu is on my laptop and on another computer) and it has the same problems...

---

### Post by kismeras on 2010-06-03
> **plucky said:**
> Go to **System > Administration > Printing > Server > Settings** and make sure the box "Show Printers shared by other systems" is checked,and then see if it finds the printer.

Good Luck

@Plucky - I tired that and got this error msg:
"There was an HTTP error: status 1000."

I'm running windows 7 Pro X64 and trying to use the Canon Pixma MX310 that is connected to it. I can use it with all of my other Windows PCs but not my Linux laptop. Not trying to hijack this thread...I'm just having the same issues. Thanks.

---

### Post by plucky on 2010-06-03
> **kismeras said:**
> @Plucky - I tired that and got this error msg:
"There was an HTTP error: status 1000."

I'm running windows 7 Pro X64 and trying to use the Canon Pixma MX310 that is connected to it. I can use it with all of my other Windows PCs but not my Linux laptop. Not trying to hijack this thread...I'm just having the same issues. Thanks.

Sorry cannot help as I don't use Windows 7,but I would try connecting the printer directly with a USB cable just to see if Linux has a driver for it as it doesn't seem to be mentioned in the [Open printing database]( http://www.openprinting.org/printers) for Canon.
It won't work unless there is a driver for it somewhere in linux.

Good Luck

p.s.Might be better to start a new thread of your own.

---

### Post by stefanmuc2k on 2010-11-06
> **plucky] Originally Posted by plucky View Post
Go to System > Administration > Printing > Server > Settings and make sure the box "Show Printers shared by other systems" is checked,and then see if it finds the printer.
[/QUOTE]

[QUOTE=kismeras said:**
> @Plucky - I tried that and got this error msg:
"There was an HTTP error: status 1000."


For the benefit of others who might encounter this thread: I got the same error message trying to access the settings dialog.
 The problem was that the user account I was logged-in with, just didn't have the permissions to modify printer settings. 
(Very unhelpful error message, it has to be said.)

To resolve: either use another account to configure the printer settings, or use:
 *System > Administration > Users and Groups* 
then enable the options to allow printer administration for that account.

---

