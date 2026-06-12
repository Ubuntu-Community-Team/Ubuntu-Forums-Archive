---
title: "Remove the System Information Banner in MOTD"
date: 2010-04-07
forum: General Help
---

### Post by GMU_ninja on 2010-04-07
Dear Ubuntu Development Team:

Thank you for creating a very user friendly and powerful Linux distribution.  I have been a long time user of both desktop and server.  However, a recent addition has caused me much torment.

Whenever I log into the system, it hangs for a few seconds while it grabs the system information and then displays it to me as such:

```
Linux virt-serv 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

  System information as of Wed Apr  7 11:01:14 EDT 2010

  System load: 0.0               Memory usage: 8%   Processes:       75
  Usage of /:  12.0% of 7.49GB   Swap usage:   0%   Users logged in: 0

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Wed Apr  7 10:30:46 2010 from 192.168.100.100
```

I am sure you all had good intentions in adding this "feature" but for many of us, we:
a)  don't use the server heavily and have no need to view the information every time we log in.
b)  have no need or desire to pay to graph this data for one seldom used server.
c)  would like to log into their system and get to work as quickly as possible.

Therefore, we would like to remove this banner and not have our system check the server information and simply log into our system immediately, without delay.

**How do I disable/remove/destroy it?**

Thanks in advance!

---

### Post by gmargo on 2010-04-07
That irritates the heck out of me too.  It is controlled by the "pam_motd" module.  You can disable the motd display (and potential delay) by editing these two files: /etc/pam.d/login, /etc/pam.d/sshd, and comment out the line that has "pam_motd" in it.  I only tested the secure shell change since gdm is running, but it worked.  Tested on Lucid Beta.

---

### Post by enorlin on 2010-04-25
I was just trying to fix this too, after being annoyed with it for a while. I ended up just making the scripts in /etc/update-motd.d not executable. Seems to have worked. 

So:
```
cd /etc/update-motd.d/
chmod 600 *
```

---

### Post by GMU_ninja on 2010-04-25
Hey,

Making the script's executable status isn't a very good solution because it (should) be generating errors.  If not visible to you, it should be somewhere.

I have not tried modifing the pam modules, but it sounds like it should work.  Although, it is a very complicated solution to a simple issue.  I think that future versions of Ubuntu should not have this 'feature' or at the least, have a way to easily disable it (thinking a quick script to enable/disable it).

Just my thoughts.  Thanks for the input!

---

### Post by dowdberry on 2010-05-11
```
apt-get remove --purge landscape-common
```

or alternatively, perhaps go through and change the settings:

```
dpkg-reconfigure landscape-common
```

---

### Post by GMU_ninja on 2010-05-11
AWESOME!  That is exactly the information I was looking for!

Thank you dowdberry for your simple solution!

---

### Post by tekkamanendless on 2011-04-09
Thank you for this little gem.  I find it extremely useful to disable the "system information" message on all of my boxes, especially my desktops.  There is a huge chance that some program is murdering my box (flash, custom tools, test code, etc.), and if it's bad enough to freeze KDE, then I need to log in *fast* and get things fixed.  Having ubuntu try to figure out what packages it can upgrade can add minutes to a problem that is quickly escalating into a box-killer (especially since the box is probably swapping hard at this point).

---

### Post by flickerfly on 2012-11-02
Thanks for the landscape-common thing. Very handy!

There are still some things getting added in from the /etc/update-motd.d directory. If you want to really clean stuff out, you'll need to spend some time in that area.

---

