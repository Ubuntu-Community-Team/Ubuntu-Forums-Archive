---
title: "Firefox 8.0.1 on ubuntu 11.04"
date: 2011-12-17
forum: General Help
---

### Post by Mr_and_Mrs_D on 2011-12-17
I spent my saturday afternoon trying to install Firefox 8.0.1 on ubuntu 11.04 x64

I feel very frustrated

I did install it to /opt - but it can never see the flash player - and the Ubuntu-Integration-Addon is all messed up

So - is there an official way to UPGRADE firefox 8.0 to 8.0.1 ?

Please help

---

### Post by Frogs Hair on 2011-12-17
Any official updates will come via the update manager . Using other methods may cause add-on compatibility problems . 

As a Nightly build user I have to use this add-on to keep my extensions working .  [https://addons.mozilla.org/en-US/firefox/addon/add-on-compatibility-reporter/](https://addons.mozilla.org/en-US/firefox/addon/add-on-compatibility-reporter/)

---

### Post by yeats on 2011-12-17
You might want to read over this wiki page:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

The mozilla stable PPA is the way I'd do it:

[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

---

### Post by lovinglinux on 2011-12-18
> **Mr_and_Mrs_D said:**
> I spent my saturday afternoon trying to install Firefox 8.0.1 on ubuntu 11.04 x64

I feel very frustrated

I did install it to /opt - but it can never see the flash player - and the Ubuntu-Integration-Addon is all messed up

So - is there an official way to UPGRADE firefox 8.0 to 8.0.1 ?

Please help

As far as I am aware, Firefox 8.0.1 is not in the repos yet, neither in the mozillateam ppa.

If you really want Firefox 8.0.1, you can install it manually as you did and make a symlink for the plugins folder:

```
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins
```

Make sure the version of Firefox you downloaded is 64bit, otherwise flash plugin won't work and won't be detected.

To be honest, it will be a waste of time to get 8.0.1 now, because Firefox 9 will be released next week.

See [Firefox 8 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247) for additional instructions.

---

### Post by Mr_and_Mrs_D on 2011-12-18
@lovinglinux :Starts to make sense - run sudo apt-get dist-upgrade with all imaginable ppas and did not get any update

I was starting to hear things

Very annoying - people make posts/blog entries/whatnot spreading misinformation,never updating it - illiterates

Frustration - i can't resist

Grrr - and this detail with the 64 version should make a difference


I messed a lot around - i guess there  are leftovers everywhere

Need 8.01 cause i am using my profile from windoz - currently i run it with FF 8.0 - hope it didn't mess it up too much :rolleyes:

EDIT : where do i get the 64 linux version from - can't seem to find it easily

Thanks

---

### Post by oklokl on 2011-12-18
[http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=natty&section=all](http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=natty&section=all)
[http://packages.ubuntu.com/search?keywords=flashplugin&searchon=names&suite=natty&section=all](http://packages.ubuntu.com/search?keywords=flashplugin&searchon=names&suite=natty&section=all)

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main multiverse
look hidn ok? &#48372;&#51060;&#51648; &#50506;&#49845;&#45768;&#45796; &#50629;&#45936;&#51060;&#53944; &#54616;&#49492;&#46020; &#44536;&#47000;&#46020; apt-get update &#54616;&#49464;&#50836;..
sudo apt-get update
sudo apt-get install firefox
sudo apt-get install firefox-locale-en
sudo apt-get install adobe-flashplugin


[http://cafe.daum.net/candan/HgwY/77](http://cafe.daum.net/candan/HgwY/77)
my home.. korea..
&#54620;&#44397;&#50612;&#47196;&#46020; &#50416;&#44192;&#49845;&#45768;&#45796; &#44277;&#49885; &#54856;&#54168;&#51060;&#51648;&#50640;&#49436; &#45796;&#50868;&#47196;&#46300; &#54616;&#45716; &#48169;&#48277; &#51077;&#45768;&#45796;..

---

### Post by Frogs Hair on 2011-12-18
The two bugs addressed in the update don't appear to be Linux related , but  I'm sure more information could be found .  [http://www.ghacks.net/2011/11/22/firefox-8-0-1-officially-available-what-you-need-to-know/](http://www.ghacks.net/2011/11/22/firefox-8-0-1-officially-available-what-you-need-to-know/)

---

### Post by ottosykora on 2011-12-18
Why do you need to update to 8.0.1?

Are you using some of the extensions this bugfix version is concerned?

On windows also there is no update to 8.0.1 unless you want to resolve some problems with particular extension and this is for windows only and otherwise there is no difference between 8.0.1 and 8.0

---

### Post by Mr_and_Mrs_D on 2011-12-18
> **oklokl said:**
> [http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=natty&section=all](http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=natty&section=all)
[http://packages.ubuntu.com/search?keywords=flashplugin&searchon=names&suite=natty&section=all](http://packages.ubuntu.com/search?keywords=flashplugin&searchon=names&suite=natty&section=all)

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main multiverse
look hidn ok? &#48372;&#51060;&#51648; &#50506;&#49845;&#45768;&#45796; &#50629;&#45936;&#51060;&#53944; &#54616;&#49492;&#46020; &#44536;&#47000;&#46020; apt-get update &#54616;&#49464;&#50836;..
sudo apt-get update
sudo apt-get install firefox
sudo apt-get install firefox-locale-en
sudo apt-get install adobe-flashplugin


[http://cafe.daum.net/candan/HgwY/77](http://cafe.daum.net/candan/HgwY/77)
my home.. korea..
&#54620;&#44397;&#50612;&#47196;&#46020; &#50416;&#44192;&#49845;&#45768;&#45796; &#44277;&#49885; &#54856;&#54168;&#51060;&#51648;&#50640;&#49436; &#45796;&#50868;&#47196;&#46300; &#54616;&#45716; &#48169;&#48277; &#51077;&#45768;&#45796;..
Are you* absolutely sure* you are not wasting my time ?

---

### Post by oklokl on 2011-12-18
sorry re install ubuntu 
Please clean system.. testing 
&#54620;&#44397;&#50612;&#47196;&#46020; &#51201;&#44192;&#49845;&#45768;&#45796;.. format&#51012; &#49352;&#47196; &#54616;&#49512;&#51012;&#46412; &#53580;&#49828;&#54021; &#54644;&#48372;&#49464;&#50836;..
&#54788;&#51228; other.. deb&#44032; &#46321;&#47197; &#46104;&#50612; &#51080;&#45716; &#49345;&#53468;&#50640;&#49436;&#45716; next Firefox or Firefox 9.. ->flash player bug..Not remove
sudo apt-get upgrade -> flash player bug &#48156;&#49373; &#54633;&#45768;&#45796;..

---

