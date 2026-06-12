---
title: "can't change file/dir permission of a dir"
date: 2009-11-10
forum: General Help
---

### Post by DocMindie on 2009-11-10
I'm kinda stuck.... 

Last night (around 1AM) I was able to run World of Warcraft (yup, Wine-user ;) )by clicking on the shortcut I had created on the desktop. I played for a couple of hours then went to bed.

When I got up and tried to run the game again, all I could get was "permission denied."

So, I searched around a little bit and now I can get full root access, which let's me run the game (as root). However, even as root, the directory refuses to change permission for user and group to 7 (read/write, scan files, execute). User get "scan files" group gets nothing.

I've tried just about everything I know, plus a few things from searching the internet, but I can't seem to reslove the issue. 

I can (with MC, as it's the one filemanager I can run as root from a  terminal window) change the permissions... or so it claims. as soon as I close the su-enabled terminal window, OR try to access the WoW directory from a normal user-account, I only get permission denied.

I don't really want to run anything I don't have to as root, or even as su..... any tricks up your sleeves I might've overlooked?

---

### Post by marwade on 2009-11-10
I'm sorry to hear you're having this issue, Doc, but I'm relieved someone other than I am suffering the same weirdness!  I played WoW (also using wine) without issue yesterday.  Around nine p.m. I clicked the panel icon as I normally would, and when the launcher window (with all the newsy tidbits and the 'play' button) popped up, it stalled . . . it had something to download.  

Eventually whatever it is Blizzard wanted to download did, and installed, and that was the end of my peaceful gaming.  When I clicked 'play', the window disappeared as it usually does but WoW itself didn't launch.  No lovely blue log-in screen with the skeletal dragon flying at me.  Just nothing. I clicked the icon again only to get the error:  [COLOR=Red] Could Not Launch Application[/COLOR] Failed to change to directory '/home/marianne/.wine/dosdevices/c:/Program Files/World of Warcraft/' (Permission denied)

Well what the . . . ?   S'okay, I went into the folder, changed permission, went back, same issue.  My housemate (who has a good amount of computer acumen) spent a good two hours with me last night shifting this permission and changing that ownership.  We even ran the WoW repair.  We determined for some reason the permissions keep getting rewritten.  He suspected it's not a WoW issue but a wine issue, because windows doesn't deal with permissions but linux does.  

I'm flummoxed!  I don't know what Blizzrd downloaded, some little patch of some kind, but it coincided with this strange denial and rewriting of permissions.  What to do?

---

### Post by abexy on 2009-11-10
I am having the same issues. Whatever thing Blizzard had to download yesterday wouldn't download for me. I checked the support forums, and they were telling Windows users to run Wow.exe as admin, so I figured run mine as root. It downloaded fine then.

But now, every time I try to run Wow.exe, the World of Warcraft directory resets all permissions for me to none. I can change them to read/write/execute and run Wow.exe directly, but they reset again immediately after, or if I try to run it from Launcher.exe they reset before WoW launches.

I tried changing the permission in the terminal with sudo chmod, but the same thing happened. From the above descriptions, it looks like it was the patch yesterday and not something I did.

---

### Post by marwade on 2009-11-10
> **abexy said:**
> From the above descriptions, it looks like it was the patch yesterday and not something I did.

I've counted four of us so far, and have only been through a few of the posts mentioning wow.  I don't know how last night's patch screwed this up so effectively for wine users but it so did.  Another post mentioned something called Crossover and that it is apparently working in place of using wine, but I don't know what it is and at this point would rather find a way to work with what I have rather than risk even *more* changes.

So you could launch the game application as root?  And that caused no (more) problems?  I'm leery when it comes to doing anything as root.  Was taught it was a pot of boiling water just like executing a 'sudo' command was--to be extra careful because of the power involved.  Am I just being overly cautious?

---

### Post by Macchia on 2009-11-10
Same here, solved by running Wow.exe directly, HTH

---

### Post by abexy on 2009-11-10
> **marwade said:**
> So you could launch the game application as root?

Sorry, I realize I wasn't clear. Not as root, but just normally I can change the permissions to the World of Warcraft folder and run Wow.exe once before it changes the permissions back again. I have to run Wow.exe directly, not from the Launcher. After this, it is reset to having no permissions.

---

### Post by marwade on 2009-11-10
> **abexy said:**
> Sorry, I realize I wasn't clear. Not as root, but just normally I can change the permissions to the World of Warcraft folder and run Wow.exe once before it changes the permissions back again. I have to run Wow.exe directly, not from the Launcher. After this, it is reset to having no permissions.


Ohhh okay.  And look at that, the word "Dur" just literally appeared above my head in a quote bubble!  It finally dinged what I needed to do to run the game directly.  I changed the permissions on the WoW folder (because as we all now know, they keep getting rewritten) opened it, scrolled down to the wow.exe icon and opened it.  Et voila! The lovely blue log-in screen.  

Of course it's Tuesday and maintenance day, and I still don't know how to resolve the permissions issue, but at least I can log in and plaaaaaaay.  Er, when server's back up.

Thank you!  :D

---

### Post by ChrissyA on 2009-11-10
Have the same problem, thanks alot for these posts, so I managed to log in without getting really frustrated!

---

### Post by fireoftroy on 2009-11-10
I have the same problem and I'm glad to see I don't have to lots of tweaking to play again!  Hopefully the launcher gets fixed soon!

---

### Post by marwade on 2009-11-10
In the other thread on this same topic, GJLenon came up with this fix.  It does work beautifully, providing the launcher window is bypassed.  It seems horribly broken for us wine users now.  So I launched wow directly and unchecked the option to show the launcher.  Now when I click the wow icon in the top panel it goes directly to login screen.  

Hoping it's okay to quote from another thread, here is GJ's fix: 

> **GJLenon said:**
> Alright, this is probably not the best method, but it is what I used.

**Step 1:** *Creating a shell script*
Open gedit (Applications/Accessories)

In gedit, type:



Obviously change the <user> to your user name and modify the directories as needed.

Then save the file as wow.

**Step 2:***Accessing the Script*
Open a Terminal (Applications/Accessories).

Type in chmod 755 ./wow

This will allow you to access the script you just created.

Close the Terminal.

**Step 3:***Modifying the Panel*
Right click on your World of Warcraft icon on the panel, and go to Properties.

Delete what it has under the Command and replace it with:



Now close out of the properties.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

That should work, again, not the most stream-lined, but it works for me. :)

---

### Post by DocMindie on 2009-11-11
Here's how I fixed it this morning... though I didn't try the Loader, it worked by just using WoW.exe

Uninstall everything of wine (which also means delete from your /home/<user> drawer
Install the latest BETA of Wine via the Ubuntu Software Centre
use Winetricks.sh to install the MSVC 2005 runtime libraries
Run WoW.exe

First thing I did, of course, was to reset the permission on the WoW drawer

---

### Post by DocMindie on 2009-11-11
Ok... I just tried the Launcher.exe.... for some reason, THAT one resets the permissions. However, it seems that Wow.exe doesn't.... so there's something fishie about the Launcher.exe, it seems.

However, everything seems to me to be working perfectly otherwise, just make a shortcut to Wow.exe on your desktop or wherever you want it, instead of the Launcher.exe.

---

### Post by fireoftroy on 2009-11-12
Thanks, marwade!  I unchecked the show laucher option and now my shortcuts work again!

---

### Post by ChrissyA on 2009-11-22
How do you get the patch downloaded now? Since Launcher is acting up...

---

### Post by DocMindie on 2009-11-22
You don't need the launcher for patching the game, mate... just launch the game as normal, and it'll tell you about the new patch and automagically apply it

---

### Post by ChrissyA on 2009-11-24
Oh, great! 
Thanks :)

---

