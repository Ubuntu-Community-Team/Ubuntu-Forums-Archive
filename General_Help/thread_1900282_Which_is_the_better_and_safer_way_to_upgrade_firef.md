---
title: "Which is the better and safer way to upgrade firefox?"
date: 2011-12-25
forum: General Help
---

### Post by arroy_0209 on 2011-12-25
If someone installs ubuntu10.04LTS, the firefox installed is an old one (may be 3.6.26). Now if one wants to upgrade to the latest, there are two ways: either upgrade from repository using sudo command, or download directly from mozilla website. I have tried the first one but then some problem occurs with the downloaded version even after trying various methods. It may happen (as some have advised) that the version downloaded from the mozilla site will not give trouble. But perhaps in that case I will not receive the security updates related to firefox from ubuntu. Or is there any way to get security updates from this kind of download also which I am not aware of? Can anybody please clarify which method is better?

---

### Post by bodhi.zazen on 2011-12-25
You will get a variety of opinions on this, personally I download from mozilla, but others use the ppa.

You identified the advantage of the ppa, use the ppa if you find manually checking for updates to be too much hassle.

---

### Post by arroy_0209 on 2011-12-26
Thanks.   I don't know if the security (and other) updates from ubuntu are notified version-wise or not. (I think it should be version-wise). But the procedure for searching version-wise updates is not known to me. Can anybody please explain this to me?

---

### Post by mc4man on 2011-12-26
If you mean this ppa, then I think it should be fine, (use it here),  and you can report bugs on.
(crashes upstream, other usage bugs with apport

[https://launchpad.net/~mozillateam/+archive/firefox-next](https://launchpad.net/~mozillateam/+archive/firefox-next)

downloaded from mozilla will likely be 'newer' versions but the ppa updates regularly - beta channel

> but then some problem occurs with the downloaded version even after trying various methods
I haven't seen any, you could be more specific

---

### Post by arroy_0209 on 2011-12-26
One problem I have right now is that after upgrading to Firefox 9.0 (with no-script, adblockplus, and apparmor in enforced mode), if I try to save some displayed page with ctrl+S, a new window appears but here if I try to create a new folder to save, the blank-new-folder comes and disappears very fast from the list of folders. Only the default "Download" folder allows me to create a new folder inside. I am not allowed to create new folder inside home. I have tried various methods, like creating new profile for Firefox etc. but none helped. This was not the case with firefox 3.6.26 (or so) earlier I had used.

---

### Post by dcstar on 2011-12-27
> **arroy_0209 said:**
> One problem I have right now is that after upgrading to Firefox 9.0 (with no-script, adblockplus, and apparmor in enforced mode), if I try to save some displayed page with ctrl+S, a new window appears but here if I try to create a new folder to save, the blank-new-folder comes and disappears very fast from the list of folders. Only the default "Download" folder allows me to create a new folder inside. I am not allowed to create new folder inside home. I have tried various methods, like creating new profile for Firefox etc. but none helped. This was not the case with firefox 3.6.26 (or so) earlier I had used.

Works perfectly for me with Firefox 9.0.1 on my 10.04 system from this PPA:

[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

---

### Post by lovinglinux on 2011-12-27
The better way is to get from the mozillateam ppa, because you don't need to update manually every new release, it has Unity integration and it is distributed by the same people responsible for Firefox on Ubuntu. 

That being said, I also use builds downloaded from Mozilla. However, I am using gnome-shell right now. If you use Unity, you don't get global menu integration.

> **arroy_0209 said:**
> One problem I have right now is that after upgrading to Firefox 9.0 (with no-script, adblockplus, and apparmor in enforced mode), if I try to save some displayed page with ctrl+S, a new window appears but here if I try to create a new folder to save, the blank-new-folder comes and disappears very fast from the list of folders. Only the default "Download" folder allows me to create a new folder inside. I am not allowed to create new folder inside home. I have tried various methods, like creating new profile for Firefox etc. but none helped. This was not the case with firefox 3.6.26 (or so) earlier I had used.

As far as I remember, you are the only person to report such issue. Have you tried to use AppArmor on complain mode, as I suggested? If it solves the problem, then you need to create a rule for AppArmor, to allow Firefox to create and save files/folder in that location. Unfortunately, I can't help you with such rules, because I don't use AppArmor.

> **arroy_0209 said:**
> Thanks.   I don't know if the security (and other) updates from ubuntu are notified version-wise or not. (I think it should be version-wise). But the procedure for searching version-wise updates is not known to me. Can anybody please explain this to me?

If you set the Update Manager to only notify, you will be warned about Firefox version updates coming from the repositories or any third-party ppa, like the suggested and recommended *firefox-stable*. Then, you will be able to verify the version and changelog and decide if you want to update or not.

If you want to use a Firefox downloaded from Mozilla, just subscribe to [Firefox 9 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247). I post on that thread whenever there is a new version of Firefox available, so you can download it and install it.

---

### Post by Zill on 2011-12-27
> **arroy_0209 said:**
> If someone installs ubuntu10.04LTS, the firefox installed is an old one (may be 3.6.26). Now if one wants to upgrade to the latest...
I have to ask *why* you want to upgrade to the "latest"?  The current version of Firefox for Ubuntu 10.04 is 3.6.24.  AIUI, this version is still "relatively" secure and suitable for home banking etc. (certainly when compared to the MS competition IMHO!)

So, unless you consider you are particularly at risk of attack then I doubt you would gain much by "upgrading" to a newer, possibly more buggy, browser.

To answer the question posed in your title, I suggest the best and safest way to upgrade Firefox is to wait a while for the dust to settle and then install the next Ubuntu LTS, 12.04 - Precise Pangolin, scheduled for release in April 2012.  This will come with the (almost!) latest package of goodies, including a later Firefox.

---

### Post by lovinglinux on 2011-12-30
> **Zill said:**
> The current version of Firefox for Ubuntu 10.04 is 3.6.24.  AIUI, this version is still "relatively" secure and suitable for home banking etc. (certainly when compared to the MS competition IMHO!)

Firefox 3.6.x is secure, since it still is a supported version.

> **Zill said:**
> So, unless you consider you are particularly at risk of attack then I doubt you would gain much by "upgrading" to a newer, possibly more buggy, browser.

I disagree. Firefox 9 has is way much better than Firefox 3.6.x in terms of performance and has tons of new features. This doesn't mean it is inherently more buggy, because those features have been added since Firefox 4, which was released 9 months ago.

---

### Post by Zill on 2011-12-30
> **lovinglinux said:**
> ...I disagree. Firefox 9 has is way much better than Firefox 3.6.x in terms of performance and has tons of new features...
Hold on, we are talking about a browser for looking at websites!!!

I haven't yet found a website that my Firefox 3.6.24 can't handle and I don't feel particularly deprived by not having "tons of new features"!

As far as "performance" is concerned, my aged brain cannot really appreciate a difference in response time measured in microseconds. ;-)

---

### Post by lovinglinux on 2011-12-30
> **Zill said:**
> Hold on, we are talking about a browser for looking at websites!!!

If your job requires to look at websites all day, then you will appreciate any performance improvements and any new feature that makes your job easier.

Besides, you can do more than just browsing web sites with Firefox. There are tons of extensions that add extra functionality, like reading mail, posting on Twitter, getting all sorts of data without entering web sites, viewing stuff in 3D and more. Sometimes these extra functionality are deeply impacted by the browser performance.

> **Zill said:**
> I haven't yet found a website that my Firefox 3.6.24 can't handle and I don't feel particularly deprived by not having "tons of new features"!

Because you can browse all the sites you like, doesn't mean other people will have the same experience. It depends on many factors. I have helped many users that had issues solved by upgrading to the latest version.

> **Zill said:**
> As far as "performance" is concerned, my aged brain cannot really appreciate a difference in response time measured in microseconds. ;-)

The performance I am talking about can actually delay browser response in a few seconds or even freeze the browser completely.

---

### Post by Zill on 2011-12-30
lovinglinux:  Fair comment.  And for those users who really do *need* these improvements I would say "go for it"!

However, I do maintain that many users insist on getting the "latest and greatest" without having any reason to do so.

In some cases this is not a problem.  Unfortunately, some users do install non-standard applications for their particular distribution and then run into problems relating to updating etc.

So, my advice is always to ask do I really *need* this "upgrade" and, unless there is a solid reason for it, not to proceed.

---

### Post by lovinglinux on 2011-12-30
> **Zill said:**
> lovinglinux:  Fair comment.  And for those users who really do *need* these improvements I would say "go for it"!

However, I do maintain that many users insist on getting the "latest and greatest" without having any reason to do so.

In some cases this is not a problem.  Unfortunately, some users do install non-standard applications for their particular distribution and then run into problems relating to updating etc.

So, my advice is always to ask do I really *need* this "upgrade" and, unless there is a solid reason for it, not to proceed.

I agree with you. If you are looking for stability, stick with what is distributed from the official repos.

That being said, Firefox 9 is far superior than 3.6 and the overall javascript performance alone is a good reason to upgrade. You will see the difference when Mozilla stops providing support for Firefox 3.6 and the Ubuntu developers push the latest version to all repositories.

---

