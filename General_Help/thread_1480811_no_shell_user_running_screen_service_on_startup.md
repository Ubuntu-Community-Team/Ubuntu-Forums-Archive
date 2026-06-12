---
title: "no shell user running screen service on startup"
date: 2010-05-11
forum: General Help
---

### Post by skidz on 2010-05-11
Hi all, still pretty new to Linux, and Ubuntu.. but getting there.. 

I am trying to run mono application at boot up.. 
Steps I have taken.. 
1) created a new no shell user: sudo adduser --shell /bin/false mydaemon
2) moved the application to his home directory
3) changed ownership and group on application directory: sudo chown -R mydaemon.mydaemon appfolder
4) changed the permissions on application directory: chmod -R 775 appfolder
5) double checked everything with: ls -l
6) in home directory made a script ".screenrc" and added:
    multiuser on
    acladd root, skidz, mydaemon
7) I have a perl script that can open the screen later as well
8 ) in the application directory I made a script to launch the mono application "applicationstartserver.sh"
    /usr/bin/screen -S Application-service -d -m -U mono Application.exe
9) added the following line to /etc/rc.local
    /bin/su -s /bin/bash -c /home/mydaemon/appfolder/applicationstartserver.sh mydaemon

It never runs at startup... and even if I run the command I placed in rc.local it will not start.. 

But, when I switch it over to me as the user.. skidz (myself).. it works! 
     /bin/su -s /bin/bash -c /home/skidz/appfolder/applicationstartserver.sh skidz

If I save that to rc.local.. it comes on at start up.. 

any ideas why the noshell user won't work? I know it has to be something simple that I am overlooking..

Thanks a bunch a head of time..

---

