---
title: "Well intended, misinformation - Lost GUI"
date: 2009-11-30
forum: General Help
---

### Post by Mahngiel on 2009-11-30
So i was having some gnome problems, and was advised to delete /.gnome, /.gnome2, and another folder i can't think of atm. 
 
As soon as i did this and re-logged, i lost all my GUI. I don't have an ethernet internet connection, only an encrypted wifi card, so i can't log in w/o auth.
 
I figure the easiest way to fix this is to restore from the trash bin. 
 
I need help finding this from the command prompt, since that's the only thing i have, and restoring these files. Please help. lol

---

### Post by doas777 on 2009-11-30
it should be in ~/.local/share/Trash
took me a little looking to find it myself.

---

### Post by Mahngiel on 2009-11-30
okay, so now how do i restore the file?

---

### Post by doas777 on 2009-11-30
hmmm. for those two folders, just run

```

cp -R ~/.local/share/Trash/files/.gnome ~
cp -R ~/.local/share/Trash/files/.gnome2 ~

```and if you do an 'ls -al' in the files directory, you should find the name of the other folder as well.

also, be careful with your paths. the folders you are missing are at ~/.gnome not /.gnome
that could be a costly mistake with some commands.

---

### Post by Mahngiel on 2009-11-30
thx doas777,
 
i read up on bash commands and used mv on the folders - the other was /.gconf.
 
anyways, after restore + reboot, i still had no GUI. i ran 'Metacity' and was told 'unable to run X session'.  
 
am i screwed?

---

### Post by doas777 on 2009-11-30
hmmm. run
```
ls -al ~ 
```and note the owner and permissions on those three folders.
they should have you as owner:group and have permissions of at least 640.
thats my best guess. 

you may wanna try renaming your home dir, then logging back on (which will recreate yourprofile), and start copying stuff to the new home. just a though.

---

### Post by Mahngiel on 2009-11-30
alright. give me 20 minutes.

---

### Post by t0p on 2009-11-30
> **Mahngiel said:**
> So i was having some gnome problems, and was advised to delete /.gnome, /.gnome2, and another folder i can't think of atm. 
 

Would you mind telling us where you got this advice from/who gave it to you?  We don't like it when members give other members malicious misinformation.  I'm not saying the person who gave you this advice did it with malice.  But it's a possibility.

---

### Post by Mahngiel on 2009-11-30
> **t0p said:**
> Would you mind telling us where you got this advice from/who gave it to you? We don't like it when members give other members malicious misinformation. I'm not saying the person who gave you this advice did it with malice. But it's a possibility.
 
it was in the #ubuntu channel. i'm not going to call him out, just yet. his explanation went something like "when you del those, gnome with reset itself to default". he claimed in channel that it wouldn't result in any harm.
 
Anyways, i can't see the file permissions because the list is too long, and i'm not sure how to view it by pages, or how to scroll. i used cmd "-m" in the trash bin, but i don't think that'd work well when trying to view perms for so many files.
 
I think i need to just cp the files i don't have backed up to a thumbdrive.  just don't know how to access that.  i've lsusb, but don't know how to access it.  i've also seen /dev/sdb pointing to it, but again, haven't been able to mount it.
 
any help would be appreciated.

---

### Post by NoaHall on 2009-11-30
It should have been /home/user/.gnome you deleted. This will delete the settings for the user. If the gui has gone, I have no idea what you've done. I don't think /.gnome exists? Not for me, anyway.~

Try adding a new user - 
```
adduser username
```

If that doesn't work, try 
```
sudo apt-get install ubuntu-desktop
```
That should bring everything back.

---

### Post by jocko on 2009-11-30
> **t0p said:**
> Would you mind telling us where you got this advice from/who gave it to you?  We don't like it when members give other members malicious misinformation.  I'm not saying the person who gave you this advice did it with malice.  But it's a possibility.
Deleting those directories will not cause any harm. They will get automatically recreated next time the user logs in (I've done it a dozen times to get rid of bad gnome and gconf settings and have never had any problems). The op's problem must be somewhere else.

---

### Post by Mahngiel on 2009-11-30
alright. well, i'll need to reinstall then. i don't have broadband internet, so i can't apt-get.  just need help finding my thumb drive so i can cp the files i want

---

### Post by NoaHall on 2009-11-30
> **Mahngiel said:**
> alright. well, i'll need to reinstall then. i don't have broadband internet, so i can't apt-get.  just need help finding my thumb drive so i can cp the files i want

Can you tell me EXACTLY the command you did? This should not have happened.

---

### Post by Mahngiel on 2009-11-30
> **NoaHall said:**
> Can you tell me EXACTLY the command you did? This should not have happened.
 
well, then i'd ahve to start at the beginning.
 
I'll preface this saying I did not have a log-in screen, which means i couldn't change sessions upon boot.
 
I was installing e16 and icewm to try them out. i didn't see any change, so i uninstalled metacity.  after reboot i ended up in xterm.  i somehow ended up at the log-in screen, which is how i found out how to change sessions.  i got in and online with e16, but was missing alot of gnome pkgs.  so i reinstalled metacity and as much gnome pkgs as i could, but gdm wouldn't install.
 
so after i got metacity up and running (which i could only run from the terminal), i del'd e16 and icewm, just so i could get back to normal.  that's when i was told to delete .gconf, .gnome, and .gnome2 from ~.  after i did that, i relogged and ended up w/o GUI.
 
and that's where i am now, flipping between windows and bash.

---

### Post by bodhi.zazen on 2009-11-30
> **Mahngiel said:**
> So i was having some gnome problems, and was advised to delete /.gnome, /.gnome2, and another folder i can't think of atm. 
 
As soon as i did this and re-logged, i lost all my GUI. I don't have an ethernet internet connection, only an encrypted wifi card, so i can't log in w/o auth.
 
I figure the easiest way to fix this is to restore from the trash bin. 
 
I need help finding this from the command prompt, since that's the only thing i have, and restoring these files. Please help. lol

First, Deleting those directories should not have caused any long term problems, they are config files and should be restored when you log out and back in .

Second, please do not start multiple threads on the same topic. Obviously you are having problems and started a thread. Now you started a new thread and we have no idea as to the problem or what you have done up to this point to solve it.

So I am sorry you are having problems, but I am going to close this thread now. Please continue on your origional thread. If you can not find it use the search function.

---

### Post by bodhi.zazen on 2009-11-30
I re-opend this thread as apparently there is no other thread on these forums.

---

### Post by NoaHall on 2009-11-30
> **Mahngiel said:**
> well, then i'd ahve to start at the beginning.
 
I'll preface this saying I did not have a log-in screen, which means i couldn't change sessions upon boot.
 
I was installing e16 and icewm to try them out. i didn't see any change, so i uninstalled metacity.  after reboot i ended up in xterm.  i somehow ended up at the log-in screen, which is how i found out how to change sessions.  i got in and online with e16, but was missing alot of gnome pkgs.  so i reinstalled metacity and as much gnome pkgs as i could, but gdm wouldn't install.
 
so after i got metacity up and running (which i could only run from the terminal), i del'd e16 and icewm, just so i could get back to normal.  that's when i was told to delete .gconf, .gnome, and .gnome2 from ~.  after i did that, i relogged and ended up w/o GUI.
 
and that's where i am now, flipping between windows and bash.

Wait, what? Why did you have to uninstall metacity? You can choose which DE/WM to use via the login in screen(change session button)

Try running ```
sudo apt-get install ubuntu-desktop
```
Hopefully the files will still be stored locally, so you won't need to download anything.
If that doesn't work, I need to know the command you did.

---

### Post by Mahngiel on 2009-11-30
thanks mod. so anyways, i lost something valuable and cannot start a X session.
 
so, if i can get a bit of help moving files to a thumb drive or any other troubleshooting tips, i'd be greatful

---

### Post by Mahngiel on 2009-11-30
> **NoaHall said:**
> Wait, what? Why did you have to uninstall metacity? You can choose which DE/WM to use via the login in screen(change session button)
 
Try running ```
sudo apt-get install ubuntu-desktop
```
Hopefully the files will still be stored locally, so you won't need to download anything.
If that doesn't work, I need to know the command you did.
 
I didn't know how to switch sessions, like I intially said, i don't use a log-in screen, so i wouldn't have seen the dialog box at the bottom. i found this when i got myself out of xterm. i was only trying to use another WM. figuring i could always reinstall metacity

---

### Post by NoaHall on 2009-11-30
> **Mahngiel said:**
> I didn't know how to switch sessions, like I intially said, i don't use a log-in screen, so i wouldn't have seen the dialog box at the bottom. i found this when i got myself out of xterm. i was only trying to use another WM. figuring i could always reinstall metacity

Okay. But have you tried running ```
sudo apt-get install ubuntu-desktop
``` yet?
You could always use your Ubuntu disk to get the packages.

---

### Post by t0p on 2009-11-30
You really do need to tell us *exactly* what you've done.  At the start you said you deleted /.gnome and /.gnome2; but those files do not exist.  You then corrected yourself and said you deleted ~/.gnome and ~/.gnome2; but deleting those folders shouldn't have permanently destroyed your GUI, they should have been recreated on reboot.

Now you say you deleted metacity; can you please tell us *exactly how* you did this?  What command did you use?  Specifically which files/folders did you delete?

You've installed and removed a lot of stuff in the build-up to this failure.  We need you to clearly describe exactly what you've done if we are to help you fix your problem.

---

### Post by Mahngiel on 2009-11-30
Foremost, for my lack of clarity, the folders I deleted were in my home folder, so yes, ~/.gconf, etc.  My appologies.
 
As many of you stated, the advice i got was not malicious, and removing those config files did not result in my lost GUI.  I was not thinking they were, only thinking that was what was responsible, hence i opened the thread trying to find out how to remove them from the Trash.
 
I know now that i lost everything in the middle of uninstalling and installing all these WMs.  
 
I used Synaptic to do everything.  I began by installing e16 and all it's components, then same with iceWM.  Then I removed Metacity.  (yes, i am now aware that i should have enabled the log-in screen and chose my session, noob mistake.)  After i rebooted, i ended up in xterm and found my way to the login screen.  This is where I was able to log into a WM.
 
I reinstalled Metacity, and it ran fine from the terminal.  So, i figured i was in the clear, and removed e16 and iceWM.  After i did that, i removed the config files as suggested from #ubuntu chat.  I updated everything then rebooted - which sent me to no GUI.
 
So i apt-cdrom add'd the LiveCD, and then tried to apt-get ubuntu-desktop.
 
Now all i get is a screen full of "Failed to Fetch"s.
 
That's what i've done

---

### Post by blueridgedog on 2009-11-30
It appears you can't use apt-get as you do not have a network connection and you simply want to copy over some essential files onto a USB flash drive, then do a re-install.  

If that is the case, can you post the output of:

```
mount
```

and 

```
sudo fdisk -l
```

(each with the flash drive plugged in)

We should be able to talk you through mounting the drive and copying over the files you want to save.

---

### Post by t0p on 2009-11-30
> **Mahngiel said:**
> 
 So i apt-cdrom add'd the LiveCD, and then tried to apt-get ubuntu-desktop.
 
Now all i get is a screen full of "Failed to Fetch"s.
 

Are you using the live cd to post here?  Reason I ask, a "screen full of 'Failed to Fetch's" suggests to me that you don't have internet connection.

I don't know for sure that installing ubuntu-desktop will fix the problem - but it certainly can't hurt.  So that's worth doing... if you can get internet access.

---

### Post by Mahngiel on 2009-11-30
> **t0p said:**
> Are you using the live cd to post here? Reason I ask, a "screen full of 'Failed to Fetch's" suggests to me that you don't have internet connection.
 
I don't know for sure that installing ubuntu-desktop will fix the problem - but it certainly can't hurt. So that's worth doing... if you can get internet access.
 
 
I appreciate you attempting to help me with this.  I do not have a net connection avail because i cannot authenticate it, so i am in Windows at the moment.  Curious though if i did run off the LiveCD if it would be of any use. Doubt it though.
 
I'll try what blueridgedog suggests to mount the thumbdrive later this evening, i must be going.  Though if i figure it out, i do understand how to mv a file/foler.
 
Take care, and thanks all.

---

### Post by doas777 on 2009-11-30
this link MAY help you get your wifi running in system space (without gnome):
[http://laic.u-clermont1.fr/~mr/linux/configreseau_en.html](http://laic.u-clermont1.fr/~mr/linux/configreseau_en.html)

you would of course have to undo that change after getting everything fixed, if you want to go back to using a user-space network manager.

---

### Post by blur xc on 2009-11-30
> **doas777 said:**
> this link MAY help you get your wifi running in system space (without gnome):
[http://laic.u-clermont1.fr/~mr/linux/configreseau_en.html]("http://laic.u-clermont1.fr/%7Emr/linux/configreseau_en.html")

you would of course have to undo that change after getting everything fixed, if you want to go back to using a user-space network manager.

I ran into trouble trying to upgrade my Nvidia driver from the CLI, which required killing X, I think, because I didn't have an internet connection.  I just ran across this, which I'll try later- [http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/), and see if the upgrade will work.

BM

---

### Post by doas777 on 2009-11-30
I hear that the new way to stop x in karmic is:
```
sudo service gdm stop
```

if that doesn't work, fall back to the old:
```
sudo killall gdm
```

---

### Post by Mahngiel on 2009-12-01
Well, I ended up having to do a fresh install.  I did some research and talked to a few smart folks who helped me alleviate getting to the point that I did. I'll post a quick tidbit in the tips & tutorial forum to help the next noob.  Thanks for all your help and assistance

---

