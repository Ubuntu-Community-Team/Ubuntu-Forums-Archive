---
title: "Big Problem - mounting portable hard drive - sudo gone"
date: 2011-06-17
forum: General Help
---

### Post by evilbrent on 2011-06-17
Hi, I'm having 2 problems. New user (6 months Ubuntu 10.04). I'll go from the start.

I have been using a portable hard drive /media/sdb1 to watch movies on my telly, but for some reason it's been set to a read-only filesystem by linux*. If you can help on that, that would be great, but my big problem is now that I've done something bad trying to fix it.

Now:

[LIST]
[*]sudo doesn't work. Every time I try to use sudo it either errors out or doesn't respond at all. Terminal responds "sudo: must be setuid root" to every sudo command. In GUI programs it just doesn't respond to SU commands - no password request no nothing.
[*]Sound on the computer has gone. Movies play but without sound. Clicking on sound preferences just returns "Waiting for sound system to respond". Hitting record on audacity gives "Error while opening sound device." Sorry - just found out that the Terminal can make a beep so there is some sound.
[*]I can now crash Nautilus by selecting /sdb1 (note, don't have to unclick to cause it to just vanish from the screen).
[*]the icon for Computer in nautilus is gone.
[*]the 34GB partition that I have for XP does not appear in Nautilus.
[*]ubuntu won't restart - gives two error messages: "could not update ICEauthority etc" and "problem with configuration server etc" then just returns to a login screen.
[*]program mountmanager not responding.
[*]I don't seem to be able to change user logins anymore - the power symbol in the top-right corner has vanished.
[/LIST]
I wasn't even doing anything at the time - I was running gksudo nautilus, and suddenly  it's opened up a terminal and started changing the permissions on thousands of files I didn't want it to, so I closed it, and accepted that it close the gksudo terminal. It all happened very quickly. I went back through the commands I was trying at the time and the closest thing I could find to malicious entries were

```
sudo chown brent -R *cd /

 sudo umount /media/sdb1
```I think the first one is a typo of my trying to cd/ and the 2nd one I've done a hundred times. All the other commands were ls or cd.

I've restarted the machine at the power but it boots up to this state. Please help - I'll go crazy if I can't get my hard-drive to work but I'll go crazier if I can't fix everything else back to how it was 30 minutes ago.:(:(:(

What have I done? 

How can I get superuser access back?

How can I get my sound device and other partition back?


----
*mount output is ```
/dev/sdb1 on /media/sdb1 type vfat  (rw,noexec,nosuid,nodev,user=brent) 
``` - the files are writeable, but  the filesystem is read-only. Drive works fine on a windows computer,  but I can't write to it on this computer at home. I think it was kicked  while I was logged on as a different user. I've worked on it for hours  and hours.

This sounds lame but we live in a very small country town and what we do for entertainment 5 nights a week is download shows and watch them after the kids go to bed. Lack of hard-drive is causing serious marital discord! :(

---

