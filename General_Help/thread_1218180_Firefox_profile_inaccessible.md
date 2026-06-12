---
title: "Firefox profile inaccessible"
date: 2009-07-20
forum: General Help
---

### Post by Ziege on 2009-07-20
I'm a brand new user, first post.  Installed Ubuntu two weeks ago and I am NOT missing the legacy operating system at all.  I am doing my best to get the most out of Linux, and have been tinkering around a little.  I decided I wanted a script that opened firefox and then opened the sites that I use constantly in tabs.  I looked up a little bit about bash scripting, and tried this:

#!/bin/bash
firefox [http://mail.mycompany.com](http://mail.mycompany.com)
firefox [http://www.pandora.com](http://www.pandora.com)
firefox [http://gmail.com](http://gmail.com)

I saved this to my desktop as open_firefox.sh.  Then in terminal I ran:  chmod +x open_firefox.sh.  Then I ran the script, but it didn't work.  I figured, heck with it, I'll read up on bash scripting and try again later.

But now, when I open firefox all my bookmarks are gone; looks like it's not opening to my profile.  I tried opening from terminal with sudo and everything is there.  I don't really want to have to open firefox that way, though, and I'm wondering what I did wrong.

---

### Post by semafor on 2009-07-20
What profile does it open? Close firefox and run ```
firefox -profilemanager
``` to see what profiles are defined.

---

### Post by y-lee on 2009-07-20
Check the permissions of ~/.mozilla/ and ~/.mozilla/firefox/ folders. If root owns these folders, then Firefox will not work properly unless opened as root.

To change the permission back to normal run this command:


```
sudo chown -R $USER:$USER ~/.mozilla

```


And btw note never open firefox as root using sudo.

---

### Post by Ziege on 2009-07-20
> Check the permissions of ~/.mozilla/ and ~/.mozilla/firefox/ folders. If root owns these folders, then Firefox will not work properly unless opened as root.



That worked!  Thank you.  I'll read up on bash scripts before I try again....I'd love to know how what I did changed permissions....

---

### Post by y-lee on 2009-07-20
Gnome users should always use **gksudo firefox** if you need to launch firefox as root, read [Running Sudo Graphically]("http://www.psychocats.net/ubuntu/graphicalsudo").

> **Ziege said:**
> That worked!  Thank you.  I'll read up on bash scripts before I try again....I'd love to know how what I did changed permissions....

Glad to be of help :D

My guess is somewhere along the line you launched firefox using sudo. That seems to be a very common problem on these forums as I have answered quite a few posts where ppl had the same problem.

---

### Post by lovinglinux on 2009-07-21
> **Ziege said:**
> That worked!  Thank you.  I'll read up on bash scripts before I try again....I'd love to know how what I did changed permissions....

When you use gksudo it's starts Firefox with administrative rights, but uses the root Firefox profiles, while sudo uses the user profiles, thus messing with the permission and preventing regular users from loading their profiles correctly.

For future reference, this is described in the **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001). As **y-lee** mentioned, this is a very common problem.

---

### Post by bronxbomberz41 on 2009-08-20
> **y-lee said:**
> Check the permissions of ~/.mozilla/ and ~/.mozilla/firefox/ folders. If root owns these folders, then Firefox will not work properly unless opened as root.

To change the permission back to normal run this command:


```
sudo chown -R $USER:$USER ~/.mozilla

```


And btw note never open firefox as root using sudo.


I have tried this and i get the following message in the terminal

```
$ sudo chown -R $brian$brian ~/.mozilla
chown: missing operand after `/home/brian/.mozilla'
Try `chown --help' for more information.

```

I can open however "shiretoko" and it runs as firefox just fine.  I looked at the troubleshooting guide and none of the things on there helped me out.

---

### Post by michy99 on 2009-08-20
Assuming your username is brian, it would be```
sudo chown -R brian:brian ~/.mozilla
```

---

### Post by lovinglinux on 2009-08-20
You have replaced USER, which is a variable and shouldn't be edited. The system will replace $USER for you, with your real user name. Run that code as it is, without changing a single letter or use the one from the post above. You can use:

```
sudo chown -R $USER:$USER ~/.mozilla
```

or

```
sudo chown -R brian:brian ~/.mozilla
```

but NOT **$brian**

---

### Post by bronxbomberz41 on 2009-08-21
OK.  I'll try it this afternoon after work and repost.  Thanks for clarifying

---

