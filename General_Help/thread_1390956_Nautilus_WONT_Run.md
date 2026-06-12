---
title: "Nautilus WONT Run"
date: 2010-01-26
forum: General Help
---

### Post by not1 on 2010-01-26
This is really starting to piss me off.

```
(nautilus:2754): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Segmentation fault
```

I get that from terminal when i try to run Nautilus. I have reinstalled it which was a bit of a hassle on its own and did nothing.

I am not computer savvy at all, and don't know what anything in that error code means. If you can at least translate it - this thread hasn't failed.

I really don't know what I could've done to cause this. Is there an actual possibility I can use a Nautilus clone in the mean time, so I can browse files?

Thanks in advance.

---

### Post by not1 on 2010-01-26
To make matters weirder for anyone reading. I get the following error when I "sudo nautilus"

```
(nautilus:3287): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3287): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3287): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3287): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

Oh and btw - this works, it makes Nautilus run. In addition Nautilus doesn't show up as a process.

---

### Post by audiomick on 2010-01-26
Hi.
You should actually use
```
gksu nautilus
```
to start nautilus as root. "gksu" is a form of sudo for starting graphical applications.

I always get a couple of errors when I start nautilus that way. From what I have read, it seems to be normal, although I have no idea what the errors mean.

Can't help with your actual problem, sorry.

---

### Post by warfacegod on 2010-01-26
> **not1 said:**
> To make matters weirder for anyone reading. I get the following error when I "sudo nautilus"

```
(nautilus:3287): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3287): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3287): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3287): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

Oh and btw - this works, it makes Nautilus run. In addition Nautilus doesn't show up as a process.

I get the same messages but Nautilus runs anyway. Here is the key phrase:

> Please ask your system administrator to enable user sharing. if you don't want to see the error.

audiomick is right, using "sudo" for Nautilus is unwise. It has the potential for corruption. "gksu" or "gksudo" are much safer and will get you basically the same permissions as "sudo"

---

### Post by not1 on 2010-01-26
Thanks for the help guys. 

Unfortunately it is very inefficient for me to go to the root Nautilus every time I want to see a file, or browse my files.

Has this error ever been seen before?
Is there an older version or clone of Nautilus I can use to get around this problem?
What the hell is going on?

"A segmentation fault (often shortened to segfault) is a particular error condition that can occur during the operation of computer software. A segmentation fault occurs when a program attempts to access a memory location that it is not allowed to access, or attempts to access a memory location in a way that is not allowed (for example, attempting to write to a read-only location, or to overwrite part of the operating system)." - *Wikipedia*


Do I need to give Nautilus permissions or something? If I can access it from root but not from my user, does that mean something?

---

### Post by audiomick on 2010-01-26
> **not1 said:**
> Thanks for the help guys. 

Unfortunately it is very inefficient for me to go to the root Nautilus every time I want to see a file, or browse my files.

It is also not a great idea. You are not hindered from erasing things that shouldn't be erased, and I think you can end up with messed up permissions if you start saving things or moving things around with root privileges.

> Has this error ever been seen before?
I haven't seen any mention of it.

> Is there an older version or clone of Nautilus I can use to get around this problem?

What the hell is going on?

I'd be guessing.

According to your error message, Nautilus is not finding some preferences, but I haven't the foggiest where they are kept.

I think that nautilus is very closely tied to the desktop. I would, at this point, possibly try re-installing the desktop.
**Bear in mind that this is a total shot in the dark**
You can do this by going to synaptic package manager and marking the package "ubuntu-desktop" for re-install and applying. You will have to decide for yourself if you want to try this or not. I can't say if it will help or not, and if something goes wrong, you will really be buggered. If you shoot down the desktop, you will only be able to work from the command line.

---

### Post by not1 on 2010-01-26
I'm just thinking - If I get an alternative file manager to Nautilus, I will still get...

```
(nautilus:2754): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Segmentation fault
```

...won't I? Because I would imagine they'd work the same way.


awwwwww this sucks :(

---

### Post by jzacsh on 2010-01-26
> **warfacegod said:**
> I get the same messages but Nautilus runs anyway. Here is the key phrase:

 if you don't want to see the error.

audiomick is right, using "sudo" for Nautilus is unwise. It has the potential for corruption. "gksu" or "gksudo" are much safer and will get you basically the same permissions as "sudo"


I believe using either sudo or gksudo are both I bad idea. Feel free to correct me here, but that's like logging into a terminal as root -- just to do routine tasks. I think launching nautilus as a super user is a very messy idea.

---

### Post by jwbrase on 2010-01-26
> **not1 said:**
> In addition Nautilus doesn't show up as a process.

Nautilus doesn't show up as a process when started by gksudo/sudo because System Monitor, if it has not itself been started with gksudo/sudo, will only show processes that belong to the current user.

---

### Post by not1 on 2010-01-26
> **audiomick said:**
> 
You can do this by going to synaptic package manager and marking the package "ubuntu-desktop" for re-install and applying. You will have to decide for yourself if you want to try this or not. I can't say if it will help or not, and if something goes wrong, you will really be buggered. If you shoot down the desktop, you will only be able to work from the command line.


Thankyou sir but I have allready tried that. I reinstalled everything that comes and goes with ubuntu-desktop - it didnt work.

There is something else at play here.

---

### Post by audiomick on 2010-01-26
> **not1 said:**
> Thankyou sir but I have allready tried that. I reinstalled everything that comes and goes with ubuntu-desktop - it didnt work.

There is something else at play here.

bugger

---

### Post by akakingess on 2010-01-26
Starting a little late as I just have seen the forum for the first time in about a week, but have you tried Dolphin or any of the other 'file managers' ? At least we could narrow it down to a system-wide issue or solely with 'Nautilus'...?

---

### Post by not1 on 2010-01-26
> **akakingess said:**
> Starting a little late as I just have seen the forum for the first time in about a week, but have you tried Dolphin or any of the other 'file managers' ? At least we could narrow it down to a system-wide issue or solely with 'Nautilus'...?

I'll give it a go and get back to you. Do you suggest Dolphin?

---

### Post by vinnywright on 2010-01-26
try this ..........make a new user acct. and log in as the new user and try to launch [B]Nautilus if it goes ok then you'v borked the prmitions in your /home dir.

by using sudo [/B][B]Nautilus 

VINNY
[/B]

---

### Post by audiomick on 2010-01-26
> **vinnywright said:**
> ...you'v borked the **prmitions** in your /home dir by using sudo Nautilus 


you mean "permissions", don't you? Could be, but I think the OP had the problem before he started using "sudo" to start nautilus.

@not1 : worth a try though. I will tell you if there is something wrong with your user account, or something system wide.

---

### Post by warfacegod on 2010-01-26
> **jzacsh said:**
> I believe using either sudo or gksudo are both I bad idea. Feel free to correct me here, but that's like logging into a terminal as root -- just to do routine tasks. I think launching nautilus as a super user is a very messy idea.

Using sudo has the potential to corrupt your filesystem? (can't quite remember) while gksudo does not. Using either for normal daily use is unwise. However, if Nautilus won't run as a normal user but will as root, as a temporary, stopgap measure, I see no harm in it as long as the OP is cautious.

---

### Post by not1 on 2010-01-26
Nautilus works on a different desktop user.

```

(nautilus:_2968_): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Segmentation fault
```

However I get that error message above when I launch from terminal in *that user*, with the notable difference in the error underlined.

What does it all mean?

I have never used sudo nautilus before this problem.

Is it time to try another file manager?

---

### Post by warfacegod on 2010-01-26
It just occured to me. Is there any particular reason that you can't run Nautilus from the Places menu?

---

### Post by not1 on 2010-01-26
> **warfacegod said:**
> It just occured to me. Is there any particular reason that you can't run Nautilus from the Places menu?

Yeah I can't run anything from the places menu, there are no icons on my desktop, et cetera

I just mentioned running from terminal because it showed the error message, and I thought that would be helpful.

If I - say - click on "music" in the places bar it will have an icon on the taskbar saying "opening music" for 10 seconds and then it will die.

---

### Post by audiomick on 2010-01-26
> **not1 said:**
> Yeah I can't run anything from the places menu, there are no icons on my desktop, et cetera

I just mentioned running from terminal because it showed the error message, and I thought that would be helpful.

If I - say - click on "music" in the places bar it will have an icon on the taskbar saying "opening music" for 10 seconds and then it will die.

Had that and fixed it, I think. I will have to do some searching, but I think I still have the solution subcribed. I'll get back to you.

---

### Post by not1 on 2010-01-26
> **audiomick said:**
> Had that and fixed it, I think. I will have to do some searching, but I think I still have the solution subcribed. I'll get back to you.

thanks buddy.

---

### Post by Rocket2DMn on 2010-01-26
Have you tried clearing your user preferences for nautilus?
```
mv .nautilus .nautilus_old
```
You may need to logout and log back in afterward.  If that doesn't work, you may want to try with the .gnome2 directory as well.  This will remove other personal settings, but they can be restored later as desired.

---

### Post by warfacegod on 2010-01-26
> **not1 said:**
> Yeah I can't run anything from the places menu, there are no icons on my desktop, et cetera

I just mentioned running from terminal because it showed the error message, and I thought that would be helpful.

If I - say - click on "music" in the places bar it will have an icon on the taskbar saying "opening music" for 10 seconds and then it will die.

This sounds, to me, like your permissions got messed up. Look in: System> Admin.> Users & Groups> Unlock it> highlight your user name and make sure you have the permissions set properly.

---

### Post by warfacegod on 2010-01-26
Another possibility that might work would be to: Right click your Applications, Places, System menu and select Edit menus. Create a new item and name it Nautilus and make the command /usr/bin/nautilus

---

### Post by not1 on 2010-01-26
> **Rocket2DMn said:**
> Have you tried clearing your user preferences for nautilus?
```
mv .nautilus .nautilus_old
```
You may need to logout and log back in afterward.  If that doesn't work, you may want to try with the .gnome2 directory as well.  This will remove other personal settings, but they can be restored later as desired.

this doesn't work:

```
mv .nautilus .nautilus_old
```

I am an absolute beginner - when you say "try with the .gnome2" do you want me to do...

```
mv .gnome2 .gnome2_old
```

??

> **warfacegod said:**
> This sounds, to me, like your permissions got messed up. Look in: System> Admin.> Users & Groups> Unlock it> highlight your user name and make sure you have the permissions set properly.

[URL="http://www.newgrounds.com/dump/item/85c8743d19ab344d0576d0038b89574b"]
These are my permissions - I have never been to this window before.[/URL]

---

### Post by audiomick on 2010-01-26
OK, don't discount the advice from the last two posters. Rocket2DMn
is a moderator, and therefore much more qualified than me, and warfacegod breaks his system and fixes it for fun.;)

This is the problem I had
[http://ubuntuforums.org/showthread.php?t=1331339](http://ubuntuforums.org/showthread.php?t=1331339)

and here is where I found the solution

[http://ubuntuforums.org/showthread.php?t=1352582](http://ubuntuforums.org/showthread.php?t=1352582)

see if that rings a bell

---

### Post by not1 on 2010-01-26
> **warfacegod said:**
> Another possibility that might work would be to: Right click your Applications, Places, System menu and select Edit menus. Create a new item and name it Nautilus and make the command /usr/bin/nautilus

nothing happens :(

---

### Post by warfacegod on 2010-01-26
> **not1 said:**
> nothing happens :(

Okay, then change the command to say gksudo nautilus (note the space in between) close the menu editor and drag it from your menu onto your desktop. That will save you the hassle of using the terminal to run Nautilus. This is temporary and remember, this is root, be careful.

---

### Post by warfacegod on 2010-01-26
> **audiomick said:**
> OK, don't discount the advice from the last two posters. Rocket2DMn
is a moderator, and therefore much more qualified than me, and warfacegod breaks his system and fixes it for fun.;)

This is the problem I had
[http://ubuntuforums.org/showthread.php?t=1331339](http://ubuntuforums.org/showthread.php?t=1331339)

and here is where I found the solution

[http://ubuntuforums.org/showthread.php?t=1352582](http://ubuntuforums.org/showthread.php?t=1352582)

see if that rings a bell

Thanks for the endorsement!:D:D...I think?

---

### Post by not1 on 2010-01-26
> **audiomick said:**
> OK, don't discount the advice from the last two posters. Rocket2DMn
is a moderator, and therefore much more qualified than me, and warfacegod breaks his system and fixes it for fun.;)

This is the problem I had
[http://ubuntuforums.org/showthread.php?t=1331339](http://ubuntuforums.org/showthread.php?t=1331339)

and here is where I found the solution

[http://ubuntuforums.org/showthread.php?t=1352582](http://ubuntuforums.org/showthread.php?t=1352582)

see if that rings a bell

Ok that thread wanted me to open up terminal, run "mimeapps.list" and search for "inode/directory"

problem is I can't find it

```

[Added Associations]
x-content/audio-player=rhythmbox.desktop;kde-amarok.desktop;
application/x-ms-dos-executable=wine.desktop;
application/x-shellscript=wine.desktop;gedit.desktop;ooo-writer.desktop;nautilus-autorun-software.desktop;
application/x-shockwave-flash=totem.desktop;vlc.desktop;firefox.desktop;
audio/mpeg=kde4-amarok.desktop;
video/x-msvideo=vlc.desktop;
video/x-flv=vlc.desktop;
```

This is what the other guy's looked like

```
[Added Associations]
application/x-extension-drive=totem.desktop;
inode/directory=totem.desktop;nautilus-folder-handler.desktop;kde4-dolphin.desktop;kde4-gwenview.desktop;kde4-kfmclient_dir.desktop;Thunar-folder-handler.desktop;
x-content/audio-cdda=sound-juicer.desktop;
x-content/video-dvd=totem.desktop;
x-content/audio-player=rhythmbox.desktop;
x-content/image-dcf=f-spot-import.desktop;

```

Is there something I'm doing wrong. I am an absolute beginner - don't laugh haha.

---

### Post by Rocket2DMn on 2010-01-26
> **not1 said:**
> this doesn't work:

```
mv .nautilus .nautilus_old
```

I am an absolute beginner - when you say "try with the .gnome2" do you want me to do...

```
mv .gnome2 .gnome2_old
```

??



[URL="http://www.newgrounds.com/dump/item/85c8743d19ab344d0576d0038b89574b"]
These are my permissions - I have never been to this window before.[/URL]

Yes, try that command with .gnome2. When you say the command I listed didn't work, did it complain when you tried to do it, or did it just not have any effect?

You may consider running a filesystem check as well.  To force the drives to get checked at next reboot, type:
```
sudo touch /forcefsck
```
Then reboot your machine - the partitions will get scanned during the startup sequence.

---

### Post by not1 on 2010-01-26
> **audiomick said:**
> OK, don't discount the advice from the last two posters. Rocket2DMn
is a moderator, and therefore much more qualified than me, and warfacegod breaks his system and fixes it for fun.;)

This is the problem I had
[http://ubuntuforums.org/showthread.php?t=1331339](http://ubuntuforums.org/showthread.php?t=1331339)

and here is where I found the solution

[http://ubuntuforums.org/showthread.php?t=1352582](http://ubuntuforums.org/showthread.php?t=1352582)

see if that rings a bell

ok I looked in "defaults.list"

and amoungst the code I got
```

inode/directory=nautilus-folder-handler.desktop
```

so I think your problem and my problem are unique. (Mine even more unique :( )

---

### Post by warfacegod on 2010-01-26
We're laughing with you not at you. We've all been in similar situations.

When you removed Nautilus did you do it from Synaptic and, if so, did you "mark for complete removal"?

---

### Post by not1 on 2010-01-26
> **Rocket2DMn said:**
> Yes, try that command with .gnome2. When you say the command I listed didn't work, did it complain when you tried to do it, or did it just not have any effect?

You may consider running a filesystem check as well.  To force the drives to get checked at next reboot, type:
```
sudo touch /forcefsck
```
Then reboot your machine - the partitions will get scanned during the startup sequence.

neither the .nautilus or .gnome2 commands told me anything in the terminal. And I don't believe either had an effect.

I will check the drives now.

---

### Post by not1 on 2010-01-26
> **warfacegod said:**
> We're laughing with you not at you. We've all been in similar situations.

When you removed Nautilus did you do it from Synaptic and, if so, did you "mark for complete removal"?

I did
```

sudo apt-get remove nautilus --purge
``` 
then
```
sudo apt-get install nautilus 
```

I might have done "ubuntu-desktop" I can't remember. I suck.

Anyway this thread is telling me there is a patch for my eel-critical error. However they are not having the same symptoms as me (not being able to launch). Maybe the Eel-critical error is unrelated to my problem of not being able to launch Nautilus?

Can you guys check it out?
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234)

---

### Post by audiomick on 2010-01-26
ok, I have to go to bed. It's 4.15 a.m. here...
good luck.
I'll have a look tomorrow to see if you won or not...

---

### Post by warfacegod on 2010-01-26
I read through a good part of that launchpad link. It looks like it is related. However, I think first reinstalling in Synaptic is a better option at the moment. Go to:

System> Admin.> Synaptic Package Manager> search for nautilus> Mark for Complete Removal> Apply> Mark for Installation> Apply> search for gnome-session> Mark for installation> Apply> Reboot

---

### Post by not1 on 2010-01-26
> **warfacegod said:**
> I read through a good part of that launchpad link. It looks like it is related. However, I think first reinstalling in Synaptic is a better option at the moment. Go to:

System> Admin.> Synaptic Package Manager> search for nautilus> Mark for Complete Removal> Apply> Mark for Installation> Apply> search for gnome-session> Mark for installation> Apply> Reboot

Won't that kill ubuntu-desktop and I won't be able to launch ubuntu?

---

### Post by warfacegod on 2010-01-26
> **not1 said:**
> Won't that kill ubuntu-desktop and I won't be able to launch ubuntu?

No. I don't even have Ubuntu-desktop installed and I have a GUI desktop running just fine (see attachment). If you are worried then before Reboot:

Top left of Synaptic:
Edit> Fix Broken Packages

---

### Post by warfacegod on 2010-01-26
If that doesn't work then go here: [https://launchpad.net/~erez-volk/+archive/nautilus]("https://launchpad.net/~erez-volk/+archive/nautilus")

It's the patch from Launchpad. About halfway down click the arrow next to Technical detains and then click Read about installing and follow those instructions.

---

### Post by not1 on 2010-01-26
Alright the reinstall did not work. I'll now try the patch, it looks incredibly difficult to install the patch - for me anyway. Here goes nothing :)

---

### Post by not1 on 2010-01-26
either i didnt install the patch properly or nothing happened. I am now willing to give up - there seems to be no workable solution except perhaps deleting my user.

---

### Post by not1 on 2010-01-27
bump for help

---

### Post by audiomick on 2010-01-27
Hallo again.
You said that nautilus runs for the new user you created, right?
So here`s a thought. If you decide to go with the new user and delete the old one, you will have to copy all your data across and change it's permissions to the new user, which sounds like a right royal pain to me.

In the last post of that lauchpad bug report, number #30, mayday describes the same symptoms you are having, i.e., the patch didn't work for him, but a new user did. He searched and removed settings files

> Guessing the problem might have a configuration aspect, I removed all nautilus/gnome related settings files from my home folder. And finally the original ubuntu maintained nautilus works again.
which is similar to what Rocket2DMn suggested you to do.

That fact that nautilus works for the new user indicates that there is something in the user folder that is messed up for the old user and not for the new one. Therefore, I would try looking  for whatever that is and copying it from the new one to the old one. I expect you would have to change the permissions on it from the new user to the old, but it would likely be only a few files instead of the entire contents of your user folder.

First of all, I would do the de-install and re-install routine again, to get back to the standard install,  although that is probably not critical. If nautilus still works for the new user after applying that patch, your probably right to go.

So, using nautilus as root so you can sniff around in both user folders, look for the two files that Rocket2DMn told you to re-name, that's .nautilus and .gnome2. To see them in nautilus, you have to enable "show hidden files" in "view".

Mayday, in his post in the launchpad thread, also refers to .local

You want to be a bit thoughtful about this. It would be a good idea not to just overwrite anything, but to re-name it as Rocket2DMn suggested so you can put it back if anything else mucks up. You can do that with a right click in a root nautilus, I think, or use the move command that Rocket2DMn suggested.

I can't look into this myself right now; I am sitting in a train station waiting on a train (the one I wanted to take is running 80 minutes late... German Punctuality ;) )and wont be home for another 4 hours or so. I'll have a bit of a look when I get there. You'll be in bed by then, I dare say, so leave it till tomorrow if you want. I'll post anything I can find.

---

### Post by warfacegod on 2010-01-27
Do the Germans own the patent on late trains?

---

### Post by warfacegod on 2010-01-27
> **audiomick said:**
> Hallo again.
You said that nautilus runs for the new user you created, right?
So here`s a thought. If you decide to go with the new user and delete the old one, you will have to copy all your data across and change it's permissions to the new user, which sounds like a right royal pain to me.

In the last post of that lauchpad bug report, number #30, mayday describes the same symptoms you are having, i.e., the patch didn't work for him, but a new user did. He searched and removed settings files


which is similar to what Rocket2DMn suggested you to do.

That fact that nautilus works for the new user indicates that there is something in the user folder that is messed up for the old user and not for the new one. Therefore, I would try looking  for whatever that is and copying it from the new one to the old one. I expect you would have to change the permissions on it from the new user to the old, but it would likely be only a few files instead of the entire contents of your user folder.

First of all, I would do the de-install and re-install routine again, to get back to the standard install,  although that is probably not critical. If nautilus still works for the new user after applying that patch, your probably right to go.

So, using nautilus as root so you can sniff around in both user folders, look for the two files that Rocket2DMn told you to re-name, that's .nautilus and .gnome2. To see them in nautilus, you have to enable "show hidden files" in "view".

Mayday, in his post in the launchpad thread, also refers to .local

You want to be a bit thoughtful about this. It would be a good idea not to just overwrite anything, but to re-name it as Rocket2DMn suggested so you can put it back if anything else mucks up. You can do that with a right click in a root nautilus, I think, or use the move command that Rocket2DMn suggested.

I can't look into this myself right now; I am sitting in a train station waiting on a train (the one I wanted to take is running 80 minutes late... German Punctuality ;) )and wont be home for another 4 hours or so. I'll have a bit of a look when I get there. You'll be in bed by then, I dare say, so leave it till tomorrow if you want. I'll post anything I can find.

I'm wondering if it would be easier to just use the other account at this point and remove the offending user account. I still suspect this has to do with fragged Permissions and it wouldn't surprise me to find out the Configuration Editor is involved too somehow.

---

### Post by not1 on 2010-01-27
Thankyou audiomick and warfacegod - you have been an amazing help thus far. It is 1AM in Melbourne, Australia at the moment; check back in about 12 hours from time of this post and I'll have an answer to your troubleshooting solutions after trying them.

Thanks again.

(edit: I'll add quickly before i sleep that I never got any sign that Rocket2DMn's recommendation failed or succeeded because Terminal didn't tell me anything. It is definitely something id like to try out)

---

### Post by warfacegod on 2010-01-27
> **not1 said:**
> Thankyou audiomick and warfacegod - you have been an amazing help thus far. It is 1AM in Melbourne, Australia at the moment; check back in about 12 hours from time of this post and I'll have an answer to your troubleshooting solutions after trying them.

Thanks again.

(edit: I'll add quickly before i sleep that I never got any sign that Rocket2DMn's recommendation failed or succeeded because Terminal didn't tell me anything. It is definitely something id like to try out)

If it didn't result in Nautilus running properly, without the need for root privileges, then I would say it failed.

---

### Post by not1 on 2010-01-28
I've been thinking it over. Nautilus works perfectly in the other user, however I still get an Eel-critical error in Terminal for both users; this could mean that the problems are unrelated however unlikely that may be.

I am completely willing to move my data. Is it really so hard? Can't I just go in root nautilus and move my music, movies, pictures and documents over to the other user? Sure it's tens of gigabytes, but it cant take too long right?

User privileges are easy to change right? Can't I just use that app in Administration? All my applications will be on the other user right?

Sure it might sound like a cop-out, but I don't feel comfortable browsing through .gnome2, et cetera and making the right decision. I'm not knowledgeable or experienced enough for that.

Or I could go on without Nautilus, to be perfectly honest - I havent really needed to use it at all. I can just use the open command in every program I have and i can browse stuff easily.

What do you guys think?

---

### Post by not1 on 2010-01-28
HAHAHAHA - I got the patch working, and Nautilus still doesn't launch.

Here is the **NEW** terminal error code.

```
Segmentation fault
```

That's it. There is no "Eel-critical" error mumbo jumbo. At least this simplifies things a bit. Perhaps I can find something on google with this error message because it is more - simple.

again: "a segmentation fault occurs when a program attempts to access a memory location that it is not allowed to access, or attempts to access a memory location in a way that is not allowed"

I am led to believe that this problem certainly involves permissions.

---

### Post by not1 on 2010-01-28
I don't understand how I get a "fresh" .nautilus and .gnome2 folder once i have renamed them.

I renamed them and logged in and out - i got brand new directories but nothing was in them. And nautilus still wasnt working.

what do i have to do?

what happens if i replace the other users .gnome2 and .nautilus with my own?

---

### Post by not1 on 2010-01-28
YYYYYESSSS!

/home/*****/.local/share/gvfs-metadata

was corrupted or something, I renamed it; logged in logged out and voilà. Nautilus was BACK. And there was a new fresh directory.

Thanks so much guys you've been an awesome help.

SOLVED.

---

