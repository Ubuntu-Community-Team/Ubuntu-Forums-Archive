---
title: "oh come on!? 30 minutes w8 for Network Manager?!"
date: 2010-06-12
forum: General Help
---

### Post by ognyang on 2010-06-12
Hey gyes.. 

I posted [my problem in Dell`s section]("http://ubuntuforums.org/showthread.php?t=1507179") but seems like nobody knows about this issue (except 1 person).
So this is embarrassing I have to wait about 30 minutes the stupid network manager to shows up. And by this time I can only connect via ethernet.

What can I do :(?

---

### Post by MichealH on 2010-06-12
Was there any hassle on first bootup or has it just only started doing this?

I her you have a keyring, It doesn't save, you have to enter it if you set one.

---

### Post by ognyang on 2010-06-12
> **MichealH said:**
> Was there any hassle on first bootup or has it just only started doing this?

I her you have a keyring, It doesn't save, you have to enter it if you set one.

No hassle at the beginning. I have 10.04 from a month or two but this happened couple days ago. I remember I installed some updates and putty tools because I wanted to establish an SFTP session and... here I am!

Any suggestions?

---

### Post by MichealH on 2010-06-12
It could be a bug in the patches. I have tried one time to get an app working properly and I had to make it "wait" so maybe Cannoncial have made a mistake. I think the most appropriate thing to do is file a bug report on Launchpad

---

### Post by s.fox on 2010-06-12
Hello,

Information on how to file a bug report can be found [here]("https://help.ubuntu.com/community/ReportingBugs").  Sorry can't help further.

-Silver Fox

---

### Post by ognyang on 2010-06-12
ok thanks I`ll report. But still.. if anyone has suggestions.. I`ll be here :)

---

### Post by 3rdalbum on 2010-06-12
Alt-F2 and type:

```
nm-applet
```

That usually pops it up into your Indicators if it's missing. If this command doesn't work, try actually running it in the terminal and then report back here with any error messages displayed.

---

### Post by pieroxy on 2010-06-12
I don't know if it is the same problem, but the network manager doesn't show up on my computer either. And of course, I am trying to setup a wifi card...

Anyways, the notification area doesn't show the icon and the nm-applet is running along with the NetworkManager. 

I've been on this for the last hour, removing the notification area, adding it again, I lost my volume control in the process, killing processes, rebooting, etc. No way, the network manager doesn't show up.

when I kill nm-applet and launch it in a terminal it says:

```
nm-applet --sm-disable
** (nm-applet:2423): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2423): DEBUG: old state indicates that this was not a disconnect 0

```and then it hangs

---

### Post by ognyang on 2010-06-12
> **pieroxy said:**
> I don't know if it is the same problem, but the network manager doesn't show up on my computer either. And of course, I am trying to setup a wifi card...

Anyways, the notification area doesn't show the icon and the nm-applet is running along with the NetworkManager. 

I've been on this for the last hour, removing the notification area, adding it again, I lost my volume control in the process, killing processes, rebooting, etc. No way, the network manager doesn't show up.

when I kill nm-applet and launch it in a terminal it says:

```
nm-applet --sm-disable
** (nm-applet:2423): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2423): DEBUG: old state indicates that this was not a disconnect 0

```and then it hangs

Hmm same here same here. I tried to start the applet from the menu>system>preferences, the window shows up and it freezes!
May be tomorrow  or Monday I will report for that.

---

### Post by imboe on 2010-06-13
I have the same problem with acer aspire 5315, the result of launching nm-connection-editor in terminal:
 
```
** Message: secret service operation failed: Did not receive a reply.
Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** Message: secret service operation failed: Did not receive a reply.
Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** Message: secret service operation failed: Did not receive a reply.
 Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** Message: secret service operation failed: Did not receive a reply.
 Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** Message: secret service operation failed: Activation of org.freedesktop.secrets timed out
** Message: secret service operation failed: Did not receive a reply. 
Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** Message: secret service operation failed: Did not receive a reply. 
Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** Message: secret service operation failed: Did not receive a reply. 
Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

I tried to delete all folders from ~ except some like .mozilla, .themes, images etc. Surprisingly, it worked! I had the default appearance, but connection editor began to start propertly. Well, after a while, it freezed again, don't know why. Updated recently, now going to restart and report the result.

---

### Post by robinparriath on 2010-06-13
I've been having the same problem.  I've filed a bug in Launchpad: [Bug#593363]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/593363")

---

### Post by ognyang on 2010-06-13
So here is a screenshot with the frozen window and "top":
[http://guglev.net/DATA/nm-applet.png](http://guglev.net/DATA/nm-applet.png)

I tried to start nm-applet from the terminal and here is the result:```
An instance of nm-applet is already running.

** (nm-applet:3000): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.
```

---

### Post by pieroxy on 2010-06-14
I was successful to show the Wifi icon of the network manager by plugging a Wifi USB stick in one of my USB ports AND adding manually a connection in the "Wireless" tab of the "Network Connections" window. And then when I unplug the wifi stick, the icon goes away.

---

### Post by Koppie on 2010-06-14
Launchpad bug report has the solution: [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/549332](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/549332)

If you're lazy:
>    gnome-keyring-daemon -f
     then
   nm-applet
     (enter same password as login password)

I guess this is a short-term "fix" rather than a solution.  This problem cropped up recently, probably due to a patch.  Hopefully it will get fixed soon.

---

### Post by KEE on 2010-06-16
> **Koppie said:**
> Launchpad bug report has the solution: [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/549332](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/549332)

If you're lazy:


I guess this is a short-term "fix" rather than a solution.  This problem cropped up recently, probably due to a patch.  Hopefully it will get fixed soon.
negative, ```
~$ gnome-keyring-daemon -f
GNOME_KEYRING_CONTROL=/tmp/keyring-Ungih0
SSH_AUTH_SOCK=/tmp/keyring-Ungih0/ssh
GNOME_KEYRING_PID=4214
** Message: another secret service is running

```

---

### Post by pieroxy on 2010-06-17
I think I'll wait for a fix. I was in need for the network manager only to configure a Wifi USB stick, but I got it now.

---

### Post by robinparriath on 2010-06-27
I had to give up on the auto-login to fix this.  I'm not sure if it's a bad thing.

:lolflag:

---

### Post by robinparriath on 2010-07-02
The update libgnome-keyring0 2.30.1-0ubuntu1 that was pushed yesterday has fixed it for me.
Good work Ubuntu! =D>

How about ognyang? Is it fixed for you?

---

### Post by baxna on 2010-07-02
I had the same problem a few days ago and posted a question here ([http://ubuntuforums.org/showthread.php?t=1520807](http://ubuntuforums.org/showthread.php?t=1520807)) but no one responded. It was taking 5 minutes or so, but eventually the wireless network came up. Even after it came up it was as slow as molasses in January. I fixed it by moving my data off the PC and totally reinstalling Ubuntu. "There, that'll learn ya!"

---

### Post by robinparriath on 2010-07-02
> **baxna said:**
> ... I fixed it by moving my data off the PC and totally reinstalling Ubuntu...

Just out of curiosity, was it set to auto-login when the issue popped up?  It looks like there was a problem with the authentication through gnome-keyring.
If re-installation of the OS helped, it would mean that it simply required re-installation of the gnome-keyring package.
I have to remember to check if the problem occurs again.

---

