---
title: "Firefox profiles, multiple versions"
date: 2010-02-01
forum: General Help
---

### Post by Luxx on 2010-02-01
I have two versions of Firefox, Namoroka and Minefeild (Firefox3.7a1pre). 

I realize Minefield is supposed to be buggy, especially the alpha prerelease versions, but I wanted to try it and I'm not sure this qualifies as a bug. I have tried several times over the last few days to set up different profiles to avoid corruption on my main profile, but it's not working. 

When I install firefox-3.7a1pre and launch it, then go back to Namaroka, I don't have Namaroka anymore. It's also Minefield. both are using the same command to open and I think this is the problem. The command they use is "firefox" or "firefox %u" (no difference without %u). 

I have used two versions before, but only one launched with "firefox" the other launched with "firefox-3.5." I never even had to worry about different profiles with them. They didn't interfere with each other. I could even have them both open at the same time.

I was expecting Minefield to launch with command "firefox-3.7" or something. Is there a way I can get one of them to open with a different command so they aren't competing, or merging or whatever they are doing? 

Is this a profile issue that be handled setting up different profiles? If so, I've missed a step somewhere.

I've googled all over and found tips for Windows users having similar issues, but they use the Windows graphical interfaces to set up separate profiles in order to fix the problem. I have pored over at least a dozen websites on firefox profiles and haven't been able to make anything work. Some of them were for Ubuntu, but details were strangely sparse.

Any help greatly appreciated.

---

### Post by raktarok on 2010-02-01
Have you tried launching them from terminal? What happens when you type firefox and then press tab in terminal? Do you get a list of commands starting with firefox?  

Or you can post the output of these:

```
ls -l /usr/bin/firefox*
ls -ld /usr/lib/firefox*
```

This will show how the two versions are installed. You used deb files to install them, right?

---

### Post by Luxx on 2010-02-01
I had removed and reinstalled them both, but now only Namoroka launches no matter how I try to launch them. There is only a link to firefox3.6.2pre. Outputs in following post.

---

### Post by Luxx on 2010-02-01
user@Unknown:~$ ls -l /usr/bin/firefox*
lrwxrwxrwx 1 root root 34 2010-01-31 23:44 /usr/bin/firefox -> ../lib/firefox-3.6.2pre/firefox.sh
user@Unknown:~$ ls -ld /usr/lib/firefox*
drwxr-xr-x  3 root root 4096 2009-04-29 13:52 /usr/lib/firefox
drwxr-xr-x  4 root root 4096 2010-01-31 23:44 /usr/lib/firefox-3.5.4
drwxr-xr-x 10 root root 4096 2010-01-31 23:44 /usr/lib/firefox-3.6.2pre
drwxr-xr-x  5 root root 4096 2010-01-31 23:44 /usr/lib/firefox-addons

---

### Post by raktarok on 2010-02-01
Is firefox-3.5.4 known by Namoroka?
If so, post the output of following.

```
ls /usr/lib/firefox-3.5.4/*.sh

```
Or you can go that directory and see if there is any script file or executable file with which you can launch firefox.

---

### Post by Luxx on 2010-02-01
Much to my surprise Namaraoka is firefox3.6.2pre. I think 3.5.4 was Shiretoko and I didn't like it.

user@Unknown:~$ ls /usr/lib/firefox-3.5.4/*.sh
ls: cannot access /usr/lib/firefox-3.5.4/*.sh: No such file or directory
user@Unknown:~$ ls /usr/lib/firefox-3.6.2pre/*.sh
/usr/lib/firefox-3.6.2pre/firefox.sh  /usr/lib/firefox-3.6.2pre/run-mozilla.sh
user@Unknown:~$

---

### Post by raktarok on 2010-02-01
Can you post the output of this then?

```
ls /usr/lib/firefox-3.5.4/
```

And how did you install Minefield? Did you use a ppa or a repo? Or did you download an archive file? Where is it installed, is it in /opt directory?

```
ls /opt
```

Also, let's see what's in the folder /usr/lib/firefox.
```

ls /usr/lib/firefox
```

---

### Post by Luxx on 2010-02-01
The firefox shellscript file for Minefield (firefox3.7a1pre) is in /usr/opt/mozilla/firefox. Double-clicking on it opened Minefield, but I swear the first time it opened Namaroka. There doesn't seem to be a link in /usr/lib anywhere.

user@Unknown:~$ ls /usr/lib/firefox-3.6.2pre/*.sh
/usr/lib/firefox-3.6.2pre/firefox.sh  /usr/lib/firefox-3.6.2pre/run-mozilla.sh
user@Unknown:~$ ls /usr/lib/firefox-3.5.4/
components  updates
user@Unknown:~$ ls /opt
boxee  firefox  mozilla
user@Unknown:~$ ls /usr/lib/firefox
plugins

I installed Minefield from the nightly builds.
firefox-3.7a1pre.en-US.linux-i686.tar.bz2

---

### Post by Luxx on 2010-02-01
So, I guess I have now successfully launched it, but was hoping to get to the point where I can add a launcher to the panel as I have before.

---

### Post by raktarok on 2010-02-01
You can link the script in /usr/opt/mozilla/firefox to /usr/bin/ and then launch it. Do this:

```
sudo ln -s /usr/opt/mozilla/firefox/script_name /usr/bin/firefox-minefield
```

Now the command firefox-minefield will launch the minefield version, while command firefox only will launch namoroka. Edit the launchers if you are using them.

If you want have a separate profile for each one, then you may have to start one of them like this. (here, I choose namoroka)
```
firefox -ProfileManager	
```
Then create a new profile, and next time, start namoroka with that profile:
```
firefox -P newly_created_profile_name
```

Edit the launchers and you should be all set.

---

### Post by Luxx on 2010-02-01
You said you choose Namaroka above, but what if I wanted to choose a different profile for Minefield?

---

### Post by Luxx on 2010-02-01
Typing firefox -ProfileManager resulted in launching Namaroka, but the profile manager did not come up.

---

### Post by raktarok on 2010-02-01
> **Luxx said:**
> You said you choose Namaroka above, but what if I wanted to choose a different profile for Minefield?

Just replace the firefox in the commands with firefox-minefield, if you have named the link file firefox-minefield, like I suggested. Make sure that you link the correct script file in /usr/opt/mozilla/firefox.

---

### Post by raktarok on 2010-02-01
> **Luxx said:**
> Typing firefox -ProfileManager resulted in launching Namaroka, but the profile manager did not come up.

Close all firefox instances and then try this both:

firefox -P 
firefox -ProfileManager

You should have a window prompting you to select/create profile. (unless the pre-release versions and alpha versions like namoroka and minefield disable them in their setup)

Also use firefox --help to see if the options are different for this version.

Why are you using unstable releases of firefox anyway? firefox-3.6 is out recently and you could use that.

---

### Post by Luxx on 2010-02-01
firefox-minefield isn't doing anything. I think I created a link with a typo, trying to sort it out. brb

---

### Post by raktarok on 2010-02-01
Do this and you will know if the link is valid or not, if you have not done this already.

```
sudo ls -l /usr/bin/firefox-minefield
```

If there is no link, you may have mistyped the script name.
```
ls -l /usr/opt/mozilla/firefox/*.sh
```

---

### Post by Luxx on 2010-02-01
I thought that was supposed to be the stable version, but ended up with 3.6.2...? My intention was to have one stable and one dev version. I'm not too worried about Namaroka though.

user@Unknown:~$ sudo ln -s /usr/opt/mozilla/firefox/firefox /usr/bin/firefox-minefield
[sudo] password for user: 
ln: creating symbolic link `/usr/bin/firefox-minefield': File exists
user@Unknown:~$ firefox-mozilla -ProfileManager
firefox-mozilla: command not found

I thought I knew what I did and had it sorted, but I have a broken link.

---

### Post by raktarok on 2010-02-01
user@Unknown:~$ firefox-mozilla -ProfileManager
firefox-mozilla: command not found

Why are you doing firefox-mozilla? Do firefox-minefield -P. It should work.

The link does not seem to be broken. To comfirm, check this:

sudo ls -l /usr/bin/firefox-minefield

(if the output is in red, then the link is broken)

---

### Post by Luxx on 2010-02-01
These things happen at 3:47am ;)

Trying this again.

---

### Post by raktarok on 2010-02-01
> **Luxx said:**
> These things happen at 3:47am ;)

Trying this again.

haha..its 5:51 am here and I should be getting some sleep now. :)
Follow all of this carefully, and you should have it working. 

Feel free to post if you have further problems, others will be still here to help you. Good luck!

---

### Post by Luxx on 2010-02-01
user@Unknown:~$ firefox-minefield
firefox-minefield: command not found
user@Unknown:~$ sudo ls -l /usr/bin/firefox-minefield
lrwxrwxrwx 1 root user 32 2010-02-01 03:44 /usr/bin/firefox-minefield -> /usr/opt/mozilla/firefox/firefox

(not in red)

The file I double-clicked to launch Minefield was named simply firefox. There was not an additional file named firefox.sh like there was for Namaroka. Does this make a difference? I would think it should work since double-clicking it launched Minefield, firefox-minefield (even the right words with the right spelling) doesn't seem to work.

Navigating to /usr/bin/firefox-minefield shows an icon with a lock and X on it. Preferences says Type: link (broken)(inode/symlink)

---

### Post by Luxx on 2010-02-01
Wait, is that the right place? usr/bin?

---

### Post by lovinglinux on 2010-02-01
Mozilla has changed the update policy and Canonical is trying to follow. This is generating a lot of confusion with packages, commands and profiles.

I'm going to write an article explaining this subject, but I need a couple of hours, because there are several possible scenarios.

In a nut shell, when you install Namoroka from the ubuntu-mozilla PPA repositories it upgrades firefox-3.5. So instead of using firefox-3.6 command to launch it, you need to use firefox-3.5 command. Weird, but that is the way it does now, since Namoroka is considered a major-minor update. Nevertheless, the files are physically stored under /usr/lib/firefox-3.6.

I don't know about Minefield but I suspect it behaves the same way. The same thing didn't happen with Shiretoko on Jaunty, because it was installed as a completely separate package and when you started it, it was configured to clone your profiles folder from  ~/.mozilla/firefox to ~/.mozilla/firefox-3.5.

Namoroka form the *ubuntu-mozilla-daily* was behaving this way, in regard to profiles, until the final release from Mozilla. Then, it started to use the same profiles folder of your default installation. So if you installed before the final release, you might have a duplicated profiles folder.

You don't need to have a complete separate profiles folder for each version. I really don't get it why they do that, instead of simply forcing the browser to start the profile manager after the upgrade. Cloning the entire profiles folder just generates confusion.

The thing is that it doesn't matter which version you are using, as long as you create a new profile from the Profile Manager, it won't interfere with the other profiles. They can be all stored under ~/.mozilla/firefox without issues and if you start all versions of Firefox adding -P to the command, they will open the Profile Manager from where you can choose the profile according to each version. 

So take a look under ~/.mozilla to see if you have different versions of profiles folder and report back.

---

### Post by lovinglinux on 2010-02-01
Luxx, stop. Let's do it the right way. Start over.

From what I have read, you have installed Minefield from a downloaded package. What about Namoroka, how did you install it?
Are you running 32bit or 64bit?

What versions do you want to use at the same time?

What folders do you see under ~/.mozilla ?

---

### Post by Luxx on 2010-02-01
For Namaroka there is a link in usr/lib/firefox3.6.2pre, but in usr/lib/mozilla-firefox there is only a folder for extensions. I had a thought there, but I'm getting too tired to figure out where it was trying to go.

I'm not having problems with Namaroka. It is behaving. I am having a problem launching Minefield. I can only launch it by double-clicking on the shell script named firefox in /opt/mozilla/firefox. I cannot launch it from a terminal command at all.

---

### Post by Luxx on 2010-02-01
In ~./mozilla I have extensions, firefox, firefox-3.5.abandoned, firefox-3.7

---

### Post by lovinglinux on 2010-02-01
> **Luxx said:**
> For Namaroka there is a link in usr/lib/firefox3.6.2pre, but in usr/lib/mozilla-firefox there is only a folder for extensions. I had a thought there, but I'm getting too tired to figure out where it was trying to go.

I'm not having problems with Namaroka. It is behaving. I am having a problem launching Minefield. I can only launch it by double-clicking on the shell script named firefox in /opt/mozilla/firefox. I cannot launch it from a terminal command at all.

The correct command would be this:

```
/opt/firefox/firefox
```

To launch the profile manager with Minefield:

```
/opt/firefox/firefox -P
```

To launch the Profile Manager with Namoroka

```
firefox -P
```

or

```
firefox-3.5 -P
```

---

### Post by Luxx on 2010-02-01
I installed Namaroka by typing "sudo apt-get install firefox" and assumed that would get whatever stable version was in the main repos, but I have [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) in my sources list, so it probably came from there.

---

### Post by Luxx on 2010-02-01
Yes. That launches Namaroka. I want to launch Minefield.

---

### Post by lovinglinux on 2010-02-01
> **Luxx said:**
> In ~./mozilla I have extensions, firefox, firefox-3.5.abandoned, firefox-3.7

OK.

run these:

```
mv ~/.mozilla/firefox-3.7 ~/.mozilla/firefox-3.7.abandoned
ln -s ~/.mozilla/firefox ~/.mozilla/firefox-3.7
```

Start Minefield with this:

```
/opt/firefox/firefox -P -no-remote

```

This will start the Profile Manager using Minefield at the same time Namoroka is running.

Untick the option "Don't ask at startup". Then create a new profile trough the profile manager, giving an easy identifiable name like minefield.

Now you can star it.

From now on, every time you start Namoroka or Minefield, the profile manager will show first, so you can choose the correct profile according to browser version.

---

### Post by Luxx on 2010-02-01
WAIT, WAIT, hold on a minute.

If the Namaraoka files are in opt/firefox/firefox, then that will launch Namaroka, NOT Minefield. How is the computer supposed to know I want it to launch something else if I'm telling it to do the same thing? That makes no sense.

Forget about the profiles for a minute. I want to launch the application. This profile thing just seems to be confusing everyone.

---

### Post by lovinglinux on 2010-02-01
> **Luxx said:**
> Yes. That launches Namaroka. I want to launch Minefield.

You need to close Namoroka first or add -no-remote to the command:

```
/opt/firefox/firefox -P -no-remote
```

---

### Post by Luxx on 2010-02-01
We already got to the point where they could be launched separately and they are both on the default profile now. I just can't launch one of them without navigating through multitudes of folders.

---

### Post by lovinglinux on 2010-02-01
> **Luxx said:**
> WAIT, WAIT, hold on a minute.

If the Namaraoka files are in opt/firefox/firefox, then that will launch Namaroka, NOT Minefield. How is the computer supposed to know I want it to launch something else if I'm telling it to do the same thing? That makes no sense.

Forget about the profiles for a minute. I want to launch the application. This profile thing just seems to be confusing everyone.

Namoroka shouldn't be on /opt/firefox. Since you are using the ubuntu-mozilla-daily PPA, then Namoroka is installed under /usr/lib/firefox-3.6 or /usr/lib/firefox-3.6pre.

The are two possible explanations:

1) you are trying to launch Minefield with Namoroka already opened. 
2) You think you have Minefield on /opt/firefox but you don't. That's I why I suggested to start over. I won't take more than 5 minutes.

---

### Post by lovinglinux on 2010-02-01
Wait a little bit. I will post all commands you need to do it right.

---

### Post by Luxx on 2010-02-01
> **lovinglinux said:**
> Namoroka shouldn't be on /opt/firefox. Since you are using the ubuntu-mozilla-daily PPA, then Namoroka is installed under /usr/lib/firefox-3.6 or /usr/lib/firefox-3.6pre.

The are two possible explanations:

1) you are trying to launch Minefield with Namoroka already opened. 
2) You think you have Minefield on /opt/firefox but you don't. That's I why I suggested to start over. I won't take more than 5 minutes.

No, I have closed my browser every time I have tried something and I have to log in again. That's why it's taking so long to answer. And I'm not sure what you mean that Minefield isn't on opt/firefox. No it's not, it's in the folder /opt/mozilla/firefox/firefox (with that last 'firefox' being the script file that I launched it from).

I'm trying to go through your instructions here, sorry it's taking so long.

---

### Post by lovinglinux on 2010-02-01
Follow exactly these instructions and you won't have any further issues.

First lets remove all instances of Firefox:

```
sudo apt-get purge firefox
sudo apt-get purge firefox-3.5 
sudo apt-get purge firefox-3.6 
sudo apt-get purge firefox-3.6pre
```

Not all commands above will work. I'm just making sure you don't have any left-overs from previous installs.

Be careful with the next commands. Make sure the paths are correct, otherwise you might delete important stuff and screw your Ubuntu.

```
sudo rm -r /opt/mozilla
sudo rm -r /opt/firefox
```

One command will fail. Just ignore it.

Now install Namoroka:

```
sudo apt-get install firefox
```

Now download Minefiled 3.7a1pre from [here]("ftp://ftp.mozilla.org/pub/mozilla.org/firefox/tinderbox-builds/electrolysis-linux/1264941020/firefox-3.7a1pre.en-US.linux-i686.tar.bz2") and save it on your home directory. (I'm assuming you have 32bit)

Then extract it to /opt with this command:

```
sudo tar -jxvf firefox-3.7a1pre.en-US.linux-i686.tar.bz2 -C /opt
```

Now, lets unify your profiles:

```
mv ~/.mozilla/firefox-3.7 ~/.mozilla/firefox-3.7.abandoned
ln -s ~/.mozilla/firefox ~/.mozilla/firefox-3.7
```

Now you can start Namoroka with  this:

```
firefox -P
```

and you can start Minefield with this:

```
/opt/firefox/firefox -P
```

The -P will force the profile manager to start first, so you can choose which profile to use with each version.

If you need to start both versions at the same time, add -no-remote to the commands:

---

### Post by Luxx on 2010-02-01
What is that link for the Minefeild download?

---

### Post by Luxx on 2010-02-01
I canot go forward with these instructions until I understand what you are doing. Why are we unifying the profiles and what is that link for Minefield?

---

### Post by lovinglinux on 2010-02-01
> **Luxx said:**
> What is that link for the Minefeild download?

The Mozilla FTP directory. Where did you get your file from?

---

### Post by lovinglinux on 2010-02-01
> **Luxx said:**
> I canot go forward with these instructions until I understand what you are doing. Why are we unifying the profiles and what is that link for Minefield?

See my previous post.

Unifying your profile directory is creating a symlink, so you will be sharing the same folder between the two versions. By default Minefield creates a new folder for storing your profiles, but you don't need that, as long as you create one profile for each version with the profile manager.

So the commands I have provided will first rename the existing profiles folder used by Minefield, so you don't loose it if you need to recover something from it later.

Then it will create a smylink between ~/.mozilla/firefox and ~/.mozilla/firefox-3.7. What this means is that all your profiles will be physically stored under ~/.mozilla/firefox but they will also be used by Minefield, which will "see" the same profiles as if they were actually under ~/.mozilla/firefox-3.7.

---

### Post by Luxx on 2010-02-01
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.7a1pre.en-US.linux-i686.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.7a1pre.en-US.linux-i686.tar.bz2)

The link you gave me was 
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/tinderbox-builds/electrolysis-linux/1264941020/firefox-3.7a1pre.en-US.linux-i686.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/tinderbox-builds/electrolysis-linux/1264941020/firefox-3.7a1pre.en-US.linux-i686.tar.bz2)

And what is this about unifying profiles?


ARGH! they show up the same but yours had tinderbox-builds/electrolysis-linux/1264941020 in the middle of it.

---

### Post by lovinglinux on 2010-02-01
> **Luxx said:**
> [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.7a1pre.en-US.linux-i686.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.7a1pre.en-US.linux-i686.tar.bz2)

The link you gave me was 
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/tinderbox-builds/electrolysis-linux/1264941020/firefox-3.7a1pre.en-US.linux-i686.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/tinderbox-builds/electrolysis-linux/1264941020/firefox-3.7a1pre.en-US.linux-i686.tar.bz2)

ARGH! they show up the same but yours had tinderbox-builds/electrolysis-linux/1264941020 in the middle of it.

See [this](https://developer.mozilla.org/en/Downloading_Nightly_or_Trunk_Builds) for explanation. Sorry, I was kind of lazy to search for it on the nightly directory. Although I have already used Firefox from the tinderbox, I think would be better to use the nightly-trunk.

[https://developer.mozilla.org/en/Downloading_Nightly_or_Trunk_Builds](https://developer.mozilla.org/en/Downloading_Nightly_or_Trunk_Builds)

> **Luxx said:**
> And what is this about unifying profiles?

See previous post.

---

### Post by Luxx on 2010-02-01
EXCELLENT!!
That seems to have cleaned things up nicely. 

I had not used the purge command before.

I went with the nightly trunk. I did after all set up profiles for each version.
Everything seems to now be in it's place. 
I have created a nice little launcher for Minefield as well, although I'll have to look for the Minefield icon.
Thank you for helping me get this all sorted and working.

---

### Post by lovinglinux on 2010-02-01
> **Luxx said:**
> EXCELLENT!!
That seems to have cleaned things up nicely. 

I have created a nice little launcher for Minefield as well. 
Thank you for helping me get this all sorted and working.

You are welcome. You might also like my [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Good luck.

---

