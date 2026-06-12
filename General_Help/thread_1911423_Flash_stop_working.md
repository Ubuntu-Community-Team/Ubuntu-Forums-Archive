---
title: "Flash stop working"
date: 2012-01-18
forum: General Help
---

### Post by goldie4042 on 2012-01-18
Has anyone  ever experienced a problem with flash like the picture attached to this  post. It seems as though I started experiencing this problem after an  update earlier today. My browsers will not play any flash video. And I  say browsers because this problem is happening with Chronium and  Firefox. Any help or guidance will be greatly appreciated

---

### Post by Diametric on 2012-01-18
Yeah, that happened to me some time ago.  I can't recall exactly what the issue was, but I do remember following this:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

And after following the instructions, and running some updates, I got it to work.

Good luck!

---

### Post by wojox on 2012-01-18
Is this only Youtube related?

---

### Post by goldie4042 on 2012-01-18
Thanks for the help guys. I actually got it to work again. I read a couple of articles on google telling me how to uninstall flash. So I uninstalled and reinstalled and it started working again. For anyone else that has this problem try this first.

sudo apt-get remove flashplugin-installer
sudo apt-get install flashplugin-installer



I assume that some settings got changed when I updated my system because I did not get the "flash plugin needs to be installed"message or any other error message. The only message or error that I was receiving was the picture above when trying to play flash video.

---

### Post by goldie4042 on 2012-01-19
> **wojox said:**
> Is this only Youtube related?

No this was not only on youtube. This was when using Chromium and Firefox. The odd thing is when I went to some foreign website that I have never been to before (just googled funny video and selected the first result) flash paused for about 3 seconds and then started working again. But that was the only site that it did it for.

---

