---
title: "WTF is Shiretoko??  Where is Firefox?"
date: 2009-08-09
forum: General Help
---

### Post by kilgore9 on 2009-08-09
Just did a software update, it said it was a firefox update.  Now I have "Shiretoko" instead of firefox, and all of my plugins are disabled because they are not compatible.  What happened to firefox?  WTF is Shiretoko and how to I get my plugins back??
THANKS :)

---

### Post by Nburnes on 2009-08-09
Shiretoko is the "codename" for Firefox 3.5.

---

### Post by kilgore9 on 2009-08-09
thanks for the quick reply...!  But why does firefox need a codename?  Why are all of my plugins suddenly incompatible?  I don't understand!

---

### Post by jocko on 2009-08-09
> **kilgore9 said:**
> thanks for the quick reply...!  But why does firefox need a codename?  Why are all of my plugins suddenly incompatible?  I don't understand!
Are you sure you don't still have firefox 3.0? The reason firefox 3.5 is not called firefox in jaunty, is that it is not meant to replace firefox 3.0, it's meant to be an optional install alongside firefox 3.0 for those that are not patient enough to wait until the next ubuntu release. You must have chosen to install firefox 3.5 yourself, as there is no update that will do it, and if you don't have firefox 3.0 you must have removed it yourself. Just reinstall it.
The plugins are not compatible with firefox 3.5 because they are made to work with firefox 3.0. You'll have to find newer versions of your plugins if you want to keep shiretoko.

---

### Post by chintan.p on 2009-08-09
First of all, it's great to know that 3.5 is available (officially) on ubuntu. I am too lazy to use anything besides apt.

And is it all the plugins? When I upgraded to 3.5 on Windows, I just lost prism and one more I can't remember.

---

### Post by kilgore9 on 2009-08-09
Aha, I see.  Actually, Ubuntu automatically tells me when updates are available (security updates, kernel updates, etc.).  Firefox updates come through that automatic update reminder as well, and I usually just click on update, which I did today as well, and suddenly had Shiretoko instead of firefox.  
But thanks for the tip, good to know I can just move back to 3.0.  But maybe shiretoko isn't bad, I'll have to try it a bit more...

---

### Post by zkriesse on 2009-08-09
> **kilgore9 said:**
> Just did a software update, it said it was a firefox update.  Now I have "Shiretoko" instead of firefox, and all of my plugins are disabled because they are not compatible.  What happened to firefox?  WTF is Shiretoko and how to I get my plugins back??
THANKS :)
Firefox 3.5 is not yet ready for Ubuntu Jaunty....the reason why your plugins don't work is amply stated by jocko in his post. If you want to keep your present add-ons you need to re-install Firefox 3.0

---

### Post by speedwell68 on 2009-08-09
The simplest way to get proper Firefox 3.5 instead of Shiretoko is to keep Firefox 3.0.xx installed and download Firefox 3.5.x from Mozilla's website.  Once you have it downloaded unpack the tar-ball into a folder called 'firefox 3.5' below your /home/.mozilla folder.  It will automatically pick up your Firefox 3.0.xx profile and load any addons that are still compatible.  Also, at first start Firefox 3.5 will prompt you to make it the default browser.  You will have to manually create a menu and desktop launcher.

When it comes to updating itself Firefox will update directly from Mozilla, rather than from your installed repositories, in much the same way that Firefox would do under Windows.

As for incompatible addons, they will either update themselves in the fullness of time or you will have to find alternatives yourself.

---

### Post by lovinglinux on 2009-08-09
> **kilgore9 said:**
> Aha, I see.  Actually, Ubuntu automatically tells me when updates are available (security updates, kernel updates, etc.).  Firefox updates come through that automatic update reminder as well, and I usually just click on update, which I did today as well, and suddenly had Shiretoko instead of firefox.  

That's not possible. Firefox 3.0 won't be updated to 3.5 in Jaunty, so you must have intentionally installed **firefox-3.5** package from Synaptic, not from an update alert. Besides, as already stated on this thread. Shiretoko is installed side-by-side with FF 3.0 and it's only accessed through "Applications >> Internet >> Shiretoko Web Browser. So, unless you edited stuff manually, you should see Firefox 3.0.13 when you click the Firefox launcher from the menu.

> **kilgore9 said:**
> But maybe shiretoko isn't bad, I'll have to try it a bit more...

Shiretoko is Firefox. The exact same program. The difference is that Shiretoko is Firefox 3.5 version, which comes with a lot of improvements over 3.0.

The thing with your extensions has nothing to do with the Shiretoko branding, but with the fact that extensions are version dependent. Usually when a new major version of Firefox is released, several extensions stop to work because they haven't been tested/modified by their authors to work with the new Firefox. Several extensions actually doesn't need any code change, just an adjustment in the installation file to tell Firefox it works with the current version. Most of the time, new extensions versions are released before Firefox hits the shelves or a couple of days after the official release. Unfortunately, some extensions do not have very active developers and sometimes they are not updated at all. If this is the case, you can edit the extension yourself or simply disable the version checking. But first you should try to update the extensions, through the add-ons preferences. There is a button there to "Find updates".

Only one between forty three extensions I use isn't updated yet. Nevertheless, it still works with the version checking disabled. You can learn how to do this in my tutorial [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). It also explains the 4 most common methods of installation of FF 3.5 with comparisons.

---

### Post by caish5 on 2009-08-09
I previoulsy had shiretoko installed as well as 3.0.
But the OP is correct, todays updates removed 3.0 and nade shiretoko default.
Which is annoying because of the horrible things the dust theme does on the adress bar drop down!

---

### Post by kilgore9 on 2009-08-09
> **lovinglinux said:**
> That's not possible. Firefox 3.0 won't be updated to 3.5 in Jaunty, so you must have intentionally installed **firefox-3.5** package from Synaptic, not from an update alert. Besides, as already stated on this thread. Shiretoko is installed side-by-side with FF 3.0 and it's only accessed through "Applications >> Internet >> Shiretoko Web Browser. So, unless you edited stuff manually, you should see Firefox 3.0.13 when you click the Firefox launcher from the menu.




No really!  I promise, it came through the auto-update!  as caish5 says, its being updated as the default....

---

### Post by lovinglinux on 2009-08-09
> **kilgore9 said:**
> No really!  I promise, it came through the auto-update!  as caish5 says, its being updated as the default....

I just have updated and there are no Firefox related updates. Besides, Firefox 3.0.13 is still installed along with my compiled version of 3.5.

Maybe something got messed up and the launcher is pointing to **firefox-3.5** instead of **firefox-3.0**. Try running Firefox with the command below and check the version in the "About Mozilla Firefox" in the Help menu.

```
firefox-3.0
```

---

### Post by kilgore9 on 2009-08-09
well running that opens up shiretoko....
A friend helped me with some links of sources in apt-get.  Maybe I'm signed up to get updates for pre-releases.....  its version 3.5.3pre

---

### Post by lovinglinux on 2009-08-09
> **kilgore9 said:**
> well running that opens up shiretoko....
A friend helped me with some links of sources in apt-get.  Maybe I'm signed up to get updates for pre-releases.....  its version 3.5.3pre

I told you it wouldn't update by itself ;)

You probably have the *proposed*, *backports* or *ubuntu-mozilla-daily* repository enabled and it updated Firefox 3.0. But I still think this is odd, since it should update the firefox-3.5 package, not firefox-3.0.

Go to "System >> Administration >> Software Sources" and disable the proposed, backports, ubuntu-mozilla-daily and ubuntu-mozilla-security if you have them. Then go to  "System >> Administration >> Synpatic Package Manager", search for firefox and mark it for re-installation. Then click apply. This should fix the problem.

---

### Post by golusweet on 2009-08-09
You can install latest firefox version using ubuntuzilla.

It's a script that lets you download latest version of Firefox.

It also gives notifications whenver Firefox latest version hits.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

:P

---

### Post by ratcheer on 2009-08-09
> **speedwell68 said:**
> The simplest way to get proper Firefox 3.5 instead of Shiretoko is to keep Firefox 3.0.xx installed and download Firefox 3.5.x from Mozilla's website.  Once you have it downloaded unpack the tar-ball into a folder called 'firefox 3.5' below your /home/.mozilla folder.  It will automatically pick up your Firefox 3.0.xx profile and load any addons that are still compatible.  Also, at first start Firefox 3.5 will prompt you to make it the default browser.  You will have to manually create a menu and desktop launcher.

When it comes to updating itself Firefox will update directly from Mozilla, rather than from your installed repositories, in much the same way that Firefox would do under Windows.



Question: I have done exactly as you say above, just by luck. I am using 3.5.2. I almost uninstalled 3.0 but I didn't because I saw that it was going to uninstall some libraries and I didn't know if that would mess stuff up, so I kept 3.0. Anyway, I have been ignoring the 3.0 updates because I don't use 3.0, anymore.

Getting to the question, does this mean that I should install the 3.0 updates that keep showing up in Update Manager? Will they help in my use of 3.5?

Thanks,
Tim

---

### Post by lovinglinux on 2009-08-09
> **ratcheer said:**
> Question: I have done exactly as you say above, just by luck. I am using 3.5.2. I almost uninstalled 3.0 but I didn't because I saw that it was going to uninstall some libraries and I didn't know if that would mess stuff up, so I kept 3.0. Anyway, I have been ignoring the 3.0 updates because I don't use 3.0, anymore.

Getting to the question, does this mean that I should install the 3.0 updates that keep showing up in Update Manager? Will they help in my use of 3.5?

Thanks,
Tim

They won't affect 3.5, but they won't hurt either. So why not?

---

### Post by ratcheer on 2009-08-09
Ok, thanks. At least it will stop prompting me to do the updates, every day.

Tim

---

### Post by JimBuntu on 2009-08-09
I had FF 3.0 and 3.5.2. Today there was an update that turned my firefox 3.5.2 into Shiretoko 3.5.3pre it also turned my FF icon into the Shiretoko icon. Also, it says on start-up that the bookmarks and history will not be used because there is another program using them. Been trying to log into FF 3.5.2 manually to no avail. It WAS an automatic update. How do I get my icon back and use FF 3.5.2?

---

### Post by JimBuntu on 2009-08-11
bump

---

### Post by lovinglinux on 2009-08-11
> **JimBuntu said:**
> bump

PM replied.

---

### Post by gibbylinks on 2009-08-11
> **JimBuntu said:**
> I had FF 3.0 and 3.5.2. Today there was an update that turned my firefox 3.5.2 into Shiretoko 3.5.3pre it also turned my FF icon into the Shiretoko icon. Also, it says on start-up that the bookmarks and history will not be used because there is another program using them. Been trying to log into FF 3.5.2 manually to no avail. It WAS an automatic update. How do I get my icon back and use FF 3.5.2?

I have the same query

Thanks

---

### Post by lovinglinux on 2009-08-11
> **gibbylinks said:**
> I have the same query

Thanks

About the update of Shiretoko 3.5 to Shiretoko 3.5.3pre is probably due to the fact that you have added **ubuntu-mozilla-daily**, **ubuntu-mozilla-security** or another firefox PPA repository to your sources list. Check "System >> Administration >> Software Sources" and disable any extra firefox/mozilla related repository to avoid these updates.

Then update your sources:

```
sudo apt-get update
```

It would be good if you could tell me which method you used to install 3.5 in the first place. If you installed Firefox 3.5 from the repositories, then simply follow the instructions below:

Remove firefox-3.5

```
sudo apt-get remove firefox-3.5
```

Now go to "System >>> Administration >>> Synaptic Package Manager", then search for firefox, then select the packages **firefox** and **[B]firefox-3.0**[/B], mark them for re-installation and click apply.

Then install Firefox 3.5 again:

```
sudo apt-get install firefox-3.5
```

I think this should fix the problem.

---

### Post by ralema56 on 2009-08-15
I thought Shiretoko was the name for the 64bit version, and the reason the plugings were not working because the plugins were made for 32bit.

---

### Post by zaghadka on 2009-09-16
Okay, some comments on this one, to whom it may concern. I had a very frustrating time with this package.

The Firefox-3.5 package appears in Jaunty Universe. It is a MOTU maintained offering, on the official repo, not some third party repo. Novice users can get at this package with a check box, and a mild sense of daring.

I have a few problems with the way this package is being maintained, and I'm willing to help the maintainer fix it if s/he doesn't have the time. I have absolutely no experience with that, but I learn fast. For the time being, I am offering constructive criticism before mailing the maintainer.

I'm just going to be blunt:

1. There is absolutely no mention in the package description that the package will install a program called "Shiretoko," and the item is not branded in the official Mozilla Firefox logo, so it's pretty hard to find. The user installs Firefox-3.5, and doesn't get anything that remotely looks like Firefox, other than a symlink named "firefox-3.5." Basically, you need to go into a terminal just to find the thing. The more likely outcome is people will assume the package is broken.

2. If you install "Firefox-3.5" concurrent with Firefox 3.0, as has been suggested was the intent, you can click your Firefox icons until the cows come home after installation, and never realize that it's launching the wrong program. Since it appears as Shiretoko, and not something recognizable like Shiretoko Firefox, the only way a user is going to realize they're still using Firefox 3.0 is by looking in the about box.

3. If you do what I did, and you *uninstall* Firefox 3.0 and then install Firefox 3.5, you can click on your icons, type your usual console "firefox" and "mozilla-firefox" and get nothing. Only trying to tab complete the line will reveal the symlink to "firefox-3.5."

4. Why exactly did the maintainer decide to go back to Dapper branding for the icons and the "about?" I extracted the Firefox-3.0 branding jars and replaced it all by hand in about five minutes. It's not hard to include the Firefox 3.0 browser-branding.jar and .manifest and include actual Firefox icons. Is there some kind of legal problem here? Why not make the thing look like Firefox? Why call the package "Firefox" if it's going to behave like IceWeasel?

As a quick fix, I humbly suggest that the thing call itself "Shiretoko Firefox" in all the menu branding, because most users are just going to expect an icon that works, and unless the word "Firefox" is in the branding, or they see the logo, they'll be hard pressed to find it. The maintainer has stripped all of the branding from the browser except for the **package name**. That's really confusing.

Mozilla carries a lot of the burden of the reputation of FOSS as commercially viable, easy to use, and nice to look at. If there's some kind of issue with using the branding, it might make more sense to just offer Iceweasel 3.5 in the repo until Canonical gets around to releasing the next distro. Calling this package "Firefox" is not doing Mozilla justice.

Why the involved response if I got everything working? Well, I just spent an *hour* trying to figure out why the "Firefox-3.5" package didn't install Firefox, and I'm pretty well versed in computers. Repos are supposed to do away with this sort of confusion, not *create* it. This is in the Universe  and 3.5 is a very desirable upgrade for many users of varying levels of sophistication. I'm sure many folks just shrugged and blamed Mozilla or Canonical for a broken package.

At a bare minimum, the package description should *mention* the Shiretoko name, but at that point, why not use Iceweasel?

This is the useragent I'm now sending:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.2) Gecko/20090803 Ubuntu/9.04 (jaunty) Shiretoko/3.5.2

This is essentially the same as IceWeasel, guys. Why go to all the trouble, and confuse end users in the process?

Feel free to contact me via email if I can be of any assistance.

---

