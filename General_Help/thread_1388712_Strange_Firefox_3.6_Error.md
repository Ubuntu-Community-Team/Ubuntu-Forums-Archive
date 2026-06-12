---
title: "Strange Firefox 3.6 Error?"
date: 2010-01-23
forum: General Help
---

### Post by moore.bryan on 2010-01-23
I downloaded and installed the latest Firefox 3.6 on my Debian machine, but got this strange error when I fired it up for the first time:
```

firefox-bin: 1: Syntax error: "(" unexpected

```
Any ideas?

---

### Post by lovinglinux on 2010-01-23
How did you install it?

---

### Post by n0dix on 2010-01-23
Hey lovinglinux.! In your opinion why it is so difficult to install F3.6 with all the functionality. I stalled Shiretoko with not big problem.

---

### Post by Leppie on 2010-01-23
i installed namoroka without any problems from ppa.

---

### Post by n0dix on 2010-01-23
> **Leppie said:**
> i installed namoroka without any problems from ppa.

I don't install yet, but i read a document [http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market](http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market). It's very pessimistic!

---

### Post by moore.bryan on 2010-01-23
> **lovinglinux said:**
> How did you install it?
Since this is on my Debian machine, my only option is to download from the [GetFirefox]("http://www.getfirefox.com/") website, untar the file, and then symlink the firefox executable. If I want to go through a repo, I can only get Iceweasel; if I wanted, I *could* use the Mozilla Daily PPA, but that still doesn't answer this original problem... it just provides me an unrelated fix.
> **Leppie said:**
> i installed namoroka without any problems from ppa.
And the fact the repo won't just label it "Firefox" irritates me, too... even though I know *why*. ;-)

---

### Post by Leppie on 2010-01-23
> **n0dix said:**
> I don't install yet, but i read a document [http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market](http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market). It's very pessimistic!
that blog really is hilarious.
i added the ppa to my repos, ran update manager which proposed to install the new version. all done within 5 min's... only thing is that it's a pre-release...

---

### Post by mkvnmtr on 2010-01-23
I ran into some problems after the last upgrade to the point that Firefox would not even start. After a couple of reinstalls I figured it might be that I have been using thr same .mozilla folder for two years and had changed repositories and versions several times. I deleted my .mozilla folder and reinstalled and it is great. I guess I should remember not to be so lazy.

---

### Post by moore.bryan on 2010-01-23
> **mkvnmtr said:**
> I ran into some problems after the last upgrade to the point that Firefox would not even start. After a couple of reinstalls I figured it might be that I have been using thr same .mozilla folder for two years and had changed repositories and versions several times. I deleted my .mozilla folder and reinstalled and it is great. I guess I should remember not to be so lazy.
Yeah, I tried this "trick;" unfortunately, no luck for me. :-(

---

### Post by lovinglinux on 2010-01-23
> **n0dix said:**
> Hey lovinglinux.! In your opinion why it is so difficult to install F3.6 with all the functionality. I stalled Shiretoko with not big problem.

Difficult? I don't think so. I have installed it from the PPA because I have switched to 64bit on the same day Firefox 3.6 was released. But I have tested the new Ubuntuzilla (it's a repo now) and the manual install and they all work great (if you have 32bit). Perhaps if you could explain what difficulties you are experiencing, then I could help you.

> **n0dix said:**
> I don't install yet, but i read a document [http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market](http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market). It's very pessimistic!

I don't completely disagree with that article, although it has some poor choice of words and generalizes things too much. The problem is that the average user just wants to click and install the new Firefox version as soon as it is released by Mozilla. But that is not exactly how Ubuntu works, not being a rolling release. Perhaps the author of that article should research a little bit more.

Anyway, keep in mind that the policy on Firefox updates has changed on the Mozilla side and Canonical is trying  to adapt. For instance, the way ubuntu-mozilla-daily PPA installs Firefox has changed since yesterday. You can't install firefox-3.6 side-by-side with firefox-3.5 anymore. It's an update. Additionally, Firefox does not require xulrunner anymore.

According to several posts on several threads about Firefox 3.6, we will start to see major-minor updates, instead of only security patches in the official repositories. So you can ignore that article. Even if the policy didn't change, we still have options like Ubuntuzilla repository, which is pretty easy to install and keep Firefox version in sync with Mozilla releases.

> **moore.bryan said:**
> Since this is on my Debian machine, my only option is to download from the [GetFirefox]("http://www.getfirefox.com/") website, untar the file, and then symlink the firefox executable. If I want to go through a repo, I can only get Iceweasel; if I wanted, I *could* use the Mozilla Daily PPA, but that still doesn't answer this original problem... it just provides me an unrelated fix.

And the fact the repo won't just label it "Firefox" irritates me, too... even though I know *why*. ;-)

I just asked to know how to proceed. I'm not familiar with Debian and never saw that error before, but have you tried to download it again? It could be a corruption cause by a faulty download. Have you checked the file hash numbers against those released by Mozilla?

---

### Post by Enigmapond on 2010-01-23
I hope this isn't considered a hi-jack...but I'm also having issues with FF. I had 3-4 different versions so I was deleting through synaptic and was unable to get them all out. I finally did, probably not the best thing, but I just went in and deleted all the folders in root pertaining to FF and just left my config file in my home directory. Well this still didn't do it and I still have a 3.5 version stuck..it won't install or purge...see the attached picture of the errors I'm getting.

I have since just gotten the files right from the site and threw them into /opt and then just made a link...I now have at least a working 3.6...but still unable to get rid of the errors and I won't be able to update it through the manager...

any suggestions on how to delete this mozilla-build?

---

### Post by lovinglinux on 2010-01-23
> **Enigmapond said:**
> I hope this isn't considered a hi-jack...but I'm also having issues with FF. I had 3-4 different versions so I was deleting through synaptic and was unable to get them all out. I finally did, probably not the best thing, but I just went in and deleted all the folders in root pertaining to FF and just left my config file in my home directory. Well this still didn't do it and I still have a 3.5 version stuck..it won't install or purge...see the attached picture of the errors I'm getting.

I have since just gotten the files right from the site and threw them into /opt and then just made a link...I now have at least a working 3.6...but still unable to get rid of the errors and I won't be able to update it through the manager...

any suggestions on how to delete this mozilla-build?

Your problem is with Ubuntuzilla install. I guess it's trying to revert things changed by Ubuntuzilla, but can find the necessary files, since you have deleted the folder manually.

Try to install Ubuntuzilla again, then remove it.

---

### Post by moore.bryan on 2010-01-23
> **lovinglinux said:**
> I just asked to know how to proceed. I'm not familiar with Debian and never saw that error before, but have you tried to download it again? It could be a corruption cause by a faulty download. Have you checked the file hash numbers against those released by Mozilla?
No worries; I thank you for your help! I had a small epiphany a moment ago... could my troubles be because my Debian install is on an iMac with a PPC, not 686 processor? When I went to re-download the tarball, I noticed Mozilla thinks I have an i686...

---

### Post by Enigmapond on 2010-01-23
It won't let me delete either the firefox-mozilla-build or ubuntuzilla. It keeps stopping at that same error message in both the console and synaptic....

---

### Post by lovinglinux on 2010-01-23
> **Enigmapond said:**
> It won't let me delete eother the firefox-mozilla-build or ubuntuzilla. It keeps stopping at that same error message in both the console and synaptic....

Hmmm, I will call for some help...

---

### Post by Enigmapond on 2010-01-23
LOL I called for help too and received none....also now this error is getting in the way. I just tried to install Google Chrome and it states that firefox-mozilla-build will need to be uninstalled first...but the error states that it is neither installed or uninstalled...it's somewhere in between....:confused:

---

### Post by lovinglinux on 2010-01-23
> **Enigmapond said:**
> LOL I called for help too and received none....also now this error is getting in the way. I just tried to install Google Chrome and it states that firefox-mozilla-build will need to be uninstalled first...but the error states that it is neither installed or uninstalled...it's somewhere in between....:confused:

I have seen those errors before, I just don't know the proper dpkg commands to fix that. Just give some time and people will come. Perhaps would be advisable to create your own thread.

---

### Post by lovinglinux on 2010-01-23
> **moore.bryan said:**
> No worries; I thank you for your help! I had a small epiphany a moment ago... could my troubles be because my Debian install is on an iMac with a PPC, not 686 processor? When I went to re-download the tarball, I noticed Mozilla thinks I have an i686...

I guess so, although I'm not familiar with MAC platform. Try to get the proper file from [Mozilla releases FTP directory](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/).

---

### Post by Leppie on 2010-01-23
> **Enigmapond said:**
> I hope this isn't considered a hi-jack...but I'm also having issues with FF. I had 3-4 different versions so I was deleting through synaptic and was unable to get them all out. I finally did, probably not the best thing, but I just went in and deleted all the folders in root pertaining to FF and just left my config file in my home directory. Well this still didn't do it and I still have a 3.5 version stuck..it won't install or purge...see the attached picture of the errors I'm getting.

I have since just gotten the files right from the site and threw them into /opt and then just made a link...I now have at least a working 3.6...but still unable to get rid of the errors and I won't be able to update it through the manager...

any suggestions on how to delete this mozilla-build?
try the following:
```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

---

### Post by lovinglinux on 2010-01-23
> **Leppie said:**
> try the following:
```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

@ Enigmapond

I told you someone would help soon....but I didn't call him :)

@ Leppie. 

Thanks. I was suspecting a divertion could fix it. Just didn't know how to do it safely.

---

### Post by Enigmapond on 2010-01-23
> **Leppie said:**
> try the following:
```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

Thank you so much! That got rid of that divert and I was able to uninstall that build.

Cheers!!

---

### Post by Leppie on 2010-01-23
> **Enigmapond said:**
> Thank you so much! That got rid of that divert and I was able to uninstall that build.

Cheers!!
you're welcome.
try the ppa, it really works well for me ;)

---

### Post by nanotube on 2010-01-23
hey guys
sorry i'm late to the party :)

but yea, the divert problem was likely caused by a local divert present from the old ubuntuzilla script, which conflicts with a divert that the new ubuntuzilla ppa package does.

thanks leppie for jumping in with the solution. :)

p.s. note that this conflict /is/ documented on the ubuntuzilla website, along with instructions on how to avoid it... but of course, who reads the documentation, right? :)

---

### Post by Leppie on 2010-01-23
> **nanotube said:**
> thanks leppie for jumping in with the solution. :)
no probs, glad to help :)

> **nanotube said:**
> but of course, who reads the documentation, right? :)
this seems to be a major issue nowadays... search engines seem obsolete as well...

---

### Post by d3v1150m471c on 2010-01-23
google chrome beta is wicked fast as long as you don't mind google probing your internet browsing. I use swiftfox because it's also very fast, especially when tweaked, and runs awesome security and privacy addons.

---

### Post by moore.bryan on 2010-01-24
> **lovinglinux said:**
> I guess so, although I'm not familiar with MAC platform. Try to get the proper file from [Mozilla releases FTP directory]("ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/").
Unfortunately, there are *no* releases listed for the PPC architecture, even though they must exist somewhere... I'm guessing third-party. All-in-all, nothing's been solved, but I installed Iceweasel (3.5.6) to tide me over.

Once again, though, this highlights the lack of development for the PPC architecture when it comes to Debian and its extended family of distros. Not that I blame that on anyone; just how it is since so few of us our actually using PPC iMacs. ;-)

Thanks for everyone's help, even if it didn't really answer the original question!

---

### Post by moore.bryan on 2010-01-24
UPDATE:
After some digging around and being unable to successfully build firefox for my PPC machine via source, I found PPCNUX's [article]("http://www.ppcnux.com/?q=firefox-360-community-build-for-linux-powerpc") on using Firefox 3.6 on a PPC machine, with a binary link. I downloaded, symlinked all I needed and, voila, running a Namoroka on my PPC with Debian!

---

### Post by n0dix on 2010-01-24
> **moore.bryan said:**
> UPDATE:
After some digging around and being unable to successfully build firefox for my PPC machine via source, I found PPCNUX's [article]("http://www.ppcnux.com/?q=firefox-360-community-build-for-linux-powerpc") on using Firefox 3.6 on a PPC machine, with a binary link. I downloaded, symlinked all I needed and, voila, running a Namoroka on my PPC with Debian!

Congratulations, now enjoy!!!!

---

### Post by moore.bryan on 2010-01-24
Thanks... the original issue still survives, but at least this was a nice workaround for me...

---

