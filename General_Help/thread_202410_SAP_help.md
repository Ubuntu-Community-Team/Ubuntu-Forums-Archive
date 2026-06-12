---
title: "SAP help"
date: 2006-06-23
forum: General Help
---

### Post by dspivey on 2006-06-23
I have installed SAPGUI for Java in Dapper, and the software does run.  However, I can't seem to access any of the SAP servers.  I have copied the saplogon.ini file from my working Windows XP station and have entered its location in the SAP guilogon app by typing the path in Options>Preferences>Configuration>Include Configuration File.  When I try to add a new connection I have red circles containing a white 'x' next to the System and Group/Server fields.  I don't know where to go from here.  Does anyone have any experience with this at all?  Thanks in advance for any help offered.

---

### Post by dspivey on 2006-06-27
bump

---

### Post by Jindro on 2006-06-28
did you changed /etc/services?

SAPGUI 6.40 Rev 6 is OK for me

---

### Post by lorenzo on 2006-06-28
Try to create new connections manually without using any windows preferences/configurations.

What I do is:
1. From the startup saplogon panel I choose "new".
2. I fill the description like "My Customer XXX PRO"
3. I go to the advanced tab and set the flag "use expert configuration" (it's the ony way it works for me
4. I write the connection string in the textbox with:

conn=/H/10.1.1.100/S/3220

where 10.1.1.100 is the sap server,
3220 consists of a static part "32" and the sap system number (in my case is 20)

That's it. Let us know If you could make it work

good luck,
Lorenzo

---

### Post by dspivey on 2006-06-28
Thank you Jindro and lorenzo!  I appreciate your replies very much!

I tried logging on using the method lorenzo described and it partially worked.  I used the expert settings and the correct connection string, but when I click on the Connect button a small window that says "Connecting" comes up, the blue progress bar goes all the way across and then goes away, but no other windows appear.  The system appears to be connected to the server, but I don't have a login window.

However, when I perform the exact same actions on my Windows XP, using the same SAPGui version (6.40rev6), everything works correctly and I am able to logon and use SAP.  

Any idea why the SAP window won't open in Ubuntu?
Thanks again!

---

### Post by dspivey on 2006-06-28
SUCCESS!

Believe it or not, the problem was starting the guilogon while logged on as root (I was actually using the root terminal).  I discovered this by doing a fresh install of dapper on another PC and the guilogon worked completely on that system.  I noticed that I had run ./guilogon as the user and not root.  I went back to my computer and started guilogon from my user account and SAP launched correctly!

Thanks again for your help!

---

### Post by fedemw on 2006-08-10
[http://www.ubuntuforums.org/showthread.php?t=232847&highlight=sapgui](http://www.ubuntuforums.org/showthread.php?t=232847&highlight=sapgui)

maybe can helo for fix guilogon

regards

---

