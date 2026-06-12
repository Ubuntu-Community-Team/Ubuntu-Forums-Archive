---
title: "tinychat.com"
date: 2009-07-29
forum: General Help
---

### Post by fcuk112 on 2009-07-29
has anyone had any success getting tinychat to work with ubuntu?  i have a logitech 4000 and an external microphone, neither of which seem to function properly within tinychat.

---

### Post by 3rdalbum on 2009-10-02
> **booyabazooka said:**
> Hate to be redundant, but... bump! Failures like these are a great embarrassment to linux in the popular eye.

It might be, if anyone used Tinychat.com apart from the three people who posted here :-)

I can use my webcam on other Flash-based websites, but not on this Tinychat. In addition, the error message "You didn't set up your camera" keeps appearing; I can't get rid of it. This is a great embarrassment to Tinychat.com for providing a buggy service.

---

### Post by to_lazy_to_fix_it_right on 2009-10-02
Solution = [https://help.ubuntu.com/community/Webcam#Fixing%20Webcam%20issues%20while%20using%20Flash%20since%20Intrepid]("https://help.ubuntu.com/community/Webcam#Fixing%20Webcam%20issues%20while%20using%20Flash%20since%20Intrepid")


**Fixing Webcam issues while using Flash since Intrepid**

 
In Ubuntu Hardy you were used to be asked to grant permission to the website you were visiting to take control on your webcam (through some flash popup with the settings). It seems that recent versions of Adobe flash player (the updated ones for Intrepid and Jaunty since June 2009, at least, and probably before also) have a bug which doesn't ask the user to grant access to a site when visiting it. Like ustream.tv for streaming using your webcam, as example. 

The workaround is to grant access to that website by default without attempting to ask you each time. 
* You need to go to: [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html) 
* Choose the "Website privacy settings" * Select the site from the list of visited websites. * click on the option "always allow" above the list. 
You should see that the icon on the left of that site in the list changes from yellowish to green colour. That's it. 
Try again visiting that website, ustream.tv in this example, and your webcam should be streaming again as it used to do back with Hardy. 
Enjoy! [IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/smile.png[/IMG]

---

### Post by ethos101 on 2009-10-03
I got it working, cam AND mic.  I'll post what I did as a sort of guide.  Hopefully more people can find this usefull.

Here's what I did: (after troubleshooting my mic)

1 - Install vloopback device
2 - Install webcamstudio
  *steps 1 and 2 details here: [http://www.ws4gl.org/installing-on-ubuntu](http://www.ws4gl.org/installing-on-ubuntu)
3 - Add group "video" and put my user in that group (this is the critical part)
Make sure /dev/videoX and /dev/videoY are in the video group:

ls -l /dev/video*

The output should read rw-rw---- root video (bla bla bla) /dev/video0
...root is owner and video is group... good.

Add video group:
The GUI way:

     >System>Administration>UsersAndGroups
     Unlock > enter root password
     AddGroup > video
     click video group > properties
     check box next to your user name

That should be it.  After you install vloopback drivers the loopback device isn't accessible until you add permission for your user to access devices owned by the "video" group.  In my case I also had to add the video group.

You can probably tell I'm not a guru but if you have problems I'll try to help.

:edit:
So I just did this on my laptop too.  I had to add /dev/video* to the video group for whatever reason.  (diff version?)
sudo grpadd video /dev/video*
I also had to restart X server for the useradd to the video group to take effect.

---

### Post by booyabazooka on 2009-10-03
Thanks for the responses.

to_lazy_to_fix_it_right's advice seems to have gotten me past the first hurdle - The permissions problem is taken care of.

My webcam does show up properly in the camera selection screen, but then it turns off when I actually start broadcasting.  ethos101, is this what your instructions fix?

---

### Post by EGadZooks on 2009-10-03
Yeah, got the first hurdle out of the way with the permissions, but in tinychat the preview thumbnail of my camera (Logitech QuickCam Communicate STX  usbid: 046d:08ad) is wack and broadcasting doesn't work.

Ethos101, I went through your instructions, even created the new group with me as a user, and I dont know how to get tinychat to act any differently.  It may be that I dont know what the loopback is for/does or how to use that, whats that all about?  Also what are the steps to take to get tinychat (or anything for that matter) to recognize a new 'webcam' source, say if I wanted to broadcast my desktop using webcamstudio.

(also as a side note, if you guys can point me in the right direction regarding getting the microphone that is built into my cam to be recognized that would be great, though I think the only drivers for my cam only work with the video.  Another idea would be to run a virtual box with windows, but I dont know how to pass the cam to virtual box)

Thank you in advance :OD

---

### Post by ethos101 on 2009-10-03
> **booyabazooka said:**
> Thanks for the responses.

to_lazy_to_fix_it_right's advice seems to have gotten me past the first hurdle - The permissions problem is taken care of.

My webcam does show up properly in the camera selection screen, but then it turns off when I actually start broadcasting.  ethos101, is this what your instructions fix?

I was getting the webcam video just fine as well but turning off when broadcast starts.  What you want to broadcast is the vloopback device.  Webcamstudio inputs your webcam and outputs to vloopback similar to how manycam works for windows (hit broadcast and pick manycam instead of your webcam).

I wasn't getting the vloopback device option in output in webcamstudio until I discovered running it as root would automatically detect the output as vloopback.  So I put all video devices in "video" group and added my user to "video" group.  Now when I start it it uses the vloopback device for output.

Then I started firefox as root and was able to see the vloopback device too.  Pick that and broadcast away.  :D

So you see the trick is to get the vloopback device as output for manycam and input for firefox app.  I just had to put my user in the same group as the vloopback device and make sure it had group RW permissions.  (probably only need R)

@egads: show me what this outputs:
ls -l /dev/video*
then this too:
groups

---

### Post by EGadZooks on 2009-10-04
Thank you Ethos101 for being awesome.  Didnt think to start firefox as root either.  Dont quite understand putting all video devices into the video group.  (is a video device the file found in /dev?)

ls -l /dev/video*

crw-rw----+ 1 root 44 81, 0 2009-10-03 11:52 /dev/video0
crw-rw----  1 root 44 81, 1 2009-10-03 12:44 /dev/video1
crw-rw----  1 root 44 81, 2 2009-10-03 12:44 /dev/video2


groups
jack adm dialout cdrom plugdev lpadmin admin sambashare
(im jack btw)

huh, thats not right, where is the video group?  I did the gui way of adding it...i'll look into this right now.  Know any sites that teach young padawan's how to create and manage groups?  (I know about WRX permissions already with chmod)

Thank you again :OD

---

### Post by EGadZooks on 2009-10-04
well under System> Administration> Users and Groups> Manage Groups thar be a video group, and I am a check marked group member.  Group ID 1002.  Yet when I run groups it still doesn't show video as a group that I belong to.  weird.  I'll keep hacking at it.  Thanks for your help sirs :OD

---

### Post by ethos101 on 2009-10-04
Try this, your device isn't in the video group yet.
sudo chgrp root:video /dev/video*

Then reboot, I dont think your user account accepts the group addition until you reboot.  I had that problem with my laptop.

---

### Post by EGadZooks on 2009-10-04
Got it to work.  Firefox wasnt running as root, so now I can export out of webcam studio and into firefox.  Thank you for your help Ethos101

---

### Post by booyabazooka on 2009-10-04
Um... yeah, I don't think I'll ever be letting Firefox run as root.

Surely there is some permission change that can be made to avoid this?

---

### Post by ethos101 on 2009-10-05
> **EGadZooks said:**
> 
crw-rw----+ 1 root 44 81, 0 2009-10-03 11:52 /dev/video0
crw-rw----  1 root 44 81, 1 2009-10-03 12:44 /dev/video1
crw-rw----  1 root 44 81, 2 2009-10-03 12:44 /dev/video2


Your video devices aren't in a specific group.  Do this:

sudo chgrp root:video /dev/video*

Then this: (replace "user" with your users name)

sudo usermod -G video user

That will do it so you don't have to start webcamstudio or firefox as root which would be a serious security risk.

---

### Post by nix-idioteque on 2009-10-06
ok, so I did this step by step and it seemed to work, but upon rebooting I seemed to have lost my sudo permissions for my default name (the only username too)  can anyone help me with this?  It won't let me access my users and group settings...  

When I added the group 'video' I may have clicked root and joel (username)..  Is there any commands that can fix this?  I'm a bit rusty with linux

---

### Post by ethos101 on 2009-10-07
> **nix-idioteque said:**
> ok, so I did this step by step and it seemed to work, but upon rebooting I seemed to have lost my sudo permissions for my default name (the only username too)  can anyone help me with this?  It won't let me access my users and group settings...  

When I added the group 'video' I may have clicked root and joel (username)..  Is there any commands that can fix this?  I'm a bit rusty with linux

Since you can't sudo to fix it anyways, you're going to have to log into the root account.  Login as root from the GDM.  Then:
adduser joel admin
Logout and login as joel and you should be able to sudo.  I may be wrong.  I'm rusty too.

Clicking those boxes didn't strip you're sudo privileges. That's what you were supposed to do.

---

### Post by nix-idioteque on 2009-10-08
> **ethos101 said:**
> Your video devices aren't in a specific group.  Do this:

sudo chgrp root:video /dev/video*

Then this: (replace "user" with your users name)

sudo usermod -G video user

That will do it so you don't have to start webcamstudio or firefox as root which would be a serious security risk.


I can't get sudo chgrp root:video /dev/video*  to work at all, it says, "root:video group does not exist" 

Which is odd because I'm looking at my groups now and I see it right below root...  What's going on?

---

### Post by ethos101 on 2009-10-08
The correct syntax it seems (after looking it up, lol) is:
sudo chgrp video /dev/video*

Odd that root:video worked for me and not you.  Different version maybe?
Make sure if the video group is capital (like "Video") then the chgrp should be Video as well.

---

### Post by patrickballeux on 2009-10-12
Ah that vloopback problem.  So here is how I do it, for WebcamStudio for GNU/Linux...

Once you're vloopback is installed, the next time it will be loaded, the security will be root:video.  So it means that you have to be part of the video group.

In Ubuntu 9.10, the video group already exists, but it is hidden.  The trick is to open "Users and Groups" from the System menu, unlock it, then edit properties of your user.  In one of the tabs, you'll see a list of priviliges. One of them is for capturing from webcams and tuners.  Make sure it is checked.  Save everyting.

Now you have to quit your session and login again so the access will be granted.

No need to run Firefox as root or any other software.

That's it!

Patrick

---

### Post by TripEEEmily on 2010-03-10
I know this thread is kind of old, but after a week or two of tinkering I was finally able to get my cam working with tinychat.

Like many others, I was having trouble getting the cam to stay on after it was selected in tinychat's preview window.  I found that by unplugging and replugging my webcam (Microsoft Lifecam v700) before opening WebCamStudio, I could finally get things outputting to vloopback.  The trouble then, was that tinychat was still getting this garbled, deinterlaced mess on vloopback.  So in WebCamStudio, I started tinkering with different output resolutions, and eventually discovered I could get the video to display normally with an output res on vloopback of 160*120.  So, the input (/dev/video0) is 640*480, and the output is 160*120.  It isn't the prettiest, but it's serviceable.

I'm going to continue to tinker and see if I can get higher output resolutions to work.  Hope this helps someone.  YMMV.

---

### Post by MissCocoGold on 2010-03-31
I probably won't get a reply but I figured, hey, it's worth a try. So when I broadcast for tinychat, everything goes fine up until the broadcast starts. Doesn't show a video feed, just sound. I'm still new at all this. But can anyone help? Thanks

---

### Post by mj_thug4life on 2010-04-12
read the whole post. its the solution to your problem.
i havent tried it yet.. but going to this afternoon..

---

### Post by Georges on 2010-05-14
the core problem is:

flash on linux can't resize a webcam video!
Proof:

mebeam.com: 2 person chat works. a 3rd person enters, the video images get resiuzed => your cam is stuck. Stop/start browser makes it work.

tinichat.com: the camera seletion shows a small preview. after enabling broadcasting it's sending a bigger sized stream => you cam is stuck. No solution as you always have to go through the thumbnail selection! Why does the vloopback cludge work? Probably because vloopback output is not resizable and flash simply takes what it gets.

Here is the adobe bug:
[https://bugs.adobe.com/jira/browse/FP-2692](https://bugs.adobe.com/jira/browse/FP-2692)

Another bug sys: install newest beta of flashplayer! And it works.
[https://bugs.adobe.com/jira/browse/FP-4126](https://bugs.adobe.com/jira/browse/FP-4126)
I just overwrote the library.

So go and download on this page the RC4 of 10.1
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

Direct link: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc4_linux_050510.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc4_linux_050510.tar.gz)

open a shell and go to your download directory (eg the desktop):

```

cd Desktop 
tar xvzf flashplayer10_1_rc4_linux_050510.tar.gz
sudo cp -p libflashplayer.so /usr/lib/flashplugin-installer/libflashplayer.so

```
restart firefox.
Go to this url: ```
about:plugins
```
and verify that it's now "10.1 r53"

Enjoy tinychat and many more video conferencing websites without unexplained lockups.

---

### Post by ZazzyE on 2010-05-17
Uh, my mic isn't working with Tinychat.  Well, I've been trying this, but nothing seems to be working.  I've played with pulseaudio preferences, alsa, flash, installed stuff for a webcam I don't have... still nothing.And that didn't install the new flash player, just put it in a nice new directory.

---

### Post by Mark Rose on 2010-06-03
I also replaced flash with the beta and it worked. Note that the beta is at rc7 now; that link to rc4 is old.

And the file to replace with the file from the download is located at /usr/lib/flashplugin-installer/

---

### Post by cain071546 on 2011-03-04
this helped me soooooooooooo much 



BUMP!

---

### Post by cain071546 on 2011-03-04
i got the cam workin still no mic but im workin on it

---

### Post by _____ on 2011-03-14
> **to_lazy_to_fix_it_right said:**
> Solution = [https://help.ubuntu.com/community/Webcam#Fixing%20Webcam%20issues%20while%20using%20Flash%20since%20Intrepid](https://help.ubuntu.com/community/Webcam#Fixing%20Webcam%20issues%20while%20using%20Flash%20since%20Intrepid)


**Fixing Webcam issues while using Flash since Intrepid**

 
In Ubuntu Hardy you were used to be asked to grant permission to the website you were visiting to take control on your webcam (through some flash popup with the settings). It seems that recent versions of Adobe flash player (the updated ones for Intrepid and Jaunty since June 2009, at least, and probably before also) have a bug which doesn't ask the user to grant access to a site when visiting it. Like ustream.tv for streaming using your webcam, as example. 

The workaround is to grant access to that website by default without attempting to ask you each time. 
* You need to go to: [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html) 
* Choose the "Website privacy settings" * Select the site from the list of visited websites. * click on the option "always allow" above the list. 
You should see that the icon on the left of that site in the list changes from yellowish to green colour. That's it. 
Try again visiting that website, ustream.tv in this example, and your webcam should be streaming again as it used to do back with Hardy. 
Enjoy! [IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/smile.png[/IMG]

I did this in 10.10 and it worked for tinychat. Thanks! I also downloaded vloopback for good measure and everything is working.

---

