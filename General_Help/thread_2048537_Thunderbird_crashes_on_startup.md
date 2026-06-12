---
title: "Thunderbird crashes on startup"
date: 2012-08-26
forum: General Help
---

### Post by Bald Kea on 2012-08-26
Hi. Relatively new Ubuntu user. 
Thunderbird continually crashes on startup. I've heard nothing back via email from Mozilla. Have tried reinstalling to no avail. The crash report is:

Add-ons: [email]langpack-en-GB@thunderbird.mozilla.org:14.0,messagingmenu@mozilla.com:0.9.3,edsintegration@mozilla.com:0.3.9,globalmenu@ubuntu.com[/email]:3.2.5,{972ce4c6-7e08-4474-a285-3208198ce6fd}:14.0
BuildID: 20120714011110
CrashTime: 1346028004
EMCheckCompatibility: true
Email: 
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1342764713
ProductID: {3550f703-e582-4d05-9a08-453d09bdfdc6}
ProductName: Thunderbird
ReleaseChannel: release
SecondsSinceLastCrash: 12657
StartupTime: 1346028000
Theme: classic/1.0
Throttleable: 1
Vendor: 
Version: 14.0

Would appreciate some help to resolve this.

---

### Post by SeijiSensei on 2012-08-26
Did you install Thunderbird from the repositories, or from somewhere else?  You should always use the Ubuntu repositories to install most any open-sourced application.

What do you see if you run "locate bin/thunderbird"?  Do you see /usr/bin/thunderbird?  If so, you can probably just run "sudo apt-get install thunderbird" to overwrite whatever you have there now.  If you see something like /usr/local/bin/thunderbird, then you can also install the repository version with apt-get.  However you should delete any other executables in places like /usr/local/bin so the operating system will not try and execute the wrong version.

If all that doesn't work, close Thunderbird and try this:

```

$ cd ~
$ mv .thunderbird .thunderbird.bad

```

then start Thunderbird again.  It should launch its mail account wizard so you can rebuild your configuration.

---

### Post by Bald Kea on 2012-08-26
Thanks for your help

Yes, I installed TB from the repositories some months ago and everything was fine until several days ago, so we've switched to using TB on our M$ 7 laptop.

locate bin/thunderbird showed /usr/bin/thunderbird.

I tried sudo apt-get and received: 

"thunderbird is already the latest version. The following packages were automatically installed and no longer required: thunderbird-locale-zh-cn thunderbird-locale-en-gb thunderbird-locale-en-us
  thunderbird-locale-zh-hans thunderbird-locale-de thunderbird-locale-en
Use 'apt-get autoremove' to remove them. 0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded."

Tried apt-get autoremove:

home@home-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

which was beyond my ken.

I've run the .thunderbird.bad and can now at least redo it. Is there any way of retrieving the emails? (not crucial)

---

### Post by SeijiSensei on 2012-08-27
> **Bald Kea said:**
> 
home@home-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

You forgot to use "**sudo** apt-get autoremove".

> Is there any way of retrieving the emails? (not crucial)

In .thunderbird.bad you'll see a folder with a name like "something.default".  Inside that folder will be one called "Mail".  If you use IMAP rather than POP, as I do, there will be an "ImapMail" folder as well.  One of them will have all the mail.  You should be able to copy the contents of the appropriate folder to the new .thunderbird directory.

---

### Post by Idefix82 on 2012-08-27
Try opening the terminal and running thunderbird from there by just typing
```
thunderbird
```

When it crashes, see if there is some useful output in the terminal and paste it here.

---

### Post by Bald Kea on 2012-08-27
> **SeijiSensei said:**
> You forgot to use "**sudo** apt-get autoremove".



In .thunderbird.bad you'll see a folder with a name like "something.default".  Inside that folder will be one called "Mail".  If you use IMAP rather than POP, as I do, there will be an "ImapMail" folder as well.  One of them will have all the mail.  You should be able to copy the contents of the appropriate folder to the new .thunderbird directory.

Thanks, still learning - have recently learned about using the terminal

How do I get to thunderbird.bad ?

---

### Post by Bald Kea on 2012-08-27
> **Idefix82 said:**
> Try opening the terminal and running thunderbird from there by just typing
```
thunderbird
```When it crashes, see if there is some useful output in the terminal and paste it here.

Thanks, but I'm getting the thunderbird set-up now

---

### Post by SeijiSensei on 2012-08-28
> How do I get to thunderbird.bad ?

If you followed my earlier advice, you have two options:

1)  In the terminal, simply use the command "cd .thunderbird.bad" to "change directory".

2)  In a graphical file manager like nautilus or dolphin, navigate to your home directory.  You then have to enable the manager to show "hidden files," which are any files that begin with a dot in their names.  You should then see ".thunderbird.bad" appear in the list of files and directories.

---

### Post by Bald Kea on 2012-08-29
> **SeijiSensei said:**
> If you followed my earlier advice, you have two options:

1)  In the terminal, simply use the command "cd .thunderbird.bad" to "change directory".

2)  In a graphical file manager like nautilus or dolphin, navigate to your home directory.  You then have to enable the manager to show "hidden files," which are any files that begin with a dot in their names.  You should then see ".thunderbird.bad" appear in the list of files and directories.

Cheers for that. Will download a graphical manager and get back once sorted :)

---

### Post by Bald Kea on 2012-09-11
Ok, sorry for time taken to get back. Got a friend to help and it turns out that the crashing was on account of having too many emails. We are running 4 accounts and 3 of them had several hundred emails each. I was able to copy the inbox folders over (installed Dolphin), which was a little tricky as the email folders in TB.bad were named only as pop Nil, 1, 2, 3 and didn't correspond to the order I'd created them in the new TB. When I copied all 4 across to the appropriate folders TB crashed again.  So I'm now going through each account at a time to delete the old emails :)  Thanks very much for your assistance.

---

### Post by Sapienso on 2012-10-09
Hi, Bald Kea and everyone. 

I have had the same problem since last week. My last crash report says: 

> Add-ons: [email]es-es@dictionaries.addons.mozilla.org:1.5,{e2fda1a4-762b-4020-b5ad-a41df1933103}:1.7,edsintegration@mozilla.com:0.3.11,thunderbird-couchdb@ubuntu.com:0.0.1,messagingmenu@mozilla.com:0.9.3,langpack-es-AR@thunderbird.mozilla.org:15.0.1,langpack-es-ES@thunderbird.mozilla.org:15.0.1,calendar-timezones@mozilla.org:1.2011n,{a62ef8ec-5fdc-40c2-873c-223b8a6925cc}:0.16,globalmenu@ubuntu.com:3.4.2,langpack-en-GB@thunderbird.mozilla.org[/email]:15.0.1,{972ce4c6-7e08-4474-a285-3208198ce6fd}:15.0.1
BuildID: 20120912042340
CrashTime: 1349774125
EMCheckCompatibility: true
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1348926947
Notes: OpenGL: NVIDIA Corporation -- GeForce 8700M GT/PCI/SSE2 -- 3.3.0 NVIDIA 290.10 -- texture_from_pixmap

ProductID: {3550f703-e582-4d05-9a08-453d09bdfdc6}
ProductName: Thunderbird
ReleaseChannel: release
SecondsSinceLastCrash: 1314
StartupTime: 1349774098
Theme: classic/1.0
Throttleable: 1
Vendor: 
Version: 15.0.1

This report also contains technical information about the state of the application when it crashed.I have sent the reports to Mozilla, and I have not received a reply yet either.

I do not thing I have particular large mail boxes. But I will check in detail. 

Thanks in advance for any help.

---

### Post by Sapienso on 2012-10-11
I have solved my problem, for the moment, entering in "safe mode", which disables add-ons. The way to do it is: from a terminal, type

$ thunderbird -safe-mode

Then disable add-ons when a dialog box opens, and click "continue in safe mode". 

Aparently my problem is that the add-on Lightning is not available for thunderbird 15.0.1. That is my guess. While there is an update, I will continue in safe mode. 

Best,

---

