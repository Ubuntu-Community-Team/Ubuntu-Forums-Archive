---
title: "Firefox Version 3.6.8"
date: 2010-09-08
forum: General Help
---

### Post by kellyapproved on 2010-09-08
I've just installed Ubuntu and did all the prescribed 274 updates that were listed in updated manager.

Firefox on my Ubuntu box is version 3.6.8 but when I go to the Mozilla site, the latest version is 3.6.9.  I'm just wondering why Ubuntu wouldn't have made the most current version of Firefox with all the security patches available to its users?

Thank you

---

### Post by inameiname on 2010-09-08
Usually it takes a while, if ever, for the official repos to update Firefox. Lately though, it has been updating, just a tad later than say the following. An alternative, to which I use, is using the Ubuntuzilla repo. It just came out with 3.6.9 today. Just add it to your sources.list.


 **If you are using Ubuntu Jaunty (9.04) or later:** 
The repository to add, if you're adding it manually to your sources.list, is  
 deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main 

and you can use the following command to add it to your *sources.list* in one step: 
 [COLOR=black][FONT=monospace]echo -e "\ndeb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main" | sudo tee -a /etc/apt/sources.list > /dev/null [/FONT][/COLOR]
 



[LIST]
[*] Then add the package signing key to your keyring, by running the following command:
[/LIST]
 sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29  
[LIST]
[*] Update your package database:
[/LIST]
 sudo apt-get update  
[LIST]
[*] Install your desired package, with the following command:
[/LIST]
 sudo apt-get install firefox-mozilla-build

---

### Post by kellyapproved on 2010-09-08
> **inameiname said:**
> Usually it takes a while, if ever, for the official repos to update Firefox. 

Thanks for the tips below, but being so new to Linux, I was hoping to rely on Ubuntu to perform the necessary updates without jumping through any extra hoops.

If it takes so long for them to update Firefox, doesn't this leave us open to risk from whatever security hole was not patched?

---

### Post by inameiname on 2010-09-08
Nevermind now. The latest firefox just came out and is in the official repos now. You were about an hour too early to post. :P


FYI, if you aren't aware, Ubuntu is not a rolling release distro, meaning for most of it's applications, it WILL NOT update. That is why those that desire the latest packages, not just later test versions but stable ones as well, installing third-party repositories are the way to go. This contrasts to what Ubuntu came from, Debian, which provides rolling releases, which means it updates it's repos. 

Fortunately though, with Lucid and on, Firefox doesn't seem to be one of those apps not updated in the Ubuntu repos.

---

### Post by kellyapproved on 2010-09-09
> **inameiname said:**
> Nevermind now. The latest firefox just came out and is in the official repos now.

You're right, just did the update.  It would have been interesting to see when the latest version of Firefox came out and then see how long it took for ubuntu to add the update to the update manager.

---

### Post by claracc on 2010-09-09
From [http://www.mozilla.com/en-US/firefox/3.6.9/releasenotes/](http://www.mozilla.com/en-US/firefox/3.6.9/releasenotes/), you can read: Firefox 3.6 Release Notes

v.3.6.9, released September 7th, 2010.

Today 9 of september, i have received the firefox update to 3.6.9.

As you can see, the update of firefox in ubuntu is very quick.

---

### Post by dcstar on 2010-09-09
> **inameiname said:**
> 
.......
FYI, if you aren't aware, Ubuntu is not a rolling release distro, meaning for most of it's applications, it WILL NOT update. That is why those that desire the latest packages, not just later test versions but stable ones as well, installing third-party repositories are the way to go. This contrasts to what Ubuntu came from, Debian, which provides rolling releases, which means it updates it's repos. 

Fortunately though, with Lucid and on, Firefox doesn't seem to be one of those apps not updated in the Ubuntu repos.

Ubuntu releases **updates** for all security related issues on every still supported release, it will not upgrade versions of those packages (there are just too many packages in all the Ubuntu releases that are still supported). Every single package to be upgraded has to be tested, I'm sure if Ubuntu had a thousand more qualified volunteers than this may be viable.

If you want new versions of **some** packages then enable the Backports repository and **some** new versions being developed for the Ubuntu version past your current one will be made available for your release.

---

### Post by inameiname on 2010-09-09
Indeed. Thanks for clarifying dcstar. Another option is to enable the proposed repo as well in software sources if desired. It was only recently that I decided to update it, fearing it mainly housed stuff that might break things, but after a lot of folks stated they always have it updated and it never gave them issues, I found it to be another option. Of course, I'm a guy with over 30 PPAs that I test and use all the time, so fearing security and instability isn't a big issue for me. ;)

---

