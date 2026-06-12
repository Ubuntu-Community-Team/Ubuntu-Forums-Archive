---
title: "Thunderbird"
date: 2010-05-17
forum: General Help
---

### Post by Drenriza on 2010-05-17
I have just installed thunderbird on my clean install 10.04.
But after the install i dont get an icon i can use, and need to start the program with

```
sudo thunderbird
```

How can i create an desktop-thunderbird-icon?

Thanks on advance
Kind Regards

---

### Post by scouser73 on 2010-05-17
Did you install Thunderbird via the Synaptic Package Manager, or did you download it from the Mozilla website and install it that way?

---

### Post by Drenriza on 2010-05-17
used
```
sudo apt-get install thunderbird
```

---

### Post by wilee-nilee on 2010-05-17
Right click on menu>edit and see if thunderbird is in the internet portion if it is tick it on then off and see if this works. Top build a launcher just right click on the desktop and click create launcher name it put 
```
thunderbird %u
``` in the command click on the icon and look in the download folder for a icon.

---

### Post by scouser73 on 2010-05-17
Ok, here's a Mozilla Thunderbird .png that you can use as a menu icon, don't worry about the size because it will fit perfectly.

[http://www.propiedadesambato.com/images/Mozilla%20Thunderbird.png](http://www.propiedadesambato.com/images/Mozilla%20Thunderbird.png)

Instructions for setting a menu icon.

**1** - Save the icon anywhere on your cumputer

**2** - Right click on the Ubuntu icon and select **Edit Menus**

**3** - Next a box will appear showing you all the applications in the menu, click on **Internet**

**4** - Then click on **Thunderbird** & then click **Properties**

**5** - Now you'll see a place where your icon should be, click on that and locate where you saved the icon on your PC & select it.

[[IMG]http://img301.imageshack.us/img301/8997/screenshoteg.th.png[/IMG]](http://img301.imageshack.us/my.php?image=screenshoteg.png)

Done, you will now have the Thunderbird icon displaying correctly.

---

### Post by Drenriza on 2010-05-17
[scouser73]("http://ubuntuforums.org/member.php?u=536148") i used your guide. And now i have an icon BUT

when i click on the icon and start thunderbird it ask me to choose an profile. I have already a profile that i made when i started the program from the command line. And that profile is not displayed in box to choose profiles from.

But if i start thunderbird again from the command line it with my profile.

?????

---

### Post by John Bean on 2010-05-17
> **Drenriza said:**
> [scouser73]("http://ubuntuforums.org/member.php?u=536148") i used your guide. And now i have an icon BUT

when i click on the icon and start thunderbird it ask me to choose an profile. I have already a profile that i made when i started the program from the command line. And that profile is not displayed in box to choose profiles from.

But if i start thunderbird again from the command line it with my profile.

?????

You had started TB using sudo (why???) so the profile you created belongs to root, not you.

---

### Post by Drenriza on 2010-05-17
Well the account need to be stored somewhere. Cant i find it from the terminal and change the user:group from root to my "normal user" ?

---

### Post by John Bean on 2010-05-17
> **Drenriza said:**
> Well the account need to be stored somewhere. Cant i find it from the terminal and change the user:group from root to my "normal user" ?

It's probably in /root/.thunderbird but I'm not going to run it as root just to find out for certain. I'd be inclined to create a new profile and put it down to experience.

Out of interest, why did you run it with sudo in the first place?

---

### Post by Drenriza on 2010-05-17
Was sleeping abit. What can i say :)

Profile couldn't be created. Probably the chosen folder isn't writable.
[Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIToolkitProfileService.createProfile]"  nsresult: "0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)"  location: "JS frame :: chrome://mozapps/content/profile/createProfileWizard.js :: onFinish :: line 233"  data: no]

........................................zzzzzz..........

---

### Post by Drenriza on 2010-05-17
i cannot see the .thunderbird folder,

i can only locate
cristian-desktop:~# locate thunderbird
/usr/share/app-install/desktop/thunderbird.desktop
/usr/share/app-install/icons/thunderbird.png

i cannot uninstall it ```
apt-get --purge thunderbird or --remove
```
i cannot write to any folders unless im root.

---

### Post by Drenriza on 2010-05-17
This starts to **** me off abit.

I have removed thunderbird with
```
sudo dpkg --purge thunderbird
```
```
sudo apt-get autoremove 
```
re-installed with
```
sudo apt-get install thunderbird
```i start the program as my normal user, click create account, enter account name click next and then

Profile couldn't be created. Probably the chosen folder isn't writable.
[Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIToolkitProfileService.createProfile]"  nsresult: "0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)"  location: "JS frame :: chrome://mozapps/content/profile/createProfileWizard.js :: onFinish :: line 233"  data: no]

Obviously some configuration files are still left behind when un-installing thunderbird....... Why wont it just un-install the program. 100%

---

### Post by Drenriza on 2010-05-17
sudo chown cristian:cristian /home/cristian/.thunderbird/ 

[email]root@cristian-desktop:/home/cristian/.thunde[/email]rbird# chown cristian:cristian appreg
[email]root@cristian-desktop:/home/cristian/.thunde[/email]rbird# chown cristian:cristian bssc4u5j.default
[email]root@cristian-desktop:/home/cristian/.thunde[/email]rbird# chown cristian:cristian profiles.ini

totalt 20K
drwx------  3 cristian cristian 4,0K 2010-05-17 11:20 .
drwxr-xr-x 31 cristian cristian 4,0K 2010-05-17 13:50 ..
-rw-r--r--  1 cristian cristian  335 2010-05-17 11:20 appreg
drwx------  5 cristian cristian 4,0K 2010-05-17 13:30 bssc4u5j.default
-rw-r--r--  1 cristian cristian   94 2010-05-17 11:20 profiles.ini


SOLVED !

Thanks for the help guys. Thank god im done with this

---

### Post by John Bean on 2010-05-17
Ah, you also fell over another no-no - you ran a graphic app (thunderbird) using sudo instead of gksu. This caused thunderbird to run as root but use your home folder instead of using /root.

Two lessons here:

1. Don't use sudo unless you really need to
2. Never run graphics apps with sudo - use gksu if you need to give root privileges to a graphics program.

---

