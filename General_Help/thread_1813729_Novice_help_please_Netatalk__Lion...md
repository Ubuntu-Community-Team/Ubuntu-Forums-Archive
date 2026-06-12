---
title: "Novice help please Netatalk ? Lion.."
date: 2011-07-28
forum: General Help
---

### Post by Michael Wayne on 2011-07-28
I have had the problem of Lion no longer connecting to my server and getting the "Cant connect to Time machine" dialogue. Now I have seen the post .....
[http://ubuntuforums.org/showthread.php?p=11071171](http://ubuntuforums.org/showthread.php?p=11071171)
and read through it and its sort of where I am at present. I have 2 Mac Minis, one of them has Lion and is in my home/office running Lion and the second is in my lounge mainly as the iTunes player link from my music collection/library stored on the server. It's running Snow Leopard and works perfectly connected to my Pioneer LX82 amp. 
I also have samba running through Ubuntu so I can back up my wifes windows7 work laptop.
I want to simply update the to the Netatalk 2.2 in order for it to work again. I dont quite know what procedure to follow in particular to my Ubuntu version and server type. My server is an HP Proliant with the specs as in my signature. 
Can any Ubuntu Ninjas guide me down the correct path. I am on a steep learning curve so you patience is appreciated.

I also came across the following item which although corrects the issue in Lion it does state that it [COLOR=DarkRed]( disables time machine function on nas )[/COLOR] [COLOR=Black]and I assume that by updating Netatalk to 2.2 this would resolve the issue. (Of course it may not be an issue if Apple releases a fix by allowing user choice to use the pre existing set up).... [/COLOR]Any way read on...
**Quote**
It seems that apple deleted DHCAST128 in Osx lion 10.7
Because they say it's nit secure enough,
Seems that most nas systems use this.
 
This is how to put it back: ( disables time machine function on nas )
 
 
 
Open Terminal
sudo chmod o+w /Library/Preferences
defaults write /Library/Preferences/com.a&#8203;pple.AppleShareClient afp_host_prefs_version -int 1
 
reboot your Mac 
 
Connect to the nas so it can make a profil
 
Open Terminal
sudo  defaults write /Library/Preferences/com.a&#8203;pple.AppleShareClient  afp_disabled_uams -array &#8220;Cleartxt Passwrd&#8221; &#8220;MS2.0&#8243; &#8220;2-Way Randnum  exchange&#8221;
sudo chmod o-w /Library/Preferences
 
Reboot you Mac again
 
Now it should work
 
 To turn it off again: ( default on lion)
 
Open terminal
sudo defaults write /Library/Preferences/com.a&#8203;pple.AppleShareClient afp_disabled_uams -array-add &#8220;DHCAST128&#8243;
**End**
UPDATE...
I followed the instructions and have enabled DHCAST128&#8243; and can now see my NAS.  Also my current version of [COLOR=DarkRed]netatalk[/COLOR] is [COLOR=DarkRed]2.0.3-9_amd64.deb[/COLOR]

Thanks,
Michael

---

