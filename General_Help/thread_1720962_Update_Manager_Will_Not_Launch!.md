---
title: "Update Manager Will Not Launch!"
date: 2011-04-03
forum: General Help
---

### Post by freesparks on 2011-04-03
Hello all,

  I've been trying to upgrade and have had no luck.  First off, the Update Manager will not launch when I go to System > Administration to launch it.  Second, in relation to this, there is a red circle with a white line through it on my panel on the desktop:

When I right click on it I get these as choices:

Show Updates
Install all Updates
Check For Updates
Start Package Manager 
Show Notifications
Preferences

I'm guessing this is stemming from a bad repository that I set because when I type:
sudo apt-get upgrade

I get this in the Terminal:

```
~$ sudo apt-get upgrade
[sudo] password for myname: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
/var/lib/dpkg/info/gconf2.postinst: 52: gconf-schemas: Permission denied
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
Setting up python-gmenu (2.30.4-0ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
/var/lib/dpkg/info/python-gmenu.postinst: 1: /usr/share/gnome-menus/update-gnome-menus-cache: Permission denied
/var/lib/dpkg/info/python-gmenu.postinst: 25: update-python-modules: Permission denied
dpkg: error processing python-gmenu (--configure):
 subprocess installed post-installation script returned error exit status 126
Errors were encountered while processing:
 gconf2
 gdm
 python-gmenu
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Other than that I'm just plain lost. Any help on this would be greatly appreciated.

Best Regards,

freesparks

---

### Post by wilee-nilee on 2011-04-03
Try these two commands.
```

sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

---

### Post by freesparks on 2011-04-04
Hello wilee-nilee,

    Thanks so much for the reply.  I'm not sure what this is suppose to do but I'm getting similar errors do the one that I posted.  This is what I get after I type the first command:

```
Setting up python-gmenu (2.30.4-0ubuntu1) ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
/var/lib/dpkg/info/python-gmenu.postinst: 1: /usr/share/gnome-menus/update-gnome-menus-cache: Permission denied
/var/lib/dpkg/info/python-gmenu.postinst: 25: update-python-modules: Permission denied
dpkg: error processing python-gmenu (--configure):
 subprocess installed post-installation script returned error exit status 126
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
/var/lib/dpkg/info/gconf2.postinst: 52: gconf-schemas: Permission denied
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-gmenu
 gconf2
 gdm
```

After typing the second command, I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  ipheth-dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
/var/lib/dpkg/info/gconf2.postinst: 52: gconf-schemas: Permission denied
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
Setting up python-gmenu (2.30.4-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
/var/lib/dpkg/info/python-gmenu.postinst: 1: /usr/share/gnome-menus/update-gnome-menus-cache: Permission denied
/var/lib/dpkg/info/python-gmenu.postinst: 25: update-python-modules: Permission denied
dpkg: error processing python-gmenu (--configure):
 subprocess installed post-installation script returned error exit status 126
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 gconf2
 gdm
 python-gmenu
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Again, I can't thank you enough  for all your help.

---

### Post by matt_symes on 2011-04-05
Hi

What version of Ubuntu are you using ?

Can you post the output of

```
cat /var/lib/dpkg/info/gconf2.postinst
ls -l $(which gconf-schemas)
```

Small -L for -l in ls.

Kind regards

---

### Post by freesparks on 2011-04-05
hello matt_symes,

   Thanks so much for your reply.  This is the result that I'm getting for the output for the commands that you had me run,  given my small amount of intuition, I have a feeling this is the result for something have to do with read and write privileges, how this occurred I have no idea:

myname@mymachine:~$ cat /var/lib/dpkg/info/gconf2.postinst
#!/bin/sh

set -e

signal_daemons()
{
    # Tell all running daemons to reload their databases
    kill -s HUP `pidof gconfd-2` >/dev/null 2>&1 || true
}

if [ "$1" = triggered ]; then
    for trigger in $2; do
        case $trigger in
            /usr/share/gconf/schemas)
                gconf-schemas --register-all --no-signal
                ;;
            /usr/share/gconf/defaults)
                update-gconf-defaults --no-signal
                ;;
            /usr/share/gconf/mandatory)
                update-gconf-defaults --no-signal --mandatory
                ;;
        esac
    done
    signal_daemons
    exit 0
fi

if [ "$1" = configure ] && dpkg --compare-versions "$2" lt 2.26.2-4; then
    update-alternatives \
        --install /usr/bin/gconftool gconftool /usr/bin/gconftool-2 25 \
        --slave /usr/share/man/man1/gconftool.1.gz gconftool.1.gz \
                /usr/share/man/man1/gconftool-2.1.gz
fi



for GCONF_DIR in \
                 /etc/gconf/gconf.xml.mandatory \
                 /etc/gconf/gconf.xml.defaults ; do
  GCONF_TREE=$GCONF_DIR/%gconf-tree.xml
  if [ ! -f "$GCONF_TREE" ]; then
    gconf-merge-tree "$GCONF_DIR"
    chmod 644 "$GCONF_TREE"
    find "$GCONF_DIR" -mindepth 1 -maxdepth 1 -type d -exec rm -rf \{\} \;
    rm -f "$GCONF_DIR/%gconf.xml"
  fi
done

# Upon installation/upgrade, regenerate all databases, because in this case 
# there will be no trigger run
gconf-schemas --register-all --no-signal
update-gconf-defaults --no-signal
update-gconf-defaults --no-signal --mandatory
signal_daemons

myname@mymachine:~$ ls -l $(which gconf-schemas)
-rwxr-xr-x 1 root root 4359 2010-10-10 03:58 /usr/sbin/gconf-schemas
myname@mymachine:~$

---

### Post by drs305 on 2011-04-05
The updates are hanging up on gconf2's post-installation script (which is why Matt asked to see it).

You could try moving the postinst file and reinstalling gconf2. It will replace the missing postinst file and this may fix the problem if the file itself was the problem.

Be careful using the sudo command; type them carefully and verify before hitting ENTER (or copy them).

```

sudo mv /var/lib/dpkg/info/gconf2.postinst /root/Desktop # Move file to root's Desktop
sudo apt-get install --reinstall gconf2
sudo apt-get update

```
If the problem isn't fixed, you can leave it as it is or run the following to move the original postinst file back:
```
sudo cp /root/Desktop/gconf2.postinst /var/lib/dpkg/info/
```

---

### Post by freesparks on 2011-04-05
No,  no luck unfortunately, copied the commands exactly as you told me to do so.  Now, the problem seems to be how to revert the file back to:

/var/lib/dpkg/info/

I can't seem to find the file!  The only thing that I noticed is that upon running this command:

sudo mv /var/lib/dpkg/info/gconf2.postinst /root/Desktop

I know see "Desktop" when I log on as root by typing:

su -

gconf2.postinst is not in /home/myname/Desktop

Please help me to revert this file back to its original location.

Best Regards,

freesparks

---

### Post by drs305 on 2011-04-05
> **freesparks said:**
> 
I know see "Desktop" when I log on as root by typing:

gconf2.postinst is not in /home/myname/Desktop

Please help me to revert this file back to its original location.



The last command I posted should have copied it back to its original location, but if you want to do it via a file browser opened as root, it will be in /root/Desktop. It's on root's Desktop, not yours.

Also, were the error messages exactly the same?

---

### Post by freesparks on 2011-04-05
Hello drs305,

 I can't thank you enough for your continued help.


These are the errors that I am now getting when I try doing the updates.

E: /var/cache/apt/archives/python-gtkspell_2.25.3-5ubuntu2.1_i386.deb: subprocess new pre-removal script returned error exit status 126
E: /var/cache/apt/archives/python-imobiledevice_1.0.6-1ubuntu1~maverick1_i386.deb: subprocess new pre-removal script returned error exit status 126
E: /var/cache/apt/archives/python-plist_1.4-1ubuntu1~mp.averick1_i386.deb: subprocess new pre-removal script returned error exit status 126

This is what I am getting in the Terminal when I try to run the third command that you said to run:

myname@mycomputer:/$ sudo cp /root/Desktop/gconf2.postinst /var/lib/dpkg/info/
cp: cannot stat `/root/Desktop/gconf2.postinst': Not a directory

Just to give a more detailed explanation, this is what I'm getting in the Teminal when I try to access the file in /Desktop:

> root@mycpuname:~# cd Desktop                                                                                                                                                                   
-su: cd: Desktop: Not a directory                                                                                                                                                              
root@mycpuname:~# ls                                                                                                                                                                           
Desktop



Best Regards,

freesparks

---

### Post by drs305 on 2011-04-05
Well, so you can see what is going on, you can do it graphically. Open nautilus as root each folder:
```

gksu nautilus /root/Desktop /var/lib/dpkg/info
```
Right click the file in /root/Desktop and select 'copy'. Then click in the other browser (/var/lib....), right click and select Paste. It will ask if you want to replace the original (which is actually the newer) file.

---

### Post by freesparks on 2011-04-05
Hello drs305,

   Yes, indeed, I know thats what I'm suppose to do, the problem is this is the error that I am getting:

Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.

I'm not even able to go into the file.  Do I have to do,

chmod +x 0777 Desktop

in order to be able to go inside the file?

Thanks again for all your help.

Best Regards,

freesparks

---

### Post by drs305 on 2011-04-05
> **freesparks said:**
> Hello drs305,

   Yes, indeed, I know thats what I'm suppose to do, the problem is this is the error that I am getting:

Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.

I'm not even able to go into the file.  Do I have to do,

chmod +x 0777 Desktop

in order to be able to go inside the file?

Thanks again for all your help.

Best Regards,

freesparks

No, you shouldn't have to do anything. In fact, you do NOT want to change any root-owner permissions.

You could simply try to open Nautilus without designating the folders. then navigate to them:
```
gksu nautilus
```
You can also verify the folders exist:
```
sudo ls /root # Look for "Desktop"
sudo ls /var/lib/dpkg # Look for "info"

```

**Added:** Really, though, all you should need to verify is that the file gconf2.postinst exists in /var/log/dpkg/info. Most likely the old and new files are identical, since replacing the old one didn't solve the problem. Given the multiple failures, it appears that the failed installation could very well have affected more than just a file or two.

You can confirm the file still exists in the proper location with:
```
sudo ls -la /var/lib/dpkg/info/gconf2.postinst

```
which should return:
> -rwxr-xr-x 1 root root ......... /var/lib/dpkg/info/gconf2.postinst

---

### Post by freesparks on 2011-04-05
Again,

the file "Desktop" is showing itself but I am not able to access it, however when I run:

> sudo ls /var/lib/dpkg # Look for "info"

I get this:
```

alternatives  available-old  diversions      info  parts     statoverride-old  status-old  updates
available     cmethopt         diversions-old  lock  statoverride  status           triggers
```

And when I run this:
```
sudo ls -la /var/lib/dpkg/info/gconf2.postinst
```

I get this:

```
ls: cannot access /var/lib/dpkg/info/gconf2.postinst: No such file or directory
```

The File is in the /root/Desktop or /Desktop rather, which again I do not have access to.  Thanks so much for your help!!

Best Regards,

freesparks

---

### Post by drs305 on 2011-04-05
I guess we aren't communicating well. My fault.

/root/Desktop is a folder, or should be. There should be a file in /root/Desktop called gconf2.postinst, whose address/filename is /root/Desktop/gconf2.postinst 

Are you not able to open Nautilus as root and explore rather than use the command line?

That is the file you want to move back to /var/lib/dpkg/info/  
Or you can just run "sudo apt-get install --reinstall gconf2" and it should recreate the file.

It's possible the file is now named "Desktop". If you have both a *folder and a file* both called Desktop in /root/ that's probably what happened. But I'd use the reinstall method first to try to restore the gconf2.postinst file.

---

### Post by freesparks on 2011-04-06
Thanks so much drs305,

Running:

sudo apt-get install --reinstall gconf2

reinstalled it back to:

/var/lib/dpkg/info/


However, my problem still remains.  I hope this isn't something that will require a reinstall.  Again, thanks so much for your help.

Best Regards,

freesparks

---

### Post by drs305 on 2011-04-06
> **freesparks said:**
> However, my problem still remains.  I hope this isn't something that will require a reinstall.  Again, thanks so much for your help.

Which error messages are you now getting - the gconf2 or the python messages, or something else?

I am not an advocate of simply reinstalling to fix problems. The reality is that often it is much faster to reinstall than troubleshoot but only you can decide at what point to reinstall.

---

### Post by freesparks on 2011-04-06
Hello drs305,

   I'm not a fan either, after all this is how you learn.  When I type:

sudo apt-get upgrade

I get:

> sudo apt-get upgrade
[sudo] password for myusername: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  python-gtkspell python-imobiledevice
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/99.2kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 311004 files and directories currently installed.)
Preparing to replace python-gtkspell 2.25.3-5ubuntu2 (using .../python-gtkspell_2.25.3-5ubuntu2.1_i386.deb) ...
/var/lib/dpkg/info/python-gtkspell.prerm: 6: update-python-modules: Permission denied
dpkg: warning: subprocess old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: update-python-modules: Permission denied
dpkg: error processing /var/cache/apt/archives/python-gtkspell_2.25.3-5ubuntu2.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 126
/var/lib/dpkg/info/python-gtkspell.postinst: 6: update-python-modules: Permission denied
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 126
Preparing to replace python-imobiledevice 1.0.4-1ubuntu1~maverick1 (using .../python-imobiledevice_1.0.6-1ubuntu1~maverick1_i386.deb) ...
/var/lib/dpkg/info/python-imobiledevice.prerm: 6: update-python-modules: Permission denied
dpkg: warning: subprocess old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: update-python-modules: Permission denied
dpkg: error processing /var/cache/apt/archives/python-imobiledevice_1.0.6-1ubuntu1~maverick1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 126
/var/lib/dpkg/info/python-imobiledevice.postinst: 6: update-python-modules: Permission denied
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 126
Errors were encountered while processing:
 /var/cache/apt/archives/python-gtkspell_2.25.3-5ubuntu2.1_i386.deb
 /var/cache/apt/archives/python-imobiledevice_1.0.6-1ubuntu1~maverick1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyway, the errors are very similar to the ones that I get when I do the upgrade graphically.  Thanks again for all of your help.

Best Regards,

Nevins Duret

---

### Post by drs305 on 2011-04-06
I keep hoping someone will jump in here.

You might try the "configure -a" and "-f install" commands again, just to make sure that doesn't fix things.

Looking at the two packages that are currently causing problems, on my system if I remove python-gtkspell it removes that package and gwibber, which are no big deals to me. The imobile package doesn't seem critical either. I don't know if your system would allow you to remove them or not. You could try the "sudo apt-get install --reinstall xxxx" approach to see if that does anything. 

If you are able to fix this and then get errors on a different package (such as you no longer get the gconf2 errors), I would suspect this is going to go on almost forever. It could be a permission problem or just general corruption, or something else. I just don't know.

---

### Post by matt_symes on 2011-04-06
Hi

> **drs305 said:**
> 
If you are able to fix this and then get errors on a different package (such as you no longer get the gconf2 errors), I would suspect this is going to go on almost forever. It could be a permission problem or just general corruption, or something else. I just don't know.

I agree with drs305 here. This could go on for a long time pulling in other packages.

The only time i have come across this error was when the file a post installation script was trying to call did not exist. You are not having that problem. Your permissions on the file of the first error you had looked fine.

I don't think this is a trivial problem. However, i cannot be sure. There is obviously something amiss with your system but it depends on the amount of time you are prepared to put in to find out why. 

I am also not an advocate of reinstalling, however in this situation i might suggest it. Unless you can work through the problem (it could be hard to crack it from a distance) or create a test bed where you can compare and contrast i would suggest going with Occam's Razor.

Kind regards

---

### Post by freesparks on 2011-04-08
Hello ubuntu collective,

    I guess this is water under the bridge then, I really didn't want to do a reinstall, but it seems in this respect I have no luck in finding someone that has had this problem and know the root cause, no pun intended.  So, with that being said would someone be able to direct me on how to reinstall with saving all my current configurations and software.  Thanks so much for all the effort, but I really want to get back to programming.

Best Regards,

freesparks

---

### Post by drs305 on 2011-04-09
> **freesparks said:**
> Hello ubuntu collective,

    I guess this is water under the bridge then, I really didn't want to do a reinstall, but it seems in this respect I have no luck in finding someone that has had this problem and know the root cause, no pun intended.  So, with that being said would someone be able to direct me on how to reinstall with saving all my current configurations and software.  Thanks so much for all the effort, but I really want to get back to programming.

Best Regards,

freesparks

Sorry we weren't able to resolve the issue. If you can access your folders you could preserve your /home folder. When you make your new install, you could create a partition for /home, copy the existing folder into it, and then elect not to format the partition during the installation. That might preserve some of your configurations.

Additionally, you could copy your /etc folder, which has many of your configuration settings, and it might be possible to 'cherry pick' some of your old configuration settings to the new setup. I probably wouldn't use an entire folder file but you could open it to see what the existing settings used to be.

And your /var/lib/dpkg/status file contains the currently-installed packages, which you could save and use to create a package list for import into your new installation.

None of this would be particularly painless but it might help get your system back to a least a bit like the original.

And finally, once you get your system set up the way you want, there are ways to make it easier the next time. Synaptic can export/import your installed package lists, and there are many ways to either image or backup your settings (partimage, rsync, fsarchiver, etc).

Hopefully the next installation will go more smoothly.

---

### Post by freesparks on 2011-04-21
Hello all,

    Thank you so much for everyone's help.  I finally figured it out, or at least fixed the issue.
The issue was a result of my symbolic link not being set properly.  In changing it back to:
what it was and deleting files that having run the symbolic link had placed in the old location,
everything seems to have reverted back to it's original state and now I am able to update.

Best Regards,

freesparks

---

### Post by rebepoi on 2011-06-12
Hi!

I have same problem with my almost fresh install of kubuntu. How do you fix'd this symlinks? I'm noob with this things sry :(

---

