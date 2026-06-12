---
title: "How to get/install Google Chrome Stable"
date: 2011-06-16
forum: General Help
---

### Post by s9032g@comcast.net on 2011-06-16
Does anyone have a definitive and tried method to get Google Chrome (replacing Chromium). I see a lot of conflicting comments on line. It seems that Google does have a 32-bit deb available.

Thanks   SteveG

---

### Post by howefield on 2011-06-16
Have you tried downloading the deb file from here...

[http://www.google.com/chrome/eula.html?hl=en-GB&platform=linux](http://www.google.com/chrome/eula.html?hl=en-GB&platform=linux)

Then double click the file to start the install process. You might want to remove Chromium first using Synaptic Package Manager.

---

### Post by s9032g@comcast.net on 2011-06-18
Thanks for the response.

I did try that link before putting out the query. The deb seemed to download but I couldn't activate anything. I had not dumped Chromium before hand. I might try that.

Has anyone actually done this and had it work?

SteveG

---

### Post by gandaran on 2011-06-18
> **s9032g@comcast.net said:**
> Thanks for the response.

I did try that link before putting out the query. The deb seemed to download but I couldn't activate anything. I had not dumped Chromium before hand. I might try that.

Has anyone actually done this and had it work?

SteveG
activate what? just click the .deb file to install.

---

### Post by knutschr on 2011-06-18
Add to repositories
```
http://dl.google.com/linux/chrome/deb/stable main
```

---

### Post by garagestmarien on 2011-06-18
Sorry, this may sound stupid, but:

What's the difference between Google Chrome and Chromium.
(I am using Chromium)

---

### Post by gandaran on 2011-06-19
> **garagestmarien said:**
> Sorry, this may sound stupid, but:

What's the difference between Google Chrome and Chromium.
(I am using Chromium)
visually nothing except the name and logo! both look, feel and work the same way but chromium is more fast with web surfing, one big deference is chromium is mainly a gtk application, try installing chromium in a KDE desktop environment and it will pull a ton of gtk dependencies while chrome works on any linux desktop environment without installing any gtk dependencies.

---

### Post by GodveX on 2011-06-19
I had the same problem with chromium it would always feel laggy and slow when i was using it to surf the web. I switched to chrome and my troubles were gone is chromium in the beta stages or something ?

---

### Post by sixcorners on 2011-06-19
> **garagestmarien said:**
> Sorry, this may sound stupid, but:

What's the difference between Google Chrome and Chromium.
(I am using Chromium)

Chromium is the open-source core of Google Chrome. Some [proprietary components]("http://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome") are left out of Chromium (I think I heard that that HTML5 speech thing is different with Google Chrome). I think it would be apt to compare it to Safari vs Webkit but I'm not sure. Webkit is supposed to be a core HTML library but when I download the Webkit builds it does everything from javascript to having that familiar Safari style.. Soo.. I don't really understand that difference.

What is the difference between installing the .deb and adding the repository and installing from there? Does the .deb prevent the package management system from updating the software? What exactly is contained in the .deb? If I install the .deb and it is outdated will I have to update my software again immediately? Why do I have to mess with authentication keys every time I add a source code repository but not when I install a .deb? Isn't there a better way to do that? SSL or something? Soon DNSSEC?

---

### Post by DeMus on 2011-06-19
Check out this website:

[Chrome Stable]("http://www.ubuntuupdates.org/ppas/8")

When you add this repository to your list you will get updates whenever they appear. Works great.

---

### Post by gandaran on 2011-06-19
> What is the difference between installing the .deb and adding the repository and installing from there?
when installing the chrome .deb first time the .deb also automatically adds the chrome repository to software sources so you will get all future updates for chrome in the update manager

---

### Post by sixcorners on 2011-06-19
> **gandaran said:**
> when installing the chrome .deb first time the .deb also automatically adds the chrome repository to software sources so you will get all future updates for chrome in the update manager

Does it also add the sources repository? Does it also add the authentication key? Does it make sure that you are installing the latest version or do you have to check for updates right after installing?

---

### Post by gandaran on 2011-06-19
> **sixcorners said:**
> Does it also add the sources repository? Does it also add the authentication key? Does it make sure that you are installing the latest version or do you have to check for updates right after installing?
yes the chrome stable deb also adds the the authentication key and if the .deb is not up to date you will get the update in update manager

---

### Post by sixcorners on 2011-06-19
> **gandaran said:**
> yes the chrome stable deb also adds the the authentication key and if the .deb is not up to date you will get the update in update manager

Ok, thanks.. I guess it makes sense now.. So the .deb is basically a way to install things offline? I wonder if .debs can be empty and just exist to add the repository.
Also I guess there wouldn't be a source repository for Google Chrome because it isn't open source..
Seems like it would be easier to distribute .sh files instead of .deb files and just install everything with the repository tools unless you needed to install something to multiple computers that are not behind a caching proxy..
Thanks again for the information.

---

### Post by s9032g@comcast.net on 2011-06-19
I did. And it did not install. If it had, then I would not be seeking answers.

SteveG

---

### Post by gandaran on 2011-06-19
> **s9032g@comcast.net said:**
> I did. And it did not install. If it had, then I would not be seeking answers.

SteveG
what was the problem? always post the errors! we cant help without knowing what went wrong!
and what ubuntu version? also 32-bits or 64-bits?

---

### Post by s9032g@comcast.net on 2011-06-24
> **s9032g@comcast.net said:**
> Does anyone have a definitive and tried method to get Google Chrome (replacing Chromium). I see a lot of conflicting comments on line. It seems that Google does have a 32-bit deb available.

Thanks   SteveG

Usually the simplest solution is best (Occam's Razor). Just download the deb from Google and install it using GDebi installer. Much faster and cleaner than Cromium. I hope that Ubuntu start using Google Chrome as standard equipment.

SteveG

---

### Post by s9032g@comcast.net on 2011-06-24
When you do it you get the backups setup automatically.

---

