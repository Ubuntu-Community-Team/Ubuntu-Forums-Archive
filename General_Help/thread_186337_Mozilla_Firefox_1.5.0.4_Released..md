---
title: "Mozilla Firefox 1.5.0.4 Released."
date: 2006-06-01
forum: General Help
---

### Post by Rackerz on 2006-06-01
Will this be avaliable for Dapper? Will it need to be backported. I'm just asking because I don't know the procedures for it.

EDIT: Here is how to update your Firefox to 1.5.0.4. Credit goes to aysiu.


Download this script
```
http://pykeylogger.sourceforge.net/installnewfirefox.sh
```

Open up the Terminal and enter these commands;
> ]cd Desktop
chmod +x installnewfirefox.sh
./installnewfirefox.sh

It will install the latest version of Firefox and will ask you your language preference.

---

### Post by ash211 on 2006-06-01
It's not in the repositories right now, since it just came out!

To install it, you will need to download the file from the Mozilla site.  Follow the instructions at [https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29) but download 1.5.0.4 instead of the 1.5.0.3 it currently references!

---

### Post by NeoChaosX on 2006-06-01
Considering Dapper's now out, I imagine the Ubuntu devs will simply backport the security fixes from the official Mozilla version, rather than repackage the whole browser after release.

---

### Post by bluevoodoo1 on 2006-06-01
I got it by altering aysiu's 1.5.0.3 script to get 1.5.0.4. Easy as pie.

---

### Post by 23meg on 2006-06-01
[QUOTE=Rackerz]I'm just asking because I don't know the procedures for it.[/QUOTE]Once a development release is past the predefined upstream version freeze date, all versions are fixed no new software versions are allowed. This means by principle Dapper hasn't had new software added to it since January, not even its release date, and it certainly won't after its release date. Stable releases only get security updates once they're out; new software versions can get backported if there is enough demand, and if it's technically feasible. Now that there are security fixes to Firefox in this new version, they'll be made available as security updates to the current version that ships with Dapper by the Ubuntu devs.

---

### Post by BoyOfDestiny on 2006-06-01
[QUOTE=23meg]Once a development release is past the predefined upstream version freeze date, all versions are fixed no new software versions are allowed. This means by principle Dapper hasn't had new software added to it since January, not even its release date, and it certainly won't after its release date. Stable releases only get security updates once they're out; new software versions can get backported if there is enough demand, and if it's technically feasible. Now that there are security fixes to Firefox in this new version, they'll be made available as security updates to the current version that ships with Dapper by the Ubuntu devs.[/QUOTE]

Of course, nothing prevents you from installing software manually. Whether it be from a deb (which now has a double click installer), source, unnofficial repo, etc.

---

### Post by FredB on 2006-06-02
[QUOTE=NeoChaosX]Considering Dapper's now out, I imagine the Ubuntu devs will simply backport the security fixes from the official Mozilla version, rather than repackage the whole browser after release.[/QUOTE]

I think they could make a 1.5.0.4 version of firefox in the next few days. Maybe before a week or so. :mrgreen:

---

### Post by henriquemaia on 2006-06-02
Thanks for the info. I have just updated it.

---

### Post by Rackerz on 2006-06-02
Yeah I used aysiu's script to upgrade to 1.5.0.4. If anyone is intrested in updating here is how you do it.

Download this script
```
http://pykeylogger.sourceforge.net/installnewfirefox.sh
```

Open up the Terminal and enter these commands;
> cd Desktop
chmod +x installnewfirefox.sh
./installnewfirefox.sh

It will install the latest version of Firefox and will ask you your language preference.

---

### Post by Zdravko on 2006-06-02
>  Of course, nothing prevents you from installing software manually.

Of course, it is not recommended to do so. When Ubuntu doesn't provide you with some functionality - there must be a reason for this.

---

### Post by FredB on 2006-06-02
[QUOTE=henriquemaia]Thanks for the info. I have just updated it.[/QUOTE]

Well, I can see that on Breezy Firefox was upgraded from 1.0.7 to 1.0.8. So, 1.5.0.3 will be upgraded with 1.5.0.4 in a few days :p

---

### Post by Rackerz on 2006-06-02
[QUOTE=FredB]Well, I can see that on Breezy Firefox was upgraded from 1.0.7 to 1.0.8. So, 1.5.0.3 will be upgraded with 1.5.0.4 in a few days :p[/QUOTE]

I hope so, even though I've upgraded to 1.5.0.4 manually I'd still like to use the official Repo's so if I get any problems I can get support for it.

---

### Post by mlind on 2006-06-02
This is a security fix release, a minor version number bumb, so I guess it's a
nobrainer that we'll get an updated firefox in next couple of days.

---

### Post by sgarman on 2006-06-02
Given how important my e-mail and web browser clients are, I like to stay current with the latest release. I have followed the wiki instructions so I can use the thunderbird and firefox tarballs from mozilla.com. 

However, the default fonts these apps use is definitely different from the ones packaged in Dapper. How do I configure them to use the same fonts as the official Dapper packages?

Thanks,

Scott

---

### Post by ruffneck on 2006-06-02
Since I manually installed FF 1.5.0 back when I had Breezy (before dist-upgrading to Dapper) all I have to do is Help --> Check for updates --> and update my FF to the latest. Easy as pie :)

---

### Post by henriquemaia on 2006-06-02
[quote=FredB]Well, I can see that on Breezy Firefox was upgraded from 1.0.7 to 1.0.8. So, 1.5.0.3 will be upgraded with 1.5.0.4 in a few days :p[/quote]

I have to update manually because I'm running the 32bit version of Firefox on my 64bit Dapper. 

On my case, update is so simple as:

1. download firefox from mozilla.
2. upackage the file
3. open the folder /usr/local/firefox32 on a sudo nautilus
4. copy the contents of the firefox folder downloaded from mozilla and paste it on the /usr/local/firefox32 nautilus. Everthing done on GUI.

Not very elegant, but easy enough. :)

---

### Post by aysiu on 2006-06-02
[QUOTE=Rackerz]
EDIT: Here is how to update your Firefox to 1.5.0.4. Credit goes to aysiu.[/QUOTE] Just to set the record straight, most of the credit actually goes to nanotube, who created all the complicated stuff in the new script.

My old script was basically just a copy and paste of the Wiki instructions. Nanotube's script is a lot smarter.

---

### Post by Fass on 2006-06-02
Another way to get the latest Firefox, and have it be speedier, is of course to use [Swiftfox.](http://www.getswiftfox.com/)

---

### Post by Mahmoud on 2006-06-03
After upgrading to 1.5.0.4 using the script, The Flash Plugin does not work. I tried to reinstall it (the flash player) using: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

but it does not work. (Firefox does not detect it)

Any idea how can I fix it?

---

### Post by benuski on 2006-06-03
if you go to the wiki entry for [FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion") there is information that tells you how to switch all your old plugins from your old version of firefox to your new version.  Of course, if you don't have your old version anymore, that would make this much harder, and something I don't know how to do off the top of my head.
If I had it in front of me I might be able to reason it out.  So tell me if this doesn't work.

And does anyone know if you can delete the repo version of thunderbird if you download it manually, or do you have to keep it for dependancies, like firefox?

In general, however, after downloading 1.5.0.4 of firefox manually, I've found there are some text and image rendering things that work better in this version than in the Ubuntu version. *shrug*

---

### Post by ash211 on 2006-06-03
I don't think you need to keep the repo thunderbird version.  I have the manual download installed, never installed the repo version, and don't have any dependency problems.  I guess the only way to know for sure is to remove it and find out.

I've experienced (and heard from others) that the Ubuntu version of firefox for some reason runs much slower than the Mozilla one.  I've always gone with Mozilla's firefox for that reason.  If you're interested in even more speed, give Swiftfox a shot at [www.getswiftfox.com](www.getswiftfox.com)  It's firefox compiled specifically for your processor, and may run even faster.

---

### Post by shuttleworthwannabe on 2006-06-03
Alternatively the new Bon Echo Alpha 3 is stable IMO and runs much better than the current FF in Ubuntu, e.g. it uses CPU and RAM more efficiently than FF. It is also noticeably faster. Bon Echo Alpha3 can be downloaded from Mozillazine.org. Give it a try.

---

### Post by BlackWoxs on 2006-06-04
[QUOTE=bluevoodoo1]I got it by altering aysiu's 1.5.0.3 script to get 1.5.0.4. Easy as pie.[/QUOTE]

Another 'Easy as Pie' way, is to run Firefox as root:

sudo firefox

and simply select the Help - Check for Updates menu option from within FireFox. This has the advantage that only a small download is required to patch the installation to 1.5.0.4

---

### Post by OffHand on 2006-06-04
[QUOTE=BlackWoxs]Another 'Easy as Pie' way, is to run Firefox as root:

sudo firefox

and simply select the Help - Check for Updates menu option from within FireFox. This has the advantage that only a small download is required to patch the installation to 1.5.0.4[/QUOTE]
As far as I know this way of updating will not work on Ubuntu's native FF.
Only when you have installed mozilla's version.

---

### Post by badrad on 2006-06-04
Woohoo, thanks for the install script.

---

### Post by aysiu on 2006-06-04
[QUOTE=BlackWoxs]Another 'Easy as Pie' way, is to run Firefox as root:

sudo firefox

and simply select the Help - Check for Updates menu option from within FireFox. This has the advantage that only a small download is required to patch the installation to 1.5.0.4[/QUOTE] I'd highly recommend *gksudo firefox* or *kdesu firefox* instead of *sudo firefox*. You may end up with root owning your preferences otherwise.

---

### Post by jdong on 2006-06-04
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/48043](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/48043)

> 
Hi,

John Dong [2006-06-04 20:30 -0000]:
> This is a security issue. Is there any plan to include this in dapper-
> security yet?

Yes, very soon (next week).


That's from Martin Pitt, he's the top dog when it comes to security updates :)

---

