---
title: "Program not responding  and Places not working? ? ? ?"
date: 2010-07-08
forum: General Help
---

### Post by beanco on 2010-07-08
Hi all,

two problems.

When I log off/shut down I get an error message saying:

Program not repsonding with the options to 

cancel, lock screen or log out anyway.

The pgr listed is file manager.

The other problem is when I go to places/documents or places/anything actually, nothing happens, nothin opens not documents, not home folder, not desktop, nothing.

so, any ideas how to fix either error?

Thanks

Rob

---

### Post by oldos2er on 2010-07-08
Need more info. Which version of Ubuntu are you using? Is this a new install, or an upgrade? Do you have all the latest updates installed?

---

### Post by beanco on 2010-07-08
Sorry, I was at work and the boss was not happy so I had to hurry...

I am on Jaunty, I have not updated in a couple of weeks max. Until now, it was all fine.

The error  is *program is not working* sorry for the mistakes and lack of info


Robi

---

### Post by oldos2er on 2010-07-08
Are you still able to logout or shutdown?

---

### Post by beanco on 2010-07-08
yes, I can logout/shut down, but I always get that error msg first.

Rob

---

### Post by oldos2er on 2010-07-08
I'm afraid I have nothing further to suggest, other than searching launchpad.net to see if it's a known bug. Sorry.

---

### Post by lidex on 2010-07-08
Try removing this, then logout/in.
```
rm -r  ~/.local/share/gvfs-metadata
```

---

### Post by beanco on 2010-07-09
> **lidex said:**
> Try removing this, then logout/in.
```
rm -r  ~/.local/share/gvfs-metadata
```

What will that do?

Oh, and Btw , the error msg is *prgrm still running* sorry to kepe getting this wrong.

and in additoin to that and the other problem, the one with places/ANYTING I also have issues with the Desktop.

I wanted to clean it up but cannot drag and drop, cannot delete, cannot do anything with it... this seems to have happened after a jpg was added there yesterday.

I just updated the system, btw, shut donw, logged back on, shut down again and still get the prgm still running error msg.

Robi

---

### Post by lidex on 2010-07-09
[http://www.google.com/search?q=gvfs-metadata&sitesearch=ubuntuforums.org]("http://www.google.com/search?q=gvfs-metadata&sitesearch=ubuntuforums.org")

---

### Post by beanco on 2010-07-09
> **lidex said:**
> [http://www.google.com/search?q=gvfs-metadata&sitesearch=ubuntuforums.org]("http://www.google.com/search?q=gvfs-metadata&sitesearch=ubuntuforums.org")


ooops should have googled before I asked....
I ran that command, btw and nothing happened.

robi

---

### Post by lidex on 2010-07-09
You could try running your file manager from a terminal and posting the error message. I have seen recently a problem with svg files on the desktop also. Remove any image files from there and logout/in.

---

### Post by beanco on 2010-07-10
Lidex, I'd be happy to, but I do not know how to .... what is the actually command? 

thanks

robi

---

### Post by lidex on 2010-07-10
I wasn't sure what you are using, hence no command. In a default ubuntu install:
```
nautilus
```

---

### Post by beanco on 2010-07-10
yeah, i realized that is what you mean and ran the command and got this



(nautilus:4046): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

---

### Post by lidex on 2010-07-10
Unfortunately that's not a very helpful message. Generic and not fatal. Anything else? Have you checked your logs? Dmesg? ~/.xsession-errors?

Try logging in as a new user - create one if need be.

---

### Post by rogerdg on 2010-07-10
From the Command Line you can do this:> cd
cd Desktop
cd ..
mkdir backup
mv Desktop/* backup/

This will make a directory named "backup" in your home directory, then move the files from your Desktop to the backup.  If the files on the desktop are causing problems this will fix the problem.  Simply restart the computer and answer the prompt about programs still running.  After the computer shuts down it will restart with an empty Desktop folder.  If the computer starts OK try shutting down again.  If you get no errors then one or more of the files in the backup folder is the problem.  If the problem still occurs then your Desktop files were not causing the problem.  In any case the files (images, links, etc) are still on the system in the backup folder and can be moved back to the Desktop if you need them.  Note:  Any symbolic links to external drives will automatically be recreated if you remove and reinsert the external device.

---

