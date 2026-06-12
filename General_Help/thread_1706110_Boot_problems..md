---
title: "Boot problems."
date: 2011-03-13
forum: General Help
---

### Post by jp1871 on 2011-03-13
I recently switched over from windows vista to the new ubuntu 10.10 maverick meerkat. it worked fine for a couple of days then i tried to install a plugin to get youtube to play fullscreen. now whenever the system boots i get three error messages after login.

1. could not update ICEauthority file /home/jamie/.ICEauthority

2. there is a problem with the configuration server (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

3. nautilus could not create the following required folders: /home/jamie/desktop, /home/jamie/.nautilus.

also when running from a live cd i can find the partition which it says is missing when i boot from the drive.

if anyone has any ideas what i can do i would be really grateful.

---

### Post by Kwijibo_Maverick_Meerkat on 2011-03-13
I don't understand what you mean by >  i tried to install a plugin to get youtube to play fullscreenI use Ubuntu Maverick every day and I play youtube fullscreen without a problem. Could you have installed malware? (I *know* linux doesn't get much malware but it is a possibility)

I don't know how to fix it (or what has gone wrong). What I suggest (although it is a pain) is to boot up a LiveCD, back up your files to USB and re-install. Sorry I couldn't be of more help.

---

### Post by jp1871 on 2011-03-13
i dont know why it didnt work. so i searched and found this link.

[http://maketecheasier.com/play-youtube-video-fullscreen-youtube-video-in-ubuntu-maverick-10-10-try-this-fix/2010/11/1](http://maketecheasier.com/play-youtube-video-fullscreen-youtube-video-in-ubuntu-maverick-10-10-try-this-fix/2010/11/1)

and followed the instructions with this code

```
 
[LIST=1]
[*]sudo mkdir /etc/adobe 
[*]echo "OverrideGPUValidation=true" >~/mms.cfg 
[*]sudo mv ~/mms.cfg /etc/adobe/
[/LIST]

```

does that make any sense to anyone?

---

### Post by oldfred on 2011-03-13
To avoid issues I ususally just install defaults and have not had any issues with videos.

It sounds like a permissions issue. /etc is a system folder and root should be the owner.

But the issues seem to be in your /home where you should be the owner and have full permissions. 

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)

Mine shows me as the owner with full permissions:

```
fred@fred-LT-A105:~$ ls -l .ICE*
-rwxrwxrw- 1 fred fred 29754 2011-03-13 09:57 .ICEauthority
fred@fred-LT-A105:~$ 

```

---

### Post by jp1871 on 2011-03-15
thanks for all the help guys. in the end i decided it would be easier for me to reinstall. with all the default settings. now everything works perfectly.

---

