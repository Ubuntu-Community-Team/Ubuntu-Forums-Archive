---
title: "Thunderbird profile not being recognized."
date: 2009-09-28
forum: General Help
---

### Post by ToshibaLaptoplinux on 2009-09-28
I had to reinstall Jaunty due to a borked Karmic upgrade.

It is a clean install on a separate partition than my home directory.

For some odd reason when I point Thunderbird to my existing profile it only picks up my address books but none of my emails boxes or account settings appear. I am at a loss because I have upgraded many times in the past and just pointed to my profile and voila it is all good. I even use the profile on other machines and it works fine.

I have A LOT of mail accounts and emails and would really have to start from scratch. I know the data is in the profile because my folder is still the correct size.

Any ideas/suggestions? Very frustrating.

---

### Post by scouser73 on 2009-09-28
When you reinstalled Thunderbird again did you remove the new profile that was created when Thunderbird started up?  I know that sounds like a daft question but I've often found that taking steps to ensure it it set up properly is paramount. If you don't mind I'll post my set of instructions, and you'll know if you have missed a step.

The Thunderbird profile can be found by showing the hidden files, to do this please follow the steps.

**1** - Go to **/home/yourname**

**2** - Press **CTRL & H** to open the hidden files & folders

**3** - Now you can see the file **/home/yourname/.mozilla-thunderbird**

***Now say for instance that you wish to move your existing Thunderbird profile to a new hard drive.***

**1** - Install Thunderbird on your new drive.

**2** - Now open the newly installed Thunderbird & then close it immediately

**3** - Now go to the newly made Thunderbird folder: **/home/yourname/.mozilla-thunderbird** and delete all the contents inside the newly created folder but not the folder itself

**4** - Now paste your existing Thunderbird profile into **/home/yourname/.mozilla-thunderbird**

**5** - Start up Thunderbird, and now you will see all your email accounts, contacts & emails

---

### Post by ToshibaLaptoplinux on 2009-09-28
Thank you for the reply and details. Yes I did do that and it didn't work.

It seems that Thunderbird is picking up everything (addressbooks, extensions, etc) except my mailboxes.

Any other ideas? Honestly I have enough mail boxes that it is easier for me to spend the time fixing this vs adding every account mailbox again manually.

How can I troubleshoot this?

---

### Post by Giblet5 on 2009-09-28
Did you back up your $HOME before attempting the upgrade?

Under the .mozilla-thunderbird directory, you should have *one* subdir named something weird like "n4kek34a.default". If there is more than one subdirectory, run:
```
du -sk *.default
```

The bigger one is probably your old profile.

Edit the "profiles.ini" file (in .mozilla-thunderbird) and change the "Path =" line to use that subdirectory.

---

### Post by ToshibaLaptoplinux on 2009-09-28
> **Giblet5 said:**
> Did you back up your $HOME before attempting the upgrade?

Under the .mozilla-thunderbird directory, you should have *one* subdir named something weird like "n4kek34a.default". If there is more than one subdirectory, run:
```
du -sk *.default
```

The bigger one is probably your old profile.

Edit the "profiles.ini" file (in .mozilla-thunderbird) and change the "Path =" line to use that subdirectory.

Thank you for you reply. My Home directory is on a separate partition so there was no need to back it up.

The profile.ini is pointing to the correct profile folder.

Thunderbird shows my addressbook and all of my extensions etc. It is only my mailboxes that are not appearing.

It is very bizarre because this is the exact same way I installed Jaunty before...clean install, home on separate partition...and Thunderbird picked up all of my profile without any problem.

Any other ideas how I can troubleshoot/solve this problem? I have a lot of boxes I am dealing with.

---

### Post by ToshibaLaptoplinux on 2009-10-05
I haven't been able to fix it yet but I have isolated that the problem is "probably" with my prefs.js file.

Thank you everyone for the replies and assistance.

---

