---
title: "Adobe-flashplugin Needs To Be Reinstalled"
date: 2009-10-07
forum: General Help
---

### Post by sethmaclaren on 2009-10-07
I got this issue after upgrading to Karmic Koala. I know the problem, I downloaded and installed something for Debian, which obviously isn't too good. I've been trying for quite a while to remove this but I'm not having any luck. And please don't tell me to google it, I've done that also. All the responses are either incomplete, or they didn't work for me.

Basically, what happens is that whenever I try and install anything, or do anything that requires access to the package manager, I'm greeted with the text "The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it." Whenever I try and open Synaptic Packager Manager, I get an error box that gives me the following message...

> E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I've tried purging, removing, force-installing, etc. etc. with no success. Still get the same message saying that the archive should be reinstalled.

Thanks for the help.

---

### Post by pmains on 2009-10-07
Maybe this is a stupid question, but have you tried using dpkg? Or just the synaptic GUI?

[http://www-rohan.sdsu.edu/doc/debian/ch-dpkg.html]("http://www-rohan.sdsu.edu/doc/debian/ch-dpkg.html") might help.

Alternatively, if you've "purged" it, but it's actually still there, I would go through and manually remove all of the associated files.

---

### Post by sethmaclaren on 2009-10-07
Yeah, I've tried using dpkg. I also tried the Synaptic GUI, but that's where I get that E: Reinstall adobe-flashplugin... message. Yeah, I was thinking I'd try to remove all the associated files. I'll try that and let you know how it goes.

---

### Post by wojox on 2009-10-07
Did you try:

```
locate adobe-flashplugin | grep postinst
```

And then once you find the file remove it?

---

### Post by t0p on 2009-10-07
Try

```
sudo find / -name adobe-flashplugin*
```

This should list all the files with "adobe-flashplugin" in their names.  Then you can manually delete them.

---

### Post by sethmaclaren on 2009-10-07
> **wojox said:**
> Did you try:

```
locate adobe-flashplugin | grep postinst
```

And then once you find the file remove it?

That didn't work for me, either.

> **t0p said:**
> Try

```
sudo find / -name adobe-flashplugin*
```

This should list all the files with "adobe-flashplugin" in their names.  Then you can manually delete them.

Nor did this :/. I deleted all the files, but it didn't do anything.

---

### Post by sethmaclaren on 2009-10-08
Well, it seems that the problem is fixed.

Last night, I ran those two searches and then removed everything that was found. That didn't do anything, and I was still getting the same error. This morning, I decided to try running Update-Manager, and having it try and remove it for me. It seems to have worked this time, though I'm not particularly sure why.

Anyways, thanks or the help everyone.

---

### Post by sethmaclaren on 2009-10-11
Actually, I lied in the previous post. That fix didn't work for me. What did seem to work though is this....

First, go to /var/lib/dpkg/status and make a backup of your status file, because if it gets messed up and you don't have a backup, then you're going to be in trouble. 

Once you have that saved, run this command in the terminal: sudo gedit /var/lib/dpkg/status .

After that file is opened, search for flashplugin-nonfree or whatever it is that's causing you problems. Then, just delete the big block of code associated with this, and save the file.

After all of this is done, you should be all set and everything should be back to normal.

Hope this helps!

---

### Post by mcdjork on 2009-10-23
Thanks Seth. That worked perfectly for me.

---

### Post by jastonas on 2009-10-30
Saved my ***.... Thank you very much!

---

### Post by vijaybilgoji on 2009-10-31
Fixed the problem for me

sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin

---

### Post by marwayusuf on 2009-11-05
> **sethmaclaren said:**
> Actually, I lied in the previous post. That fix didn't work for me. What did seem to work though is this....

First, go to /var/lib/dpkg/status and make a backup of your status file, because if it gets messed up and you don't have a backup, then you're going to be in trouble. 

Once you have that saved, run this command in the terminal: sudo gedit /var/lib/dpkg/status .

After that file is opened, search for flashplugin-nonfree or whatever it is that's causing you problems. Then, just delete the big block of code associated with this, and save the file.

After all of this is done, you should be all set and everything should be back to normal.

Hope this helps!

Solved for me also. Thanks.

---

### Post by jareddlc on 2009-11-21
Thx!!! problem fixed!

---

### Post by tajasel on 2009-12-05
Hi,

My mum is having problems with this on her laptop also; I've followed the instructions here, but to no avail.  Below is results from various terminal commands following a partial upgrade from Update Manager.

```
karen@karen-laptop:~$ sudo apt-get install adobe-flashplugin
[sudo] password for karen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
adobe-flashplugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
karen@karen-laptop:~$ sudo gedit /var/lib/dpkg/status
karen@karen-laptop:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate
karen@karen-laptop:~$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
karen@karen-laptop:~$ sudo dpkg-reconfigure adobe-flashplugin --force
karen@karen-laptop:~$ sudo dpkg --purge --force-all adobe-flashplugin
dpkg: warning: ignoring request to remove adobe-flashplugin which isn't installed.
karen@karen-laptop:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate
karen@karen-laptop:~$ 
```Help?!  Currently getting the "this is all your fault, you convinced me to delete Vista and use Ubuntu instead!" treatment :-(

---

### Post by Leppie on 2009-12-05
> **tajasel said:**
> Help?!  Currently getting the "this is all your fault, you convinced me to delete Vista and use Ubuntu instead!" treatment :-(

May I say that IMHO editing the dpkg status file isn't a very smart thing to do...


To install the adobe flash plugin:
```
$sudo apt-get install flashplugin-nonfree
```

Or install the adobe flash plugin installer from synaptic.

---

### Post by tajasel on 2009-12-05
> **Leppie said:**
> May I say that IMHO editing the dpkg status file isn't a very smart thing to do...
I can't stop you saying whatever you like.  I don't generally subscribe to the idea that editing files that the system writes to is a smart idea, but in this instance, it was a recommended fix for my problem ([given by a user on this very thread]("http://ubuntuforums.org/showpost.php?p=8086156&postcount=8")) which apparently worked for others.  (It should *definitely* be noted that before doing anything, I made a backup of the file.)

> **Leppie said:**
> To install the adobe flash plugin:
```
$sudo apt-get install flashplugin-nonfree
```
I have previously been deliberately choosing adobe-flashplugin over nonfree as it works so much better.  Of course, in this instance, I thought since adobe-flashplugin wasn't working at all, trying nonfree was better than nothing.  However, once it was installed and the iPlayer website was loaded, my mum was presented with the message that she should install flash, so whilst installation succeeded, nonfree is apparently not good enough for the websites she uses...

> **Leppie said:**
> Or install the adobe flash plugin installer from synaptic.
Already installed.

---

### Post by Toadmund on 2009-12-19
Thanks sethmaclaren, I also had the same problem as you, flashplayer and synaptic.
My problem arose because of one of our cats jumping onto the monitor via the keyboard during a 'simple' .deb install of flashplayer.

(never say "this is going to be easy and strait forward" you will jinx yourself!)

Instead of searching through all that text in gedit, a good tip is to use the magnifying glass icon in gedit which searches terms like 'flashplayer'

I had something else to say, but tuff turds to that, I forgot.

Thanks a lot for sharing your solution!

---

