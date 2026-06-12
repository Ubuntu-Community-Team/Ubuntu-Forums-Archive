---
title: "Poorly Computer -- re:Top location bar and nautilus"
date: 2011-12-19
forum: General Help
---

### Post by Mat11 on 2011-12-19
Hi i'm using Maverick 10.10 on a 64 system and had a minor problem which lead to a serious problem because i like to fix things.
 
Originally i found folders in the places bar of which i did not put there so i tried to delete them of which i found near on impossible.So i right clicked on the top location bar and clicked on do you want to delete yes -without reading it all because it was so late at night. After which i had serious computer stability problems i lost the internet connection so now i'm writing on a backward Windows machine !
I managed to get back the use of some of the top panel components by playing with the bottom panel properties but with no internet connection until i tried sudo "gnome panel" which logged me in as root.But that was only temporary because when i logged back in i was back to square one --- no location bar.
I noticed i had a problem with user rights so i ran sudo apt-get updates etc and it did'nt help so i uninstalled nautilus and reinstalled it then rebooted the machine to find my user panel on log-in was blanked out and unusable. My laptop is basically cocked -- i have the master 10.10 CD can anyone help.? Also can anyone explain why my folders were jumping into (Places on the location bar at the top) without user authorisation ?
 
Must admit i'm surprised that i was able to create an unstable machine by being able to delete the top location bar?
 
Hope someone can help please.:confused:
 
Thanks.
 
Matt

---

### Post by MartijnNL on 2011-12-19
Are you talking about folders like Documents, Music, Videos, Pictures and so on? These are part of places by default.

Removing folders from places is done by opening Nautilus (the file manager) and removing the folders from the left pane by right clicking on them and choosing 'Remove'. The shortcuts in Nautilus are the same as the ones in places.

If you delete a panel, you delete every item on it as well. You can manually add them again by right clicking a panel and selecting 'Add to panel' (after adding a new panel of course).

---

### Post by pqwoerituytrueiwoq on 2011-12-19
What exactly did you delete?
ie a folder name would be helpful were you deleting a folder as root?

do you want to restore the default gnome-panel? if so
[FONT="Courier New"]gconftool --recursive-unset /apps/panel[/FONT]

---

### Post by MartijnNL on 2011-12-19
By the way: when you run sudo gnome-panel you get the panels for the root user, which are not the same as your own. That's why you temporarily had the top panel back.

---

### Post by Mat11 on 2011-12-19
Hi many thanks for your replies i will try them but now i can't get into any users on Log-in can you help ?

---

### Post by MartijnNL on 2011-12-19
You may have uninstalled other software when you removed nautilus, which you didn't automatically reinstall when you installed nautilus again.

You might want to try pressing Ctrl+Alt+F1, logging in and running:

```
sudo apt-get install ubuntu-desktop
```

This should re-install the basic desktop system with everything that belongs to it. (Without removing other software you may have installed.)

By the way: problems with rights normally just can't be solved by uninstalling and reinstalling software.

Edit:I just removed the first sentence, which was no longer relevant.

---

### Post by pqwoerituytrueiwoq on 2011-12-19
> **Mat11 said:**
> Hi many thanks for your replies i will try them but now i can't get into any users on Log-in can you help ?
probally messed up permissions using sudo on gui apps when you should have used gksu
boot to recovery mode and run
```
chown -R $USER:$USER /home/$USER
```
replace $USER with your user name in lower case

---

### Post by Mat11 on 2011-12-19
> **MartijnNL said:**
> You may have uninstalled other software when you removed nautilus, which you didn't automatically reinstall when you installed nautilus again.
 
You might want to try pressing Ctrl+Alt+F1, logging in and running:
 
```
sudo apt-get install ubuntu-desktop
```This should re-install the basic desktop system with everything that belongs to it. (Without removing other software you may have installed.)
 
By the way: problems with rights normally just can't be solved by uninstalling and reinstalling software.
 
Edit:I just removed the first sentence, which was no longer relevant.
 
Hi i tried the Ctrl Alt F1 and managed to force myself onto a blk screen which wanted a log-in and password but when i put my usual password in it keeped on saying incorrect log-in and password.I vagely see in the background after i escape this screen for a few seconds Udev 378 will no longer be in a future version.Also theres a mention of Apport Armour when i leave the window then i'm redirected to the blanked out log-in box which is no use.
Would my 10.10 Cd be of any use ?

---

### Post by Mat11 on 2011-12-19
> **pqwoerituytrueiwoq said:**
> probally messed up permissions using sudo on gui apps when you should have used gksu
boot to recovery mode and run
```
chown -R $USER:$USER /home/$USER
```replace $USER with your user name in lower case

Hi i many thanks for your reply i have to first find a way of using the boot CD to sort things out because i'm unable to get past the user log-in which is blanked out.Once i managed to get into the command terminal which asked me for a user name and password of which my laptop did not recognise. I'm tempted to reinstall Maverick 10.10 once again fully but will think about it.

---

### Post by MartijnNL on 2011-12-20
You can get into recovery mode by holding the shift key right at te beginning of the boot sequence, just after the screen where you can enter the BIOS (usually with the logo of your laptop manufacturer) when the screen turns black. Hold it until you see the GRUB (bootloader) menu. Then select the recovery mode from the first kernel. You will not need any password.

By the way: you said the system didn't accept your username and password: are you aware that your username is not the full name you entered during installation which is normally shown in the login menu?

If you're going for a reinstall, I would not install Maverick, if I were you. Because it will no longer be supported with updates from April on. Either move back to Lucid (which will be supported till April 2013, or go for 11.04 (11.10 seems to have a lot of problems) if you're willing to work with Unity or try something else like Xubuntu 11.04 or Linux Mint.

---

### Post by Mat11 on 2011-12-20
Thanks for your reply. I managed to enter the recovery using the disk and found the terminal page and ran the Ubuntu desktop install and it worked i was able to access my user box at log-in.Your help has been appreciated although i'm half way to fixing my problem of no location bar and no acess to the internet using myself as a continuing user.
I'm fully aware that support finishes for Maverick 10.10 in April as i'm aware that versions after mine are having problems that would drive me crazy.If the LTS release
does'nt work i'm looking else where despite the fact that Maverick overall is brilliant and delivers what it offers - mine was hitched to medibuntu when i first had it for skype and google earth.
Just want to say i do not understand why i was able to delete my top location bar very late at night because i was angry about the fact that one of files i was using had jumped into Places located in the top location bar.At the time i remember that the file i was opening in my Documents was dead for clicking into it.It just wounld'nt open.
For a moment i thought it was a security problem ! 
I have recently read others having the same problem of folders jumping into places recently ??? How can it just start happening ?
Just thought i'd say i'm still writing from a non Ubuntu OS because i have no access to the internet !

---

### Post by Mat11 on 2011-12-20
> **pqwoerituytrueiwoq said:**
> probally messed up permissions using sudo on gui apps when you should have used gksu
boot to recovery mode and run
```
chown -R $USER:$USER /home/$USER
```
replace $USER with your user name in lower case
 
Hi thanks for the reply i tried your chown code and i'm having permission problems with HPLIP and my folders which are all locked.I stopped what was happening in the terminal at the time because i'm worrying about getting further problems after many permission denied warnings and exclaimations.
Just thinking on what to do next carefully.
 
Thanks once again nearly there.:)

---

### Post by MartijnNL on 2011-12-21
> **Mat11 said:**
> Hi thanks for the reply i tried your chown code and i'm having permission problems with HPLIP and my folders which are all locked.I stopped what was happening in the terminal at the time because i'm worrying about getting further problems after many permission denied warnings and exclaimations.
Just thinking on what to do next carefully.
 
Thanks once again nearly there.:)

Did you run it from the recovery mode? If you did it logged in as yourself you shut have put 'sudo' before the command.

---

### Post by Mat11 on 2011-12-21
> **MartijnNL said:**
> Did you run it from the recovery mode? If you did it logged in as yourself you shut have put 'sudo' before the command.
 
Hi Martin,
 
Have tried booting in Recovery mode and tried the sudo chown code exactly which bumped up to resume normal boot of which i did and found nothing happened.I tried it again and the same thing occured but i did notice that some of the computers own listed commands dropping down in sequence indicated that -- recovery is required on a read only filesystem. Is that because of some locked files ??
 
Nothing happened with the sudo chown -R $user:$user /home/$user 
 
I'm thinking i have to get back online so a reinstall is on the cards, also i'm wondering if i've damaged something to do with file permissions.:(
 
Thanks.

---

### Post by MartijnNL on 2011-12-21
In recovery mode you don't need to use sudo (as you have a root prompt). I assume you select the root option in the recovery menu (bottom one). And did you replace $user (all three times) with your actual username?

---

### Post by MartijnNL on 2011-12-21
Another thing: did you also try my earlier suggestion:

```
sudo apt-get install ubuntu-desktop
```

Just in case you accidentally uninstalled software.

You can do this from a recovery mode with networking (netroot, one of the options in the menu). If you do it from the recovery menu, remove the sudo from the command.) After you do this, you can return to the menu with the 'exit' command and then choose resume.

---

### Post by Mat11 on 2011-12-22
> **MartijnNL said:**
> Another thing: did you also try my earlier suggestion:

```
sudo apt-get install ubuntu-desktop
```Just in case you accidentally uninstalled software.

You can do this from a recovery mode with networking (netroot, one of the options in the menu). If you do it from the recovery menu, remove the sudo from the command.) After you do this, you can return to the menu with the 'exit' command and then choose resume.

Hi your suggestion worked when i used the code in recovery mode earlier,because i've just played around with the bottom panel after unlocking it and deleted a greyed out windows symbol square,and hey presto a top panel emerged where it should be.My internet access is back on brill.
Have noticed that my cairo dock is back and operational although it needs reinstalling as its blacked out too much background.The bottom pane seems to be more stable and fixed no longer flickering.Have reset all my system tools and the correct app pointers to the top panel above.

Problem solved Thank you.
Hope you have a Merry Xmas and Happy New Year.

Thanks Matt

---

