---
title: "Can't get past login screen in Ubuntu 10.04 Lucid Lynx."
date: 2010-06-11
forum: General Help
---

### Post by donaloflynn on 2010-06-11
I installed Ubuntu for the first time yesterday by running Wubi on Windows Vista Home Premium. For all of yesterday and up to lunchtime today Ubuntu was working fine. I followed the instructions on a forum post to remove Evolution Mail via the synaptic applications menu. I proceeded to log out of Ubuntu and reboot (I hoestly can't remember what for) Anyway, ever since I have not been able to log in to Ubuntu. I enter my username and password as normal and they are accepted, however moments the log in page displays again. This continues in an endless loop.

The password is definitely correct because I get an authentication error if I enter anything else. I know I am not the only person experiencing this issue. None of the suggestions I have found by searching this forum have worked.

Someone must be able to fix this problem, please offer any advice you can.

Thanks a lot!

---

### Post by beckols on 2010-06-11
You didn't say what all you have tried from the other "suggestions".

Are you able to get to a console from the login screen by pressing Ctrl-Alt-F2?

If so, login and try typing 'df -h' to see if you have enough disk space.

Also here is a post talking about some of the reasons the loop occurs: [http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9321636&postcount=2](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9321636&postcount=2)

---

### Post by donaloflynn on 2010-06-11
I have plenty disk space, 13GB out of 17GB.

Anything else I should try as I'm in there?

---

### Post by beckols on 2010-06-11
I would try maybe reconfiguring gdm:
```
sudo dpkg-reconfigure gdm
```

---

### Post by donaloflynn on 2010-06-11
> **beckols said:**
> I would try maybe reconfiguring gdm:
```
sudo dpkg-reconfigure gdm
```

What should happen if that works?

---

### Post by beckols on 2010-06-11
After you do that, switch back to the GUI by hitting 'Ctrl-Alt-F8' then attempt to log on again.

Edit: Actually, you might want to restart gdm first
```
sudo /etc/init.d/gdm restart
```

I'm not sure if you need to or not, but it won't hurt.

---

### Post by donaloflynn on 2010-06-11
That hasn't worked either I'm afraid. Any other ideas?

(Thanks a lot for your help by the way)

**EDIT:** No joy following the gdm restart either unfortunately.
[B]
EDIT 2:[/B] Don't know if this helps, but I restarted the computer and on booting Ubunrtu I was told that my drive was being checked for errors. That doesn't seem to have fixed anything though.

---

### Post by beckols on 2010-06-11
Hm, well try these commands:
```

grep -i gnome /var/log/auth.log
grep -i gnome /var/log/daemon.log
grep -i gnome /var/log/syslog

```
See if there are any error messages from the last time you tried to log on. If it helps, go ahead and try to log on before you look at the logs.  That way, errors will be at the bottom of the list.

It's too bad you can't post the logs, that would make it a lot easier.

---

### Post by beckols on 2010-06-11
Also one more thing you might check:
```
cat ~/.xsession-errors
```

There might be some interesting snippets in there from when you tried to login.

---

### Post by donaloflynn on 2010-06-11
I don't understand or recognise anything in the auth log.

The daemon log mentions that I couldn't launch evolution-on-alarm-notify.desktop (it took a couple of attempt to uninstall Evolution Mail). There's also something about gnome-mah jongg.

The last piece of code didn't work.

---

### Post by donaloflynn on 2010-06-11
the xsession code told me "Can't open /home/donal/.profile

---

### Post by beckols on 2010-06-11
At the command line:
```
ls -l /home
```
You will get something like this:
drwxr-xr-x 34 beckols beckols 4096 2010-06-11 13:29 beckols

What exactly does yours say where mine says: drwxr-xr-x

Explanation (if you don't know):
This is the permissions, the d means that it is a directory. The first 'rwx' is th permissions for the owner of the file (read, write, execute respectively).  The middle 'r-x' is group permissions, and the last 'r-x' is everyone permissions.  Also the first two names after the permissions are the file owner followed by the group owner.  For your home folder, both of these should be set to your username.  If they aren't, then you have a permissions problem.  You should also go into your home folder and see if any files are like that:
```

ls -la /home/[username]

```

---

### Post by beckols on 2010-06-11
OK, I think I might have just hit the answer.  Apparently uninstalling Evolution can uninstall gnome-session.  So before any of that other gobbledegook, go ahead and do this:
```

sudo apt-get install gnome-session

```

Then try logging in again.

---

### Post by donaloflynn on 2010-06-11
Mine says: drwxr-xr-x 47 donal donal 4096 2010-06-11 19:35 donal

the majority of files in /home/donal are drwxr-xr-x

some others are -rw-------.

Every file has my username as twice (file owner and group owner).

---

### Post by beckols on 2010-06-11
OK, that's good then.  Try doing the gnome-session install and see if that does it.

---

### Post by donaloflynn on 2010-06-11
only saw your gnome-session post now. Gnome appears to be installing.

---

### Post by donaloflynn on 2010-06-11
the last line I can see is
> ldconfig deferred processing now taking place

Nothing else has happened in about 2 mins. Does that mean it's finished and I can try to log in again?

---

### Post by beckols on 2010-06-11
Yep, now try logging in.  And at the login screen, make sure 'Sessions' (at the bottom of the screen) is set to 'Gnome'

---

### Post by donaloflynn on 2010-06-11
It works!

Thank you ever so much for all your help, I wish I could do something for you!

I think I uninstalled too many files with Evolution in the title as Ubuntu is now working, but there's no sign of Evolution Mail!

I thought I'd end up having to do a clean install, you have restored my faith in the Linux community!

Thanks again, 
Dónal

---

### Post by beckols on 2010-06-11
No problem, it was fruitful for both of us: nothing like a little knowledge in the afternoon.  Make sure to mark the thread as [Solved].  Good luck!

---

### Post by donaloflynn on 2010-06-11
Just noticed that the interface I have now is a little different: no power symbol in the top corner nor the social icon with my username displayed. Also the networking icon is in the top corner rather than to the far left.

Presumably something reverted to a slightly older version? I'm running Gnome 2.30.0 if that helps.
Any ideas on how I can get this back to the default Ubuntu 10.04 design?

---

### Post by beckols on 2010-06-11
Yes, Evolution might have gone a little deeper.  If things aren't the way you like them, try doing a full removal/reinstall of gdm.  First log out, then go the the console again (Ctrl-Alt-F2):
```

sudo service gdm stop
sudo apt-get remove gdm
sudo apt-get install gdm

```
Additionally try to install these, as there are cases where they didn't install correctly with the reinstallation of gdm:
```

sudo apt-get install gnome-session
sudo apt-get install indicator-applet-session
sudo service gdm start

```

Now this might automatically switch you back to the GUI, but if not just hit 'Ctrl-Alt-F8' to switch to it, and try it again.

---

### Post by donaloflynn on 2010-06-11
Is there any danger this will mess things up further?

---

### Post by beckols on 2010-06-11
I'm not a Grandmaster of Ubuntu (tm) but basically all this is doing is removing all of the packages that come with gdm then putting them back on like it would be from a base-install.  It doesn't remove any configuration files you have in place or anything like that, only the packages (which are immediately restored).  This is helpful because it allows you to start fresh with your whole display manager since the removal of Evolution might have uninstalled little unknown pieces that break it.

---

### Post by donaloflynn on 2010-06-11
That seems to have sorted things once and for all. Thanks again, now hopefully I can get to enjoy and learn about Ubuntu without being plagued by problems!

---

### Post by maxpoweron on 2010-06-18
> **beckols said:**
> OK, I think I might have just hit the answer.  Apparently uninstalling Evolution can uninstall gnome-session.  So before any of that other gobbledegook, go ahead and do this:
```

sudo apt-get install gnome-session

```

Then try logging in again.

Beckols,

Thanks for the suggestion on how to fix the endless loop at gdm login.  I removed everything that contained Evolution using Synaptic Package Manager and it trashed gnome-session.

---

### Post by SirPecanGum on 2010-06-27
> **beckols said:**
> OK, I think I might have just hit the answer.  Apparently uninstalling Evolution can uninstall gnome-session.  So before any of that other gobbledegook, go ahead and do this:
```

sudo apt-get install gnome-session

```

Then try logging in again.

Thanks!

---

### Post by mrinvader on 2010-08-30
Hi all!! I am experiencing the GDM logon loop issue, but mine arose with i think the 255.44 nvidia driver.. but i'm not sure.. My reason for wanting the latest nvidia driver was for better offloading of video playback. the youtube is 60-80% cpu on athlon64/3200 with 2.5gb memory on latest flash.

this driver is from the [https://launchpad.net/~ubuntu-x-swat](https://launchpad.net/~ubuntu-x-swat) group as the mainline ubuntu and backports repos arent current.

I have removed the 256.44 line from with --purge and reverted to nouveau (foss driver), lucid-updates nvidia-current, and 173 driver... 

i have downgraded from lucid-updates gdm to lucid gdm with purge..

I have made gdm the owner of /var/lib/gdm and etc/gdm

gnome-session has been reinstalled with --purge..


I have compared /var/log/gdm to another lucid machine's /var/log/gdm and can't find anythin different between them.

As of now the only way to have a fully graphical logon with any video driver is with kdm. I also can ctl-alt-f1, logon to any account, stop kdm as root, and run startx.. that works too.

---

### Post by Objekt on 2010-09-30
This thread saved my bacon.  I was having almost exactly the problem described by the thread starter.  Chief difference: I don't run Ubuntu through Wubi, but rather have a triple-boot configuration (Windows XP + Ubuntus 9.10 and 10.04).

I never messed with Evolution, but it seems that my gdm-session install must have been trashed, because the steps suggested here fixed the problem.  

It's unsettling when stuff breaks for no apparent reason.  I still haven't a clue how mine got broken.  My 10.04 install is fixed now, but boy am I glad I kept my Ubuntu 9.10 install.

---

### Post by mrowl on 2011-01-12
Thank you thank you beckols. You may not be a "Grandmaster" but you saved my bacon with this solution

---

### Post by t54 on 2012-04-03
@ beckols

Thank you very much for your excellent solution to the lucid endless login loop problem.  Clearly written and it worked perfectly for me after ATI proprietary driver install corrupted numerous files. 

I did remove and purge the ATI drivers completely and reinstalled the open source ati pkgs drivers but that was not enough.  Your solution finished the job and I can login to the GUI with no problem.  

Thanks again.

---

### Post by simitchdar on 2012-04-04
I needed to create you a very small observation so as to give thanks the moment again with your striking pointers you've contributed on this website. It's  extremely generous of people like you to supply easily all that a lot of folks might have distributed as an e book to help with making some bucks on their own, mostly since you might well have tried it in the event you desired. The good ideas as well served as the great way to recognize that other individuals have the same dream just as mine to see great deal more with reference to this problem. I'm certain there are many more fun sessions in the future for folks who see your blog post.

---

### Post by trellis2 on 2012-04-06
I have the same problem. What am I looking for in the /var/log/auth.log? I'm not even sure what log to look into. How do you remove the ATI proprietary drivers?? I have tried bechols' steps removing and reinstalling gdm, but with out knowing what is causing the loop I can go on for days guessing at removing and installing back login files. any help would be appreciated.

---

### Post by KurikuKuM on 2012-04-06
Câåæèå êëþ÷è äëÿ Êàñïåðñêîãî, 24.02. 2012, ñêà÷àòü.Radmin viewer 3 3 êîä àêòèâàöèè, ïðîâåðåíî 100% íå ïîæàëååòå, keygen, àêòèâàöèÿ windows xp; Èíòåðåñíûå ôàéëû; àêòèâàöèÿ ñëóæá òåðìèíàëîâ.ñêà÷àòü steam keygen 2010, xyvuuosuyid1990s Space.Welcome to Crackspider.net! mountblade 1.011 crack serial.Ñîñàòü õóé ñïåðìà Ïîðíî 2000õ ñêà÷àòü ðóñèôèêàòîð guitar rig 3, ïîðíî, äèñêè äåøåãî ñêà÷àòü ôèëüìû ââñ ñêà÷àòü photoshop cs7.Replay Converter Keygen, Free Software Download.Photoshop cs 5 crack Äîáðî ïîæàëîâàòü íà íàø ñàéò.5 Jan 2012, VMware Vsphere 5 Final, 7.82 GB VMware vSphere, the most trusted, most, widely deployed virtualization, VMware workstation keygen.Windows 8 build 7850 KMS Activator and Timebomb Remover 0.9.Download alawar keygen from Rapidshare, Megaupload, Hotfile.

---

### Post by Patsfriend on 2012-05-28
Hooray!
It Pays to keep searching the threads! 
Thank You for helping!
This was exactly what I needed to repair my mistake(s).
;)
Sincerly,
Patsfriend.

> **beckols said:**
> Yes, Evolution might have gone a little deeper.  If things aren't the way you like them, try doing a full removal/reinstall of gdm.  First log out, then go the the console again (Ctrl-Alt-F2):
```

sudo service gdm stop
sudo apt-get remove gdm
sudo apt-get install gdm

```Additionally try to install these, as there are cases where they didn't install correctly with the reinstallation of gdm:
```

sudo apt-get install gnome-session
sudo apt-get install indicator-applet-session
sudo service gdm start

```Now this might automatically switch you back to the GUI, but if not just hit 'Ctrl-Alt-F8' to switch to it, and try it again.

---

### Post by uRock on 2012-05-28
Old thread.

Closed thread.

---

