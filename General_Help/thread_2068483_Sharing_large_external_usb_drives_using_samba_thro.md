---
title: "Sharing large external usb drives using samba through my network"
date: 2012-10-09
forum: General Help
---

### Post by markrichardmanley on 2012-10-09
Hi im a Noob and i have been converting my system away from windows to Ubuntu and im loving it, learning terminals etc, i run 7 computer on my network  and i must say the ones running Ubuntu are great !.
Ive sorted out a lot of issues with audio etc and blue tooth using Google, my main machine serves the household by streaming media, my network is set up correctly, no issues, i see all my machines on my work group, which i use for ham radio purposes, but my x4 2tb usb drives which used to use windows home group show up on and off after reboots, i understand that this is a permission problem in Ubuntu and i need to tell the computer to own the drives and grant permission , some times i can connect sometimes i cant, is there a newbie way to do this ?

thanks
mark):P

---

### Post by bart.a on 2012-10-09
are you sharing your usb-drives with samba?
what does your /etc/fstab file look like?

On my server I use a windows share for backing up (long story, don't ask). But it does not automount after ar reboot.
I replaced the automount for a mount on logon.

Would that suit your needs? Check out [http://wiki.ubuntu.com/MountWindowsSharesPermanently]("http://wiki.ubuntu.com/MountWindowsSharesPermanently")
 and point to mount directory of your usb-drive.

[B]Mount during login instead of boot
If for some reason (networking problems for example) the automatic mounting during boot doesn't work, you can add the "noauto" parameter to your smbfs fstab entry and then have the share mounted at login.[/B]

In /etc/fstab:

//servername/sharename  /media/windowsshare  cifs  noauto,credentials=/home/ubuntuusername/.smbpasswd  0  0

In /etc/rc.local:

mount /media/windowsshare
exit 0

Please let me know if it worked for you..

---

### Post by Statia on 2012-10-09
This might be a useful link too:

[http://ubuntuforums.org/showthread.php?t=1169149&highlight=hostnames+network](http://ubuntuforums.org/showthread.php?t=1169149&highlight=hostnames+network)

I have an external drive that is connected to my router via USB.
I have it in my fstab so it gets mounted at boot.
That looks something like:

```
//router_hostname/path  /mnt/samba  cifs noperm,guest,_netdev  0 0
```

---

### Post by bart.a on 2012-10-18
Hi mark..

Did any of the replies serve your needs?
If it did please provide feedback on what you did to solve your problem so others can benefit and mark your post as [SOLVED]

Thank you..

---

