---
title: "How do I update Skype on Ubuntu 10.04?"
date: 2012-08-01
forum: General Help
---

### Post by ShowMeGrrl on 2012-08-01
Today my Upgrade Manager popped up with various proposed upgrades. But I got a warning that the proposed Skype update was "not authenticated" and thus could be malware.

I unchecked it and did the other proposed upgrades but not the Skype upgrade.

I then opened Synaptic and searched for Skype. It had a grayed-out box with an exclamation point. The "Icon Legend" said this means the app is "upgradeable."

The question is: How do I do the upgrade? 

Within Synaptic, I clicked on the "Mark all upgrades" button and got a warning something like "you are about to install software that cannot be authenticated" and thus could be malware. 

I currently have Skype 2.2.0.35 on my Ubuntu 10.04 computer. The upgrade version, according to Synaptic, is 4.0.0.8, and both of these versions are for lucid (10.04).

I've done various searches on Ubuntu Forums Ubuntu Documentation and the Web generally. I have read that it is better to do installs and upgrades from the repositories rather than from Skype directly, and I generally try to stick to the repositories. 

I have also read that before installing the new Skype (4.0.0.8), I should uninstall the old (2.2.0.35) or there will be conflicts. But if I do the upgrade from within Synaptic, won't Synaptic take care of all that?

I am very uncertain about how to proceed in order to get the Skype upgrade. Suggestions/information appreciated.

---

### Post by Kundan Negi on 2012-08-01
if your are worried that your skype is not authentic then download it from Skype site "http://www.skype.com/intl/en/get-skype/on-your-computer/linux/"

after downloading it, go to the directory where skype is donwloaded usually Downloads directory.Then open your Terminal and type this
 sudo dpkg -i downloaded_package_name.deb

---

### Post by Dave_L on 2012-08-01
I'm also on Ubuntu 10.04.

Using synaptic, I upgraded skype from 2.2.0.35-0lucid1 to 4.0.0.7-0lucid1 on July 30, and from 4.0.0.7-0lucid1 to 4.0.0.8-0lucid1 on July 31. There were no warning messages or other problems.

I just searched for skype at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and it doesn't seem to be there.

Maybe it's just a temporary glitch with the repositories, and you should try again in a day or two.

---

### Post by ShowMeGrrl on 2012-08-01
> **Kundan Negi said:**
> if your are worried that your skype is not authentic then download it from Skype site "http://www.skype.com/intl/en/get-skype/on-your-computer/linux/"

after downloading it, go to the directory where skype is donwloaded usually Downloads directory.Then open your Terminal and type this
 sudo dpkg -i downloaded_package_name.deb
Yes, but this does not answer the warning I read online (sorry can't remember where I read that but it seemed a reputable site) against installing Skype directly from the Skype site (risk of conflicts, I believe)

nor my concern about whether I first need to uninstall the 2.2.0.35 version. I'd hate to uninstall it (it's working) and then be left with no Skype if the upgrade from the Skype site doesn't work. 

What I am really hoping for is a way to make the normal Update Manager/Synaptic process work and to understand why I am getting these "unauthenticated" warnings for the Skype update that is being proposed by the Update Manager.

---

### Post by plucky on 2012-08-02
> What I am really hoping for is a way to make the normal Update Manager/Synaptic process work and to understand why I am getting these "unauthenticated" warnings for the Skype update that is being proposed by the Update Manager. 

The unauthenticated warning is usually "Update Manager" not getting the right authentication information from the repositories.This can be caused by a number of things,including the repository not in sync with the Main Repository.

It is worth changing to the MAIN Repository to see if the problem goes away,but remember to change back to your local repository to get faster downloads.

Open a terminal and run ```
sudo apt-get update
``` and post back if there are any errors.

Good Luck

---

### Post by ShowMeGrrl on 2012-08-02
> **plucky said:**
> The unauthenticated warning is usually "Update Manager" not getting the right authentication information from the repositories.This can be caused by a number of things,including the repository not in sync with the Main Repository.

It is worth changing to the MAIN Repository to see if the problem goes away,but remember to change back to your local repository to get faster downloads.

Open a terminal and run ```
sudo apt-get update
``` and post back if there are any errors.

Good Luck
OK, thanks for your post. I ran the suggested command in the terminal, which produced 39 lines of "Get" and ended with this:


> Fetched 13.2MB in 28s (457kB/s)                                                
W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  non-free/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Last week I was getting warnings that the Google update was not authenticated. I couldn't figure that one out either. I have Chromium and also Google Earth. I think the unauthenticated updates were for Chromium.

Very aggravating. I prefer these updates be painless!

---

### Post by plucky on 2012-08-02
Open Software Sources and un-tick the Google Repository and see if the error goes away.

I think if Software Sources is not in the DASH,you can get to it through the **Settings** button in Update Manager.

Then run the "Check" in Update Manager and see if it gives you the Skype Update.

Good Luck

---

### Post by ShowMeGrrl on 2012-08-02
> **plucky said:**
> Open Software Sources and un-tick the Google Repository and see if the error goes away.

I think if Software Sources is not in the DASH,you can get to it through the **Settings** button in Update Manager.

Then run the "Check" in Update Manager and see if it gives you the Skype Update.

Good Luck
Hey, guess what! Before I saw the above message, but after running the > sudo apt-get update command in my terminal, I went to the Update Manager and ran check and it installed not only the Skype update without complaint but also the Chromium updates without complaint. So all of my problems have been solved! Thank you very much!!

I should note that the Chromium update problem may have been solved by an action I took a couple days ago of typing this line in the terminal:

> sudo add-apt-repository ppa:chromium-daily/stable If you want me to provide you with the response I got back in the terminal from this command I would be happy to. I don't believe I ran Update Manager after typing that command -- until now. 

I did not uncheck the Google Repository, because I didn't see your post until after I had run the Update Manager and done the install.

I just now tried out Skype and I do now have the new 4.0.0.8 version. I did a test call, which worked. That tested audio; I haven't yet tested video. (All of my contacts are sane and asleep at this hour.)

I have one last question. You gave me a command to use what you called the Main repository and then advised me to return to my local repository. I don't really know what my local repository is. How do I return to it?

---

### Post by plucky on 2012-08-02
> I have one last question. You gave me a command to use what you called the Main repository and then advised me to return to my local repository. I don't really know what my local repository is. How do I return to it? 

If you open Software Sources in 10.04,In the first TAG it refers to the "Download Server",which you can change to any mirror that is available at your location.
You can also test to see which is your fastest repository.
You can also select the "Main" repository,which is the repository that all other mirrors are synced to.


Good Luck

Glad you got it fixed.

---

### Post by ShowMeGrrl on 2012-08-02
> **plucky said:**
> If you open Software Sources in 10.04,In the first TAG it refers to the "Download Server",which you can change to any mirror that is available at your location.
You can also test to see which is your fastest repository.
You can also select the "Main" repository,which is the repository that all other mirrors are synced to.


Good Luck

Glad you got it fixed.
OK, I see. Thanks! I will mark this thread as SOLVED! Thank you so much!

---

