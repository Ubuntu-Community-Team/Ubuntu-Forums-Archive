---
title: "Thunderbird is already running, but not responding"
date: 2010-07-11
forum: General Help
---

### Post by giddyup306 on 2010-07-11
Hi all.  I'm trying to install Thunderbird on my mom's desktop.  She has been using Outlook Express for years, and I want her to get away from that as well as Windows in general (her computer has a true 1.8 GHZ single-core processor and only 512MB of ram).  The first thing I did was install Thunderbird on her XP partition, then I copied the .default file to a flash drive and copied it into the folder where I saw that Thunderbird had another .default folder in (although I never created a user for it).  I deleted that folder and replaced it with the .default folder from her XP system. I then went to load Thunderbird, and it gave me the error message that is in the title.  I restarted Ubuntu, and it still gave me the same error message.  I then deleted Thunderbird from the Synaptic, Software Center, and Terminal.  Every time I went to re-install it I got the same message when I tried to open the program.  I did find a couple of threads here that had problems with the same error, but it was after they upgraded the software.  I found a lot of threads on Google on how to convert from Outlook to Thunderbird, but most of them were 2-3 years old, and the instructions were useless.  

If you could help me out I'd appreciate it.  I've been trying to configure her email now for about two hours, and I have had no success.

---

### Post by John Bean on 2010-07-11
When you say "the .default folder" I'm not sure what you mean. In either OS there is a folder in which Thunderbird stores its data; for some user (johnb in my example) on Ubuntu it uses /home/johnb/.thunderbird and in XP it uses "c:\Documents and Settings\johnb\Application Data\Thunderbird". The contents in each case are similar but don't contain a file or folder called ".default".

If you want to clone an existing XP Thunderbird installation to Ubuntu you should copy the folder contents from c:\...\Thunderbird to /.../.thunderbird.

---

### Post by giddyup306 on 2010-07-11
I guess I'm confused then.  Here are two screenshots of what I have going on.  The first one 7......default folder is what Thunderbird created in Linux when I installed it.  The other 5....default is what I was told to copy.  The first time I deleted the 7.... folder and copied the entire 5... folder in it's place, then it gave me the error message.  What I ended up doing was deleting the . thunderbird folder to manually delete it.  What's the point of using the terminal, synaptic, or software center if you have to manually delete the file?  Oh well.  This time I copied all the stuff inside from 5 to 7 (about 800 MB) and it still doesn't work.  What am I doing wrong?

[IMG]http://i169.photobucket.com/albums/u219/giddyup306/thunder.png[/IMG]

[IMG]http://i169.photobucket.com/albums/u219/giddyup306/thunder2.png[/IMG]

---

### Post by giddyup306 on 2010-07-11
Okay I think I'm getting close.  Here's what it says on Mozilla's site.

> **Move an existing profile or restore a backed up profile**

 It's possible to move the location of a profile folder. This could be  useful if you have a backed up profile folder somewhere on your hard  drive and want to tell Thunderbird to use that as your profile. This  section explains how to do this.
    
[LIST=1]
[*]Shut down Thunderbird completely (File >  Exit).
[*]Move the profile folder to the desired location. For example, on  Windows XP, move the profile from C:\Documents  and Settings\[username]\Application Data\Thunderbird\Profiles\xxxxxxxx.default to D:\Stuff\MyMailProfile. If you are reading these  instructions because you want to restore a previously backed up  profile, this step isn't necessary. Just note the current location of  the profile you want to restore.
[*]Open up profiles.ini in a text editor.  The file is located in the *application data folder* for  Thunderbird:
[LIST]
[*]On **Windows Vista/XP/2000**, the path is   [%AppData%]("http://www.mozilla.org/support/thunderbird/profile#appdata")\Thunderbird\
[*]On **Windows 95/98/Me**, the path is usually   C:\WINDOWS\Application Data\Thunderbird\
[*]On **Linux**, the path is   ~/.thunderbird/
[*]On **Mac OS X**, the path is   ~/Library/Thunderbird/
[/LIST]
  
[*]In profiles.ini, locate the entry for  the profile you've just moved. Change the Path= line to the  new location. **IMPORTANT NOTICE:** If you switch from a  relative path to a non-relative one, the direction of the slashes may  need to change (e.g. in Windows, non-relative paths use backslashes,  whereas relative ones use forward slashes).
[*]Change IsRelative=1 to IsRelative=0.
[*]Save profiles.ini and restart  Thunderbird.
[/LIST]


When I open the .ini file (step 4) I change it to the IsRelative to 0 and put the proper folder in the Path= line.  Every time I do this it creates another .default folder!  I have no idea what is going on.  It Thunderbird works fine in XP, but I can't get it to work in Ubuntu.

---

### Post by John Bean on 2010-07-11
Read what I wrote in my earlier reply and just copy the contents of the XP %AppData\Thunderbird folder to replace the contents of the Ubuntu ~/.thunderbird folder. This of course includes the <something-or-other>.default folder and the profile.ini file that refers to it. Don't edit anything, just copy it.

This is not theory, it's something I've done many times. You don't need to do anything else to get it up and running.

---

### Post by oldfred on 2010-07-11
+1 on John Bean's comments

I regularly copy entire profile to my portable (was XP now Ubuntu) when we travel and back without issue.

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

[http://kb.mozillazine.org/Category:Issues_%28Thunderbird%29]("http://kb.mozillazine.org/Category:Issues_%28Thunderbird%29")

---

### Post by giddyup306 on 2010-07-11
Anyone?  I'm not dead set on Thunderbird.  I tried Evolution with the same amount of success.  If there is another option that is easier, please let me know. I just need to be able to import from Outlook.

EDIT:

For some reason Firefox didn't load the last two posts when I wrote this....

---

### Post by giddyup306 on 2010-07-11
> **John Bean said:**
> 

This is not theory, it's something I've done many times. You don't need to do anything else to get it up and running.

Well then the tutorial that I read was wrong.  I didn't edit anything either.  I copied the entire folder and pasted it into Thunderbird.  Let me go one or more levels up and see if that helps anything.  BRB I need to get into windows...

---

### Post by oldfred on 2010-07-11
what version of thunderbird? They moved the profile folder for version 3 from 
.mozilla-thunderbird
to
.thunderbird

[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by giddyup306 on 2010-07-12
Thanks for the help everyone.

I finally got it figured out!  The 3 or 4 turorials that I read were way outdated.  Part of my problem was that one said to copy the .default folder.  You need ALL of the contents of the Thunderbird folder.  Second, they did move the folder in Linux to .thunderbird.  So I was fighting two problems. After I converted them with Thunderbird in XP, all I had to do was copy the entire folder and replace it in the .thunderbird folder.

---

