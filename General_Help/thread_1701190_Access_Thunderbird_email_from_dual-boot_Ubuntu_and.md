---
title: "Access Thunderbird email from dual-boot Ubuntu and Windows"
date: 2011-03-06
forum: General Help
---

### Post by David_UK on 2011-03-06
I expect many here will be confident to do this, but I struggled through many sets of instructions before I figured out all the details.  Documented here for others to refer to.
This guide assumes you are dual-booting Ubuntu 10.10 and Windows and want to access your Thunderbird 3 email in both operating systems. 

**1) Automount your windows partition**
Working in Ubuntu, download ***ntfs-config*** from the repositories.
It's found in System>Admin> and is fairly self-explanatory.  Select your windows (NTFS) partition to automatically mount, and make sure you select 'enable write support for internal devices'.  Reboot.

**2) Set up Thunderbird in Ubuntu**
Once it's set up and tested, we'll need to move your profile to a place where both OS's can access it.  Note, you MUST set up Thunderbird first or there will be no profile to move.

**3) Move your profile to Windows**
Because windows can't access your linux partition, we'll have to store your profile on the NTFS partition.  To avoid problems with file paths, I put mine at the root of the windows partition:
Navigate to your Ubuntu home folder.
Ctrl+H to reveal hidden folders.
Copy your .thunderbird folder
My windows partition is called 'Acer' so I navigated into Acer and pasted it straight away.  One might be tempted to put it into your 'Documents and Settings' folder, but I didn't know how to overcome the spaces in the filepath that introduces.
Right-click on the .thunderbird folder you've just pasted and select 'properties'.  I could see that my folder was now called '/mnt/Acer/.thunderbird'.  Make a note of this.

**4) Direct Thunderbird to the new profile location**
Navigate back to your Ubuntu home folder and into the .thunderbird folder.  The actual mail is stored in a folder named <random_string>.default.  Edit this to rename it <random_string_old>.default or similar to check it can be safely removed later.
There is also a file in this folder called 'profiles.ini'.  Make a copy in case it all goes wrong, then open the original with a text editor:
Change 'IsRelative=1' to '=0'
Edit 'Path=<random_string>.default' to include the location of the profile on Windows you noted earlier - eg: '=/mnt/Acer/.thunderbird/<random_string>.default'
Save and close.
Open Thunderbird and check it's still working.

**5) Boot into Windows and install Thunderbird (use the same version number)**
Create a dummy profile when run for the first time:
eg - Name = sdfjksj
eg - Email = [email]fjks@fjks.com[/email]
eg - Password = fsjks
Thunderbird will try to retrieve server settings, but will fail.
Select 'Manual setup' and under 'Server Settings' make a note of this *first* local directory location shown at the bottom of the page.  As I'm using Windows 7, my directory location was 'C:\Users\<myname>\AppData\Roaming\Thunderbird\Profiles\<other_random_sring>.default'
Ok everything and close Thunderbird.

**6) Locate the genuine profile**
Show hidden files and folders.
Navigate to the root of the windows partition and into your '.thunderbird' folder you moved there from Ubuntu.
Right-click on the '<random_string>.default' folder and select 'properties'.  Make a note of this *second* location (mine is 'C:\.thunderbird\<random_string>.default'.

**7) Point Thunderbird towards the genuine profile**
Navigate to the *first* local directory you noted a moment ago, stopping at the 'Thunderbird' folder.  Don't forget to 'show hidden files and folders' to see the AppData folder.
Locate and edit the 'profiles' configuration file:
Change 'IsRelative=1' to '=0'
Edit 'Path=Profiles/<other_random_string>.default' to be the *second* location and the original random_string name.  For me it's:
'Path=C:\.thunderbird\<random_string>.default'.

**8) Test Thunderbird and tidy up**
Open Thunderbird and check you can see your mail.
When you're happy, you could delete your dummy profile folder (rename it first and retest in case you've made a mistake).  Remember though, the 'profiles' configuration file must remain unmoved and intact to direct Thunderbird to the correct place.
Back in Ubuntu, you can also delete the <random_string_old>.default folder you renamed in step 4 above.  My mail folder is several hundred MB so it's worth removing once all is checked.

**9) Back it up!**
Whatever system you use, don't forget to adjust your backup software to the new email folder location (or, periodically make a copy of the folder to your backup location).

---

### Post by familiarmoniker on 2011-08-09
It works! I just used these implements to migrate my Thunderbird 5.0 profile from Ubuntu 11.04 to Windows 7 and it transferred seamlessly [all profiles and extensions included]. Thanks for the guide. \\:D/

---

### Post by David_UK on 2011-08-25
Great to hear!  Thanks for the feedback.

---

