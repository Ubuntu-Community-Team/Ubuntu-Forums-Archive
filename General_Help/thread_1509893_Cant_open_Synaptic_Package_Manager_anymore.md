---
title: "Cant open Synaptic Package Manager anymore"
date: 2010-06-14
forum: General Help
---

### Post by steve509 on 2010-06-14
Hello all, I'm running ubuntu 9.10 64 bit. I've been trying to get a .mov file to play with no luck. I came across some directions to download files from the medibuntu repository and I followed the directiond to get medibuntu into synaptic, which i don't know if it worked at all because now i cant open synaptic at all. This is the error message i get. Heres the screenshot:  [ATTACH]160472[/ATTACH]

---

### Post by steve509 on 2010-06-14
PS, Can't open Update manager either...please help

---

### Post by howefield on 2010-06-14
Click the close button on the error dialogue window, then select Settings > Repositories menu option.

Then click the "Other Software" tab, and uncheck the medibuntu repository. Then press the reload button.

That should get you back to where you started, you can then try again to add the medibuntu repository.

You can also download the packages from the Medibuntu site and install the downloaded .deb package.

---

### Post by steve509 on 2010-06-14
When I click on the Close button, synaptic also closes and i can't get to it

---

### Post by howefield on 2010-06-14
In that case, I'd open a terminal and type

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

Enter your password if prompted and fix or comment out with a # sign the offending line. 

Save the file, and try Synaptic again.

---

### Post by steve509 on 2010-06-14
Fantastic, that worked howefield. Thanks so much for both of your inputs

---

### Post by howefield on 2010-06-14
Glad to hear it, if you have any more problems adding the Medibuntu repository, as I said above you can download the packages from

[http://packages.medibuntu.org/karmic/index.html](http://packages.medibuntu.org/karmic/index.html)

Was it the w64codecs you needed ?

Click on the relevant package, then on the relevant package architecture, in your case amd64, then double click the downloaded file to install.

---

### Post by steve509 on 2010-06-14
Yes I think thats what I need. My original problem is that I can't get a .mov file to play in any of the players. I've tried mplayer, and vlc and so far nothing.

---

