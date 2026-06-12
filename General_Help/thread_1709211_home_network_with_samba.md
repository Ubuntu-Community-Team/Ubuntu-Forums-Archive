---
title: "home network with samba"
date: 2011-03-17
forum: General Help
---

### Post by ewaynec on 2011-03-17
I am using lucid lynx, it is my only OS. I have a home network using samba with another machine using Windows 7 (I know, it is my wife and she is not ready to change to Linux yet) I just built her machine and went from Windows XP to Windows 7. The network was working great for over a year, then with the new OS I cannot get Windows to share. I can go from the windows to the Linux fine, but when I go from Linux to Windows, I see the machine and the folders that I have shared, when I click on one it says "failed to mount", if I physically mount it it ask for a password, (I have it set up to connect without a password) I set up myself as a user and try to use my log-in password, the window pops back up asking for the password. I tried my wife's password, no joy. 
  Windows 7 is a weird OS it wants to tell you what you should do and then does it for you. I won't let you do what you want, it does what it wants. Does anyone know enough about Windows 7 to help me with this one?

---

### Post by varunendra on 2011-03-18
Have you tried this :- [http://ubuntuforums.org/showthread.php?t=1709219](http://ubuntuforums.org/showthread.php?t=1709219)

Default workgroup in Win7 maybe 'workgroup' instead of 'MSHOME', so make sure it is identical in both machines.

Windows firewall also blocks communication sometimes, so try disabling it .If you don't want to disable it, then just try it temporarily, if it works, you may further try creating an exception for your ubuntu machine in it and then enable it for everything else.

---

### Post by ewaynec on 2011-03-18
Thank you for the advice, I looked at the link you provided. It tells how to set up the Linux box, I have no trouble with it. I had it set up and working before windows 7 and I have changed nothing. 
  Windows 7 instructions are for setting up a network with other windows 7 users called "homegroup". It tells me this is what I need to do. There are no instructions for a mixed network, it says "it is best to not do this". I did change the name to "workgroup" and that matches the Linux box.
  I see the windows box but cannot access it.

---

### Post by Jerry N on 2011-03-18
In Windows Explorer right click on the folder or file you want to share.  Select "Share With".  Select "Specific People".  Then select "Everyone", or the specific group or person you want to share with.  Select "Add" to add "Everyone" to the list.  Change sharing options, if desired.  Select "Share".

Works for me.  For some reason Mint 9 is easier (for me) to get set up for sharing than Ubuntu 10.04.  

Jerry

---

### Post by ewaynec on 2011-03-18
I had everything set up as you said, but I went over it again to make sure and it is setup to share like you said.
  I also have Direct TV connected through the network (with Whole Home, their set up). I can see everything from the windows box, (the Linux, the Direct TV, all three TVs, and the media server). I can access everything from windows. From Linux I can see the windows box but none of the TVs. From the TV I can see the windows and the Linux box, and can access both.
Everything connects to everything except, I cannot access win from Linux

---

### Post by Jerry N on 2011-03-18
Something else to look at:
Go to the control panel, select "Network and Sharing Center", and "Advanced Sharing Settings".

My settings:
Turn on network discovery
Turn on file and printer sharing
Turn on sharing so anyone with network access .... etc
Media streaming is off 
      (You might want it on)
Use 128 bit encryption ....
Turn off password protected sharing
Allow windows to manage homegroup connections

--------------------
Win 7 is a lot more security conscious than previous versions.

---

### Post by ewaynec on 2011-03-21
Is there something maybe in the Linux set-up that is causing the problems? It is still set-up just as it was for the Windows XP. Is there something different? 
  I have done everything in windows suggested here and in the Win 7 help. It appears as though everything is as it is supposed to be.
  When I access the Windows box I get "C" (I have the C drive shared) and a "C$". I shared a folder named "Test" and it also shows a folder named "Test$". I get the same error trying to access either.

---

### Post by ewaynec on 2011-03-23
I can't find a way to mark this thread as unsolvable.
I still have not found a solution

---

### Post by dmizer on 2011-03-23
You might find "Problem 5" useful here: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149) (includes directions on how to configure Windows 7 for regular file sharing).

---

### Post by ewaynec on 2011-03-27
A very well written How-to on setting up the connection. I do not have a problem with the connection. I have a problem with mounting, (I believe ) because Windows is not shareing.
  I have the old HDD I use to have with Windows XP on it. I put it in and booted to it. I set up the network and it acts just like it does with Linux. So to me that is proof that the problem is the Windows 7 setup,  and my ignorance on setting up the Windows end.
   There are some How-to on setting up Windows networks but they skip over the part on shareing.

---

### Post by dmizer on 2011-03-27
> **ewaynec said:**
> There are some How-to on setting up Windows networks but they skip over the part on shareing.

This is covered in the howto I linked:
> **dmizer said:**
> Windows 7 seems to be bent on wanting you to use "HomeGroup" file sharing, but this will not work with Samba, it will only work with other Windows 7 computers, and you're probably better off disabling it if you need things to work correctly in a mixed network.

In order to get simple file sharing to work, you'll need to click on the "Change advanced sharing settings", and make sure you have network discovery, file and printer sharing, and public folder sharing enabled in the "home or work" profile (also, make sure that "home or work" is labeled as your current profile). You should be able to use 128 bit encryption, and use either enable or disable password protected shares (depending on how much security you desire).

Then, go to "Change adapter settings", right click on your connection and select "properties". Click on the "Internet protocol version 4 (tcp/ipv4)" and select "properties". Then click on "advanced ..." (at the bottom), and select the "WINS" tab. Make sure that "Enable LMHOSTS lookup" is enabled (no need to import), and make sure that "default" is selected for NetBIOS setting.

Now, go to a folder (try the public folder first), and right click on it. Select "properties", and click on the "sharing" tab. Click on "Advanced sharing", and put a check mark in "Share this folder". Change the "share name" if you like, and click on the "permissions" button. Make sure you have permissions set as you desire (a checkmark in "change" = writeable). If you've enabled password protected shares, you'll have to tweak settings here to make sure that your Ubuntu user is included for permission.

In some situations, you will find it necessary to add your Ubuntu username and password as an account on your Win7 machine. This may seem tedious, but that's the way secure Samba servers work.

Once this is all set, then your folder will show "shared" and it's network path will be displayed.

You will also be unable to share files with Ubuntu if you have Windows Live ID installed. Make sure you do not have this installed, as it often installs itself without you asking.

---

