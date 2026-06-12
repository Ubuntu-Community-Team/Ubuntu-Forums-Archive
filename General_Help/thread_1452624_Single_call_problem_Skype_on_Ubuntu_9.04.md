---
title: "Single call problem Skype on Ubuntu 9.04"
date: 2010-04-12
forum: General Help
---

### Post by tlg on 2010-04-12
I am experiencing a problem with Skype (2.1.0.47-1 installed from deb on 9.04) whereby the first call is OK but on subsequent calls the microphone signal is just a loud hissing sound at the other end. This is true for test calls or calls to another machine running Skype.

Quitting and restarting Skype makes no difference, but killing pulsaudio and restarting it fixes the problem for the next call.
     ~$ pkill pulseaudio; sleep 2; pulseaudio -D

Skype is using pulseaudio for both mic and speaker by default. 
Restarting pulseaudio needs to be done after quitting Skype or Skype just dies anyway when you try to make a call.

I've looked through many of the large number of posts devoted to Skype problems on Ubuntu but have not found any mention of this problem. 
I have tested on several different machines running 9.04 with the same result.
I have also tested against both Ubuntu and Windows machines at the other end.

I have also tried installing Skype from here:
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free #Skype
as described in Ubuntu Community page here:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

This is a slightly different version (2.1.0.81-1) and results in the microphone sound always being a hissing noise regardless of first call or restarting pulseaudio.

Any thoughts on diagnostics or a cure would be appreciated.

---

