---
title: "Ubuntu 10.04/ 10.10 youtube videos lagging!"
date: 2010-10-11
forum: General Help
---

### Post by sudoer541 on 2010-10-11
Does anyone have problems viewing youtube videos on ubuntu? 
Whenever I watch a 720 HD youtube video, it lags like crazy... I feel like I am watching a slide show. 
I never had this problem with ubuntu 9.04 and under.

I tired to:
remove and reinstall flash from the beginning. 
Removed ubuntu restricted extras and reinstall them again. 
I tried Chrome instead of Firefox.
Installed the proper drivers from my video card. 
removed proper drivers for my video card and stayed with the open source drivers. 

Here are my specs: 
1 GB RAM
2.20 GHz AMD Athlon processor
ATI Radeon 9250 @ 128 MB
Windows xp SP3 / ubuntu 10.04


Anyone else have this issue? How did you solve it?

---

### Post by kevin11951 on 2010-10-11
What is your graphics card?

---

### Post by sudoer541 on 2010-10-11
> **kevin11951 said:**
> What is your graphics card?


ATI Radeon 9250 @ 128 MB

---

### Post by kevin11951 on 2010-10-11
> **sudoer541 said:**
> ATI Radeon 9250 @ 128 MB

Are you able to enable Compiz?

---

### Post by juancarlospaco on 2010-10-11
Use HTML5, youtube support HTML5

---

### Post by cariboo on 2010-10-11
This is not a Cafe question, moved to General Help.

---

### Post by lovinglinux on 2010-10-11
See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) and [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by sudoer541 on 2010-10-11
> **kevin11951 said:**
> Are you able to enable Compiz?


Yes, compiz works perfectly!

---

### Post by |{urse on 2010-10-11
Html5 is the way to go here. You can thank adobe for their wonderful "cross-platform" flash. You can really smooth things out with the suggestions in post #7 however.

---

### Post by sudoer541 on 2010-10-11
> **|{urse said:**
> Html5 is the way to go here. You can thank adobe for their wonderful "cross-platform" flash. You can really smooth things out with the suggestions in post #7 however.


How to enable HTML 5 video on youtube?

---

### Post by |{urse on 2010-10-11
right here =)

[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by sudoer541 on 2010-10-11
> **|{urse said:**
> right here =)

[http://www.youtube.com/html5](http://www.youtube.com/html5)


Do I have to have an account to enable this? 

Thanks btw!

---

### Post by |{urse on 2010-10-11
I'm not 100% but I'm pretty sure all you get is a cookie and that sets your prefs every time youtube is opened in your browser.

---

### Post by Reileigh on 2010-10-11
Lately, my youtube has been lagging on Windows 7, Windows 2008 Server, Windows XP (at school), Ubuntu 10.04...

---

### Post by sudoer541 on 2010-10-12
I have been trying to install Gnash and other alternatives to Adobe's Flash. However whenever I visit youtube, it asks me to install Adobe's Flash and there is no option to install other flash players other than Adobe Flash.. 
I installed Gnash and another flash player (cant remember the name) and no matter what I install, youtube asks me to install Adobe Flash. 
Is there a way to fix this?

---

### Post by davidmohammed on 2010-10-12
> **sudoer541 said:**
> I have been trying to install Gnash and other alternatives to Adobe's Flash. However whenever I visit youtube, it asks me to install Adobe's Flash and there is no option to install other flash players other than Adobe Flash.. 
I installed Gnash and another flash player (cant remember the name) and no matter what I install, youtube asks me to install Adobe Flash. 
Is there a way to fix this?

I think you may be talking about lightspark - try [here]("http://www.omgubuntu.co.uk/2010/07/lightspark-0-4-2-released-adds-chromeium-support-better-youtube-support-ppa/") for some instructions.

---

### Post by sudoer541 on 2010-10-12
Update: 

I just installed Gnash and youtube videos still lag. :(

I tried the  HTML 5 option as well, but videos dont play at all. :(

---

### Post by lovinglinux on 2010-10-12
> **sudoer541 said:**
> Update: 

I just installed Gnash and youtube videos still lag. :(

I tried the  HTML 5 option as well, but videos dont play at all. :(

If you are on a single core processor, then I'm afraid there is not much you can do. I was only able to view HD videos os YouTube without lagging when I upgraded from a P4 to a Core2 Duo. Nevertheless, you could try the third item on [this list]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html").

If that doesn't help, then get [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/") extension. It will allow you to watch HD videos on YouTube with a different plugin like totem or gecko-mediaplayer, which uses a lot less CPU and uses xv.

---

### Post by requeth on 2010-10-12
I have been having issues with flash on Linux for many, many, years. And I always solve the issue by a dozen hackjobs coiled together. I just reformatted my system yesterday and decided to find an easier hack, and I have found it. As the inventor of this hack implies, Adobe built flash to run on Nvidia cards, and nothing else. His hack is for Intel chipsets, but I have an ATI HD5XXX series and this worked flawlessly, though it is highly  gritty.

Link to the hack: [http://www.linuxquestions.org/questions/slackware-14/choppy-flash-streaming-620030/](http://www.linuxquestions.org/questions/slackware-14/choppy-flash-streaming-620030/)
Post by Creepytennis.

Ultimately you install ghex2

Then:
backup /usr/lib/xorg/modules/extensions/libglx.so
run: sudo ghex2 /usr/lib/xorg/modules/extensions/libglx.so
Hit Ctrl F to do a find. This is where it gets gritty. Put on zerozero 00 in the hex field, go over to the right side box and put in SGI then go back to hex and put in 00. Ignore the extra 0 showing up, it's displaying the cursor.
Hit Find.
It should get one hit. The 00's are identifying (null) in hex incase your confused, as you should be.
Now do a replace, replacing (null)SGI(null) with (null)ATI(null), using the 00's as above.
Save the file.
Reboot.
Pray to god you didn't just hose X.
If your graphical system comes back on: go to youtube and test a video. Mine worked great after this. Creepytennis had another file he had to edit, it wasn't on my system. I'm using the proprietary ATI driver, may make a difference.

If your graphical system doesn't come back on: blame Creepytennis. He's a techie, he's used to it. ;)

After 10 years of Linux: the end all to the flash choppy problem!

---

### Post by sudoer541 on 2010-10-13
> **lovinglinux said:**
> If you are on a single core processor, then I'm afraid there is not much you can do. I was only able to view HD videos os YouTube without lagging when I upgraded from a P4 to a Core2 Duo. Nevertheless, you could try the third item on [this list]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html").

If that doesn't help, then get [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/") extension. It will allow you to watch HD videos on YouTube with a different plugin like totem or gecko-mediaplayer, which uses a lot less CPU and uses xv.

eeeekk! :eek: I am on a single core processor!!!:o
Ill give the plugin a try. 
Thanks

> **requeth said:**
> I have been having issues with flash on Linux for many, many, years. And I always solve the issue by a dozen hackjobs coiled together. I just reformatted my system yesterday and decided to find an easier hack, and I have found it. As the inventor of this hack implies, Adobe built flash to run on Nvidia cards, and nothing else. His hack is for Intel chipsets, but I have an ATI HD5XXX series and this worked flawlessly, though it is highly  gritty.

Link to the hack: [http://www.linuxquestions.org/questions/slackware-14/choppy-flash-streaming-620030/](http://www.linuxquestions.org/questions/slackware-14/choppy-flash-streaming-620030/)
Post by Creepytennis.

Ultimately you install ghex2



Then:
backup /usr/lib/xorg/modules/extensions/libglx.so
run: sudo ghex2 /usr/lib/xorg/modules/extensions/libglx.so
Hit Ctrl F to do a find. This is where it gets gritty. Put on zerozero 00 in the hex field, go over to the right side box and put in SGI then go back to hex and put in 00. Ignore the extra 0 showing up, it's displaying the cursor.
Hit Find.
It should get one hit. The 00's are identifying (null) in hex incase your confused, as you should be.
Now do a replace, replacing (null)SGI(null) with (null)ATI(null), using the 00's as above.
Save the file.
Reboot.
Pray to god you didn't just hose X.
If your graphical system comes back on: go to youtube and test a video. Mine worked great after this. Creepytennis had another file he had to edit, it wasn't on my system. I'm using the proprietary ATI driver, may make a difference.

If your graphical system doesn't come back on: blame Creepytennis. He's a techie, he's used to it. ;)

After 10 years of Linux: the end all to the flash choppy problem!

sounds risky, but ill try it the above solution first. If it doesn't work (since I have nothing to lose) I will try this solution.

Thanks!

---

