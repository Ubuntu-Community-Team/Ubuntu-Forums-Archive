---
title: "How to connect to a Flash Drive connected to my Router"
date: 2012-10-12
forum: General Help
---

### Post by a216vcti on 2012-10-12
This is my first Ubuntu install. I have Version 12.04 installed on a Dell XPS M140.  I was wondering how do I connect to the external hard drive connected to my router.  I have a cisco E4200 router and with a western digital external hard drive configured through the router.  In windows, I am able to type in the name of the share \\XXXXX\e42001 and it takes me right to it.  I don't know how to pull up that directory in Ubuntu.  Thanks in advanced.

---

### Post by a216vcti on 2012-10-13
Ok, so this may be an issue of the external hard drive being fat32.  Will ubuntu recognize a share that is fat32?

---

### Post by a216vcti on 2012-10-13
Hello everyone, I'm new to the Ubuntu world and quite bad with computers in general. This is my first install of linux on any machine ever. I was able to get everything up and running flawlessly except one thing. I have a external hard drive that is connected via usb 2.0 to my router, a cisco e4200.  I created a share on it that I can access when on my windows machines by typing in \\cisco19294\e42001 in the run prompt, or in windows explorer.  I don't know how to do that using Ubuntu.  I tried opening it through mozilla, but that doesn't seem to work.  I posted this question in the networking section, but I think I might have put that in the wrong spot. I was wondering if you guys could help me?

---

### Post by coffeecat on 2012-10-13
Hi - I've merged your two threads since duplicates in different places dilutes community effort. Since you didn't get any replies (yet) in the Networking Forum I've moved the combined thread to General Help, but this can be moved again if need be.

As far as your question goes, if your router creates a standard Windows share in the USB drive, it should be very easy to connect to this from Ubuntu. The filesystem doesn't matter. The Cisco device reads this.

Open a Nautilus file browser window (click on the home icon near the top of the launcher). In the left pane click on "Browse Network" at the bottom of the list. Hopefully, your share will appear in the main pane and you can double-click on it and enter your authentication details (if any). If you get an error, open the Windows Network folder -> WORKGROUP folder and try from there.

Alternatively, from the Nautilus menu in the top bar, File -> Connect to Server. Choose Windows Share and smb://cisco19294/e42001 in the share field.

If they don't work, post back and someone will be able to help you.

---

### Post by a216vcti on 2012-10-13
> **coffeecat said:**
> Hi - I've merged your two threads since duplicates in different places dilutes community effort. Since you didn't get any replies (yet) in the Networking Forum I've moved the combined thread to General Help, but this can be moved again if need be.

As far as your question goes, if your router creates a standard Windows share in the USB drive, it should be very easy to connect to this from Ubuntu. The filesystem doesn't matter. The Cisco device reads this.

Open a Nautilus file browser window (click on the home icon near the top of the launcher). In the left pane click on "Browse Network" at the bottom of the list. Hopefully, your share will appear in the main pane and you can double-click on it and enter your authentication details (if any). If you get an error, open the Windows Network folder -> WORKGROUP folder and try from there.

Alternatively, from the Nautilus menu in the top bar, File -> Connect to Server. Choose Windows Share and smb://cisco19294/e42001 in the share field.

If they don't work, post back and someone will be able to help you.

Thanks for the response.  Very sorry for the duplicate.  Thank you for merging threads.  I tried what you told me and when I click on WORKGROUP it says "Unable to mount location. Failed to retrieve share list from server."  I tried adding the server from File > connect to Server and wasn't sure what to put in the blank fields.  For the server name, should I have put WORKGROUP?  Also, should I have put "smb://xxxxx/e42001" in the share field or just "//XXXXX/e42001?"

Thanks!

---

### Post by coffeecat on 2012-10-13
> **a216vcti said:**
> Thanks for the response.  Very sorry for the duplicate.  Thank you for merging threads.  I tried what you told me and when I click on WORKGROUP it says "Unable to mount location. Failed to retrieve share list from server."  I tried adding the server from File > connect to Server and wasn't sure what to put in the blank fields.  For the server name, should I have put WORKGROUP?  Also, should I have put "smb://xxxxx/e42001" in the share field or just "//XXXXX/e42001?"

Thanks!

WORKGROUP is probably your Windows share group - it's the default group name but some devices define other groups. Don't put that in the server name.

Let's start again. If you are getting "unable to mount location" (I thought you might - seen that more often than I've had hot dinners), open the Windows Network folder. *Then* open the WORKGROUP folder (or any other folder that might appear) and see if your Cisco share is showing in that, and try to open it. That sometimes works when it won't open from the main Browse Network folder.

If that doesn't work, my apologies - I made an error in my last post. From Connect to server, try smb://XXXXX/ in the server field, not the share field. You can try with e42001 in the share field or not. Try both. Without, you should be offered a browser window with the shares as folders. Don't omit the smb:// bit from the server address, although that might not matter if you've specified Windows Share.

I suggested smb://cisco19294/ rather than smb://XXXXX/ because that it was you had put in one of your posts. XXXXX would be the Cisco device name and e42001 the share name. 

Another thing to try, if your router IP is 192.168.1.1, use smb://192.168.1.1/ . Substitute your router IP is it's different - say 192.168.0.1.

I'm having to assume your router sets up a share in a conventional way, as I have no experience of shares using a USB drive attached to a Cisco router.

---

### Post by coffeecat on 2012-10-13
Just to add:

I have a Netgear router and I'd never bothered to try a share with an attached USB drive. I've just done so - my share path is smb://readyshare/usb_storage. I think you can see the pattern. For me, "READYSHARE" does not appear in the Browse Network folder, but if I open the "Windows Shares" and then WORKGROUP folders, I can see READYSHARE in the WORKGROUP folder and it opens just fine and I can copy files to and from it.

Double-check the WORKGROUP folder. It could be that Cisco works in a similar way.

---

### Post by a216vcti on 2012-10-13
> **coffeecat said:**
> WORKGROUP is probably your Windows share group - it's the default group name but some devices define other groups. Don't put that in the server name.

Let's start again. If you are getting "unable to mount location" (I thought you might - seen that more often than I've had hot dinners), open the Windows Network folder. *Then* open the WORKGROUP folder (or any other folder that might appear) and see if your Cisco share is showing in that, and try to open it. That sometimes works when it won't open from the main Browse Network folder.

If that doesn't work, my apologies - I made an error in my last post. From Connect to server, try smb://XXXXX/ in the server field, not the share field. You can try with e42001 in the share field or not. Try both. Without, you should be offered a browser window with the shares as folders. Don't omit the smb:// bit from the server address, although that might not matter if you've specified Windows Share.

I suggested smb://cisco19294/ rather than smb://XXXXX/ because that it was you had put in one of your posts. XXXXX would be the Cisco device name and e42001 the share name. 

Another thing to try, if your router IP is 192.168.1.1, use smb://192.168.1.1/ . Substitute your router IP is it's different - say 192.168.0.1.

I'm having to assume your router sets up a share in a conventional way, as I have no experience of shares using a USB drive attached to a Cisco router.


WOOOHHH!!!!!!! YOU ARE THE MAN!  I dunno what was going on, but I added the network share by going to Nautilus File > Connect to server.  I inputted smb://192.168.1.1 and hit connect and saw the E42001 shared folder in Nautilus.  I can now access all of my files that are on my external hard drive. Thank you so much for the help! I hope you have a great weekend.

---

### Post by a216vcti on 2012-10-13
> **coffeecat said:**
> Just to add:

I have a Netgear router and I'd never bothered to try a share with an attached USB drive. I've just done so - my share path is smb://readyshare/usb_storage. I think you can see the pattern. For me, "READYSHARE" does not appear in the Browse Network folder, but if I open the "Windows Shares" and then WORKGROUP folders, I can see READYSHARE in the WORKGROUP folder and it opens just fine and I can copy files to and from it.

Double-check the WORKGROUP folder. It could be that Cisco works in a similar way.

Well, it's strange, because that's when I was getting the mounting errors. I saw the workgroup folder but was never able to drill down into the folder.  But it's all fixed now. Thanks again!

---

### Post by coffeecat on 2012-10-13
> **a216vcti said:**
> Well, it's strange, because that's when I was getting the mounting errors. I saw the workgroup folder but was never able to drill down into the folder.  But it's all fixed now. Thanks again!

Glad it's working. :) Sometimes it takes a bit of time for the smb server information to show up in Nautilus. 

Just one other fyi comment seeing as you are new to Linux. Linux is severely case-sensitive and throws an error if you get the case wrong in a file or path. Windows isn't and this extends to Windows shares. If you try ringing the changes with upper and lower case with the share server name and the share name, it probably won't make any difference. You won't be able to do that in a pure Linux environment.

Good luck!

---

