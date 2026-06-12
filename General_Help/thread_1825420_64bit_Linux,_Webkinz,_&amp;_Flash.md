---
title: "64bit Linux, Webkinz, &amp; Flash"
date: 2011-08-15
forum: General Help
---

### Post by neu5eeCh on 2011-08-15
Just noticed that my kids are no longer able to play webkinz on my 64bit system (Edubuntu). Webkinz also doesn't work on my 64bit Xubuntu system. Looks like 64bit Flash is broken? -- or something is broken between Webkinz and the latest flash. Webkinz, predictably enough, works on Windows, but also works on my 32bit Linux system with the latest flash.

Just wondering if any of you out there with a 64bit system could try accessing Webkinz (if you can see the Login moniker and click it, then it's working on your system). I'm just trying to work out where the problem is and a possible solution.

---

### Post by imortalninja161 on 2011-08-15
Hay man i checked it our for ya and the bottom link under the customer service button is a dead link 
But the top login link (top right) works fine for me also consider there has been an new official release for adobe flash player for ubunut 64bit.  if that isn't the issue then try 

```
sudo apt-get update
```If that dusent do it go here 

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

and choose APT for Ubuntu 10.04+

The file will by Default Be Downloaded to Home/ what ever your user name is/Downloads

Lunch the installer from there 

Post if that didn't fix it 

Hope this helps

Thanks
imortalninja161

---

### Post by neu5eeCh on 2011-08-15
Thanks imortalninja161, I'll try all of that out. Something strange happened. My kids were able to access the site with no issues and then something broke (which makes me think Webkinz changed something?). I then upgraded to the latest Flash (11.x) and it still didn't work. So... something along the lines of what you suggest might work. I'll work on it this evening.

**Edit: **If I have to,Is there a way to run 32bit firefox and Flash in 64?

---

### Post by blazemore on 2011-08-15
Open up a terminal and go
```

sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install flashplugin64-installer

```

Enjoy

---

### Post by imortalninja161 on 2011-08-15
the above sounds good

---

### Post by neu5eeCh on 2011-08-15
> **blazemore said:**
> Open up a terminal and go
```

sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install flashplugin64-installer

```Enjoy

Thanks. Yes, I found that earlier, but it doesn't help. I then removed the repository and tried going back to an earlier version. That also didn't help me.

I'm wondering if Webkinz has done something that conflicts with the Linux 64bit version of flash. The only way to know is if others go there (who have a similar system) and tell me if flash works for them. All you have to do is press the login button on the left. If the login popup appears, then it works and there's something wrong with **my** systems. If it doesn't work, then there's a bigger problem.

---

### Post by lovinglinux on 2011-08-15
Try [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/").

---

### Post by neu5eeCh on 2011-08-15
> **lovinglinux said:**
> Try [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/").

Thanks, Flash-Aid was already installed (in both Edubuntu & Xubuntu) but the issue persists.

Does anyone use a 64bit non-Ubuntu distro who can check this out? Just wondering if its distro specific.

Also, the site doesn't work in Firefox, Opera or Gnome. This argues that the problem isn't related to a given browser.

---

### Post by lovinglinux on 2011-08-15
> **VTPoet said:**
> Thanks, Flash-Aid was already installed (in both Edubuntu & Xubuntu) but the issue persists.

Does anyone use a 64bit non-Ubuntu distro who can check this out? Just wondering if its distro specific.

Also, the site doesn't work in Firefox, Opera or Gnome. This argues that the problem isn't related to a given browser.

It also doesn't seam to work on 32bit here, with flash 11 Beta 2.

When I access the site, I see a sign with Flash download warning.

---

### Post by kyletstrand on 2011-08-15
Check out this website.  I run 64 bit 10.04 and I couldn't get flash to work either, but I found this script that manually installs flash 11 beta and that solved my problems.

[http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html)

Check it out and see if you can get it to work.

---

### Post by bodhi.zazen on 2011-08-15
My children like webkinz, and from time to time we have problems with it.

What I do to run webkinz currently is to use midori.

I use the most recent 64 bit flash from Adobe.

---

### Post by lovinglinux on 2011-08-15
> **kyletstrand said:**
> Check out this website.  I run 64 bit 10.04 and I couldn't get flash to work either, but I found this script that manually installs flash 11 beta and that solved my problems.

[http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html)

Check it out and see if you can get it to work.

That is already covered by Flash-Aid and it didn't work.

---

### Post by neu5eeCh on 2011-08-15
> **bodhi.zazen said:**
> My children like webkinz, and from time to time we have problems with it.

What I do to run webkinz currently is to use midori.

I use the most recent 64 bit flash from Adobe.

I'll install Midori and see.

---

### Post by neu5eeCh on 2011-08-15
Using Midori didn't help. The Log In applet still claims Flash isn't installed. 

Curiously, when I click on the Log In* text* at the bottom of the website, I get the login popup. I'm still not sure Webkinz will work. I need to wait until the kids get home. I don't know their Webkinz password!

---

### Post by bodhi.zazen on 2011-08-15
> **VTPoet said:**
> Using Midori didn't help. The Log In applet still claims Flash isn't installed. 

Curiously, when I click on the Log In* text* at the bottom of the website, I get the login popup. I'm still not sure Webkinz will work. I need to wait until the kids get home. I don't know their Webkinz password!

It should work, that is the same behavior I am getting.

---

### Post by neu5eeCh on 2011-08-15
**Update:** Just happened to talk to my kids on the phone - good timing. As it turns out, I can log into Webkinz via the text 'Log In' option at the bottom of the screen, but the regular Log In applet on the left claims that Flash isn't installed. So... whatever is going on seems to be limited to the Webkinz start page? I can live with this, but it's still very odd -- something screwy with Webkinz or 64 Linux Flash.

---

### Post by bodhi.zazen on 2011-08-15
> **VTPoet said:**
> **Update:** Just happened to talk to my kids on the phone - good timing. As it turns out, I can log into Webkinz via the text 'Log In' option at the bottom of the screen, but the regular Log In applet on the left claims that Flash isn't installed. So... whatever is going on seems to be limited to the Webkinz start page? I can live with this, but it's still very odd -- something screwy with Webkinz or 64 Linux Flash.

Yes, that is my "work around" for webkinz.

Only so much time I was willing to up into it at this point although I am not convinced it is a flash problem, I think the problem is in the javascript.

---

