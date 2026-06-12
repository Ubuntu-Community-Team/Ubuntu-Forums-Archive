---
title: "kubuntu or ubuntu"
date: 2009-10-18
forum: General Help
---

### Post by phrednj on 2009-10-18
I new to linux and have been running Ubuntu with the Gnome desktop. Recently I was trying to get several different programs to backup my cellphone contacts (one of the few things I still use Vista for). One of these was kmobiletools which tries to download the information to kaddressbook. This almost worked, kmobiletools seemed to find my phone though the USB cable and then bombs out somewhere in the sequence. 
       Anyway I thought the problem might be the programs needed something in the KDE desktop, so I installed it. This didn't work either, but now when I boot  or shutdown the computer it shows the Kbuntu splash screen even after I booted back into gnome and uninstalled the KDE desktop. This wouldn't bother me that much but what is annoying is that when the laptop goes into suspend mode it won't take my password. I can choice switch user and it informs me I'm already logged in but it still takes my password and opens the Gnome desktop. 
       I can't help but think the two incidents are related, anyone have any idea why it won't take my password after suspend?

---

### Post by bruno9779 on 2009-10-18
To fix your splash screen read [here]("http://embraceubuntu.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/").
I doubt that this will solve your suspend issue too, but it is worth a try.

To know what goes wrong with kmobiletools, run it from terminal, so when it crashes you will have an output, telling you what is missing or what else went wrong.
(this works as a general rule/practice when trying to get something to run in linux but it doesn't).

---

### Post by phrednj on 2009-10-18
Thanks you for your suggestion and link, this'll cure the minor annoyance, I'll keep looking for the suspend solution.

---

### Post by phrednj on 2009-10-18
:)I couldn't figure out how to add this to my original post, but the reply by bruno9779 fixed the splash screen. 
I found an old post (10/11/2008) by iLoveRuby in the "Desktop Environments" forum, that solved the password problem.  
"You may also need to change the group permission of /etc/shadow

have a look at the files /etc/shadow and /sbin/unix_chkpwd. The owner
should be "root" for the user, and "shadow" for the group. 

(See: [http://groups.google.com/group/linux.debian.user/browse_thread/thread/4f487ced7818487c](http://groups.google.com/group/linux.debian.user/browse_thread/thread/4f487ced7818487c))

So, the revised solution would perhaps be:

CAUSE:
/sbin/unix_chkpwd and /etc/shadow have wrong group/permissions

SOLUTION:
chown root:shadow /sbin/unix_chkpwd
chmod 2755 /sbin/unix_chkpwd
chown root:shadow /etc/shadow"

this sudo sequence fixed my password problem in Jaunty Jackolope.

   iLoveRuby

---

