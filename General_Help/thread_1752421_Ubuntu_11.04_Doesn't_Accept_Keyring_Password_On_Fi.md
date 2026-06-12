---
title: "Ubuntu 11.04 Doesn't Accept Keyring Password On First Try"
date: 2011-05-07
forum: General Help
---

### Post by lexen on 2011-05-07
Hey everyone.  This is a small problem, but I thought I should bring it up.  In ubuntu 10.10, I had this weird problem where after I have logged in and it asks me for my keyring password, it won't accept it.  It's a 1 letter password, so I know I am getting it right.  I put it in, and it will never work, but it will usually work the second time, though it occasionally waits until the 3rd time.  I assumed it would go away when I did a clean install of 11.04, but the problem persists.

Like I said, it's a small problem, but I wanted to know if anyone else was having this problem and if I should file a bug report.


Thanks,
Lexen

---

### Post by dontbejeff on 2011-05-08
Hello,

I am now having the same problem of the Keyring manager not accepting the password. I know I am getting it right (as it is a standard password of mine, and it worked yesterday), so it basically stopped accepting the password I had assigned. Is there a fix to this? Even better, is there a way to turn it off for the storage of wireless passwords? It's just plain annoying signing in, then having to put in a password to connect to my wireless router.

---

### Post by felipeochoa0918 on 2011-05-08
Go to your network manager, hit "edit connections". Go to the wireless tab, select the network you want to un-password-protect, and hit edit on the right. Type in your password and check the box at the bottom "make available for all users." That at least sovles half your problem.

---

### Post by fragos on 2011-05-08
I believe there's a bug where if multiple aps use keyring you get multiple password requests instead of just one.

---

### Post by cespinal on 2011-05-08
plus one

---

### Post by Blasphemist on 2011-05-08
System settings, passwords and encryption keys. You'll find two or more entries. Delete any that doesn't show Passwords: login. Then reboot.

With your next boot you will get multiple prompts for passwords but they should all build under one heading. After that, your login will be all that is needed.

---

### Post by alienmindtrick on 2011-06-21
> **Blasphemist said:**
> System settings, passwords and encryption keys. You'll find two or more entries. Delete any that doesn't show Passwords: login. Then reboot.

With your next boot you will get multiple prompts for passwords but they should all build under one heading. After that, your login will be all that is needed.

I've found a lot of "simple solutions" to this problem, and like this one, none of them work. Power down, restart, and you still get this:  

Unlock keyring

• An application wants access to the keyring 'Default', but it is locked.

Click the 'Details' tab and the options are:

• Automatically unlock this keyring whenever I'm logged in
• Lock this keyring when I log out
• Lock this keyring after ____ minutes
• Lock this keyring if idle for ____ minutes

I've clicked 'Automatically unlock...' in all 3 screens multiple times; I've gone into 'Keyrings and Password Encryption' multiple times and unlocked, deleted, made default, both the 'Default' keys and the 'Login' keys alternately. I even deleted the 'Login' key to see if that would help. Nada. Nothing. No change. I still get the 3 'Unlock Keyring' prompts. I can click cancel on each one and it seems to have no different effect than if I enter my password and click enter. But, SOMETHING must be done with the popups or you can do nothing else until you do.

This is beyond frustrating and it's baffling.

---

### Post by fragos on 2011-06-21
My default keyring was called passwords. The 3 login thing started again so I looked in .gnome2/keyrings and found a "login" keyring had been created. I did the following:

edited file "default" to login and deleted passwords.keyring.

At the next login all keys in user.keystore were referenced in "login" when viewed with "Passwords and Encryption Keys" in Dash. Now I'm back to one login but on ocassion 3 logins are required. Not quite fixed but better than before. No phantom keyrings have been created since the change so a default keyring of login.keyring has had a positive effect.

---

### Post by alienmindtrick on 2011-06-22
> **fragos said:**
> My default keyring was called passwords. The 3 login thing started again so I looked in .gnome2/keyrings and found a "login" keyring had been created. I did the following:

edited file "default" to login and deleted passwords.keyring.

At the next login all keys in user.keystore were referenced in "login" when viewed with "Passwords and Encryption Keys" in Dash. Now I'm back to one login but on ocassion 3 logins are required. Not quite fixed but better than before. No phantom keyrings have been created since the change so a default keyring of login.keyring has had a positive effect.

Tried it. Still get 3 login prompts.

---

### Post by Graham C Williams on 2011-06-25
Like you I've gone from one login to 3 overnight. I've seen this with 10.04 (32bit) but that never got worse than 2 logins needed.

I'd too like a resolution to this problem. It's a pain but not the end of the world.

Graham

Aspire 8935G
11.04 64bit

---

### Post by fragos on 2011-06-25
I've been fighting this for a long time. This all started for me at the same time I started using Ubuntuone, empathy and gwibber. For IM I also had Gmail and I started to use Tweetdeck for Twitter. So I uninstalled gwibber and empathy and it went back to one login for a while. Next I found that a login.keyring kept being created. As I've said before changing my default keyring to login and deleting my old default passwords.kingring brought me down to one login again. But low and behold now I occasionally have three logins but mostly only one. Very bizarre. I believe the steps I've taken having impacted the problem in a positive direction but the root cause may still exist. On my laptop, also running 11.04, I've never used Ubuntuone, empathy or gwibber. There I've no keyring logins what so ever.

---

### Post by sgreene59 on 2011-06-25
Same here, this is highly annoying.  How was Natty released like this?  How is this not fixed already?  I don't use Uone, Facebook or Twitter.  I should only have passwords for Evolution and my wireless keys stored.  I have 4 different Ubuntu systems at home and all are effected.

---

### Post by alienmindtrick on 2011-06-25
To keep from having more than one login prompt, I changed my login preferences at System > Administration > Login Screen (I'm using Gnome3 vice Unity...which I call Untidy) such that I now have to login at startup (sigh). Oh well. As inelegant as it is, it's better than having 3 or more pop up.

Just keep in mind that this minor inconvenience aside, Ubuntu is still better than Mac or Windoze. Sometimes I get frustrated and lose sight of that, but I never forget the big picture in the end.

---

### Post by evan54 on 2011-07-07
Hi all,

so I've been fighting with this issue since I set up 11.04 this week and finally today think I understood enough to fix it.

So in the folder:

~/.gnome2/keyrings/

all the settings are stored, so any time things screw up / you forget passwords this that and the other you can just delete everything in that folder and on the next log on you will simply be asked to enter a new keyring and you 'll have to set up everything again related to them. (Wireless, empathy, UbuntuOne for me).

Provided you enter a password to log in it should be fairly simple to get this working.
In the aforementioned directory there should be at least two files:

- login.keyring
- user.keystore

and potentially:

- default

all text files.

If you have a keyring that is not blank then "login.keyring" is encrypted and information in it protected.

No idea what user.keystore does and to be honest didn't have to deal with it once.. also is encrytped.

The "default" text file holds the value of the default keyring, which should be set to "login". This is done by opening "default" with any text editor and entering "login" as it's only content, saving and closing.

Now, the idea is that the login.keyring should be encrypted using the same key as your login password. Ie that when you are prompted to enter a keyring password enter the same password as when you login. Also, this can be later changed from the system > Preferences > Passwords and Encryption keys right click etc menus.

To summarise, you need to have:

- login.keyring and the password for it (also called key) to be the same as your log on password.
- user.keystore should appear automatically
- default if it exists it should have "login" as its content.

If you set up your computer to automatically log on it is a huuge pain in the but since the keyring doesn't get automatically unlocked and you will have to enter the keyring however many number of times it is required unless you have a blank password for the keyring. (in which case if you open the ~/.gnome2/keyrings/<name>.keyring file everything is readily available... generally a bad idea

Hope this was helpful and not too long.

---

### Post by eMJayy on 2011-07-14
Thanks Evan54

I started having this issue a day ago after being forced to do a hard reset due to a failed piece of hardware. You had the key bit of info that I was looking for to solve this problem - the location of the config files associated with the keyrings. The other stuff I already knew, but I suspected from the beginning that doing the keyring deletions without also deleting the config files won't fix the problem. The problem was that I didn't know where to find those particular config files. 

Apparently, when I did the hard reset, some of these config files got messed up. A little experiment I did earlier showed that deleting the keyrings in the **Passwords and Keyrings** window didn't delete the config files in .gnome2/keyrings.

[U]Basically what I did to solve the problem was this -
[/U]
*1. Delete all the keys in the Passwords and Keyrings window. (Normally, there should only be one password:login key in there, but once the problem began, multiple login keys were suddenly being created and being marked as default every time I rebooted)*

*2. Delete all the files found in ~/.gnome2/keyrings/ as Evan54 suggested. This is very important, because failure to do so is the reason why just deleting the keys in the **Passwords and Keyrings** window fails to fix the issue.* 

*3. Restart the machine*

My machine is configured to manual login. Once logged in, I got a prompt asking for the password to my wireless network. No other login prompts appeared. I then reactivated my accounts in Gwibber (each account stores separate login info in the keyring and is the reason why the unlock prompt may appear up to 3 or 4 times in a row at startup) and logged into my UbuntuOne account. Everything logged in automatically on restart for the first time since the problem started, confirming that the problem has been fixed. Thanks again!

---

### Post by fragos on 2011-07-14
> **eMJayy said:**
> Thanks Evan54

I started having this issue a day ago after being forced to do a hard reset due to a failed piece of hardware. You had the key bit of info that I was looking for to solve this problem - the location of the config files associated with the keyrings. The other stuff I already knew, but I suspected from the beginning that doing the keyring deletions without also deleting the config files won't fix the problem. The problem was that I didn't know where to find those particular config files. 

Apparently, when I did the hard reset, some of these config files got messed up. A little experiment I did earlier showed that deleting the keyrings in the **Passwords and Keyrings** window didn't delete the config files in .gnome2/keyrings.

[U]Basically what I did to solve the problem was this -
[/U]
*1. Delete all the keys in the Passwords and Keyrings window. (Normally, there should only be one password:login key in there, but once the problem began, multiple login keys were suddenly being created and being marked as default every time I rebooted)*

*2. Delete all the files found in ~/.gnome2/keyrings/ as Evan54 suggested. This is very important, because failure to do so is the reason why just deleting the keys in the **Passwords and Keyrings** window fails to fix the issue.* 

*3. Restart the machine*

My machine is configured to manual login. Once logged in, I got a prompt asking for the password to my wireless network. No other login prompts appeared. I then reactivated my accounts in Gwibber (each account stores separate login info in the keyring and is the reason why the unlock prompt may appear up to 3 or 4 times in a row at startup) and logged into my UbuntuOne account. Everything logged in automatically on restart for the first time since the problem started, confirming that the problem has been fixed. Thanks again!

the config files are in ~/.gnome2/keyrings

---

