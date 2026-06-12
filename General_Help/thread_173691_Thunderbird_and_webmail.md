---
title: "Thunderbird and webmail"
date: 2006-05-10
forum: General Help
---

### Post by Hoffmann on 2006-05-10
By the way, is it possible to make Thunderbird (on Ubuntu) to access  free webmail systems such as yahoo.com?

---

### Post by adssse on 2006-05-10
Havent done it, but you may look at this...
[http://webmail.mozdev.org/index.html](http://webmail.mozdev.org/index.html)

---

### Post by Omnios on 2006-05-10
[QUOTE=adssse]Havent done it, but you may look at this...
[http://webmail.mozdev.org/index.html](http://webmail.mozdev.org/index.html)[/QUOTE]

 If this works the way it sounds it works it is bleeping amazzing exactly what im looking for if I choose to change my isp to one with linited web mail.

---

### Post by Hoffmann on 2006-05-11
[QUOTE=Omnios]If this works the way it sounds it works it is bleeping amazzing exactly what im looking for if I choose to change my isp to one with linited web mail.[/QUOTE]

Did you test the approach above? Did it work with the Ubuntu Thunderbird?

---

### Post by Omnios on 2006-05-11
Actualy just checked on the page they are for ThunderBird 1.5 only so probably will have to wait till Dapper unless I can 1.5 installed.

---

### Post by Hoffmann on 2006-05-11
[QUOTE=Omnios]Actualy just checked on the page they are for ThunderBird 1.5 only so probably will have to wait till Dapper unless I can 1.5 installed.[/QUOTE]

I have also noticed that. That is the reason I asked you if you already tested it. One more question: I realized that the installation program is a .xpi file. Do you know how to install a program with that kind of format on Ubuntu?

---

### Post by Omnios on 2006-05-11
So far I have managed to get Thunder Bird 1.5 installed using a install script.
Link: This is a Firefox thread but has a install Thunderbird 1.5 script its about half way down.
[http://ubuntuforums.org/showthread.php?t=151179&highlight=thunderbird+1.5]("http://ubuntuforums.org/showthread.php?t=151179&highlight=thunderbird+1.5") 
also it is archived here.
[http://doc.gwos.org/index.php/Install_script_Thunderbird_1.5]("http://doc.gwos.org/index.php/Install_script_Thunderbird_1.5")
[http://doc.gwos.org/index.php?title=Install_script_Firefox_1.5.0.1]("http://doc.gwos.org/index.php?title=Install_script_Firefox_1.5.0.1")
ALso not "DO NOT USE sudo" to run this script firefox will not lauch. Also I recomend using synaptic to install the Ubuntu 1.08 thunderbird first as it is required to install 1.5. I made the mistake of using sudo sh and it took me about an hour to recover my Thunderbird which would not launch because I used sudo. Also If you make the mistake of using sudo use sudo uninatall script followed by a complete removal of the ubuntu thunderbird to recover then repeat above without sudo.

 Also installing the extentions turned out to be a bit of a trick as when I tryed to install the extentions the normal way it tryed to install them in firefox, lol. Anyways I got around this by opening thunderbird and opening the extention window. Then from the website drag and drop the links into the thinderbird extention window.

 Now for testing... I have to set up my email and test this out I will get back to yuo shortly. Also .xpi seems to be a extention format not shure on that though.

---

### Post by Hoffmann on 2006-05-11
[QUOTE=Omnios]So far I have managed to get Thunder Bird 1.5 installed using a install script.
Link: This is a Firefox thread but has a install Thunderbird 1.5 script its about half way down.
[http://ubuntuforums.org/showthread.php?t=151179&highlight=thunderbird+1.5]("http://ubuntuforums.org/showthread.php?t=151179&highlight=thunderbird+1.5") 
also it is archived here.
[http://doc.gwos.org/index.php?title=Install_script_Firefox_1.5.0.1]("http://doc.gwos.org/index.php?title=Install_script_Firefox_1.5.0.1")
ALso not "DO NOT USE sudo" to run this script firefox will not lauch. Also I recomend using synaptic to install the Ubuntu 1.08 thunderbird first as it is required to install 1.5. I made the mistake of using sudo sh and it took me about an hour to recover my Thunderbird which would not launch because I used sudo. Also If you make the mistake of using sudo use sudo uninatall script followed by a complete removal of the ubuntu thunderbird to recover then repeat above without sudo.

 Also installing the extentions turned out to be a bit of a trick as when I tryed to install the extentions the normal way it tryed to install them in firefox, lol. Anyways I got around this by opening thunderbird and opening the extention window. Then from the website drag and drop the links into the thinderbird extention window.

 Now for testing... I have to set up my email and test this out I will get back to yuo shortly. Also .xpi seems to be a extention format not shure on that though.[/QUOTE]

Thanks a lot for the nice hints about installing Thunderbird 1.5 using the script. Yes, after you test the mozdev program for using Thunderbird with Yahoo webmail, please, let me know.

---

### Post by Omnios on 2006-05-11
I already ran into a serios snag, it does not seem to work as a regular user as of yet. I ran Thunderbird as root and installed the extention which seemed to work in root. It adds a webmail option to the accounts wizards / preferences which does not seem to be applied to the regualr user. Also the pop light does not come on when running in regular user. I think im going to have to look in the root files and probably trnasfer some stuff from either root to user of user to root. Anyways im going to play around with it a bit.

---

### Post by Omnios on 2006-05-11
K got it to work in root so far and it looks pretty sweet now to see if we can get it to work in regular user mode

---

### Post by Hoffmann on 2006-05-11
[QUOTE=Omnios]K got it to work in root so far and it looks pretty sweet now to see if we can get it to work in regular user mode[/QUOTE]

That's great! I am keeping my fingers crossed now. :-D

---

### Post by sinkxdie on 2006-05-11
Wait, isn't Yahoo program access restricted without a "plus" account?

---

### Post by Hoffmann on 2006-05-11
[QUOTE=sinkxdie]Wait, isn't Yahoo program access restricted without a "plus" account?[/QUOTE]

I have no idea. I don't know. Probably, the guys from Mozdev are doing the right thing....:confused:

---

### Post by Omnios on 2006-05-12
Well I played around with it abit and got no ware, I think it has to do with the way Thunderbird 1.5 was isntalled. I even tryed adding permitions to the thunderbird files and still nothing. Hopefully it will work in Dapper

---

### Post by Hoffmann on 2006-05-12
[QUOTE=Omnios]Well I played around with it abit and got no ware, I think it has to do with the way Thunderbird 1.5 was isntalled. I even tryed adding permitions to the thunderbird files and still nothing. Hopefully it will work in Dapper[/QUOTE]

I found this program: [http://www.ypopsemail.com/](http://www.ypopsemail.com/)

I didn't download or install it.

Well, I am not sure if the usage of those programs are allowed or not. I am not a lawyer. So, it is best to read the Yahoo license first to check it out if those programs are legitimate for using or not!!!

Hoffmann

---

### Post by Omnios on 2006-05-12
Aperently Yahoo has only did the pop change in the USA well im not in the use and the canadian yahoo mail still seems to support pop. Currently I have MyISP.Yahoo mail but am thinking about changins isp's as my isp is being real idoits in that they raise the speed a little and uped the price of the service way up. I found an isp that is less then there low speed with speeds greater than there high speed lol. Anyways if it came to it I have been using yahoo mail for so long I would pay for a yahoo mail account if it did not have a @yahoo address. 

 Anyways the problem is that the plug in can not change thunderbird with the current set up and requires write privalages to Thunderbird which sseems almost impossible with Thunderbird installed with that script. It should be fairly easy to set up when Dapper comes out. Also its not what service you have that is inportant but rather having the abiltiy to manage your emial online and the ability to download it for achiving. SPan is a minor problem with this approach as you can deleate it before doanloading your email. WIth Yahoo its real simple choose span select all and delete, and problem solved.

---

