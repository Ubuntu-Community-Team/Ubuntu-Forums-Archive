---
title: "Skype issues"
date: 2006-06-10
forum: General Help
---

### Post by boyx on 2006-06-10
Hi, 
I am having trouble with skype. Whenever I make one call, I can hear everything just fine, but after that call is over, I cant make another call until i restart skype. I get an error saying that "call failed". what is the solution for this.

Another question, is it possible to use a bluetooth headset with skype on ubuntu? if so, can anyone tell me how? I can do that on windows.

thanks

---

### Post by thasheep on 2006-06-10
As for your first question, this is a common problem with skype. It is possible to 'fix' it by stuffing around with an asoundrc file but the easiest way is to use a programme called skype-dsp-hijacker. It 'hijacks' the sound in skype and makes it behave. It's in the breezy seveas repositories. Even though it's designed for Breezy, it works fine with Dapper. Add this to /etc/apt/source.list
```
deb http://seveas.theplayboymansion.net/seveas breezy-seveas extras
```Then```
sudo apt-get install skype skype-dsp-hijacker
```The seveas skype package is designed to work with the hijacker so it's better than the skype.com one.

---

### Post by diamand on 2006-09-06
Try the new beta version 1.3-something... download from the official page.

---

### Post by egoldtech on 2006-09-16
the new beta version solve this problem, here.
thanks

---

