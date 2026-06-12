---
title: "Changing login sound - Natty Narwhal  (total noob)"
date: 2011-07-08
forum: General Help
---

### Post by RogueGrendel on 2011-07-08
Hello everybody.

I have recently installed ubuntu on an old Dell Optiplex GX280.

I am finding the learning curve a little steep, but this forum has resolved a lot of issues for me just by searching and judicious use of copy & paste.

One of the reasons I chose to move to linux was the customising options available and I was hoping to set up a simple minimal but personalised desktop, however, my inexperience is letting me down.

I have searched for this topic and attempted to follow the instructions but to no avail so I am now looking for some one to one help.

_**SUMMARY OF STEPS SO FAR AND PROBLEM ENCOUNTERED**_

I found out that I need to either replace or add a new sound file to:
File System > usr/share/sound

I then found out i needed to login with root permission to change files in that folder so I did that.

Everything went fine, new sound files added, and while in root I could preview the sounds by mousing over the files.

But when I restart and login as normal, no sounds play at login.

Sounds in general are working, because when I enabled window and menu sounds I get the normal beeps and stuff.

However, when I go into File System > usr/share/sound/ubuntu the files are showing with an x (error icon), is there a file size limit or have I just missed out a step?

Any advice would be greatly appreciated.
Thanks in advance.

---

### Post by e79 on 2011-07-08
I think that this post (from 10.04 version ) should still work in your case, it's about editing the 'Startup Application' to replace the 'desktop-login' file with your own .mp3.
 
[http://ubuntuforums.org/showthread.php?t=1520547](http://ubuntuforums.org/showthread.php?t=1520547)
 
Hope this helps

---

### Post by ruffEdgz on 2011-07-08
Have some questions:

* What version of Ubuntu are you using?
```

cat /etc/lsb-release

```
**If you are using 11.04**
* Can you perform the following command and post the results here?
```

sudo cat /usr/share/sounds/ubuntu/index.theme

```
```

ls -l /usr/share/sounds/ubuntu/

ls -l /usr/share/sounds/ubuntu/stereo/

```

Cheers!

---

### Post by RogueGrendel on 2011-07-08
Thanks very much you are top people.

_**[ruffEdgz]("http://ubuntuforums.org/member.php?u=147600")**_

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
pete@RogueGrendel:~$ 


[Sound Theme]
Name=Ubuntu
Directories=stereo
[stereo]
OutputProfile=stereo
pete@RogueGrendel:~$ 


pete@RogueGrendel:~$ ls -l /usr/share/sounds/ubuntu/
total 8
-rw-r--r-- 1 root root   76 2011-03-02 15:22 index.theme
drwxr-xr-x 2 root root 4096 2011-07-08 18:38 stereo
pete@RogueGrendel:~$ 


pete@RogueGrendel:~$ ls -l /usr/share/sounds/ubuntu/stereo/
total 392
-rw------- 1 root root 31624 2011-07-08 17:01 activating.ogg
-rw-r--r-- 1 root root  5016 2011-03-02 15:22 bell.ogg
-rw-r--r-- 1 root root  8997 2011-03-02 15:22 button-pressed.ogg
-rw-r--r-- 1 root root  4035 2011-03-02 15:22 button-toggle-off.ogg
-rw-r--r-- 1 root root  4035 2011-03-02 15:22 button-toggle-on.ogg
-rw------- 1 root root 29003 2011-07-08 17:38 deploying.ogg
-rw------- 1 root root 31624 2011-07-08 17:01 desktop-login.ogg
-rw------- 1 root root 32254 2011-07-08 17:28 desktop-logout.ogg
-rw-r--r-- 1 root root 10660 2011-03-02 15:22 dialog-error.ogg
-rw-r--r-- 1 root root  5377 2011-03-02 15:22 dialog-information.ogg
-rw-r--r-- 1 root root  9851 2011-03-02 15:22 dialog-question.ogg
-rw-r--r-- 1 root root 12217 2011-03-02 15:22 dialog-warning.ogg
-rw-r--r-- 1 root root 22733 2011-03-02 15:22 message-new-instant.ogg
-rw-r--r-- 1 root root 10429 2011-03-02 15:22 message.ogg
-rw-r--r-- 1 root root 29299 2011-03-02 15:22 phone-incoming-call.ogg
-rw-r--r-- 1 root root  7996 2011-03-02 15:22 phone-outgoing-busy.ogg
-rw-r--r-- 1 root root  4792 2011-03-02 15:22 phone-outgoing-calling.ogg
-rw-r--r-- 1 root root 17274 2011-03-02 15:22 service-login.ogg
-rw-r--r-- 1 root root 14573 2011-03-02 15:22 service-logout.ogg
-rw------- 1 root root 32254 2011-07-08 17:28 shuttingdown.ogg
-rw------- 1 root root 29003 2011-07-08 17:38 system-ready.ogg
-rw-r--r-- 1 root root  6994 2011-03-02 15:22 window-slide.ogg


I really appreciate the help, thanks very much.

---

### Post by RogueGrendel on 2011-07-08
> **e79 said:**
> I think that this post (from 10.04 version ) should still work in your case, it's about editing the 'Startup Application' to replace the 'desktop-login' file with your own .mp3.
 
[http://ubuntuforums.org/showthread.php?t=1520547](http://ubuntuforums.org/showthread.php?t=1520547)
 
Hope this helps


Thanks for the help E79 but that was one of the posts i was trying to follow.
It made sense, if you swap the original file with a new one in.oog format and name it the same it should work, but alas no joy.
Cheers for looking for it though.

---

### Post by e79 on 2011-07-10
> **RogueGrendel said:**
> Thanks for the help E79 but that was one of the posts i was trying to follow.
It made sense, if you swap the original file with a new one in.oog format and name it the same it should work, but alas no joy.
Cheers for looking for it though.

I'm sorry it could not help you; I could not find anything else related; even this post speak about replaing that .ogg file :s

[http://tech.mobiletod.com/how-to-disable-or-change-login-sound-in-ubuntu-10-10/](http://tech.mobiletod.com/how-to-disable-or-change-login-sound-in-ubuntu-10-10/)

I'll keep looking and will post if I find anything.

p.s: sry for the late reply, I was away camping for the weekend :)

---

### Post by RogueGrendel on 2011-07-11
@e79

Thanks very much for your help.

I will see if I can track down an alternative sound file and try the same steps to qualify whether the sound file is the issue. Will keep you posted.

I hope you had a good weekend camping, hope the weather was good to you.

---

### Post by tredegar on 2011-07-11
From your post at #4:
```
-[COLOR="Red"]r[/COLOR]w-[COLOR="Red"]-[/COLOR]--[COLOR="Red"]-[/COLOR]-- 1 root root 31624 2011-07-08 17:01 desktop-login.ogg
```
So, only root can read that file.
To fix the permissions:
```
sudo chmod 644 /usr/share/sounds/ubuntu/stereo/*
```
Which will give permissions like this
```
-[COLOR="Red"]r[/COLOR]w-[COLOR="DarkGreen"]r[/COLOR]--[COLOR="DarkGreen"]r[/COLOR]-- 1 root root 31624 2011-07-08 17:01 desktop-login.ogg
```
then your user can read (use) the sounds.

---

### Post by ruffEdgz on 2011-07-11
> **tredegar said:**
> From your post at #4:
```
-[COLOR="Red"]r[/COLOR]w-[COLOR="Red"]-[/COLOR]--[COLOR="Red"]-[/COLOR]-- 1 root root 31624 2011-07-08 17:01 desktop-login.ogg
```
So, only root can read that file.
To fix the permissions:
```
sudo chmod 644 /usr/share/sounds/ubuntu/stereo/*
```
Which will give permissions like this
```
-[COLOR="Red"]r[/COLOR]w-[COLOR="DarkGreen"]r[/COLOR]--[COLOR="DarkGreen"]r[/COLOR]-- 1 root root 31624 2011-07-08 17:01 desktop-login.ogg
```
then your user can read (use) the sounds.

Great catch tredegar, that does look like the issue once I looked at my ogg sound files on my 11.04 Ubuntu.

My next question was to ask which file in the /usr/share/sounds/ubuntu/stereo/ do you want to play since the sound file is in the right place.

Give tredegar's suggestion a try and get back to us on how it went.

---

### Post by RogueGrendel on 2011-07-12
Woot! Woot! That has indeed fixed it!

Thanks tredegar for the solution, that was a brilliant catch and a very simple solution.
Thanks also for explaining what was wrong and what the fix was doing, it gave me a good insight into how ubuntu works.

Also thanks to everyone else who took the time to help me with this issue.
I am really impressed with the generosity of this community.

My computer now announces: "Deploying", "Activated" and "Shutting Down" in the cute voices of the turrets from Portal. :D

---

### Post by e79 on 2011-07-12
I'm glad you could fix it !  Nice job to **tredegar** since he pointed you i the right direction !

Cheers

---

