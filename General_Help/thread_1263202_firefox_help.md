---
title: "firefox help"
date: 2009-09-10
forum: General Help
---

### Post by -_- Joseph -_- on 2009-09-10
Hey its me Joseph and im pretty new to ubuntu and i am having a little trouble with firefox.

Im trying to update my version to 3.5. so i asked my dad (being using ubuntu for over a year(maybe 2))
he said it was already installed (and updated) its just when i open up firefox its not updated 
what do i do.

   plzz respond 

  p.s it for ubuntu 9.0.4 

                                                                    ,Joseph

and also im glad i now got forum i can trust where i get the answers quick and easy

---

### Post by chriskin on 2009-09-10
you can always install firefox-3.5 from synaptic package manager if it's not updated. 

it might be named shiretoko but it's the exact same as firefox 3.5

---

### Post by bodhi.zazen on 2009-09-10
Easiest way to update, IMO, is to download the binary from mozilla :

[http://download.mozilla.org/?product=firefox-3.5.3&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-3.5.3&os=linux&lang=en-US)

[http://www.mozilla.com/en-US/products/download.html?product=firefox-3.5.3&os=linux&lang=en-US](http://www.mozilla.com/en-US/products/download.html?product=firefox-3.5.3&os=linux&lang=en-US)

Extract the archive and run it.

---

### Post by sahabcse on 2009-09-10
Hi

For Installing firefox 3.5 please follow below url

[http://ubuntulinux.co.in/Firefox-3-5-in-Ubuntu-9-04-Jaunty-Jackalope.php](http://ubuntulinux.co.in/Firefox-3-5-in-Ubuntu-9-04-Jaunty-Jackalope.php)

---

### Post by herbertportillo on 2009-09-10
Mozilla came out with 3.0.14, and today Ubuntu upgraded my Firefox. Sweet. But, I use Swiftweasel 3.5.2 which is optimized for my AMD64 computer. But Mozilla also came out with 3.5.3 today. I went to firefox.com and downloaded the archive, firefox-3.5.3.tar.bz2, and extracted it to my desktop.

I then created a launcher to the 'firefox' shell script in the 'firefox' directory which was created when I extracted the archive. I double-clicked on the launcher, and Firefox 3.5.3 opened. Except there was one problem. The program doesn't connect to the internet, which is the most important part of the browser, haha (see Screenshot.png). Firefox 3.0.14 works fine, though. Does anyone know why? Any help appreciated. Thanks.

---

### Post by sahabcse on 2009-09-10
check your internet connection, are you able to ping outside the network, check with other browser also

---

### Post by Earl_Maroon on 2009-09-10
I beg to differ with all of the above responses. I suggest Ubuntuzilla.py.


Uninstall any versions of Firefox other than firefox-3.0 in the repos, making sure that is installed.

Then install and run ubuntuzilla.py, which you can get here:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

This installs Mozilla's latest release of Ubuntu flawlessly.

---

### Post by herbertportillo on 2009-09-10
My internet connection is fine. Right now I'm using Swiftweasel to browse, and when I open Firefox 3.0.14 it works fine, as well. It's only when I open Firefox 3.5.3 that I can't connect to the internet. The program opens, but it doesn't connect to the internet. The proxy settings for all three are exactly the same (no proxy settings).

---

### Post by herbertportillo on 2009-09-10
Earlier today I tried installing Firefox 3.5.3 with Ubuntuzilla, as well. Exact same thing happened. Firefox 3.5.3 would open, but no internet connection. Swiftweasel, perfectly fine.

---

### Post by lovinglinux on 2009-09-10
> **-_- Joseph -_- said:**
> Hey its me Joseph and im pretty new to ubuntu and i am having a little trouble with firefox.

Im trying to update my version to 3.5. so i asked my dad (being using ubuntu for over a year(maybe 2))
he said it was already installed its just when i open up firefox its not updated 
what do i do.

Currently, Firefox 3.5 is only available as a side-by-side installation. So you won't update your current version, but install another one. Firefox will be 3.5 by default on the next Ubuntu release.

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

> **herbertportillo said:**
> Earlier today I tried installing Firefox 3.5.3 with Ubuntuzilla, as well. Exact same thing happened. Firefox 3.5.3 would open, but no internet connection. Swiftweasel, perfectly fine.

See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [url=http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT
005]**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**[/url].

---

### Post by hal10000 on 2009-09-10
> My internet connection is fine. Right now I'm using Swiftweasel to browse, and when I open Firefox 3.0.14 it works fine, as well. It's only when I open Firefox 3.5.3 that I can't connect to the internet. The program opens, but it doesn't connect to the internet. The proxy settings for all three are exactly the same (no proxy settings).

Perhaps it's just working in "Offline Mode" (see File--->Work Online/Offline)

---

### Post by nanotube on 2009-09-10
> **herbertportillo said:**
> Earlier today I tried installing Firefox 3.5.3 with Ubuntuzilla, as well. Exact same thing happened. Firefox 3.5.3 would open, but no internet connection. Swiftweasel, perfectly fine.

this is a known problem with 32bit firefox on 64bit ubuntu that seems to happen with some regularity. there's a fix for it described on the ubuntuzilla faq: 

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_I_installed_the_latest_Firefox.2C_but_cannot_connect_to_any_websites._Any_suggestions.3F](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_I_installed_the_latest_Firefox.2C_but_cannot_connect_to_any_websites._Any_suggestions.3F)

in brief: Set the network.dns.disableIPv6 setting to true in about:config

---

### Post by herbertportillo on 2009-09-10
> **hal10000 said:**
> Perhaps it's just working in "Offline Mode" (see File--->Work Online/Offline)

I wish the solution were that simple, haha.

Oh well. Screw it. I guess I'll just wait for the cute and cuddly Karmic Koala.

---

### Post by 16sinker on 2009-09-11
I got my upgrade to 3.5 here:
[http://www.mozilla.com/en-US/product...nux&lang=en-US](http://www.mozilla.com/en-US/product...nux&lang=en-US), my question is-do 3.0 and 3.5 have to run side by side or can I uninstall 3.0?

---

### Post by bodhi.zazen on 2009-09-11
> **16sinker said:**
> I got my upgrade to 3.5 here:
[http://www.mozilla.com/en-US/product...nux&lang=en-US](http://www.mozilla.com/en-US/product...nux&lang=en-US), my question is-do 3.0 and 3.5 have to run side by side or can I uninstall 3.0?

You may un-install 3.0.x

---

### Post by hal10000 on 2009-09-11
I have 3.5.2 installed from the repository (Shiretoko) and it runs perfectly.

@16sinker:
> my question is-do 3.0 and 3.5 have to run side by side or can I uninstall 3.0
You can remove 3.0, but if firefox 3.0 is your standard brower by now, then you should run
 [COLOR="Red"]sudo update-alternatives --config x-www-browser[/COLOR] and choose firefox 3.5

---

### Post by 16sinker on 2009-09-11
> **hal10000 said:**
> I have 3.5.2 installed from the repository (Shiretoko) and it runs perfectly.

@16sinker:

You can remove 3.0, but if firefox 3.0 is your standard brower by now, then you should run
 [COLOR="Red"]sudo update-alternatives --config x-www-browser[/COLOR] and choose firefox 3.5

Did as you suggested. Everything went great. My only question now is: Will Shiretoko be updated automatically by Mozilla or do I go elsewhere for updates?

---

### Post by sharath0007 on 2009-09-11
I dont know if this will help ya, but i had the same problem. Even after updating,  from firefox 3.2 to .5 at the mozilla site, when i checked the "about mozilla firefox", it still said 3.2
after that, i downloaded a tarball of the 3.5 and then made a launcher for the same. So i had two fire foxes now! One that was bundled with ubuntu, and the other i'd just set up.

But after that, when i checked the version on both the browsers, it had changed to 3.5!!!
The settings i apply to the newer one(themes addons etc) doesn't apply to the bundled version!

---

### Post by 16sinker on 2009-09-11
Actually, I'm not having a problem, as everything with the upgrade went smoothly and Firefox 3.5 is noticably quicker on this computer. My question should have been: Will Ubuntu notify me of updates to Shiretoko?

---

### Post by hal10000 on 2009-09-11
@16sinker:
> Will Ubuntu notify me of updates to Shiretoko
yes, if you installed it from the repsitory.

---

### Post by 16sinker on 2009-09-11
> **hal10000 said:**
> @16sinker:

yes, if you installed it from the repsitory.

Synaptic shows Firefox 3.5 and Firefox 3.5 branding as installed. The pkgs.FF 3.5 dbg, FF 3.5 dev and FF 3.5 gnome support were not installed. Does this mean they were installed from the repository? And should the other pkgs., relative FF 3.5 that I just mentioned, be installed?

---

### Post by hal10000 on 2009-09-11
> Synaptic shows Firefox 3.5 and Firefox 3.5 branding as installed. The pkgs.FF 3.5 dbg, FF 3.5 dev and FF 3.5 gnome support were not installed. Does this mean they were installed from the repository? And should the other pkgs., relative FF 3.5 that I just mentioned, be installed?

If you installed it with synaptic or another package manager or via [COLOR="Red"]apt-get install[/COLOR] then they were installed from the repositories.

Packages ending with dev are usually development packages, you don't need them unless you are a programmer and like to change the firefox source code.

-dbg packages are usually for debugging purposes and also mostly needed by programmers.

you may install firefox-3.5-gnome-support if you are using gnome and like to integrate firefox into your gnome environment.

---

### Post by daisyashe on 2009-09-11
You need to check the addons.
Whenever there is update a message appears on your screen you need to update everytime when ot appears.
Check the firefox addons for linux.

---

### Post by herbertportillo on 2009-09-11
> **nanotube said:**
> this is a known problem with 32bit firefox on 64bit ubuntu that seems to happen with some regularity. there's a fix for it described on the ubuntuzilla faq: 

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_I_installed_the_latest_Firefox.2C_but_cannot_connect_to_any_websites._Any_suggestions.3F](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_I_installed_the_latest_Firefox.2C_but_cannot_connect_to_any_websites._Any_suggestions.3F)

in brief: Set the network.dns.disableIPv6 setting to true in about:config


It works! Thank you!

---

### Post by 16sinker on 2009-09-11
> **hal10000 said:**
> If you installed it with synaptic or another package manager or via [COLOR="Red"]apt-get install[/COLOR] then they were installed from the repositories.

Packages ending with dev are usually development packages, you don't need them unless you are a programmer and like to change the firefox source code.

-dbg packages are usually for debugging purposes and also mostly needed by programmers.

you may install firefox-3.5-gnome-support if you are using gnome and like to integrate firefox into your gnome environment.
Thanks Hal. Just got notification of an update for FF 3.5, so I'm good to go.

---

### Post by nanotube on 2009-09-11
> **herbertportillo said:**
> It works! Thank you!

you're quite welcome :)

---

### Post by billstei on 2009-09-12
I installed firefox-3.5 and removed firefox 3.0, and everything seems to be working, however in menu Tools->Add-ons->Languages there is Firefox (en-GB) 3.0.7, and XULRunner (en-GB) 1.9.0.8, both listed as "Not compatible with Shiretoko 3.5.3", and clicking the Uninstall button does not remove/replace/update them.  In Synaptic I see that both xulrunner-1.9 (1.9.0.14) and xulrunner-1.9.1 (1.9.1.3) are both installed.  Attempting to uninstall xulrunner-1.9 would remove to many other programs that depend on it, so that is not a good option at this point.  Is there anything that can be done to clean this up?

Edit: I see now that the package update needed is language-pack-en, which has the correct language versions in Karmic but not Jaunty.  So the Jaunty Firefox 3.5 package should depend on these newer language packages in order to install correctly.  I did not install the Karmic language-pack-en, as it looked a little too dependency hellish just to get rid of a couple of exclamation points.

---

