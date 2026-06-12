---
title: "Another Flash related problem... but with webcam problems!"
date: 2011-06-04
forum: General Help
---

### Post by lifelike27 on 2011-06-04
I've used this video conferencing web app on Windows 7 and it works perfectly. [www.aim.com/av](www.aim.com/av)

But I'm having flash problems. Flash doesn't load and the light at my webcam doesn't switch on at all.

Things to note:
[LIST]
Cheese works so I know my webcam in Ubuntu is functional.[/LIST]
[LIST]
[*]I've tried purging the flash plugin and reinstalling it.
[/LIST]
[LIST]
[*]It doesn't work on Chrome and Firefox so it's definitely only a flash problem.
[/LIST]
[LIST]
[*]I'm not using any medication so I know it isn't me just imagining it.
[/LIST]

EDIT: I checked out [http://testmycam.com/](http://testmycam.com/) and I can see my face perfectly.

Here's a screenshot: [http://dl.dropbox.com/u/8515110/temp/Test.png](http://dl.dropbox.com/u/8515110/temp/Test.png)

I'll check back later, Charlie the Unicorn just rang my doorbell and invited me to tea on the magic hot air balloon. Definitely not hallucinating. Definitely. Definitely.

---

### Post by no2498 on 2011-06-04
you may try right clicking the flash app at the site you use
to set adobe flash player to allow and remember

or you can set it at the adobe site
look for the settings manager
set it to allow and remember for the site's you use

---

### Post by lifelike27 on 2011-06-05
I tried that too. Should have mentioned it my initial post. I checked the Global Privacy Settings and all, but the problem is flash just doesn't load for this website. I did report it to the website. I tried running this with Google Chrome Unstable, nothing there either.

It might also be a problem because the feature is still in beta...

---

### Post by no2498 on 2011-06-06
install the plugin flash aid for fire fox
then run flash aid

---

### Post by lifelike27 on 2011-06-08
> **no2498 said:**
> install the plugin flash aid for fire fox
then run flash aid

Tried it - didn't work. Thanks though.

---

### Post by linuxinstalledfromhdd on 2011-06-08
Try installing Flash Aid again this way:

[http://cinderbox.net/2011/03/22/flash-aid-addon-for-firefox-automatically-detects-best-flash-version-for-your-system/](http://cinderbox.net/2011/03/22/flash-aid-addon-for-firefox-automatically-detects-best-flash-version-for-your-system/)

And what you need to try that's different this time is use the dropdown and select (stable) adobe flash plugin. You are probably using a beta version. 

Good luck.

PS if you are using a 11.04 64-bit installed version of Ubuntu, make a live 32-bit disc of 10.10 and boot from that live disc you have created, and see if that solves your issues, if all else fails. :)

---

### Post by no2498 on 2011-06-08
install opera web browser
i had problems with fire fox now that i think abought it

---

### Post by lifelike27 on 2011-06-08
> **linuxinstalledfromhdd said:**
> Try installing Flash Aid again this way:

[http://cinderbox.net/2011/03/22/flash-aid-addon-for-firefox-automatically-detects-best-flash-version-for-your-system/](http://cinderbox.net/2011/03/22/flash-aid-addon-for-firefox-automatically-detects-best-flash-version-for-your-system/)

And what you need to try that's different this time is use the dropdown and select (stable) adobe flash plugin. You are probably using a beta version. 

Good luck.

PS if you are using a 11.04 64-bit installed version of Ubuntu, make a live 32-bit disc of 10.10 and boot from that live disc you have created, and see if that solves your issues, if all else fails. :)

I tried Flash Aid this way as well. Nothing =\

Will try the live disk after trying Opera! I happen to have a 32 bit version of 10.10 somewhere around me. Thanks! =)


> **no2498 said:**
> install opera web browser
i had problems with fire fox now that i think abought it

Installing opera now!

---

### Post by xjonquilx on 2011-06-11
I can't get this to work either. Using 11.04 and have tried all the suggestions here.

---

### Post by VOT Productions on 2011-06-11
Install Ubuntu Restricted Extras.

---

### Post by linuxinstalledfromhdd on 2011-06-11
Install WebcamStudio.

Try bringing that up first before running whatever you are doing with your webcam.

First Click on "Sources" scroll down to "Webcams" and select your webcam (it should be detected).

---

### Post by xjonquilx on 2011-06-12
I found a solution to this. Go to the website you want to use your webcam on first and try to use it even though its not going to work. Then go to this link:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)

Select the website from the list and put a bullet next to "always allow".

---

### Post by lifelike27 on 2011-06-14
I tried all your answers, I think it's just website. Like I mentioned earlier. 

My webcam works on testwebcam.com so it can't be an internal webcam problem. Therefore, it must be a problem with the website. I've reported it to the website and hopefully it'll be fixed soon.

I'm marking this thread as solved.

[COLOR="Red"]EDIT: This is also happening for imo.im/now as well so it's not only the aim website. Marking it as unsolved now.[/COLOR]

---

### Post by no2498 on 2011-06-15
what adobe flash player you have the number of it

---

### Post by lifelike27 on 2011-06-16
> **no2498 said:**
> what adobe flash player you have the number of it

I was using the 32 bit version earlier (10.3.181.22ubuntu0.11.04.1)

I've just installed the 64 bit version available on Adobe's website (10.3.162)

> **xjonquilx said:**
> I found a solution to this. Go to the website you want to use your webcam on first and try to use it even though its not going to work. Then go to this link:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)

Select the website from the list and put a bullet next to "always allow".

xjonquilx's comment helped me for part of my problem. imo.im/now works but aim.com/av doesn't work. However, now the light on my webcam comes on for a second and then switches off. That's good news since the light wouldn't come on at all in the beginning.

---

### Post by lifelike27 on 2011-06-16
Success! It now works for aim.com/av as well! I'm using the 32 bit version of Flash back again! 

Just to summarize:

aim.com/av ---> works with 32 bit flash ONLY.

imo.im/now ---> works with 32 bit AND 63 bit flash.

To get it to work you have to go to [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html) and select 'Always Allow' for the website that's trying to use the webcam. Always Ask DOES NOT WORK.

In my case, I had to allow imo.im and o.aolcdn.com from the Website Privacy Settings list of visited websites.

Solved!

---

