---
title: "Network Problem"
date: 2011-01-02
forum: General Help
---

### Post by TheMaker on 2011-01-02
Hi all.
I have just installed Ubuntu 10.10 and everything was fine , network (Wireles) worked.
Then i restarted computer and the sign ,up on the panel missed (This sign : [IMG]http://img87.imageshack.us/img87/4164/signzf.png[/IMG]) What is the problem ? 

Please HELP ! Thanks.

---

### Post by TheMaker on 2011-01-02
ANYBODY ??? !! PLease:confused::confused::confused::confused::confused:

---

### Post by WlaadDyaab on 2011-01-02
> **TheMaker said:**
> ANYBODY ??? !! PLease:confused::confused::confused::confused::confused:

Hi

I had a problem exactly like you:) Lol

Laptop: HP ProBook 4510s
Wireless card: Broadcom....

(I don't know, but maybe one of the two things I mentioned might help you or someone else looking at this thread)

I seen one of the threads here on Ubuntuforums.org, it mentioned something about a problem with one of the Firefox Plugins (I was obviously using another computer in my house that had Internet access)

...etc

Conclusion

I re-installed Ubuntu 10.10, just like in your case; wireless card working at first and when I restarted the Laptop the wireless connection stopped working

So I re-installed Ubuntu 10.10 (for like the third time or something), uploaded the updates but NEVER opened Firefox, and clicked on Applications then Ubuntu Software Centre and downloaded Chromium web browser

Up to now the wireless Internet is working fine for me :)

I hope that also works with your Laptop/Computer

(Don't worry about what I said (about me re-installing Ubuntu 3 times), all you need to do is re-install Ubuntu 10.10 once - that's how it worked with me anyways)

---

### Post by Vigh on 2011-01-02
you probably accidentally deleted the top menu- network applet, no need to reinstall ubuntu just right click the top menu bar, click add to panel, indicator applets, add, that should fix it

---

### Post by TheMaker on 2011-01-03
Thanks , but nothing worked so i find this :
sudo iwconfig wlan0 essid "Your Network name"
sudo pon dsl-provider

Then :
sudo pppoeconf

---

