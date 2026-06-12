---
title: "Launcher problems/questions"
date: 2011-07-28
forum: General Help
---

### Post by BuddyThirteen on 2011-07-28
When I first was setting up 11.04 and getting it the way I thought I wanted it, I removed the "Home" folder from the launcher. Because I was used to the Gnome panels. But it turns out that getting to folders in Natty without that is kind of a pain. I.E., horribly counterintuitive and not-thought-out. So, now that I know I want it there, I tried to restore it by opening the Home folder and checking the "Keep in Launcher". But that just keeps the File Manager there. Which I guess works, but the icon is ugly compared to the Home folder icon (Faenza icons). So I unchecked the "Keep in Laucher" -- and it disappeared. Even though the window was still open. And now opening the file manager to any folder doesn't make it show up on the launcher. What's up with that? How do I both restore the Home Folder and also make it so the File Manager shows up when windows are open?

Thanks.

---

### Post by yetiman64 on 2011-07-28
From [[COLOR=Blue]--this link--[/COLOR]]("http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html"), the section down the page entitled > **Missing a quick way to access your Downloads / Pictures / Documents / Videos folders?** may actually help you restore your home folder icon on the menu bar. You will end up with links to all the other folders "videos documents music pictures and downloads" in the context menu of the home icon as well following this, if unwanted alter the instructions to suit, though I suspect this may be handy to you as well.

Note: copy the entire contents (with or without alterations) of the code box there as a single command and paste it to your terminal.

Good luck.

Edit: you may need to logout and log back in (or restart Unity) for the changes to take effect.

---

### Post by BuddyThirteen on 2011-07-28
Hmm. Well, I tried it. Nuthin. Except your post gave me an idea: I just logged out and logged in, and now the File Manager pops up on the launcher when I have windows open. So that's fixed. But that Home folder won't come back.

I'm sad now. Especially now that you showed me that thing. Because that context menu thing seems like it would be amazingly convenient!

---

### Post by yetiman64 on 2011-07-28
I did exactly as you did and removed the home folder icon in Unity and then had to recover it. Those are the instructions that got it back for me at the time.

I would suggest you check you didn't miss out a bit of the code on the end of the instructions,>  | sudo tee /usr/share/applications/nautilus-home.desktop you can navigate to that address in /usr/share/applications in a nautilus window and check the desktop file "nautilus-home.desktop" exists. If it doesn't it may be you missed the last of the command. Creating this launcher and restarting the machine is what should create the home folder icon on the menu bar for you.

You could also in the terminal use the up arrow on your keyboard to review your last code entered. If all is ok with it I'm baffled as to why the icon is not back for you.

---

### Post by BuddyThirteen on 2011-07-28
Copied and pasted in whole, nothing much seems to happen. I'm still kind of a noob at Linux, and I don't know the commands very well. But it seems that the command it lists is just "Echo" and then the long string of things. And with my experience from DOS, "echo" just means repeat it, right? Which is exactly what it seems to do. I copy/paste "echo [long string]" and it spits out "[long string]" without actually seeming to have done anything. Am I doing something wrong?

And no, that file doesn't exist. I have tried it several times, logged out and in, restarted, et cetera. Nothing seems to help. I'm trying it one more time.d

---

### Post by yetiman64 on 2011-07-29
echo does do as you suggest but the last bit of code pipes (|) the output of echo to the file /usr/share/applications/nautilus-home.desktop (that is writes the file contents) - note, the "sudo tee" is to elevate privileges to write to that particular location.

If that file doesn't exist then try creating it first with ```
sudo touch /usr/share/applications/nautilus-home.desktop
``` then use the code in terminal from the link I posted earlier. Hopefully that will allow the output from "echo" to be successfully piped to the launcher file, then do a restart.

I don't remember having to do this, I only remember having used that site instructions and it fixed my (similar) situation. I may not have totally removed the launcher file though.  Good luck once again, worth another try.

---

### Post by BuddyThirteen on 2011-07-29
Gah! I see via "touch --help" that touch will create an empty file if it doesn't exist. But for some reason "sudo touch /usr/share/applications/nautilus-home.desktop" absolutely refuses to create the file no matter how many times I try.

So I navigate to the folder, thinking "Well, I'll just create it myself and put the text in there" but I don't have authority to create a new file in there that way.

This is getting rather frustrating. The terminal isn't giving me any errors, either. No indication that anything is going wrong during any of these processes, yet nothing happens.

I'm feeling rather stupid at the moment.

---

### Post by BuddyThirteen on 2011-07-29
[FONT=Trebuchet MS]Huh. Oddness. I still can't find or see the file (Ctrl+H won't reveal it, either), but on a  hunch, I tried using "gedit /usr/share/applications/nautilus-home.desktop" and it opened it up and the text from the previous steps is in there. So gedit can find it, but nothing else can? Not even my eyeballs? I'm so confused. And if indeed it does exist, as gedit claims it does, why isn't it working? Where's my Home Folder launcher dealy?!?!?!?!

Further experiment: I clicked "Save As..." in Gedit, and guess what? There's tons of files listed there that I can't otherwise see. How? How?!
[/FONT]

---

### Post by yetiman64 on 2011-07-29
Good pick using gedit, I was just doing some experimenting here and the desktop file may not be enough alone. Note there are a few nautilus desktop files so look carefully at all of them and you will probably find it in the folder. 

In rechecking on a Natty install here I had to use the command,
```
unity --reset-icons
``` to get the home icon to come back, warning though it caused a segmentation fault here I've only just recovered from, it should be ok for you to try, I suspect some of my many tweaks may have been at fault there.

Edit: note I had a standard nautilus-home.desktop file before using the reset icons unity code and then ran the code from the previous link and logged out/in the get the context menu entries on the home icon.

---

### Post by BuddyThirteen on 2011-07-29
So that'll reset the launcher to "factory defaults"? I think I can live with that, I've only made a couple minor changes which should be easy to re-do.

[edit]: Okay, I did it. There was a terrifying moment when EVERYTHING DISAPPEARED! But then it all came back. Though the terminal seems to be stuck. The last thing it says is "setting update "panel_opacity"" and it's just hanging there... I'm scared to close it before it's done.

But hey, Home Folder is back! Whoo! As well as the three hundred LibreOffice icons. So I'll just remove all but Writer and then put it back (mostly) the way I had it. Thank you so much! And once the terminal is done being silly, I'll do that other thing to add the context menu, because that'll be great.

Thanks again!

[further edit]: Oh wait, I don't have to do that again. Right click reveals the context menu is already awesomed. Woot! Now if only the terminal would finish.

---

### Post by BuddyThirteen on 2011-07-29
Well, it said something about debug, and I went to copy it to paste here, and out of habit I hit Ctrl+C instead of Ctrl+Shift+C and interrupted it, then everything disappeared again, it wouldn't come back, I couldn't really click on anything, window borders and panels and everything were gone, except the contents of the windows oddly. But I restarted and now everything looks fine. But I'm worried I may have broken something by interrupting the process. Should I reset the icons again and just let it run its course and hopefully fix anything that may be broken? Or do you think it's okay? I'm scared.

---

### Post by yetiman64 on 2011-07-29
Resetting the icons sometimes hangs the terminal like that, particularly if you changed a few of the icons, it should be ok as it is, just keep an eye on it for a while before trying to run the reset again. Good to hear the launcher changes stuck, I was unsure if it would do so.

---

