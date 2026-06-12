---
title: "Flash Problems"
date: 2010-01-25
forum: General Help
---

### Post by benrufus on 2010-01-25
**Flash Problems** 			
 			 			 		   		 		 		Hi

I am having some problems with flash. Full screen flash is really jumpy and basically unwatchable for example on You Tube. I am using Jaunty 9.04. I have checked to make sure swfdec is not installed, i have tried installing the flash package instead of from the repositories and also tried using flash 9 instead of 10. nothing seems to work. I am using an old Toshiba Amilo but i had the same problems on my girlfriends brand new Sony Vaio W series netbook using 9.10 Karmic. I am trying to get everyone i know to switch to Ubuntu and this is probably the biggest problem i have of persuading them. I have tried using Seamonkey Firefox and Chromium and the problem is the same in all browsers.

The other little problem i have is with Facebook Poker (flash based). In Firefox and Chromium it loads really slowly and then i dont get the list of tables to choose from i can only play if i click the FIND ME A TABLE button. Facebook Poker works perfectly in Seamonkey though.

Any help would be greatly appreciated.

Thanks

Ben

---

### Post by llawwehttam on 2010-01-25
Try using 10.1 from adobe. It works better for me.

---

### Post by benrufus on 2010-02-03
> **llawwehttam said:**
> Try using 10.1 from adobe. It works better for me.
I just been reading that the beta release can completely ruin my system, am i just being naive or is it risky. 

Also does it sort out the problems above. 

I installed 7.04 on my brothers laptop and it all worked great - is there any reason why i shouldnt go back to that?  The thing is im sure that 7.04 came with flash 9 but when i tried to install that on 9.04 after removing flash 10 it was just as bad with audio out of sync, yet the flash 9 worked perfectly on my brothers old 7.04 install!!!!

---

### Post by edanto on 2010-02-03
I'm having similar problems with flash, I see it when I try to play videos from Vimeo.

Tried uninstalling and re-installing from the Ubuntu Software Centre, but it hasn't improved. Grateful to know of any workarounds.

---

### Post by benrufus on 2010-02-03
ive just installed flash 10.1 beta. Facebook poker now works. you tube video is still jumpy full screen and now firefox and swiftfox crash every few seconds when using flash. it also maxes out cpu in a scary way, i know flash does this anyway, but its hammering cpu even more. PLEASE PLEASE HELP!!!!!!!!!!!!

i cannot find  ** libflashplayer.so**  or ** flashplayer.xpt** file in [B] /home/<user>/.mozilla/plugins/ 
[/B]to delete them, in fact i cant find them anywhere on my system, i have disabled the plugin but i dont want to go back to the repository one until i delete this.

---

### Post by benrufus on 2010-02-03
> **llawwehttam said:**
> try using 10.1 from adobe. It works better for me.

> **benrufus said:**
> i just been reading that the beta release can completely ruin my system, am i just being naive or is it risky. 

Also does it sort out the problems above. 

I installed 7.04 on my brothers laptop and it all worked great - is there any reason why i shouldnt go back to that?  The thing is im sure that 7.04 came with flash 9 but when i tried to install that on 9.04 after removing flash 10 it was just as bad with audio out of sync, yet the flash 9 worked perfectly on my brothers old 7.04 install!!!!

> **benrufus said:**
> ive just installed flash 10.1 beta. Facebook poker now works. You tube video is still jumpy full screen and now firefox and swiftfox crash every few seconds when using flash. It also maxes out cpu in a scary way, i know flash does this anyway, but its hammering cpu even more. Please please help!!!!!!!!!!!!

I cannot find  ** libflashplayer.so**  or ** flashplayer.xpt** file in [b] /home/<user>/.mozilla/plugins/ 
[/b]to delete them, in fact i cant find them anywhere on my system, i have disabled the plugin but i dont want to go back to the repository one until i delete this.


io

---

### Post by benrufus on 2010-02-04
bump

---

### Post by benrufus on 2010-02-04
> **benrufus said:**
> ive just installed flash 10.1 beta. Facebook poker now works. you tube video is still jumpy full screen and now firefox and swiftfox crash every few seconds when using flash. it also maxes out cpu in a scary way, i know flash does this anyway, but its hammering cpu even more. PLEASE PLEASE HELP!!!!!!!!!!!!

i cannot find  ** libflashplayer.so**  or ** flashplayer.xpt** file in [B] /home/<user>/.mozilla/plugins/ 
[/B]to delete them, in fact i cant find them anywhere on my system, i have disabled the plugin but i dont want to go back to the repository one until i delete this.

The folder  ** /home/<user>/.mozilla/plugins/  **dosent even seem to exist but that is where adobe tells me its supposed to be in their uninstall pdf. a search gives me nothing and all the help i can find on the internet is about installing it not removing it. 

ive only just put all my data back on it after doing a clean install - dont fancy shipping it back and forth with a little pen drive again!!


PLEASE PLEASE HELP!!!!

---

### Post by 3rdalbum on 2010-02-04
The plugin is probably inside /usr/lib/mozilla/plugins/

Full-screen Flash is jerky and jumpy. It's a known issue that Adobe claims is Linux's fault, but you have to wonder why they're the only Linux software vendor that can't make their program work smoothly in full-screen mode.

If you want to watch Youtube videos in full-screen, you can use Compiz to zoom in; that's what I do (or save the Youtube video and play it in VLC; this can be done by looking in the /tmp directory while the video is fully loaded and on the screen).

---

### Post by benrufus on 2010-02-04
Hi 

I only have** libjavaplugin.so libtotem-cone-plugin.so libtotem-gmp-plugin.so libtotem-mully-plugin.so libtotem-narrowspace-plugin.so nphelix.so and nphelix.xpt** in this folder, im sure it should be here but its not, i cant seem to find it anywhere. Adobe says the files should be **libflashplayer.so**                                                                        
and** flashplayer.xpt** and they should be in **/home/<user>/.mozilla/plugins/**  but i cannot find those files anywhere and the install did not create the** /home/<user>/.mozilla/plugins/** directory.

---

### Post by plucky on 2010-02-04
Open a terminal and ```
locate libflashplayer
``` will tell you where it is installed.

Good Luck

---

### Post by benrufus on 2010-02-04
> **plucky said:**
> Open a terminal and ```
locate libflashplayer
``` will tell you where it is installed.

Good Luck


thanks, yeah it tells me that it is at **/home/ubuntu/.mozilla/plugins/libflashplayer.so**
**ubuntu** being my username but when i look for it in nautilus or nautilus in root mode i cannot see this** .mozilla** folder, any chance you could tell me how to do it in terminal. also what about the **flashplayer.xpt** file. thanks for the help

---

### Post by plucky on 2010-02-04
```
cd /home/ubuntu/.mozilla/plugins/
ls -l
```

When using Nautilus,you have to tick the box that shows hidden files under **View** for the .mozilla folder to show itself.

My flash files are in ```
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

``` in Ubuntu 9.10

Good Luck

---

### Post by benrufus on 2010-02-04
> **plucky said:**
> Open a terminal and ```
locate libflashplayer
``` will tell you where it is installed.

Good Luck


thanks, i managed to deleted the **libflashplayer.so** through the  terminal after finding it using the **locate** command you mentioned, i no longer see the plugin in swiftfox/firefox.[I] 

(i have just downloaded a list of terminal commands, i think it would  be useful to know them!!)[/I] 

but i cannot locate **flashplayer.xpt. **Adobe  says i need to remove this as well to uninstall the 10.1 beta, is it  safe to reinstall the repository 10.0 version without removing this?

cheers

---

### Post by plucky on 2010-02-04
> **benrufus said:**
> thanks, i managed to deleted the **libflashplayer.so** through the  terminal after finding it using the **locate** command you mentioned, i no longer see the plugin in swiftfox/firefox.[I] 

(i have just downloaded a list of terminal commands, i think it would  be useful to know them!!)[/I] 

but i cannot locate **flashplayer.xpt. **Adobe  says i need to remove this as well to uninstall the 10.1 beta, is it  safe to reinstall the repository 10.0 version without removing this?

cheers

Never heard of flashplayer.xpt so cannot help with that.

Good Luck

---

### Post by veggen on 2010-02-04
I had the same problem... I uninstalled and reinstalled both Flash 10 and my browser (Opera) and it generally helped. From what I could gather, Flash acts completely unpredictably across installations. Once, I could get it working under Firefox but not under Opera.

Could someone share their experience with swfdec and/or gnash? Are they viable alternatives?

---

### Post by edanto on 2010-02-07
> **3rdalbum said:**
> 
Full-screen Flash is jerky and jumpy. It's a known issue that Adobe claims is Linux's fault, but you have to wonder why they're the only Linux software vendor that can't make their program work smoothly in full-screen mode.

If you want to watch Youtube videos in full-screen, you can use Compiz to zoom in; that's what I do (or save the Youtube video and play it in VLC; this can be done by looking in the /tmp directory while the video is fully loaded and on the screen).

Thanks for explaining that it's a known issue - but as a new user I'm quite disappointed to discover this problem!  I often want to watch videos in full screen, it's a real pain to know that this isn't something that will work reliably.

Just to give you an indication of how much of a linux amatuer I am, I don't know how to 'use compiz' to zoom in as you mentioned.  The terminal is a complete mystery to me, and I can't find compiz in the menus.... but in the Software Centre it says it's installed.

I'm not asking for detailed instructions (that would be too much trouble) but wanted to explain that something basic like flash not working properly is fairly frustrating for me and it'll be something that I tell people when they ask how my experiment with Ubuntu is going.  Hopefully, I'll learn enough to find a workaround and it'll be a story with a happy, if complicated, ending.

---

### Post by benrufus on 2010-02-10
the **locate libflashplayer** command helped me find the 10.1 beta file i couldnt find and i managed to remove it so i guess the original post is kind of solved..... i ended up doing a fresh install anyway!! 

Yeah this flash thing is really a bit of a pain....

I love Ubuntu open-source but some things just dont work well, i know half the fun is messing around with and tweaking things, but some things dont seem to have a fix, like Flash at the moment!!! 

Oh and Propellerhead Reason on Ubuntu would be great!

Im using Ubuntu because my Mac broke although I did used to run it in a virtual machine. I used it to bring my brothers computer back to life and i keep trying to get my mates to install it on their laptops, my mum is now using it, I Love Ubuntu!!!!... but I have to say when I have the money I will be using a Mac with osx again as my main computer just because it does everything its supposed to when its supposed to. Although I will definately still be playing with Linux in one way or another dual boot with bootcamp or something........

P.S any flash fixes would be great, its stopping me converting people, for most people Ubuntu would be fine if Flash worked properly!!!

P.P.S I cant write messages properly!!!!!!!

---

### Post by rayburn0 on 2010-02-10
I am having a minor problem with Flash 10 and Firefox-3.5.7. I have another computer running Firefox-3.0.5 and Adobe Flash 10 and everything is working fine. 

So far, everything I've seen on the forum refers to fixing flash, but what if it's not flash that is broken?
I was wondering, has anyone tested to see if the offending application isn't Firefox 3.5? 
Has anyone reverted to FF 3.0.5 and had success?

---

### Post by cyberghoser1 on 2010-02-11
Flash problems in linux are well known, a workaround for youtube videos in firefox to play smoothly even in fullscreen, is to install greasemonkey, then google for userscript 50771 (Youtube without flash) and install it, you will then watch youtube videos using totem and videos are way better now, also use flashblock plugin to make surfing better.

---

### Post by benrufus on 2010-03-02
> **cyberghoser1 said:**
> Flash problems in linux are well known, a workaround for youtube videos in firefox to play smoothly even in fullscreen, is to install greasemonkey, then google for userscript 50771 (Youtube without flash) and install it, you will then watch youtube videos using totem and videos are way better now, also use flashblock plugin to make surfing better.



Absolutely Brilliant!!!!!!! Been trying to sort this out for ages.... this is the closest thing to perfect i have seen. Cant seem to move the slider to where i want though... watching the whole video seems only option. But VERY VERY GOOD!!!! Thanks a lot Cyberghoser!!

---

### Post by Bahb on 2010-03-02
> **cyberghoser1 said:**
> Flash problems in linux are well known, a workaround for youtube videos in firefox to play smoothly even in fullscreen, is to install greasemonkey, then google for userscript 50771 (Youtube without flash) and install it, you will then watch youtube videos using totem and videos are way better now, also use flashblock plugin to make surfing better.

just did this, and no luck, still an annoying message "Old Flash? Go Upgrade!" at the top of my screen. anyone have more info?

---

### Post by benrufus on 2010-03-02
> **Bahb said:**
> just did this, and no luck, still an annoying message "Old Flash? Go Upgrade!" at the top of my screen. anyone have more info?


Are you using Flash 10?  Im using 10.0.45.2 and it works great for full screen....

You can get the .deb from Adobe if you dont have it in synaptic

Good Luck

---

### Post by edanto on 2010-03-05
Thanks, that tip really did wonders for Flash playing in Firefox!

If anyone's looking for something cool to watch in flash, MIT have entire lecture courses online now... [http://academicearth.org/](http://academicearth.org/)

---

### Post by benrufus on 2010-03-06
> **edanto said:**
> Thanks, that tip really did wonders for Flash playing in Firefox!

If anyone's looking for something cool to watch in flash, MIT have entire lecture courses online now... [http://academicearth.org/](http://academicearth.org/)
Cool Dude, glad it worked, the Greasemonkey script posted above by cyberghoser1 is great for full screen You Tube as well.... the only thing i can't do in Firefox now is Facebook Poker but that works fine in Seamonkey....

---

### Post by benrufus on 2010-03-23
I haven't marked this post as solved because Flash is still a bit of a pig to use!!  i still cant use poker in Firefox and the Greasemonkey script works really good for full screen video but thats all, you lose all the controls of the You Tube player for example....

These are just 2 of many Flash issues.... I know some of the fun of Ubuntu is constantly tweaking and playing with it, but i think it's about time Adobe sorted this out!!

Flash content is everywhere and we are all using it, it works fine on Mac and Windows so why can't they sort it out for us? 

Seems a bit suspect to me!!! 

Who knows hopefully the new 10.1 will sort it out when it comes out.....

Good Luck with all your Flash problems....!!?*:¿?=%$·!!!!?¿¿¿?

Peace

---

