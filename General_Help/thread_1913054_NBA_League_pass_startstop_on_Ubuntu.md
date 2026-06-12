---
title: "NBA League pass start/stop on Ubuntu"
date: 2012-01-21
forum: General Help
---

### Post by db579 on 2012-01-21
I have the NBA tv league pass for this year. Trying to watch games on my 64 bit Ubuntu 11.10 laptop results in the feed pausing and playing so often that it is unwatchable almost as if it were constantly buffering.

The feed is absolutely fine on my android phone and windows laptops using the same connection hence I'm assuming this is Ubuntu related. 

The problem occurs in both Chromium and Firefox. YouTube videos and movies play fine. Anybody got any suggestions? Thanks.

---

### Post by Claus7 on 2012-01-21
Hello,

2 quick ones actually:

1) send an email to where you took the league pass and ask them if (other) linux users have any problem.

2) use opera

edit 
and a third one would be: use wine and internet explorer (provided for example that you have problems with firefox from windows...)

Regards!

---

### Post by db579 on 2012-01-21
Thanks for the suggestions, same problem occurs in Opera. have tried emailing the support team but still waiting on a response so was hoping somebody here might have run into this.

---

### Post by NightFoxyarrith on 2012-01-22
League pass worked fine for me. Maybe try reinstalling flash, or using google chrome (as it comes pre-packaged with flash, and I always found that this worked way better than any other flash install on linux). Otherwise, try using 64-bit flash, install it using these commands:
```
sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install flashplugin64-installer 
```

---

### Post by db579 on 2012-01-22
Thanks. Installing 64 bit stable flash fixes this in small screen mode (works fine now) but full screen the frame rate is still low enough to seem noticeably laggy. I'm using the latest fglrx driver from the ati website (11.11 I think) if that helps.

Thanks again for any help solving this.

---

### Post by Claus7 on 2012-01-22
Hello,

I think that this sound as a compiz issue. If I were in your shoes I would try this:
[http://ubuntuforums.org/showthread.php?p=11425057](http://ubuntuforums.org/showthread.php?p=11425057)

My mind did not go to flash issue, because you mentioned that youtube was working ok. In case you want the best configuration about flash for your system you can try flashaid in firefox as well.

Regards!

---

### Post by db579 on 2012-01-22
Hi thanks, my compiz settings are already set up as described in the link you posted and I used have also tried flash-aid. I still have poor full screen performance.

Is there anything else I could try? Thanks again.

---

### Post by NightFoxyarrith on 2012-01-22
You can try disabling hardware accelaration in flash. Just right-click on some flash content, click settings and there should be an option there. The video quality might be a little worse, but it's still pretty nice in my experience.

---

