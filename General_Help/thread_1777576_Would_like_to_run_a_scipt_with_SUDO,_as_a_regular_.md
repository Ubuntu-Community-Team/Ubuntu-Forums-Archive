---
title: "Would like to run a scipt with SUDO, as a regular user"
date: 2011-06-07
forum: General Help
---

### Post by themnotme on 2011-06-07
Hello Everyone,

 Been a long time since i've had to post here. But after several days of failure i'm hoping i can find a resolution here.
 Long story short. Upgraded to 11.04 and was having an issue with my digital came not working. A workaround was using the "sudo killall gvfs-gphoto2-volume-monitor" command in terminal. 
 Anyways i decided to try making a shell script with that, put it "sudo killall gvfs-gphoto2-volume-monitor" into a text editor and saved it as byebye.sh. Seems to work when i'm logged in as the admin. 
 Here's were the fun begins.. i also have a regular user account that i use for normal day stuff. I would like to be able to run that script from that account but don't want to give the account total SUDO privileges. I tried adding some line to SUDOERS file but have failed miserably. Had to log into the recovery counsel to fix my mistakes :)
 Anyone got a suggestion what i could add to the SUDOERS file to allow my to run that file? I have it saved in my regular users home directory under a dir called batch - /home/(user name)/batch/byebye.sh.
Tried (user name) ALL= /home/(user name)/batch/byebye.sh but that didn't seem to work. When i tried running the script in the terminal is was getting an message i can't run /usr/bin/sudo killall gvfs-gphoto2-volume-monitor as root.
 Do i have to also add /usr/bin to the SUDOERS file also? And if i do would that allow me to run killall commands on anything?

  Sorry for the long post and if i overlooked adding anything. Several days with little sleep has made me abit loopey.

 TIA for any help or suggestions

---

### Post by Junkieman on 2011-06-08
Hi there. 

Well I guess you can [edit the sudoers file]("https://help.ubuntu.com/community/Sudoers") properly to include the user to sudo, or you also [try this long-term fix #2]("http://www.ubuntugeek.com/some-of-known-ubuntu-904jaunty-jackalope-bugs-with-workarounds.html"). Hope that helps :)

---

### Post by themnotme on 2011-06-08
> **Junkieman said:**
> Hi there. 

Well I guess you can [edit the sudoers file]("https://help.ubuntu.com/community/Sudoers") properly to include the user to sudo,

 True.. i could easily add that user via the user/group GUI to the SUDO group, and also remove him when done. But i'm trying to get the hang of just granting SUDO permission for certain files/services.
 

>  or you also [try this long-term fix #2]("http://www.ubuntugeek.com/some-of-known-ubuntu-904jaunty-jackalope-bugs-with-workarounds.html"). Hope that helps :)

I saw that fix when i was poking around for the solution. Thats how i found the work around. But i don't know if any other programs i use also rely on that service. So i hate to crush it permanently and then have further issues.

 Thanks very much your suggestions and for taking the time to reply. I do appreciate it. :)

---

