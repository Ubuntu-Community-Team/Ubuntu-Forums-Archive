---
title: "Help with Atheros wireless"
date: 2009-07-27
forum: General Help
---

### Post by hinesdeal102 on 2009-07-27
Hello everyone, I have searched and searched and still have not found a solution to my problem.  I just bought an Asus K50ij laptop and windows performs horribly with this notebook pretty much due to the slow hard drive and the borked installation of windows from the factory.  Anyway I should start by saying I'm using my neighbors wireless connection and therefore I need to have my wireless working in ubuntu.  I ran the live cd and ubuntu performs beautifully with this notebook, however wireless didn't work...well its more like its just simply not turned on.  Windows device manager detects the wireless card as an Atheros AR9285.  Ubuntu also detects this atheros card which leads me to believe that its just not turned on.  In windows there is a hotkey Fn+F2 to enable/disable wireless.  Now this function is done through a program called wireless console 3 and when the wireless is turned on in windows I get a solid green led for wireless.  In ubuntu up in the corner where the network applet is it shows the bars for wireless but there is an x on them as if wireless is there but disabled.  ifconfig does not mention anything of wlan0 or anything to do with wireless.  So is there simply a way to turn on the wireless card without the use of the hotkeys, or is it more than that?  The hotkeys work for pretty much everything else in ubuntu (sound, brightness, sleep, change display) so yea I'm stumped and I'm desperately in need of a decent stable os.  I don't know what Asus did to this os but it is not smooth or stable, first time using vista 64 so maybe thats why but any help would be greatly apreciated.  Remember for now I'm just going to be running from the live cd until I figure this out so let me know any information you guys need from my part. Oh forgot to mention that this is ubuntu 9.04. Thank you.

---

### Post by t4thfavor on 2009-07-27
In the past I have had laptops disable the radio under Windows, and then I was unable to enable them without booting Windows and telling their software to enable it.


You say there is no mention of wlanX, what does iwconfig tell you?

Check this link, I think theres a fix there.

[http://ubuntuforums.org/showthread.php?t=1179951](http://ubuntuforums.org/showthread.php?t=1179951)

---

