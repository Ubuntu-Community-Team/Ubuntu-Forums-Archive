---
title: "Skype problems"
date: 2010-09-22
forum: General Help
---

### Post by thefallofroy on 2010-09-22
Just installed Skype and it works fine except for the person I'm chatting with can't see me. My webcam is a built-in Chicony USB 2.0 Camera (/dev/video0) and this is on my Toshiba Satellite laptop. When I go into Skypes options, and click the test button to test the video it works and shows myself in the little window. But like I said the other person cant see me. What should I do? Thanks in advance.

---

### Post by thefallofroy on 2010-09-22
Bump

---

### Post by thefallofroy on 2010-09-23
Aww come on, don't tell me there's nobody else that uses skype...

---

### Post by æøå on 2010-09-23
I had the same problem in the beginning, but then I installed WebcamStudio and then it worked fine.

```
sudo apt-get install webcamstudio
```

---

### Post by thefallofroy on 2010-09-23
I just tried it and it said it couldnt find the package

---

### Post by Vigh on 2010-09-23
I have the exact same webcamera and its working fine. Make sure the room has plenty of light, otherwise the camera will just display night-black. Failing that, try searching for the webcam packages suggested through the synaptic. Although camera is working fine without the packages for me. Sometimes if its not working, make sure lighting is good, turn off video in skype and then turn on again. Usually fixes the problem.

---

### Post by oldsoundguy on 2010-09-23
> **thefallofroy said:**
> I just tried it and it said it couldnt find the package

Same here.

using 10.04

---

### Post by thefallofroy on 2010-09-23
Heres a site that has the debian package, just installed it. I dont know if it fixed it tho 'cause I havent skyped with anyone yet. Worth a try tho, if someone downloads it and it does indeed fix it, please let me know :)

[http://www.ws4gl.org/download/installing-on-ubuntu](http://www.ws4gl.org/download/installing-on-ubuntu)

---

### Post by oldsoundguy on 2010-09-23
> **thefallofroy said:**
> Heres a site that has the debian package, just installed it. I dont know if it fixed it tho 'cause I havent skyped with anyone yet. Worth a try tho, if someone downloads it and it does indeed fix it, please let me know :)

[http://www.ws4gl.org/download/installing-on-ubuntu](http://www.ws4gl.org/download/installing-on-ubuntu)


Well, that was a really weird experience!  Had to kill all processes when the thing was trying to install .. it opened up about 20 install windows.

Reboot did not work so did a fix boot THEN re-booted.

Something wrong with that program!! (really do not think it is Source Forge's fault!

---

### Post by Vigh on 2010-09-23
I could have warned you, in my opinion dont download any packages from any websites. Use the software manager, the synaptic manager in ubuntu, or the official ubuntu packages website, sourceforge being the exception. Other websites are a NO GO! Not trustworthy.

---

### Post by thefallofroy on 2010-09-23
Hmm, terribly sorry it didn't work. It installed just fine for me. Are you using 9.10?

---

### Post by oldsoundguy on 2010-09-23
> **thefallofroy said:**
> Hmm, terribly sorry it didn't work. It installed just fine for me. Are you using 9.10?

As stated before 10.04.  

Have two other 10.04 machines where it works fine.  It is just with this one with a NON STANDARD display (using a Cinema Display) that uses a different than standard resolution, Skype will not even access the web to test.

---

