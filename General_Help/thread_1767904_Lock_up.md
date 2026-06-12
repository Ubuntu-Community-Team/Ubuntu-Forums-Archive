---
title: "Lock up"
date: 2011-05-26
forum: General Help
---

### Post by Kissell on 2011-05-26
I recently upgraded to 11.04 and now the computer locks up sometimes...  I'll be using it from across the network and then it'll just lock up, I'll physical go to that computer and it is entirely locked, no video output, no network connections, so I just reboot it and then it is okay again for a few hours...

but then it locks up again.

Maybe it is unrelated to the upgrade.

Where can I look to see why this is happening?

---

### Post by Topsiho on 2011-05-26
Hello,

I don't know why you mention that it's possibly unrelated to the upgrade. Did your computer lock up before the upgrade too?

If it did, then chances are much greater that the cause is hardware, and the first thing to check is the ram in your computer. So you could test this ram (working memory in the computer) using memtest, by starting the computer from the LiveCD, and select memtest from the menu. This test should be run a couple of passes, as sometimes a defective address shows only up intermittently.

If you get errors, then you know what's hurting you :)

Topsiho

---

### Post by Kissell on 2011-05-26
I just mention that it may not be software, because it might be unrelated to the upgrade to 11.04.  I don't want to jump to assuming it is Ubuntu causing the system to lock up, I have been using Ubuntu for years and it never had a problem like this before.  Then again, the box was fine before upgrading.  I just don't have enough information to say it is the new OS.

What I'm looking for is a way to see what caused the crash, or what was running at the time of the crash.  Certainly there are some system log files somewhere for me to access.

---

### Post by Kissell on 2011-05-26
I guess, what I really want, is to see the errors.  I'm not seeing any errors, and if the system is going to lock up I might expect there to be some errors written to a log file somewhere.

---

### Post by Kissell on 2011-05-26
The more I use Ubuntu 11.04 the more I think my problem is related to the upgrade.  Earlier this evening I opened a drive with about 400 folders and they started randomly disappearing from file manager..  that made me really worried, I thought they were being deleted in front of my eyes...  Turns out that when I access that folder from a symbolic link it shows up fine, but anytime I access the drive directly they kept disappearing, folders would just start rapidly disappearing...  

I installed via the GUI prompt from last october's version, 10.10 I think it was...  and I just remembered near the end of the installation it locked up.  The server had never locked up before, but near the end of the 11.04 upgrade it locked...  I powered it off and rebooted and it worked, so I didn't think anything of it anymore...  now a few days, and several lock ups later, I would like to know how to identify the problem so I can fix it without doing a fresh installation.

---

### Post by wildmanne39 on 2011-05-27
> **Kissell said:**
> The more I use Ubuntu 11.04 the more I think my problem is related to the upgrade.  Earlier this evening I opened a drive with about 400 folders and they started randomly disappearing from file manager..  that made me really worried, I thought they were being deleted in front of my eyes...  Turns out that when I access that folder from a symbolic link it shows up fine, but anytime I access the drive directly they kept disappearing, folders would just start rapidly disappearing...  

I installed via the GUI prompt from last october's version, 10.10 I think it was...  and I just remembered near the end of the installation it locked up.  The server had never locked up before, but near the end of the 11.04 upgrade it locked...  I powered it off and rebooted and it worked, so I didn't think anything of it anymore...  now a few days, and several lock ups later, I would like to know how to identify the problem so I can fix it without doing a fresh installation.
Hi, are you sure the upgrade completed, I tried to upgrade from a livecd it would get right to the end and revert back to the previous system. If the upgrade completed do you see the unity side launcher? did you install the drivers for video card that are in the additional drivers? What are your system specs? Is it possible this system needs cleaned so it is getting hot?

---

### Post by Topsiho on 2011-05-27
Looks like the upgrade process was not succesful, possibly aborted too soon. An upgrade (from one version to the [COLOR="Red"]next[/COLOR]) is really a gigantic update, and to my experience it is not always successful.
If it were, it would be a very nice way to get up to date again, versionwise. As it is, it is risky. And it takes time, and a lot of download, and a lot of memory and hard disk space. So possibly a shortage of memory space might have been the cause.

So probably you could better do a nice clean install. I don't know whether you have a partition specially for containing the /home directory. Anyway, before installing again you should back up your precious personal documents, you should have done this already before the upgrade. When finished you'll have to install all updates from after the LiveCD was made, and also all applications that you want to use, so after the install you´ll be busy for some time :) But we love computing, don't we? :P

Topsiho

---

### Post by Topsiho on 2011-05-27
I forgot: of course things going on in your computer are logged. A GUI way to see the logs is found in System>Administration>View log books (or so, I had to translate from Dutch). So you could try that :)

Topsiho

---

### Post by Kissell on 2011-05-28
> **wildmanne39 said:**
> Hi, are you sure the upgrade completed, I tried to upgrade from a livecd it would get right to the end and revert back to the previous system. If the upgrade completed do you see the unity side launcher? did you install the drivers for video card that are in the additional drivers? What are your system specs? Is it possible this system needs cleaned so it is getting hot?

I have the unity launcher, and the ati drivers were still loaded from the previous version.  I noticed that as long as I don't try to make the server do too many file operations concurrently across the network that it seems to not hang, and I really don't want to reinstall, the data is all on a different partition, however many things have been configured, like automated scripts, and I don't want to risk missing one when I reinstall, so I think I will just wait until some updates come out that hopefully fix it.  It was annoying because I had a lot to do yesterday and it kept locking up, but most days like today the server pretty much sits idle, so I think I might be able to wait it out.

---

### Post by Kissell on 2011-05-28
> **Topsiho said:**
> I forgot: of course things going on in your computer are logged. A GUI way to see the logs is found in System>Administration>View log books (or so, I had to translate from Dutch). So you could try that :)

Topsiho

Now that I have the unity launcher, how do I access things in the old way (ie System>Administration)???  This has been a constant problem ever since Unity was added.  I get lucky most times and can find it easily by searching in the launcher at the top left, but I don't always know the name, sometimes I just kinda find it somewhere under the administration or preferences menus. "its up there somewhere" or at least it used to be, now I don't know how to access things, because it was such a radical change to the way I find my launchers.

---

### Post by wildmanne39 on 2011-05-28
> **Kissell said:**
> Now that I have the unity launcher, how do I access things in the old way (ie System>Administration)???  This has been a constant problem ever since Unity was added.  I get lucky most times and can find it easily by searching in the launcher at the top left, but I don't always know the name, sometimes I just kinda find it somewhere under the administration or preferences menus. "its up there somewhere" or at least it used to be, now I don't know how to access things, because it was such a radical change to the way I find my launchers.
Hi, you can type in the search box when you click on the little ubuntu logo in the left upper corner, if you know the first few letters of what you are looking for it will bring it up. Also if you want the old menu,it would be easier on resources and might stop your problems too, log out click on user name, go to bottom of screen and choose ubuntu classic without effects.
:)

---

### Post by hawthornso23 on 2011-05-28
I think you would be better off using the Ubuntu classic desktop. Natty with the Ubuntu classic desktop is generally more stable which is usually what you want in a server. And then you can access things in the old way without having to fuss about with the launcher.

---

