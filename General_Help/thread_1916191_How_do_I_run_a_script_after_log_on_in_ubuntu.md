---
title: "How do I run a script after log on in ubuntu?"
date: 2012-01-27
forum: General Help
---

### Post by chrisgreg on 2012-01-27
Hi, I'm not sure where the best place to put this is, but hopefully you guys can help.

I  have set up a laptop with ubuntu, linked to server with nfs and set up  MPD. This all works great, but the problem is on startup the NFS drive  tries to mount at boot up, but the wireless doesn't connect until I log  in, at which point the NFS isn't mounted and then MPD stalls. I have to  manually re-mount and restart MPD. To start with I have written a script  to mount the nfs drive after the network is up, I plan on adding a  command to start the MPD after I figure out how, 

What I would like to know is how to get this script to run after I log  in and after everything else has started. I have been reading forums for  a few days trying to figure it out but I just ended up getting really  confused.

My understanding so far, place script.sh in /etc/profile.d, make it  executable for all, then run update-rc.d default Is this correct? When I  run the script manually it needs root, is this because I havent used  the correct chmod command? I used chmod +x.

From reading another post on NFS mounting I know that there is another  way to get the drive to mount after network is up, but I would like to  get the script to run anyway and I'm not sure if this method would work  with wireless. 

Thanks in advance if anybody is able to point me in the right direction.

---

### Post by Lars Noodén on 2012-01-27
The script in /etc/profile.d gets run as your account.  So if you need root privileges for mounting a drive you'll need to set up a special line in [sudoers](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html).

---

### Post by chrisgreg on 2012-01-27
so if I put the script in etc/profile.d, run update-rc.d , and add a line into sudoers this should work on login? Or is there a better place to put this?

---

### Post by Lars Noodén on 2012-01-28
[update-rc.d](http://manpages.ubuntu.com/manpages/oneiric/en/man8/update-rc.d.8.html) is not needed if the script is in [font=Courier New]/etc/profile.d/[/font].  But yes, if you put your script there and then add the appropriate lines to sudo (with NOPASSWD) the script will run.

Alternately, if you want the script to run when the system starts and before the user logs in, you can put it in [font=Courier New]/etc/rc.local[/font].  There it will by default run as root.

---

