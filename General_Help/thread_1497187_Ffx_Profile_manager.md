---
title: "Ffx Profile manager"
date: 2010-05-30
forum: General Help
---

### Post by Randymanme on 2010-05-30
How can I open the Firefox Profile Manager.  I've googled and read but the directions don't work for me:

  	 	 	 	 	 	  randymanme@randymanme-desktop:~$ /usr/lib/mozilla/firefox -ProfileManager  
 bash: /usr/lib/mozilla/firefox: No such file or directory  
 randymanme@randymanme-desktop:~$ /home/randymanme/mozilla/firefox -ProfileManager  
 bash: /home/randymanme/mozilla/firefox: No such file or directory  
 randymanme@randymanme-desktop:~$ usr/lib/firefox-3.6.3/ ProfileManager  
 bash: usr/lib/firefox-3.6.3/: No such file or directory  
 randymanme@randymanme-desktop:~$

---

### Post by Randymanme on 2010-05-30
follwing the directions given at  [[IMG]http://ubuntuforums.org/images/misc/navbits_start.gif[/IMG]]("http://ubuntuforums.org/showthread.php?t=1494757&highlight=firefox+profile+manager#")   [Ubuntu Forums]("http://ubuntuforums.org/index.php") > [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130") > [Main Support Categories]("http://ubuntuforums.org/forumdisplay.php?f=327") > [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331")  [[IMG]http://ubuntuforums.org/images/misc/navbits_finallink_ltr.gif[/IMG]]("http://ubuntuforums.org/showthread.php?t=1494757&highlight=firefox+profile+manager") **[COLOR=#980101][ubuntu][/COLOR]**** Annoying, strange Firefox behavior - Can anyone help? ** 
 

 randymanme@randymanme-desktop:~$ firefox -p 
  
 run-mozilla.sh: Cannot execute /usr/lib/firefox-3.6.3/firefox-bin.pure. 
  
 randymanme@randymanme-desktop:~$

---

### Post by lovinglinux on 2010-05-30
See the [Profiles](http://firefox-tutorials.blogspot.com/2010/05/profiles.html) section of  [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Keep in mind that if Firefox is already opened, then you will need to add -no-remote to the command.

If that doesn't work, then see [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by WorMzy on 2010-05-30
Close Fx and run 'firefox -P'.

---

### Post by lovinglinux on 2010-05-30
> **WorMzy said:**
> Close Fx and run 'firefox -P'.

Yes, that is the correct command. If you use **-p** instead of **-P** it will give that error.

---

### Post by Randymanme on 2010-05-30
"Yes, that is the correct command. If you use -p instead of -P it will give that error."

You're absolutely correct.  Thank you very much.  Thanks to WorMzy too.

I haven't moved the profiles yet, but I don't see how I could have begun without first opening Profile Manager.  If I have any problems, I'll be back.  And, of course, if I don't have any problems, I'll be back about something else.

Much appreciation.

---

