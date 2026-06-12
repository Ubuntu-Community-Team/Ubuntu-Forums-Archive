---
title: "[SOLVED] Shiretoko to Firefox 3.5 Upgrade"
date: 2009-07-06
forum: General Help
---

### Post by DaftPyramid on 2009-07-06
I've been using the firefox-3.5 package, which until today was Firefox 3.5 beta 4 "Shiretoko". Today, it updated to the full release of Firefox 3.5 and everything seems fine. However, the application is still titled Shiretoko and it still has the Shiretoko logo. Is there a simple way to change this?

Also, I supposedly downloaded the update for the original Firefox install that comes pre-installed with Ubuntu, but it still says version 3.0.11. Why didn't this update correctly?

---

### Post by ajgreeny on 2009-07-06
I think you will need to change the command of your launcher for firefox in the menus or your desktop to **firefox-3.5** to actually get the new version running instead of the old one.  Try it in terminal first to see if I'm right.

---

### Post by lovinglinux on 2009-07-06
**Short answer: **you can't.

**Long answer:** uninstall Shiretoko and install the official Firefox 3.5 from Mozilla


The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Shiretoko+PPA, Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT). I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

Uninstall Shiretoko from terminal [see footnote] or synaptic:

```
sudo apt-get remove firefox-3.5
```

Then follow the method 1 of that tutorial and you will have the original Firefox 3.5 in no time.

Keep in mind that Shiretoko stores user profiles in the folder ~/.mozilla/firefox-3.5 instead of ~/.mozilla/firefox, so you might want to copy the profile from Shiretoko if you did important changes to it while using Shiretoko.

> **DaftPyramid said:**
> Also, I supposedly downloaded the update for the original Firefox install that comes pre-installed with Ubuntu, but it still says version 3.0.11. Why didn't this update correctly?

Because it's not available yet for update and probably won't be available until next Ubuntu release. They provide the Shiretoko with updates as a side-by-side installation for those who can't wait or want to test it in advance.





> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations. 
[url=http://www.uluga.ubuntuforums.org/showthread.php?t=1200781]

36 and counting...[/url]

---

### Post by DaftPyramid on 2009-07-06
Thanks lovinglinux, that worked.

---

### Post by lovinglinux on 2009-07-07
> **DaftPyramid said:**
> Thanks lovinglinux, that worked.

You are welcome.

---

### Post by ajgreeny on 2009-07-07
I have only installed FF3.5 on my test install of ubuntu on a separate partition, but I did not use any of the methods you mention.  I installed mine through the jaunty proposed repositories where the final version is available.  It appears to work very well, is a separate install to the FF3.0.11, but the profile was automatically copied from ~/.mozilla/firefox to ~/.mozilla/firefox-3.5, keeping them identical, but separate as well.

Is this "proposed" version of FF3.5 different from the ubuntzilla version you mention or the version direct from mozilla.  This is all getting very confusing, and I would like to know which way to jump.  Is there anything wrong with the jaunty "proposed" final version of FF3.5?

---

### Post by lovinglinux on 2009-07-07
> **ajgreeny said:**
> I have only installed FF3.5 on my test install of ubuntu on a separate partition, but I did not use any of the methods you mention.  I installed mine through the jaunty proposed repositories where the final version is available.  It appears to work very well, is a separate install to the FF3.0.11, but the profile was automatically copied from ~/.mozilla/firefox to ~/.mozilla/firefox-3.5, keeping them identical, but separate as well.

The proposed repositories are for proposed packages. Once they are reviewed and approved, they get into the regular repositories. That's what happened yesterday. You don't see it on my tutorial, because it is not needed anymore, since firefox-3.5 from the universe repository already contains this proposed package. Essentially, you have the same version of the first item of method #4, which is Shiretoko 3.5 final release. The difference is that you updated before they were approved. I also don't like the idea of including the proposed repository, because it will propose to update not only Firefox. 

> **ajgreeny said:**
> Is this "proposed" version of FF3.5 different from the ubuntzilla version you mention or the version direct from mozilla.  This is all getting very confusing, and I would like to know which way to jump.  Is there anything wrong with the jaunty "proposed" final version of FF3.5?

Here is a comparison that I included in the tutorial a couple of minutes ago:

> **lovinglinux said:**
> 

[size="4"][color=#CC0000]Method Comparison[/color][/size]

All methods install another version of Firefox on a separate location and can be used side-by-side with the official Ubuntu Firefox of your distribution.

[size="3"][color=#CC0000]**#1**[/color][/size] - this method is easy to perform, gives you total control of which version you will install and it gives you only official Mozilla releases, with Firefox branding (name and logo). Additionally, it uses the same Firefox profiles as the official Ubuntu version and updates your Firefox launchers automatically. It does not provide new version checking and download. You have to download new versions manually, remove the old version before updating with a new one and perform the installation commands for each new install.

[size="3"][color=#CC0000]**#2**[/color][/size] - essentially the same as the method #1, but provides a way to check for updates from Mozilla [releases site](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/) and install them automatically. Also provides an automated method of removal. Initial setup is not as easy as the manual installation, but is not complicated at all, since the automated script is provided as a deb install. It requires a single command to perform installation/removal of Firefox and other Mozilla applications.

[size="3"][color=#CC0000]**#3**[/color][/size] - more complicated to setup, since you need to configure additional PPA repositories. Depending on the PPA selected, you will get Firefox updates that are currently undergoing security testing or updates that are currently under development. This is not recommended if you want only stable releases, since you will probably get pre-alpha, alpha and beta releases as well. Additionally, all versions will not be Firefox branded. They use the development codenames, like Shiretoko or Minefield, and a default blue logo. These versions are not only installed side-by-side with Firefox 3.5, but also have their own Firefox profile folders, which might be complicated to maintain if you go back to stable official releases or when you upgrade Ubuntu. Versions installed by this method also have their own menu launchers, available through the "Appplications >> Internet" menu.

[size="3"][color=#CC0000]**#4.1**[/color][/size] - this method allows you to install unlicensed development versions of Firefox like the method #3 (actually this method is included in the method #3 procedures), but updates are performed only after being proposed by the universe repository maintainers and approved to enter this repository. You won't get regular updates like using the PPA repositories, but it's easier to configure and more stable. For instance, when Jaunty was released, the version installed by this method was Shiretoko 3.5 beta4pre, then it as updated to rc2 a couple of weeks before the official release of Firefox 3.5 and was updated to the final release less then a week after Mozilla.This method also creates new launchers. Your current Firefox profiles are automatically copied and put on a separate folder under ~/.mozilla

[size="3"][color=#CC0000]**#4.2**[/color][/size] - this method allows you to install cutting-edge versions of Firefox, optimized for your processor and branded as Swiftfox. It can be installed by using deb files or the Swiftfox repositories. Depending on which deb file you get or which updates you accept from the repositories, you might also get development versions. For instance, by the time of writing, Swiftfox version being provided was 3.5rc3-1. The major advantage of this method is the availability of versions optimized for your processor, which might result in a considerable performance boost. In the other hand, the major disadvantage is that these versions are non-free and the source code is not available. Unlike Shiretoko, Swiftfox versions uses the same profiles as your official Ubuntu Firefox installation, but also creates it's own launchers.

---

### Post by ajgreeny on 2009-07-07
OK, I think I see the difference.  I enabled the proposed repos just to install the final version of 3.5 then disabled them immediately so I didn't also update lots of other apps and do not get the update notifications again and again for things I don't want to update.  This was on a test installation of ubuntu, so it does not matter what happens, but as I said, it was all getting totally confusing.

Perhaps I shouldn't be in such an all-fired rush to update all the time!

---

### Post by lovinglinux on 2009-07-07
> **ajgreeny said:**
> OK, I think I see the difference.  I enabled the proposed repos just to install the final version of 3.5 then disabled them immediately so I didn't also update lots of other apps and do not get the update notifications again and again for things I don't want to update.  This was on a test installation of ubuntu, so it does not matter what happens, but as I said, it was all getting totally confusing.

Perhaps I shouldn't be in such an all-fired rush to update all the time!

I have updated the previous post with a simpler explanation, comparing all methods, that I just wrote for the tutorial. Thanks for asking. I this was really missing from the tutorial.

---

### Post by ajgreeny on 2009-07-08
No, thank you for the great resource of information.  It is really helpful to get all this, and now know what is what.

---

### Post by lovinglinux on 2009-07-08
> **ajgreeny said:**
> No, thank you for the great resource of information.  It is really helpful to get all this, and now know what is what.

You are welcome.

---

### Post by DaftPyramid on 2009-07-20
Don't mean to necropost here, but is there any way to update Firefox once I've installed it using this method? The "Check For Updates" option is greyed out.

---

### Post by scouser73 on 2009-07-20
The only way I can think of checking for updates in Firefox would be to uninstall your current version of Firefox.

I went to this site: [HERE]("http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/")


I used this method and I am able to check for updates, as happened when I updated to 3.5.1 (which was issued because of a security update).

There may be a much more simple approach than mine, but it's worth a go.

---

