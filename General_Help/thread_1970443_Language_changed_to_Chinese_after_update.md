---
title: "Language changed to Chinese after update"
date: 2012-05-01
forum: General Help
---

### Post by cazazo on 2012-05-01
Hi, what is going on with this version of ubuntu??? after a sudo apt-get update and sudo apt-get upgrade, my system changed the menus to Chinese... to bad I don't speak or read chinese... Can some one help me to change it back to English... via terminal, no way I can find anything in these menus...
Really getting tired of Ubuntu...
Please help!

---

### Post by philinux on 2012-05-01
> **cazazo said:**
> Hi, what is going on with this version of ubuntu??? after a sudo apt-get update and sudo apt-get upgrade, my system changed the menus to Chinese... to bad I don't speak or read chinese... Can some one help me to change it back to English... via terminal, no way I can find anything in these menus...
Really getting tired of Ubuntu...
Please help!

If you are logged, save anything you're doing and then press Alt+ PrtScr+ k which will get you back to login screen. Look top right for the keyboard icon. Select the language there.

---

### Post by cazazo on 2012-05-01
Can any one suggest me a new Linux Distro????

---

### Post by philinux on 2012-05-01
> **cazazo said:**
> Can any one suggest me a new Linux Distro????

[http://forums.linuxmint.com/viewtopic.php?f=90&t=98684](http://forums.linuxmint.com/viewtopic.php?f=90&t=98684)

[http://forums.fedoraforum.org/showthread.php?p=1561783](http://forums.fedoraforum.org/showthread.php?p=1561783)

Erm. I've never encountered a problem like this in 5 years. Are you sure you did not do something?

Did you try what I posted.

---

### Post by cazazo on 2012-05-01
Since Unity is around my problems have started... now after a simple update not all but some items of the menu are in english, some in chinese. I check the icon in the login screen and it is english selected. I can't change the language back to english... will be the 5 time I have to reinstall ubuntu in the last 60 days.
Really annoying.
I'm using the gnome classic... and have installed the Cinnamon and mat desktops...

---

### Post by philinux on 2012-05-01
Even though you're in chinese this shoudld work.
On the desktop. Click the top right Gear icon. First option is system settings.

The Keyboard layout icon is the the 3rd on the top row.

Either choose the preferred or Reset to default.

---

### Post by cazazo on 2012-05-01
Not all the menus are in Chinese... What i did was going to the terminal (ALT+CTRL+T) and did an usual update upgrade... after boot the computer the "Aplications" word is in chinese, the Synaptic is completely in chinese, few firefox, tunderbird and few other apps are in chinese and others such as skype  in english. I have not change a thing but upgraded. I've been using Ubuntu for 5 years and I usually know my way around the system... this time I can't find were can I change things.

---

### Post by cazazo on 2012-05-01
Thats from my terminal now...

> ~$ sudo apt-get upgrade --fix-broken
[sudo] password for cazazo: 
&#27491;&#22312;&#35835;&#21462;&#36719;&#20214;&#21253;&#21015;&#34920;... &#23436;&#25104;
&#27491;&#22312;&#20998;&#26512;&#36719;&#20214;&#21253;&#30340;&#20381;&#36182;&#20851;&#31995;&#26641;       
&#27491;&#22312;&#35835;&#21462;&#29366;&#24577;&#20449;&#24687;... &#23436;&#25104;       
&#21319;&#32423;&#20102; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#26032;&#23433;&#35013;&#20102; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#35201;&#21368;&#36733; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#26377; 0 &#20010;&#36719;&#20214;&#21253;&#26410;&#34987;&#21319;&#32423;&#12290;

---

### Post by philinux on 2012-05-01
> **cazazo said:**
> Thats from my terminal now...

What happens when you try what i said in post #6?

---

### Post by philinux on 2012-05-01
See this.

[http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html](http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html)

If still no joy you could run this.

Remove unnecessary locale data

For this we need to install localepurge.Automagically remove unnecessary locale data.This is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.

Install localepurge in Ubuntu

sudo apt-get install localepurge

Then run localepurge

[http://ubuntuforums.org/showthread.php?t=1695276](http://ubuntuforums.org/showthread.php?t=1695276)

---

### Post by cazazo on 2012-05-01
the language is all in chinese the keyboard layout is in English

---

### Post by philinux on 2012-05-01
> **cazazo said:**
> the language is all in chinese the keyboard layout is in English

Follow post #10 then. Good luck.

---

### Post by cazazo on 2012-05-01
The localepurge was in chinese as well... I went to google translate that was all in chinese) typed "English" saw the translation and changed at the system language back to english! After reboot did work. 
After that I did run the localepurge to remove all the other languages that I don't need. 
Thank you for your help! I appreciated it.
Sorry for the bad mood... 

Hope now I can have a "smooth run"...

---

### Post by cazazo on 2012-05-01
Oh, I don't think I can change this thread to "solved"... not enough privileges or something...
If you can change it would be great!
Thanks.

---

### Post by philinux on 2012-05-01
> **cazazo said:**
> Oh, I don't think I can change this thread to "solved"... not enough privileges or something...
If you can change it would be great!
Thanks.

Great stuff. Yes you can mark it solved. Thread Tools pull down menu, 4th option down.

---

### Post by cazazo on 2012-05-01
Thank you!!!

---

### Post by nghalion on 2012-05-01
Not yet Gents.. I have the EXACT same problem and gona try what you said.. Mark it "SOLVED" when it works for me too..:popcorn:

---

### Post by nghalion on 2012-05-01
Yepp..

[[COLOR=#d40000]**[COLOR=Black]..[/COLOR]philinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=353083") "eye-gor" is the MAN. Followed #10, rebooted and worked like a charm. Back to english.

It can be marked "SOLVED" now :guitar:

---

### Post by philinux on 2012-05-01
> **nghalion said:**
> Yepp..

[[COLOR=#d40000]**[COLOR=Black]..[/COLOR]philinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=353083") "eye-gor" is the MAN. Followed #10, rebooted and worked like a charm. Back to english.

It can be marked "SOLVED" now :guitar:

Blimey what's going on with all this Chinese stuff. Weird innit.

---

### Post by Vikky.20 on 2012-05-25
Hi, 

thanks for the instructions, however it did not work completely for me. I installed localepurge and selected en, en_GB and then run it as it was said I should. Most of the things changed to english, so I can work, but not all :(. 
Several things are still in Chinesse and several programs also (for example chromium, virtualbox). Also if I look to the System Settings->Language Support "Chinese" is still there and it can`t be removed.

Please could you tell me what to do and how did my system change the language, since I don`t recall setting it to chineese....

Viktor

---

### Post by Vikky.20 on 2012-05-25
Hi, 

I solved it just by pushing the chinesse language down in the language support. However the fact, that it can`t be removed from there still stands.

---

### Post by yoramdavid on 2012-06-24
> **Vikky.20 said:**
> Hi, 

I solved it just by pushing the chinesse language down in the language support. However the fact, that it can`t be removed from there still stands.

Hello all, I have the exact or worse problem. I am opening a new thread.

---

### Post by elingeniero on 2012-07-14
Old thread but I'm another one who was saved by localepurge in post #10. I don't know where the Chinese came from, all I did was some apt-get update and installing conkyforecast.


Good 10 minutes it was, learned lots of Chinese :D

---

### Post by yoramdavid on 2012-07-14
> **elingeniero said:**
> Old thread but I'm another one who was saved by localepurge in post #10. I don't know where the Chinese came from, all I did was some apt-get update and installing conkyforecast.


Good 10 minutes it was, learned lots of Chinese :D

Welcome to the club then, yes old thread but there are still remains of Chinese on my system, such as a language entry I cannot get rid off and recently there were some Chinese on the main menu. I installed English as a second language hoping that the Chinese will be override with English.

---

### Post by capngloval on 2012-07-14
Local purge doesn't work either. I have re installed ubuntu 3 times now, still i get this. Not at the first, or second or even third reboot, but usually after about five or six.

please help.

---

### Post by Jedcurtis on 2012-07-30
My two cents worth.

This happened to me this morning when I logged in.  Last night I did install the weather-indicator app.  I also installed some additional themes via synaptic.  When I logged in, voila, now I have to learn Chinese! (voila is the only French I know though I am fluent in pig-Latin!!!)

I simply logged out, changed the shell from Gnome back to Ubuntu (unity) and logged back in.  This worked for me, though I did as post 10 suggested (after the successful logout and login) and installed localepurge and selected "en" and "en_US-UTF-8".  I also removed the "theme" packages and "weather-indicator app" I added last night.

I love accidental learning!!!  Ubuntu RULES!!!

Jed

---

### Post by Serguey Basalaev on 2012-08-02
Hi, I had the Chinese issue too. I also used that hack localepurge, but some menu captions and package descriptions still were in Chinese. I've asked the question here with no help:
[https://answers.launchpad.net/ubuntu/+source/langpack-locales/+question/186658](https://answers.launchpad.net/ubuntu/+source/langpack-locales/+question/186658)

I finally found where it hides. In ~/.pam_environment here was a line
```
LANGUAGE=ru:zh_CN:en_US:en
```I changed it to
```
LANGUAGE=ru:en_US:en
```and then I was able to remove Chinese from list of languages. Hope it helps for someone else.

---

### Post by dingd0ng on 2012-08-10
Thanks Philinux (post #10) for having this solution.

I'm running 12.04 and after running system update Chinese language took over my computer - which would be cool with me if I would be able to read it. 

localepurge saved my butt and was really easy to use. Thanks a ton!

---

### Post by davidwillis on 2012-08-11
I just run into this problem today.  I have most of it fixed now, using the suggestions here, but I still get a popup in chromium asking me if I want to translate (at least that is what I think it is asking me).

---

### Post by davidwillis on 2012-08-11
nevermind, I finally got it working by doing this:
	

Solution:

1) edit /etc/default/locale:

LANG="en_US"

LANGUAGE="en_US:en"

2) edit ~/.pam_environment:

LANG=en_US

Language=en_US

Logout and Login or Reboot.

---

### Post by davidwillis on 2012-08-15
I see I have 45 updates right now, but I don't know if I want to update, since the last time it changed to chinese.  Does anyone know why, or if this has been fixed?

---

### Post by yoramdavid on 2012-08-15
> **davidwillis said:**
> I see I have 45 updates right now, but I don't know if I want to update, since the last time it changed to chinese.  Does anyone know why, or if this has been fixed?

I have ran updates often since then and it did not change to Chinese any more. It seems fine now.

---

### Post by davidwillis on 2012-08-15
Thanks.  I just did an update, and it didn't cause any problems this time.

---

### Post by davidwillis on 2012-08-16
I just noticed one more thing.  I am not sure it is casuing any problems, but I noticed this:

$ man sed
man: can't set the locale; make sure $LC_* and $LANG are correct


The man page came up fine, and I just noticed this when I closed it.

---

### Post by cbanakis on 2012-08-17
Such an odd bug?

I had to run "localepurge" as suggested in post 10.

That fixed most of it.

Then I had to change my language back to English in keyboard layout.

Seems to have cleared things up now.

So weird?

---

### Post by 344a on 2012-09-22
I'm having the same problem here.
I was using Mint Cinnamon few days ago and changed to KDE last night.  Now I've found some applications are using Simplified Chinese and English together, especially my Chromium browser.  It's quite anonying.  It was perfectly fine when I was using Cinnamon :(

Followed #10, problem hasn't been solved.

[IMG]http://i1229.photobucket.com/albums/ee479/dww5/Temp/snapshot1_zpsc5600440.jpg[/IMG]

And the Software Manager
[IMG]http://i1229.photobucket.com/albums/ee479/dww5/Temp/snapshot2_zps2953112b.jpg[/IMG]:

---

### Post by 344a on 2012-09-22
I love you so much... it works for me too =D>

> **davidwillis said:**
> nevermind, I finally got it working by doing this:
	

Solution:

1) edit /etc/default/locale:

LANG="en_US"

LANGUAGE="en_US:en"

2) edit ~/.pam_environment:

LANG=en_US

Language=en_US

Logout and Login or Reboot.

---

### Post by rag2 on 2012-09-22
This just happened to me, after Saturday's update.

**An alternative solution**
The solution was to go to System Settings, find the icon that's a United Nations (blue) Flag (ignore the Chinese text underneath), click on the icon, wait for the activity bar to complete. Then drag the line that says English (United Kingdom) or English (Wherever) to the top of the screen, so that it will look something like the screen grab below.

Your screen will have a line of Chinese ideograms on the top line, and that is where English (United Kingdom) or your local language should be dragged to. The system defaults to using the language at the top, and defaults to English if no other language is present.

[IMG]http://ubuntuone.com/6DgjntOMWCDdFYRdTWpxZX[/IMG]

---

