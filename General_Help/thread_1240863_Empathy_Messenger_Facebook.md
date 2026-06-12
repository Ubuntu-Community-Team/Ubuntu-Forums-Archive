---
title: "Empathy Messenger Facebook"
date: 2009-08-15
forum: General Help
---

### Post by guppygould on 2009-08-15
Hey all! 

Seeing as Empathy is being substituted for Pidgin in Karmic Koala I thought I might as well install get ahead of the game and install it. It's now installed and works really well. However, in my old Pidgin I used to use the Facebook chat plugin quite a lot. I've tried installing the plugin for Empathy by following the instructions posted [here](http://ubuntuforums.org/showpost.php?p=6366218&postcount=8). 

It seems to have installed correctly. I've tried putting my username and password in but it just kicks out "Authentication Error" ever ytime I try to connect. Does anyone know how to fix this or can confirm that it's doing the same for them?

Any help is appreciated,

-Leo

---

### Post by guppygould on 2009-08-16
Bump.

---

### Post by guppygould on 2009-08-17
Bump.

---

### Post by 3rdalbum on 2009-08-17
As far as I know, the only instant messenger that Facebook recommends is Meebo. It supports all the protocols that Pidgin and Empathy do, plus it has official Facebook Chat support.

---

### Post by glroig on 2009-08-20
wget [https://bugs.freedesktop.org/attachment.cgi?id=20810](https://bugs.freedesktop.org/attachment.cgi?id=20810)
sudo mv attachment.cgi?id=20810 /usr/share/telepathy/managers/haze.manager
wget [https://bugs.freedesktop.org/attachment.cgi?id=20811](https://bugs.freedesktop.org/attachment.cgi?id=20811)
sudo mv attachment.cgi?id=20811 /usr/share/mission-control/profiles/bigbrownchunx-facebookim-haze.profile

---

### Post by MTHarden on 2009-08-26
I ran those commands and it does install and my contacts load up for about 2 seconds and then I get a network error and they are gone. Do I need to put something int he advanced --> server field?

---

### Post by Katalog on 2009-08-27
I'd also like to know if anyone has any insight on how to resolve this. I had Facebook working just fine in Empathy until there was an update to telepathy haze today, and now I can't get it to connect anymore. I've removed and re-added my Facebook account, etc. etc. I'm on my way back to re-installing Pidgin real soon. It's turning out to not be worth the hassle.

---

### Post by travnewmatic on 2009-09-02
> **glroig said:**
> wget [https://bugs.freedesktop.org/attachment.cgi?id=20810](https://bugs.freedesktop.org/attachment.cgi?id=20810)
sudo mv attachment.cgi?id=20810 /usr/share/telepathy/managers/haze.manager
wget [https://bugs.freedesktop.org/attachment.cgi?id=20811](https://bugs.freedesktop.org/attachment.cgi?id=20811)
sudo mv attachment.cgi?id=20811 /usr/share/mission-control/profiles/bigbrownchunx-facebookim-haze.profile

yeah i think i know what that guy was talking about.  

whenever i did it, i went to that website in firefox (instead of using wget), and it asked me if i wanted to confirm the security exception.  i did, saved those two files in the proper locations, restarted empathy, added my facebook account, and was up.

worked for me, thanks a lot man!

---

### Post by Katalog on 2009-09-02
> **travnewmatic said:**
> yeah i think i know what that guy was talking about.  

whenever i did it, i went to that website in firefox (instead of using wget), and it asked me if i wanted to confirm the security exception.  i did, saved those two files in the proper locations, restarted empathy, added my facebook account, and was up.

worked for me, thanks a lot man!

Was this on a fresh install of Emapthy? Because I wiped out everything I could think of, reinstalled everything I could think of, and still couldn't get Facebook back working the way it was before. I'm wondering if there's something I missed. I hated having to go back and install Pidgin and set my accounts up all over again, and would really like to get back to using Empathy since it's going to be the default, but I don't know what I'm doing wrong. Maybe I'm just not holding my mouth right. :P I'll probably just wait until the end of October, do a fresh install of Karmic and try again.

---

### Post by andresmh on 2009-09-21
This didn't work for me on Karmic Alpha 6.

---

### Post by dwinks on 2009-09-29
Karmic Alpha 6 doesn't seem to have "/usr/share/mission-control/" folder, so that step fails, and consequently the plugin doesn't work.  Is there somewhere else to copy the second file to in Karmic to get this to work.  Out of all the chat protocols I used in Pidgin, the Facebook chat was by FAR the most common, and I will be quite displeased if it doesn't work in Karmic.  I know I can install Pidgin, but that won't integrate with the log-in/reboot/shutdown menu thing, will it?

---

### Post by CrusaderAD on 2009-10-03
I'm interested in this fix too... 

> sudo mv attachment.cgi?id=20811 /usr/share/mission-control/profiles/bigbrownchunx-facebookim-haze.profile

Doesn't work, no file or directory exists.

---

### Post by chriswyatt on 2009-10-09
[http://live.gnome.org/Empathy/Protocols](http://live.gnome.org/Empathy/Protocols)

I followed the directions here and managed to get Facebook to appear on the list in Empathy (Karmic Koala).  At first nothing happened when I clicked Connect.  I tried it several times and also restarting Empathy and killing mission control a few times as well.  Still no luck.  Then I restarted my PC (as I had installed some updates).  By some stroke of luck when I tried Facebook Chat again, it worked!

\\:D/

---

### Post by hanzomon4 on 2009-10-10
reboot worked here too... Karmic 64bit

---

### Post by talkingwires on 2009-10-14
> **chriswyatt said:**
> By some stroke of luck when I tried Facebook Chat again, it worked!

I can't get this to work. Empathy crashes with a message saying that the Facebook protocol can't be found.

---

### Post by bradshawd on 2009-10-18
> **raptormanad said:**
> I'm interested in this fix too... 



Doesn't work, no file or directory exists.

I am getting the same error message.  That folder or file does not exist

Jaunty Jackelope..  

Hope somebody can help

Derek

---

### Post by dansanti on 2009-11-03
> **chriswyatt said:**
> [http://live.gnome.org/Empathy/Protocols](http://live.gnome.org/Empathy/Protocols)

I followed the directions here and managed to get Facebook to appear on the list in Empathy (Karmic Koala).  At first nothing happened when I clicked Connect.  I tried it several times and also restarting Empathy and killing mission control a few times as well.  Still no luck.  Then I restarted my PC (as I had installed some updates).  By some stroke of luck when I tried Facebook Chat again, it worked!

\\:D/

thanks that work so fine ..

---

### Post by nortexoid on 2009-11-05
I had facebook chat working on my fresh Karmic install but now it doesn't log in. I notice also that by trying to login via Empathy, when I access the Facebook site in a browser I'm asked to log in again. So something odd is going on. Anyone else getting this?

---

### Post by beastrace91 on 2009-11-05
Alot of the connectivity issues are due to Facebook's messaging protocol being so poor. Random connects/disconnects are common using Pidgin, Meebo, or heck even the in browser chat often times. Its largely an issue on their end.

~Jeff

---

### Post by nathanernest on 2009-11-07
Same problem here all, got the protocol installed easily. But now I get "network error". :(
Help us all great gods of ubuntu! :-)

Nath

---

### Post by chriswyatt on 2009-11-07
Make sure it is the latest version of the plugin as there was a protocol change.

---

### Post by nathanernest on 2009-11-08
Thanks! Upgrading from 1.61 to 1.62 fixed it for me.

---

### Post by nucleuskore on 2010-05-06
Those of you still struggling tru this
[http://ubuntuforums.org/showthread.php?p=9211014#5](http://ubuntuforums.org/showthread.php?p=9211014#5)

---

### Post by Melclic on 2010-12-10
Here is an easy fix for all of you that are still struggling with Facebook on empathy. Use Jabber!!!

No need to create an account just choose jabber in the place of facebook chat and fill the Login ID with:

[email]your.username@chat.facebook.com[/email]

and your regular facebook password

---

