---
title: "Latest Firefox-3.6 From Ubuntu-Mozilla-Daily Won't Start"
date: 2010-01-21
forum: General Help
---

### Post by AdemoS on 2010-01-21
Ubuntu 9.10 64-bit
Firefox 3.6 

I just upgraded to the latest build from [Ubuntu-Mozilla-Daily]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa") and I recieved the following error:

```

/usr/lib/firefox-3.6pre/firefox: 59: dirname: Permission denied
/usr/lib/firefox-3.6pre/firefox: 88: /bin/pwd: Permission denied
/usr/lib/firefox-3.6pre/run-mozilla.sh: 39: dirname: Permission denied
/usr/lib/firefox-3.6pre/firefox-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory

```

Any ideas what might be wrong?


Thanks for reading.

---

### Post by Tourdog on 2010-01-21
ademos,

My thread brought out many items for you to look at for the clues:

[http://ubuntuforums.org/showthread.php?t=1387249](http://ubuntuforums.org/showthread.php?t=1387249)

My case was for 64 bit and yours may be 32 bit.   Look at the resources that Guru "Nanotube" has provided .....................

You've got a number of hoops to jump through............   :(

---

### Post by AdemoS on 2010-01-21
> **Tourdog said:**
> ademos,

My thread brought out many items for you to look at for the clues:

[http://ubuntuforums.org/showthread.php?t=1387249](http://ubuntuforums.org/showthread.php?t=1387249)

You've got a number of hoops to jump through............   :(

Thanks for trying, but this method worked prior to the latest update.


> **Tourdog said:**
> My case was for 64 bit and yours may be 32 bit. Look at the resources that Guru "Nanotube" has provided 

I also use 64 bit Firefox, but I seem to be having an issue with an .so library.

---

### Post by lovinglinux on 2010-01-21
Re-install **xulruner-1.9.1**. 

```
sudo apt-get --reinstall install xulruner-1.9.1
```

---

### Post by JoZ3 on 2010-01-21
Hello all, i upgrade my abrowser (firefox) from the ppa a few minutes a go, and not run, whe i try to run in console receive this error:
```
/usr/lib/firefox-3.6pre/abrowser: 59: dirname: Permission denied
/usr/lib/firefox-3.6pre/abrowser: 88: /bin/pwd: Permission denied
/usr/lib/firefox-3.6pre/abrowser: 88: dirname: Permission denied
/usr/lib/firefox-3.6pre/abrowser: 88: /bin/pwd: Permission denied
/usr/lib/firefox-3.6pre/abrowser: 88: /bin/ls: Permission denied
/usr/lib/firefox-3.6pre/run-mozilla.sh: 39: dirname: Permission denied

run-mozilla.sh: Cannot execute /usr/lib/firefox-3.6pre/-bin.

```

whats happend??

---

### Post by AdemoS on 2010-01-21
> **lovinglinux said:**
> Re-install **xulruner-1.9.1**. 

Thanks for the idea, but after re-installing I get the same results.

I also have every version of Xulrunner I could find installed, from 1.9.1 to 1.9.3, in addition to xulrunner-gnome-support for each.

---

### Post by lovinglinux on 2010-01-21
> **AdemoS said:**
> Thanks for the idea, but after re-installing I get the same results.

I also have every version of Xulrunner I could find installed, from 1.9.1 to 1.9.3, in addition to xulrunner-gnome-support for each.

It's weird. As far as I know, FF 3.6 should be using *xulrunner-1.9.2*, but I only have *xulrunner-1.9.1* installed. I also installed FF 3.6pre 64bit form *ubuntu-mozilla-daily*.

Perhaps you could go to Synaptic and select all those xulrunner for removal and check it complains about dependencies. If not, then just remove those you don't need and then try to re-install the one actually used by Firefox 3.6.

You could also achieve that with this command:

```
sudo apt-get autoremove
```

It will suggest to remove packages that are no longer needed.

---

### Post by AdemoS on 2010-01-22
> **lovinglinux said:**
> It's weird. As far as I know, FF 3.6 should be using *xulrunner-1.9.2*, but I only have *xulrunner-1.9.1* installed. I also installed FF 3.6pre 64bit form *ubuntu-mozilla-daily*.

Perhaps you could go to Synaptic and select all those xulrunner for removal and check it complains about dependencies. If not, then just remove those you don't need and then try to re-install the one actually used by Firefox 3.6.

No complaints, same issue. 




> **lovinglinux said:**
> 
You could also achieve that with this command:

```
sudo apt-get autoremove
```

It will suggest to remove packages that are no longer needed.

Tried that, but it wanted to remove a huge list of things, some of which I needed. It did want to remove xulrunner-1.9.2 though; so I went into Synaptic and removed that one----no change, same error.


By the way, I'm typing this from Firefox 3.7, which runs just fine...but I was trying to avoid using Firefox 3.7 because it's only an alpha and can be unstable.

---

### Post by lovinglinux on 2010-01-22
> **AdemoS said:**
> No complaints, same issue. 

Try this, if it doesn't complain about some gnome dependencies (I'm on KDE).

```
sudo apt-get purge firefox firefox-3.5
sudo apt-get install firefox-3.6
```

I guess it will complain about *ubuntu-desktop*, which is a meta-package. You can live without it if you do only clean installs, not Ubuntu upgrades. Or you can install this package again, before an upgrade. Or you can try this:

```
sudo apt-get purge firefox firefox-3.5
sudo apt-get ubuntu-desktop
```

---

### Post by akwala on 2010-01-22
Same problem here -- Ubuntu 9.10 amd64.

Reinstalled xulrunner-1.9.1 and uninstalled xulrunner-1.9.2. This hasn't fixed the problem.

(BTW, I also have FF 3.6 updated via ubuntuzilla, and it launches fine.)

---

### Post by akwala on 2010-01-22
@lovinglinux - I did the following, per your suggestion (there was no complaint re ubuntu-desktop):

sudo apt-get purge firefox firefox-3.5
sudo apt-get install firefox-3.6
sudo apt-get install firefox-gnome-support

The problem persists.

---

### Post by lovinglinux on 2010-01-22
> **akwala said:**
> @lovinglinux - I did the following, per your suggestion (there was no complaint re ubuntu-desktop):

sudo apt-get purge firefox firefox-3.5
sudo apt-get install firefox-3.6
sudo apt-get install firefox-gnome-support

The problem persists.

Perhaps you should send a bug report. It seems there was a similar probem on an alpha version that should have been fixed.

---

### Post by alfito on 2010-01-22
Same problem here.
I try'ed also switching to default repository, installed firefox, added ppa repo and upgraded, but same "permission denied" issue...

---

### Post by linoleum13 on 2010-01-22
I have the same problem with slightly different error messages:
/usr/lib/firefox-3.6.1pre/firefox: 59: dirname: Permission denied
/usr/lib/firefox-3.6.1pre/firefox: 88: /bin/pwd: Permission denied
/usr/lib/firefox-3.6.1pre/run-mozilla.sh: 39: dirname: Permission denied
/usr/lib/firefox-3.6.1pre/firefox-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory

This occurs when I execute the firefox script in /usr/bin/. (type which firefox at the comman line to see which firefox script you are probably using).

I got firefox3.6 to run, however, by executing the firefox script from the /usr/lib/firefox-3.6.1pre/ directory. It seems that the firefox launcher script is not running correctly unless it is executed in its own directory. 

Im sure its a bug with the PPA installation. Hopefully, they will fix it soon.

---

### Post by jimmyfergus on 2010-01-22
Seems to be related to this issue, about the apparmor profile:[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/510644](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/510644)

Fixed by adding the following dirname and pwd lines to /etc/apparmor.d/usr.bin.firefox-3.6 and then doing /etc/intit.d/apparmor reload

***************
*** 60,65 ****
--- 60,67 ----
    # These are needed when a new user starts firefox and firefox.sh is used
    /usr/lib/firefox-3.*/** ixr,
    /usr/bin/basename ixr,
+   /usr/bin/dirname ixr,
+   /usr/bin/pwd ixr,
    /sbin/killall5 ixr,
    /bin/which ixr,
    @{PROC}/ r,

---

### Post by nilarimogard on 2010-01-22
I fixed it by just: sudo apt-get remove firefox && sudo apt-get install firefox

Now firefox-3.6 is firefox (3.5 has been replaced with 3.6 for the default name "firefox)! That's what cause this error.

Update: I was wrong, I was in the firefox-3.6.1pre directory when I executed Firefox, I though I launched it from /usr/bin.

---

### Post by bangmalley on 2010-01-22
> **jimmyfergus said:**
> Seems to be related to this issue, about the apparmor profile:[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/510644](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/510644)

Fixed by adding the following dirname and pwd lines to /etc/apparmor.d/usr.bin.firefox-3.6 and then doing /etc/intit.d/apparmor reload

***************
*** 60,65 ****
--- 60,67 ----
    # These are needed when a new user starts firefox and firefox.sh is used
    /usr/lib/firefox-3.*/** ixr,
    /usr/bin/basename ixr,
+   /usr/bin/dirname ixr,
+   /usr/bin/pwd ixr,
    /sbin/killall5 ixr,
    /bin/which ixr,
    @{PROC}/ r,

The config has been automatically added after I install 3.6
So, I just need to 
```
sudo /etc/init.d/apparmor reload
```
and I can start using firefox
Anyway, thanks for the fix. :D


**Edit:** turns out the command can only solve the problem temporary, I can't launch firefox after restart.
I didn't add these two lines, that's why.
```
  /usr/bin/dirname ixr,
  /usr/bin/pwd ixr,
```

---

### Post by He4dShOt on 2010-01-22
> **bangmalley said:**
> The config has been automatically added after I install 3.6
So, I just need to 
```
sudo /etc/init.d/apparmor reload
```and I can start using firefox

It's worked for me too, thanks :D

---

### Post by anagdul on 2010-01-22
> **He4dShOt said:**
> It's worked for me too, thanks :D

Me too! I had exactly the same problem after the last update. I tried removing/installing/reinstalling, but nothing worked. I finally installed Midori and came here to find this answer and I'm glad I did!
There is only one thing I'd like to add - BEFORE you start playing games trying to fix the firefox starting problem, go to your home files, save a copy of your .mozilla folder and rename it .mozilla_old (or something similar). That way, when you finally do get Firefox running again, you can delete the new .mozilla folder, rename your .mozilla_old back to .mozilla and keep your bookmarks and configurations the way they were before.

Thanks much for the help!

---

### Post by !@!@! on 2010-01-22
> **bangmalley said:**
> The config has been automatically added after I install 3.6
So, I just need to 
```
sudo /etc/init.d/apparmor reload
```
and I can start using firefox
Anyway, thanks for the fix. :D
This worked for me! Thanks so much man!

---

### Post by AdemoS on 2010-01-22
> **bangmalley said:**
> 
So, I just need to 
```
sudo /etc/init.d/apparmor reload
```
and I can start using firefox

This worked for me too.

But if running that command is necessary, then the package maintainers should add it to the script, so that other people don't encounter the same snag we did. 

Should I file a bug?

---

### Post by akwala on 2010-01-23
> **AdemoS said:**
> 
But if running that command is necessary, then the package maintainers should add it to the script, so that other people don't encounter the same snag we did. 

Should I file a bug?

I'd say so. I just had to do the apparmor reload again, after an update. It is most likely not intended behavior to require this after updates.

---

### Post by AdemoS on 2010-01-23
After rebooting, I had to use the command again...

Definitely filing a bug.

---

### Post by akwala on 2010-01-23
As a workaround, I switched the apparmor profiles for firefox to complain mode (they were in enforce mode.) Now I don't need to reload the apparmor profiles after every restart.

I had the following profiles:

[LIST]
[*]/etc/apparmor.d/usr.bin.firefox
[*]/etc/apparmor.d/usr.bin.firefox-3.5
[*]/etc/apparmor.d/usr.bin.firefox-3.6
[/LIST]
Of these, I disabled the one for firefox-3.5, since I no longer have FF 3.5, and switched the other 2 to complain mode. See the refs below for details:
- [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)
- [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

---

### Post by AdemoS on 2010-01-24
> **akwala said:**
> As a workaround, I switched the apparmor profiles for firefox to complain mode (they were in enforce mode.) Now I don't need to reload the apparmor profiles after every restart.


Is there any security risk, from adjusting AppArmor settings for a web browser?

---

### Post by akwala on 2010-01-25
> **AdemoS said:**
> Is there any security risk, from adjusting AppArmor settings for a web browser?

Turning off 'enforce' would mean that AppArmor wouldn't enforce the rules for Firefox to access system resources; instead, it'll 'complain' about any rule violations in /var/log/messages. This is obviously "riskier" than letting AppArmor enforce its rules. However, to put this in perspective, AppArmor support was added for FF 3.5 in Ubuntu 9.10, so the risk would be no greater than when you used FF in Ubuntu 9.04 and earlier.

Disclaimer: The above is based on what I've gathered -- this issue has introduced me to AppArmor, and I don't have detailed knowledge of it yet. Check out the links in my previous post and here's one more: [http://apparmor.wiki.kernel.org/index.php/Main_Page](http://apparmor.wiki.kernel.org/index.php/Main_Page)

---

### Post by selectstar on 2010-01-26
this is unbelivable! I already wasted a few hours at work where Firefox was having problems with Firebug (ubuntu 64 bit). I managed to fix it but now I am unable to make firefox plugin work.

The worst thing is that I got back home now and discovered that firefox won't start at all on my laptop (ubuntu i386). On the task bar "firefox is starting" appears. After a few seconds it disappears and that's all. I have tried all suggestions in this post (ie. uninstalling etc...)

---

### Post by AdemoS on 2010-01-26
> **akwala said:**
> Turning off 'enforce' would mean that AppArmor wouldn't enforce the rules for Firefox to access system resources; instead, it'll 'complain' about any rule violations in /var/log/messages. This is obviously "riskier" than letting AppArmor enforce its rules. However, to put this in perspective, AppArmor support was added for FF 3.5 in Ubuntu 9.10, so the risk would be no greater than when you used FF in Ubuntu 9.04 and earlier.
[/url]

For now I decided to use Firefox 3.7a, simply because I didn't want to have to tweak every computer using that PPA.

But if the 3.7 alpha starts giving me problems, I'll definitely use your tip in the future.

---

