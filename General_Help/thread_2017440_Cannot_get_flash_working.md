---
title: "Cannot get flash working"
date: 2012-07-05
forum: General Help
---

### Post by wvcaudill2 on 2012-07-05
Hey everyone, I just installed Lubuntu 12.04 to my 8-yr old desktop yesterday, and everything is running beautifully! There is just one problem though. I can't for the live of my get flash working!

Now, I've been using Ubuntu for many years now, and I know I've successfully had flash working before, but I don't know what im doing wrong.

Here is what I've tried so far:
1. Installed Lubuntu-restricted extras/addons
2. Installed Firefox w/ Flash-aid and run the wizard every way possible.
3. Directly installed from Adobe

Flash refuses to work in both Chromium and Firefox. In fact, in Chromium, it immediately says the flash plugin has crashed the second I try to load a flash vid.

I've searched online, but it seems as if I've done everything people recommend. Do you guys have any ideas whats going on here?

---

### Post by msammels on 2012-07-05
Have you tried installing Google Chrome from [here](http://www.google.com/chrome)?

---

### Post by wvcaudill2 on 2012-07-05
> **msammels said:**
> Have you tried installing Google Chrome from [here](http://www.google.com/chrome)?

I have not. I didn't think this was a browser issue as both browsers were unable to display flash properly. I will, however, reinstall from there.

---

### Post by wvcaudill2 on 2012-07-05
I completely uninstalled Google Chrome and Chromium and still have the same problem.

---

### Post by msammels on 2012-07-05
Google Chrome comes with it's own version of Flash, so if you have a problem, perhaps it related to your operating system. Try logging with "Ubuntu 2D".

---

### Post by wvcaudill2 on 2012-07-05
> **msammels said:**
> Google Chrome comes with it's own version of Flash, so if you have a problem, perhaps it related to your operating system. Try logging with "Ubuntu 2D".

I am running lubuntu, there is no "Ubuntu 2D." However, I did try it in Lubuntu Netbook, and the flash plugin is still crashing.

---

### Post by haresear on 2012-07-05
Some (including me) have had problems with the latest version of Flash (11.3). It won't run for me in any browser from any source. I finally was able to find and download an older version (11.1) that runs fine.

---

### Post by wvcaudill2 on 2012-07-05
> **haresear said:**
> Some (including me) have had problems with the latest version of Flash (11.3). It won't run for me in any browser from any source. I finally was able to find and download an older version (11.1) that runs fine.

Do you happen to still have the link you used for the flash download?

---

### Post by haresear on 2012-07-05
> **wvcaudill2 said:**
> Do you happen to still have the link you used for the flash download?

I don't have the link I used, but you might check the following thread which has some links for older versions of Flash:

[http://ubuntuforums.org/showthread.php?t=1953796]("http://ubuntuforums.org/showthread.php?t=1953796")

---

### Post by wvcaudill2 on 2012-07-05
I've just discovered something. Youtube videos will work, but some other sites that rely on flash still will not work. So, what is going on?

---

### Post by msammels on 2012-07-05
What browser do the YT vids work on? All browsers?

---

### Post by wvcaudill2 on 2012-07-05
> **msammels said:**
> What browser do the YT vids work on? All browsers?

Seems as if the YT videos only play in Chromium, as when I opened the same vid in Firefox, it just shows a blank box where the vid should be.

---

### Post by msammels on 2012-07-05
Here's the problem: flashplayer-plugin isn't maintained by Adobe anymore. Chromium has it's own player implemented. Stick with Chromium, and your problem **should** disappear.

---

### Post by QIII on 2012-07-05
Correction:  The Linux Flash plugin is not *under active development any longer.  *It will be receiving security updates for 5 years, which qualifies as maintenance.

---

### Post by wvcaudill2 on 2012-07-05
But, even with Chromium, some websites with flash fail to work properly. For example, on one of these sites, I instantly get the message "The following plugin has crashed: Shockwave Flash."

For example, I get this error message when I go to my Gmail inbox.

---

### Post by wvcaudill2 on 2012-07-05
Well, I just realized that the only reason YT is working is because the videos are rendered with HTML 5, so I am pretty sure Flash is not working AT ALL. 

Come on guys, I need some solutions here!

---

### Post by claracc on 2012-07-06
The solution is to use and adobe flash plugin under release 11.2.

I recommend to install it through the lovinglinux addon for firefox flash aid, selecting the custom installation.

Previously you have to download the old flash plugin from [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html) I am using the 10.3.183.20 release. You have to select the linux .tar.gz

A very good thread to solve and understand the problem is : [http://ubuntuforums.org/showthread.php?t=1953796&page=3](http://ubuntuforums.org/showthread.php?t=1953796&page=3)
There are well explained solutions to fix flash, the only problem is you will run flash in older releases so it can be security problems

---

### Post by ricardisimo on 2012-07-06
It's hit-or-miss for me in Firefox, but I get nothing in Chrome. Has anyone tried Opera?

---

### Post by wvcaudill2 on 2012-07-06
> **claracc said:**
> The solution is to use and adobe flash plugin under release 11.2.

I recommend to install it through the lovinglinux addon for firefox flash aid, selecting the custom installation.

Previously you have to download the old flash plugin from [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html) I am using the 10.3.183.20 release. You have to select the linux .tar.gz

A very good thread to solve and understand the problem is : [http://ubuntuforums.org/showthread.php?t=1953796&page=3](http://ubuntuforums.org/showthread.php?t=1953796&page=3)
There are well explained solutions to fix flash, the only problem is you will run flash in older releases so it can be security problems

This solution worked perfectly, thanks!

---

### Post by claracc on 2012-07-06
You are welcome.

As you got the problem fixed, please mark the thread as solved with  "thread tools" in the upper right part of the page.

---

### Post by ricardisimo on 2012-08-15
Why is this only a problem for me on my 32-bit, nvidia system, but not my 64-bit with the ATI card? Also, Flash-Aid "has been removed by its author." Not sure if it's an absolute necessity or not, but...

---

