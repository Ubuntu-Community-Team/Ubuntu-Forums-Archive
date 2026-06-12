---
title: "DELL XPS 1530 running Ubuntu 10.04 cannot connect to Dell BH200 Bluetooth headset"
date: 2010-06-23
forum: General Help
---

### Post by godplayer on 2010-06-23
Hello,

 I am running Ubuntu 10.04 in my Dell Xps 1530. I was using BH200, dell bluetooth headset, with windows 7. I had no luck connecting the same headset with the ubuntu karmic and neither can I do it after upgrading to 10.04. 

 I have gone through a lot of the stuff given in many forums. But all of that is for jaunty(ubuntu 8) or before !! 

 Can anyone help me !! Please. 

 By the way : " [http://forums.overclockers.com.au/showthread.php?t=780054](http://forums.overclockers.com.au/showthread.php?t=780054) " is where I found a work around .. but could not get this to work either. Someone with XPS1530 says that he got the headset to work ... but cant reach him !!

---

### Post by godplayer on 2010-06-28
Update: I have found a way out of this problem ... and it is called blueman. I was using the inbuild bluez for connecting my headset. But once I got blueman, which is available by apt-get or in the package manager, installed and all is fine now. Infact the connection is faster than it is in windows 7 ... 

 NB: I was having the same problem in karmic also. So, maybe this will work for that also !!

---

### Post by marianom on 2010-07-05
Hi there godplayer. I'm more on less on the same situation you were so I hope you can help me. I'm using the same headphones with XPS M1330. I can get them connected with blueman but they only remain connected for a few seconds and then the headphones just turn off (I don't even have time to press play).
Did you have this problem? How did you fix it? Can you share your configuration?

TIA,
Mariano

---

### Post by godplayer on 2010-07-06
Well, I am not exactly the ubuntu geek .. infact, I am a noob. But what I did was just routine .. that is uninstall all the bluetooth related stuff from my system first .. then, I put in only blueman .. and its dependencies .. Then it was working alright .. 

 If that is not working, I had first got it working following the steps as given in the two links  : 

 [http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html)

[http://blueman-project.org/forum/viewtopic.php?f=5&t=5&sid=92f8775388fe6ca0d9155cd416a715f3&start=10](http://blueman-project.org/forum/viewtopic.php?f=5&t=5&sid=92f8775388fe6ca0d9155cd416a715f3&start=10)

 Hope you can follow them and remember when it says, reboot, you better reboot !! These tuts will get your headset working for sure, but you will need to run the two commands everytime you restart. The bluman thingy had no such trouble.   

 Hope, this helps you.

---

### Post by marianom on 2010-07-06
Thanks for your followup, I really appreciate it. 
Actually I have them working: the thing is that I was selecting them as Headset service and not as Audio Sink. As audio sink they work ok, I can listen to music with rhythmbox and movies in Totem and all keys work ok. But if I select them as Headphone Service (to answer a call in Ekiga, for example) they turn off in seconds.
Do you use it for music or are you able to use them for call too?

---

### Post by godplayer on 2010-07-06
Hmm .. okay, I have also not been able to get it working in the headphones mode. I dont usually make calls using BH200, I use it mostly with my laptop. 

 Another bit is that I have not been able to get the function buttons on the headset to work either. 

 But, as much as I am aware, no one has been able to do the above stuff .. Say about moving with the crowd ;)

---

### Post by marianom on 2010-07-06
Sorry to say this but all buttons worked out of the box for me (once I got the HS working of course). BTW, your advice about rebooting hit the bull's eye: blueman is accepting both headset service and audio sink so I can listen to calls. The only thing that's not working is the mic (I might conclude that actually I'm getting the call through the audio sink but at least HS are not turning off as soon as I start the headset service). I have one mic integrated in my laptop so I can still talk without taking off the HS although I have to stay on the mic's range so folks can hear me.
Let me know if I can assist you to make your buttons work.

---

### Post by godplayer on 2010-07-07
Hmm .. good to know that all the buttons are working for you  \\:D/. I have the volume buttons working, but the play/pause and next and back buttons are not working ... 

 And since I have actually moved back to windows 7, due to the less power consumption factor, I am not really worried about it any longer. All my interests is, as they say, purely educational  !! Thanks for your help though, hope I can reserve it for another time :).

---

### Post by Nightfly24 on 2010-09-11
High all,
I have setup the blueman on ubuntu 10.4 and my dell bh 200 gets paired with blueman. After that I select the audio sync(a2dp) option. Now,when I play audio I am not getting any sound.... are there some additional steps to do to get it working with a2dp?...

---

### Post by godplayer on 2010-09-11
I hope you selected audio sink !! 

 Then you have to pair the headphones and then go to the sound preferences of the ubuntu and select your headphones as the playback device .. you might have to do this selection everytime you connect the headphone ..

---

