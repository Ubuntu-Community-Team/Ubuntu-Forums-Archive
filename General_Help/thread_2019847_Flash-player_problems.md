---
title: "Flash-player problems"
date: 2012-07-07
forum: General Help
---

### Post by gabmuks on 2012-07-07
Hello and good day to all.

So far I have been unable to get a working browser
that doesn't crash flashplayer.

Google Chrome works best. But then the Ubuntu updates somehow disabled the Chrome browser. Ubuntu forums was able to get Chrome working again but now no flashplayer.

I know that someone is working on this bug.
I just can't make sense of why one computer works with Chrome
and another does not.

I have an old computer that I have not updated.
Chrome still works great on that computer.

The only thing I could think of was to re-install 12.04
to try to get rid of whatever is interfering with Chrome.
I had to install 11.10 CD and then update to 12.04.

It's the only sure way that I've found so far.

Any way... re-installing the 12.04 didn't eliminate the Google Chrome problem on the 2007 computer.

It just don't make any sense...

On my old 2003 computer, I can remove and re-install Chrome,
and it works perfectly! Flash-player works great.

But on my 2007 computer, everything works except Chrome.

Although I have gotten the Chrome to load on the 2007 computer,
with the help from this forum, the flash-player will no longer work. So I am back to square one.

The only difference between the two computers that I know of,
is that I haven't installed the Ubuntu updates on the 2003
computer yet. Does anyone know what was in the Ubuntu updates
that could cause this problem? Or is it caused simply by my computer somehow?


Thank you for your time

Best regards

Pat L.

---

### Post by vasa1 on 2012-07-07
What happened to your other thread?

Okay. They're here:
[http://ubuntuforums.org/showthread.php?t=2018554](http://ubuntuforums.org/showthread.php?t=2018554)
and
[http://ubuntuforums.org/showthread.php?t=2016373](http://ubuntuforums.org/showthread.php?t=2016373)

I'm sorry I missed your other posts. I blame the time zone :( You get active at the exact time I get sleepy.

And this forum can get slow at times so it's better to provide information by plain text rather than by using images (whenever possible).

If you want to provide information you get from a terminal, you can copy stuff by dragging with the mouse and then right-clicking and choosing copy.

You can then come over here and paste it into your post between code tags (```
 and 
```).

---

### Post by vasa1 on 2012-07-07
In the other thread I asked you to post the version of the Chrome browser.

Could you do so again for both browsers? If one is version 20, then a problem with Flash is possible. If the other is version 19 or older, then a problem is _not_ expected.

---

### Post by gabmuks on 2012-07-07
Thank you for kind reply.

Here is working version of Google Chrome on old computer....


Google Chrome	20.0.1132.47 (Official Build 144678)
OS	Linux
WebKit	536.11 (@121111)
JavaScript	V8 3.10.8.19
Flash	11.3.31.109
User Agent	Mozilla/5.0 (X11; Linux i686) AppleWebKit/536.11 (KHTML, like Gecko) Chrome/20.0.1132.47 Safari/536.11
Command Line	 /opt/google/chrome/google-chrome --flag-switches-begin --enable-sync-tabs --flag-switches-end
Executable Path	/opt/google/chrome/google-chrome
Profile Path	/home/pat/.config/google-chrome/Default



I checked back on the older post and the Google Chrome version on the 2007
machine is the same 20.0.1132.47 version.


I actually removed Google Chrome from the old 2003 machine and then re-installed it.
And it still works great! I'm afraid that if I allow updates on the 2003 computer, it will disable my Chrome browser also.

Thank you for your time

Pat L.

---

### Post by gabmuks on 2012-07-08
Hello and good day.

Here is new symptom....

[COLOR=Black]When I try to open any browser on the 2007 computer,
a dialog box pops up and says....
[/COLOR]
[COLOR=Navy]"Enter Password For Keyring 'default' To Unlock."
"An application wants access to the keyring 'default' but it is locked."[/COLOR]

What is keyring 'default' ?
Why has this never been required before on either computer?

Thank you for your time.

---

### Post by gabmuks on 2012-07-08
I just tried this out of desperation. Found it on Launchpad questions.
[COLOR=Blue]
[actionparsnip (andrew-woodhead666)]("https://launchpad.net/%7Eandrew-woodhead666")[/COLOR] [COLOR=Blue]          said     on 2010-12-14:                  #1               sudo apt-get --purge remove flashplugin-nonfree flashplugin-installer; sudo apt-get -clean; sudo apt-get update; sudo apt-get install mozilla-plugin-gnash
 You will then be using Gnash[/COLOR]

Also installed browser-plugin-lightspark because it was suggested on Terminal.
I was able to see Youtube after that, which is an improvement, but other things
like the little advertisements that play next to my email are blinking and corrupted.
The blinking is the most annoying.

***UPDATE:***
Actually after starting up the computer the next day, Chrome would not load.

[COLOR=Green]_***So I am sorry to say  that installing Gnash didn't really solve the problem.***_[/COLOR]

---

### Post by gabmuks on 2012-07-12
Hello and good day.

I just found this fix on a site that vasa1 had posted.
I would like to try this fix.
Could someone walk me through the steps?
Thank you for your time.




Comment  76  by    [akox_...@yahoo.com]("https://code.google.com/u/116886491786565277348/"),  Today (5 hours ago)   first sorry my english first this my solution 1- go to the [http://get.adobe.com/tr/flashplayer/otherversions/](http://get.adobe.com/tr/flashplayer/otherversions/) select ur version and download rpm files i download this one "[http://get.adobe.com/tr/flashplayer/completion/?installer=Flash_Player_11.2_for_other_Linux_(.rpm)_64-bit]("http://get.adobe.com/tr/flashplayer/completion/?installer=Flash_Player_11.2_for_other_Linux_%28.rpm%29_64-bit")" 2-open with archive manager and goto /./usr/lib64/flash-plugin/ and extract libflashplayer.so and rename "libgcflashplayer.so" 3-then open terminal sudo nautius first then goto the '/opt/google/chrome/' and copy renamed libgcflashplayer.so 4-if not work goto the "chrome://plugins/" than advanced settings and if active flash version 11.3.31.115 disable it 5-done this is work 12.04 ubuntu cheers

---

### Post by vasa1 on 2012-07-12
You have a 64-bit CPU?

The Flash story seems to be different for 32-bit and 64-bit. I have no knowledge of 64-bit :(

---

### Post by gabmuks on 2012-07-12
Thank you for kind reply.

I only have 32 bit.

---

### Post by vasa1 on 2012-07-12
Comment 76 by akox_...@yahoo.com, Today (5 hours ago) first sorry my english first this my solution 1- go to the [http://get.adobe.com/tr/flashplayer/otherversions/](http://get.adobe.com/tr/flashplayer/otherversions/) select ur version and download **rpm** files i download this one "http://get.adobe.com/tr/flashplayer/completion/?installer=Flash_Player_11.2_for_other_Linux_(.**rpm** )_**64-bit**" 2-open with archive manager and goto /./usr/**lib64**/flash-plugin/ and extract libflashplayer.so and rename "libgcflashplayer.so" 3-then open terminal sudo nautius first then goto the '/opt/google/chrome/' and copy renamed libgcflashplayer.so 4-if not work goto the "chrome://plugins/" than advanced settings and if active flash version 11.3.31.115 disable it 5-done this is work 12.04 ubuntu cheers

Note rpm and 64-bit.

---

### Post by gabmuks on 2012-07-12
Sorry for mistake.

I read somewhere that problem might be due to my old AMD  Athlon processor.

And that using older Google Chrome Version 19 would work on older machine.

Do you know where I could get Google Chrome Version 19?

Thank you for your  time.

---

### Post by gabmuks on 2012-07-12
Also read that using older flash-player version 10 might work on AMD Athlon machines.

I have found and downloaded Flash-player Version 10, but I do not know how to install
via terminal.

---

### Post by vasa1 on 2012-07-12
> **gabmuks said:**
> Sorry for mistake.

I read somewhere that problem might be due to my old AMD  Athlon processor.

And that using older Google Chrome Version 19 would work on older machine.

Do you know where I could get Google Chrome Version 19?

Thank you for your  time.

I have seen quite a few posts asking for how to revert to an older version of Chrome.
A couple of points:
My feeling is that Chrome will not, in future versions, support the CPUs that are currently not supported for Pepper Flash functionality.
If correct, would that would mean staying on version 19 and not updating and ignoring the fact that there are security updates to most Chrome versions?
In other words, one would be using an insecure browser for the purpose of having a functional Flash?

I suggest a workaround which would allow a person to use the latest version of Chrome and have a version of Flash that will receive security patches from Adobe for the next few years:
Install **flashplugin-installer** with ```
sudo apt-get install flashplugin-installer
``` or **preferably** get it from the Ubuntu Software Center where it is called **Adobe Flash plugin**. That will fetch and install the other Flash plugin for you. Read the USC page carefully:

> **Downloads and Installs the Adobe Flash Player plugin**. The Adobe Flash Player plugin supports playing of media and other dynamic content online.
...
WARNING: Installing this Ubuntu package causes the Adobe Flash Player plugin to be downloaded from the Adobe web site. The distribution license of the Adobe Flash Player plugin is available at [www.adobe.com](www.adobe.com). Installing this Ubuntu package implies that you have accepted the terms of that license.


Once the download is done, ~ 13 MB, you should start Chrome and Flash should work.

All the best.

---

### Post by gabmuks on 2012-07-12
Thank you for kind reply vasa1.

I installed Chrome then the code: sudo apt-get install flashplugin-installer.

I thank you for trying to help. I think it is a shame that the older machines with the Athlon processors like mine will no longer
function well with newer flash-player. Not all of us can afford
to buy newer machines. And the old ones are still useful
for most applications.

I guess I will give up my quest now.
Thank you for your time.

---

### Post by vasa1 on 2012-07-12
> **gabmuks said:**
> Thank you for kind reply vasa1.

I installed Chrome then the code: sudo apt-get install flashplugin-installer.

I thank you for trying to help. I think it is a shame that the older machines with the Athlon processors like mine will no longer
function well with newer flash-player. Not all of us can afford
to buy newer machines. And the old ones are still useful
for most applications.

I guess I will give up my quest now.
Thank you for your time.
You did not mention whether that worked or didn't work for you :)
That, to me, is the part most relevant to _this_ thread.
The other comments, while absolutely true, may be better off in a thread devoted to keep older machines going and many of us do have older machines to take care of.

---

### Post by gabmuks on 2012-07-13
Sorry for mistake.

I could see no improvement for flash-player.

I followed your suggestions.

Installed new Ubuntu 12.04.

I then installed Google Chrome.

Then in terminal...sudo apt-get install flashplugin-installer.

Did I miss something?

Thank you for kind reply.

---

### Post by vasa1 on 2012-07-13
> **gabmuks said:**
> Sorry for mistake.

I could see no improvement for flash-player.

I followed your suggestions.

Installed new Ubuntu 12.04.

I then installed Google Chrome.

Then in terminal...sudo apt-get install flashplugin-installer.

Did I miss something?

Thank you for kind reply.
When you entered "sudo apt-get install flashplugin-installer" what happened then? What did you see in the terminal?

---

### Post by vasa1 on 2012-07-13
Also, since you installed Ubuntu 12.04, did you install restricted packages and codecs?

---

### Post by vasa1 on 2012-07-13
Can you put up a picture of this and of the tab in red? Make sure you enlarge the window vertically to show all the items.

---

### Post by gabmuks on 2012-07-13
liz@liz:~$ sudo apt-get install flashplugin-installer
[sudo] password for liz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
liz@liz:~$ 

[ATTACH]221193[/ATTACH]

---

### Post by gabmuks on 2012-07-13
[attach]221194[/attach]

---

### Post by vasa1 on 2012-07-13
> **gabmuks said:**
> liz@liz:~$ sudo apt-get install flashplugin-installer
[sudo] password for liz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
liz@liz:~$ 

I meant **your** picture of the corresponding tab! Sorry for not being clear :(

---

### Post by vasa1 on 2012-07-13
> **gabmuks said:**
> liz@liz:~$ sudo apt-get install flashplugin-installer
[sudo] password for liz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
liz@liz:~$ 
...
Okay.

Now type **about : plugins** without leaving any spaces in your Chrome browser address bar and hit enter. A tab will open showing the plug-ins that Chrome sees. Look on the right-hand side for the word details and next to the word will be a - sign or a + sign. If it's a + sign click on that to get a detailed view. Now search for the part dealing with Flash. Do you see anything like the picture I put up? Please post what you see in your browser.

---

### Post by gabmuks on 2012-07-13
[attach]221198[/attach]

---

### Post by vasa1 on 2012-07-13
So you should be able to view Flash according to that last pic. It's enabled. What happens when you go to YouTube?

Are you by any chance blocking javascript or do you have some extensions that could be blocking Flash from running?

If you open Chrome incognito (shift+control+N), can you view Flash videos?

---

### Post by vasa1 on 2012-07-13
I just noticed that you have a couple of plug-ins enabled that may not be necessary and may even be problematic.

Please disable all the plug-ins except for the Flash one. You can enable them later on.

---

### Post by vasa1 on 2012-07-13
Also, type **about:** in the address bar and hit enter. Then copy paste that stuff here.
Mine looks like this:
```

Google Chrome	20.0.1132.57 (Official Build 145807)
OS	Linux
WebKit	536.11 (@122148)
JavaScript	V8 3.10.8.20
Flash	11.3.31.115
User Agent	Mozilla/5.0 (X11; Linux i686) AppleWebKit/536.11 (KHTML, like Gecko) Chrome/20.0.1132.57 Safari/536.11
Command Line	 /usr/bin/google-chrome -start-maximized --flag-switches-begin --enable-sync-tabs --flag-switches-end
Executable Path	/opt/google/chrome/google-chrome
Profile Path	/home/vasa1/.config/google-chrome/Default
```

---

### Post by gabmuks on 2012-07-13
[ATTACH][ATTACH]221200[/ATTACH][/ATTACH]

I have added no extensions or manipulated this Ubuntu install
or this Chrome install in any way.

Except for what you have instructed me in terminal.


I have shown Incognito also.

---

### Post by gabmuks on 2012-07-13
Google Chrome	20.0.1132.57 (Official Build 145807)
OS	Linux
WebKit	536.11 (@122148)
JavaScript	V8 3.10.8.20
Flash	11.2 r202
User Agent	Mozilla/5.0 (X11; Linux i686) AppleWebKit/536.11 (KHTML, like Gecko) Chrome/20.0.1132.57 Safari/536.11
Command Line	 /opt/google/chrome/google-chrome --flag-switches-begin --flag-switches-end
Executable Path	/opt/google/chrome/google-chrome
Profile Path	/home/liz/.config/google-chrome/Default


I don't know why the smiley face shows there.
I did not add anything.

---

### Post by gabmuks on 2012-07-13
[ATTACH]221201[/ATTACH]


Everything disabled but flash-player

---

### Post by vasa1 on 2012-07-13
Did you click on the little jigsaw piece? What happens when you click on it?

---

### Post by gabmuks on 2012-07-13
[ATTACH]221202[/ATTACH]

I clicked on puzzle piece. It says "Can't load plugin."

---

### Post by vasa1 on 2012-07-13
> **gabmuks said:**
> ...I don't know why the smiley face shows there.
I did not add anything.

Oh, at last something I can answer :)

I used the code tag so when I put something within code tags it looks like ```
(@122148)
```but having it as "plain" text causes the 8 followed by ) to be interpreted as a smiley.

It's a practical joke that the forum software plays on unsuspecting people. That's why I asked you to enter **about : plugins** without spaces. If : and p are together without a space you'd see another smiley.

---

### Post by vasa1 on 2012-07-13
> **gabmuks said:**
> 
I clicked on puzzle piece. It says "Can't load plugin."

Okay, I give up. I can't see anything wrong with your set-up and I'm out of ideas :(.

---

### Post by gabmuks on 2012-07-13
Thank you for your efforts vasa1.

And good day to you.

Best regards

Pat L.

---

### Post by vasa1 on 2012-07-17
Posts by AWB70 [here]("http://productforums.google.com/forum/#!category-topic/chrome/linux/UVGRyv50t0E") give the impression that the newer Flash versions whether from Google or from Adobe will not support older computers. You can go through that longish thread in case you haven't already.

---

### Post by gabmuks on 2012-07-17
Thank you for kind reply vasa1.

Yes that thread is helpful for those of us with some of the
older affected CPU's.

I also noted from AWB70's post that our older CPU's do not
exhibit the flash-player problem if Windows OS is used.
It seems to be a problem associated with the Linux OS.

Is that correct?

---

### Post by BoogeyOfTheMan on 2012-07-17
What other browsers have you tried?

---

### Post by gabmuks on 2012-07-17
> **BoogeyOfTheMan said:**
> What other browsers have you tried?

I had always used Firefox browser until flash-player with Firefox would no longer function.

That is the only reason I switched to Chrome in the first place.

The Chrome with flash-player worked great until a recent Ubuntu update.

That has been my experience anyway. Whether that is the real reason for the
flash failure, I do not know. I am still learning.

I have tried switching back to Firefox, but Firefox still does not
work with flash-player. Installing Gnash will allow some sights
to display. But I like to watch the news clips and Gnash wont work with many of the news clips.

Thank you for your time.

---

### Post by BoogeyOfTheMan on 2012-07-17
Have you tried installing 12.04 from scratch, not an upgrade?

Or any other browsers? Opera, Konquerer, etc?

---

### Post by gabmuks on 2012-07-17
> **BoogeyOfTheMan said:**
> Have you tried installing 12.04 from scratch, not an upgrade?

Or any other browsers? Opera, Konquerer, etc?

Yes. If you have time to read earlier parts of this thread,

you will see that all attempts to correct problem have so far failed.

---

### Post by vasa1 on 2012-07-17
> **gabmuks said:**
> ...

I also noted from AWB70's post that our older CPU's do not
exhibit the flash-player problem if Windows OS is used.
It seems to be a problem associated with the Linux OS.

Is that correct?
That is the impression I got from the post. I can't say whether it is correct or not, because I don't have access to such a system. But the poster seems to have looked into the matter in great detail and I'm inclined to go along with what was said.

---

