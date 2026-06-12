---
title: "Samba Problems with Ubuntu and Mac OS X"
date: 2006-06-30
forum: General Help
---

### Post by jeradzan12 on 2006-06-30
Hi,

I didn't see a specific "networking" thread to post this under, so sorry if it is in the wrong place.  I have read everything I could find and nothing seems to work.  I have a laptop (Dell C600) running Dapper 6.06.  Ths is on a samba network with a Mac OS X 10.4.7 computer and Windows XP Pro.  It will share files fine with the WinXP computer, but not with the Mac OS X.  It will see the computer, but won't show the shared files.  I thought it was the samba version issue that everybody was talking about here, but dapper has version 3.0.22, so it's not that.  I am at a loss here.  Any ideas?

Thanks.

---

### Post by xslf on 2006-06-30
Try connecting to the osx share using the "connect to server" option in the "places" menu. Make sure to enter the correct user name and password (when prompted)

---

### Post by shaviro on 2006-07-03
I've been reading lots of posts on getting Samba to work between my Ubuntu machine and my Mac PowerBook, but I still can't do anything. I installed samba, set up an account with a password, set up a folder to share, etc. But whenever I try to connect to the Ubuntu machine from the Mac, I get an Error -36 message. According to Apple support, this can happen if the password is not encrypted, but if that is not the reason (which it is not in this case) then all they say is to do the usual troubleshooting. So I am at a total loss...

---

### Post by shanesaysno on 2006-07-05
I was having the same problem. I fixed it with a program called [Sharepoints]("http://www.hornware.com/sharepoints/") for  my OS X computer. I used the program to create a share (directory /Users/Shared, if you want to use your regular OS X shared folder) and enabled SMB sharing for it. The folder showed up in Ubuntu then, and I could copy files over without any problems.

---

### Post by xkiddiegrinders on 2006-07-17
wow I was having big troubles trying to share with my mac and that Sharepoints program fixed everything! Awesome, and also, thank you.

---

