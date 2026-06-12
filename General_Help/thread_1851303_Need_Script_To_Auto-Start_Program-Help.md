---
title: "Need Script To Auto-Start Program?-Help"
date: 2011-09-28
forum: General Help
---

### Post by Return Privacy on 2011-09-28
Hi All,
Can someone please help me with some kind of script (I don't know how to do them) to make FileZilla FTP Server start automatically when Ubuntu (10.04) boots up? I have FileZilla running under Wine, and it won't come on when the machine boots, even though I added it to the currently running preference thing to start all currently running programs. I guess it's because it runs under Wine? 
I know you will probably say I should just use Proftpd, and I did try that, but I could never get it to work, even with Gadmin. So, I am using FileZilla FTP server under Wine, and it works pretty good, but if the power goes out and the machine re-boots, FileZilla FTP server and wine do NOT come back on, and I loose my FTP server. I know it's not ideal, but I need a script or something to tell Wine and FileZilla Server to start automatically when Ubuntu boots up. Thank you in advance for your help.
-RP

---

### Post by hal8000 on 2011-09-28
One way of doing this is to create a bash script:

#!/bin/bash
wine  filezilla

You need to find the exact command to start filezilla. Save it as
filezillastart.sh and make it executable.

Test your script from the terminal first, then you can add it to Gnome Autostart
[http://www.ghacks.net/2009/04/08/add-an-application-to-gnomes-autostart/](http://www.ghacks.net/2009/04/08/add-an-application-to-gnomes-autostart/)

---

### Post by Return Privacy on 2011-09-30
That sounds good, but I don't really understand how to do this?
I looked in the properties of FileZilla when it is running and found
env WINEPRFIX="/home/ubuntu10/.wine" wine C:\\Program\Files\\FileZilla\Server\\FileZilla\Server\interface.exe
I copied and pasted that and put it in Startup application Preferences
as an additional startup program. Now when Ubuntu boots up, it trys to 
load FileZilla, but when FileZilla opens, it says it is trying to connect to the
server, can't, then tries every 5 seconds for a minute or so, then times out
and says the FileZilla server isn't connected and stops.
I'm thinking it is trying to start too quickly, and needs to wait until Ubuntu
is fully booted up before starting FileZilla? 
Is there a way to have FileZilla wait until Ubuntu is fully booted up and 
then launch FileZilla automatically? The reason I am doing this is because
if the power goes out, and then comes back on, and I'm not there, I loose
my FTP server. That's why I need Wine & FileZilla to autostart on bootup,
for those times when I'm not home and there is a re-boot.

---

