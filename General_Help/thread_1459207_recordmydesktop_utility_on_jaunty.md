---
title: "recordmydesktop utility on jaunty"
date: 2010-04-21
forum: General Help
---

### Post by Stonerz on 2010-04-21
I need to video screen capture a linux system on jaunty at work. I have been working with recordmydesktop and it works really well and is so configurable. The only problem is that I cannot get it to run on system boot or as a cron job.

I have written a bash script which reads if directory exists and creates if not, then cds into directory and calls the recordmydesktop command which records the video with date,time filename. If I execute this command through bash using either sh filename.sh or ./filename.sh everything runs fine. So, I have then tried to run the script from /etc/init.d and run update-rc.d filename.sh defaults so it initialises at startup but it does not work. I can type sudo /etc/init.d/scriptname start in bash and the process starts. Also tried placing the script in the RC*.d folders with S** prefix but this does not work and called the script from rc.local but no joy.

Next, I tried running a cron job for it, crontab -e and added 
@reboot 'path-to-script' . This carried out the first part of the job in so much that the folder was created but then the recordmydesktop command was not triggered. 

Next, I tried to place the command in the startup apps and manually created the folder, again this does not run. If I hit alt-F2 and enter the command with or without run through terminal checked recordmydesktop will not run. 

If I make the sh file executable and double click it, it runs perfectly

Am I simply asking recordmydesktop to do something that it cannot do? I am hoping that there is someone who has experience of recordmydesktop and can help me with this issue with either a work around or a reason why it will only run if the command is executed through bash. Also, suggestions of other software that could be used would be good.

Any help would be much appreciated

---

