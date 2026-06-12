---
title: "Ubuntu 11.10 failing to load"
date: 2011-11-07
forum: General Help
---

### Post by F1lthym0nk3y on 2011-11-07
So I've recently updated to ubuntu 11.10 from 11.04 in which I had been using the "ubuntu classic" desktop because I personally HATE unity.. anyways I upgraded through the package manager then scoured through the internet to look for a way to get rid of unity and use the traditional desktop environment and found this..

[http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html](http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html)

I used several of the commands listed there;

But now when I try to boot into Ubuntu I will continuously display the loading screen and bar loading on a loop and will not boot. I have tried safe mode but it gets stuck as well.

So how can I fix this? I have alot of important files on there and had the system configured to just my liking? Are there any possible ways I could fix it with a LiveCD?

As usual - many thanks ubuntu forums!

---

### Post by sirvinniei on 2011-11-07
> **F1lthym0nk3y said:**
> So I've recently updated to ubuntu 11.10 from 11.04 in which I had been using the "ubuntu classic" desktop because I personally HATE unity.. anyways I upgraded through the package manager then scoured through the internet to look for a way to get rid of unity and use the traditional desktop environment and found this..

[http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html](http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html)

I used several of the commands listed there;

But now when I try to boot into Ubuntu I will continuously display the loading screen and bar loading on a loop and will not boot. I have tried safe mode but it gets stuck as well.

So how can I fix this? I have alot of important files on there and had the system configured to just my liking? Are there any possible ways I could fix it with a LiveCD?

As usual - many thanks ubuntu forums!

the  problem i encoutered the first time was not setting the GRUB to fit my graphics card (nomodeset) this  looks very similar

if it doesn work try to boot using older linux versions and choose the  upper one.
if you are able  to boot ubuntu normally then immediatly use update centre to  update

---

### Post by F1lthym0nk3y on 2011-11-07
Many thanks! Will give it a try now..

---

### Post by F1lthym0nk3y on 2011-11-07
I've just tried booting with the previous Linux Kernel/Version which it boots into Kubuntu 11.04 and comes up with the same problem.. Freezing after waiting for network configuration then says booting without full network configuration then just doesn't load from there... :confused:

---

### Post by F1lthym0nk3y on 2011-11-07
Bump

---

### Post by F1lthym0nk3y on 2011-11-07
Bump

---

### Post by F1lthym0nk3y on 2011-11-07
Anyone? :(

---

### Post by F1lthym0nk3y on 2011-11-08
Epic bump for justice.

---

### Post by F1lthym0nk3y on 2011-11-08
Anyone I beg of you!

---

### Post by critin on 2011-11-08
I'm truly sorry for your problems. 

> [B]
 I have alot of important files on there and had the system configured to just my liking?[/B] 

Save your files on a flash drive or cd/dvd and reinstall 11.04.  Then add your saved files.  And don't be too quick to upgrade if the system is configured to your liking.  :confused:

> 
 because I personally HATE unity.

11.10 is Pure Unity.

---

### Post by BillyBoa on 2011-11-08
Just boot with the CD you are using for the installation and don't install but just use Ubuntu. Afterwards enter to your drive and backup all your files.
Then do a fresh install of the system you like.

---

### Post by F1lthym0nk3y on 2011-11-08
> **critin said:**
> I'm truly sorry for your problems. 



Save your files on a flash drive or cd/dvd and reinstall 11.04.  Then add your saved files.  And don't be too quick to upgrade if the system is configured to your liking.  :confused:



11.10 is Pure Unity.

Is there no way I can fix the loading screen so it boots up then I can get into ubuntu and install gnome classic..

Reinstalling is the last option for me I had hours on there of customizations, files, configs and shell scripts.. 

I will definitely take your advice next time though and not upgrade before checking out whether it has unity... :(

---

### Post by F1lthym0nk3y on 2011-11-08
> **BillyBoa said:**
> Just boot with the CD you are using for the installation and don't install but just use Ubuntu. Afterwards enter to your drive and backup all your files.
Then do a fresh install of the system you like.


No I upgraded from 11.04... I have hours of customization on there which I simply can save to disk from a LiveCD unfortunately :(

---

### Post by Immolatus on 2011-11-08
sudo apt-get install gnome-fallback-session

or go to /etc/inittab and manually remove unity from startup deamons.

P.S. gnome requires DBUS to be running first so add that in first(deamons are loaded in order left to right).

---

### Post by critin on 2011-11-08
> I will definitely take your advice next time though and not upgrade before checking out whether it has unity.

Ubuntu is Unity.  It's not going away.  lol
The next version will be a LTS I believe, so it will be a more stable version.  12.04.

---

### Post by F1lthym0nk3y on 2011-11-08
> **Immolatus said:**
> sudo apt-get install gnome-fallback-session

or go to /etc/inittab and manually remove unity from startup deamons.

P.S. gnome requires DBUS to be running first so add that in first(deamons are loaded in order left to right).

I don't understand how I can do this as I cant boot into ubuntu it gets stuck at "booting without a network configuration" then the loading bar continuously does its thing but the login screen doesn't come up..

---

### Post by F1lthym0nk3y on 2011-11-08
> **critin said:**
> Ubuntu is Unity.  It's not going away.  lol
The next version will be a LTS I believe, so it will be a more stable version.  12.04.

Its such a shame though, I'm sure some people like unity.. BUT why couldn't they leave the option of the ubuntu/gnome classic environment? Its frustrating and making me think of switching to Mint.

---

### Post by critin on 2011-11-08
> **F1lthym0nk3y said:**
> Its such a shame though, I'm sure some people like unity.. BUT why couldn't they leave the option of the ubuntu/gnome classic environment? Its frustrating and making me think of switching to Mint.

Searching and reading the forums will give you the answer.  Gnome is a gnome project, not a ubuntu project.  Gnome developers decided that gnome needed to be updated--so they did.  Ubuntu had to use what gnome offered or go in another direction.  They chose Unity, with a users choice of gnome 3.  Someone also tried their best to get gnome 3 to act as much like gnome classic as they could for users like you and me, who preferred it.  I haven't tried to change it though, I'm trying to use unity.  

Other versions are still using gnome 2,  but unless they continue the development on their own, they will all create their own versions of what they want to do.  Developers all contribute their own projects, it isn't just one developer -(ubuntu).  It's a community thing that sometimes grow away from each other.  I may not have this exactly right, but the gist is correct.  gnome is gnome and ubuntu is ubuntu.  I can still use gnome classic, the real classic in 11.04, so I will keep it for awhile.

I think we can get used to unity if we want to.  If not, there are other distros to use that are not using unity.  Choices are many.

---

### Post by F1lthym0nk3y on 2011-11-11
> **critin said:**
> Searching and reading the forums will give you the answer.  Gnome is a gnome project, not a ubuntu project.  Gnome developers decided that gnome needed to be updated--so they did.  Ubuntu had to use what gnome offered or go in another direction.  They chose Unity, with a users choice of gnome 3.  Someone also tried their best to get gnome 3 to act as much like gnome classic as they could for users like you and me, who preferred it.  I haven't tried to change it though, I'm trying to use unity.  

Other versions are still using gnome 2,  but unless they continue the development on their own, they will all create their own versions of what they want to do.  Developers all contribute their own projects, it isn't just one developer -(ubuntu).  It's a community thing that sometimes grow away from each other.  I may not have this exactly right, but the gist is correct.  gnome is gnome and ubuntu is ubuntu.  I can still use gnome classic, the real classic in 11.04, so I will keep it for awhile.

I think we can get used to unity if we want to.  If not, there are other distros to use that are not using unity.  Choices are many.


Well said, couldn't of put it better myself.. I agree with most of what you said. BUT, I really think the team at ubuntu are alienating a large majority of their current users with the whole unity thing - I know quite a lot of people who have now switched to another distro because they cannot get along with unity but as you said - choices are many..

Anyways, back to my problem.. Can anyone help? :confused:

---

### Post by F1lthym0nk3y on 2011-11-14
Bump

---

