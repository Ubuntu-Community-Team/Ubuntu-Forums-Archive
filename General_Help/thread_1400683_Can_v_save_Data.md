---
title: "Can v save Data"
date: 2010-02-07
forum: General Help
---

### Post by CatchItBaby on 2010-02-07
This is my First time I tried Ubuntu or any Other OS except window 

so i m just confused but after searching throughout net i got some useful points or tricks or method how to install / update data through out ubuntu OS

Problem is that I hv slow internet speed and it take a lot of time in downloading from main site i m considering one example 

Jdownloader 

it take 30 minute in downloading from there main website through some terminal commands and isn't it possible that i can store these software and when next time i tried ubuntu in my laptop or in some other pc i didn't follow same process again 

Suppose in window if i need jdownloader i download them and save in Hard Disk in secure place so next time if  i will format my PC i will install jdownloader from Dump without dowloading again ..
I hope u understand what i mean Plz suggest me how to do :popcorn:

---

### Post by rahilm on 2010-02-07
what are you downloading exactly?

---

### Post by The Cog on 2010-02-07
Any software from the Ubuntu repositories that you download and install with synaptic or apt-get will be stored in /var/cache/apt/archives. You can save it to another drive from there to avoid having to download it again. 

This looks like a useful tutorial:
[http://www.dedoimedo.com/computers/aptitude.html](http://www.dedoimedo.com/computers/aptitude.html)

---

### Post by rahilm on 2010-02-07
so...i take it that u want to save the installer file so you can download them again...
well. it is not that easy with ubuntu. one way was pointed before using /var/cache/apt/archices folder which stores the installer files...other is using synaptic's downloadscript (if you want to use download accelerator)

but overall, these techniques may be easy sometimes and sometimes it'll be a little difficult.
if the applcation you mention has no dependencies, then it will work definitely.. if it has many (like you re installing vlc or amarok) then forget it...

I have the installer file for every single application or upgrade i downloaded, but they become outdated after some time and then you have to force install them which may not be pleasAnt everytime..


anyway, i have another technique of doing it, i'll post it if u want...welcome to ubuntu...this is the only feature of ubuntu that sucks for people who don't have unlimited broadband, for the gifted ones its paradise..(it is kinda paradise for me too, but that's because i am patient enough nd i kno every OS has some bad points)

---

### Post by CatchItBaby on 2010-02-07
Yes , right i hv slow internet connection and Limited bandwidth i was thinking... i will update my laptop from pc but didn't find a way

Plz share Your idea

Thanks

---

### Post by rahilm on 2010-02-07
lets assume that you download things to your PC and want to install them in the laptop...then do:
Update the repositories on you PC..reply if you don't know how to do that

DOWNLOAD:
then open synaptic , and install the required software..but wait...
do it like this...first mark what is to be installed then in the File menu there is an option "Make download script"..
go there and save it someplace, it will create a file that has all the links to the the required packages, then you can do either of these:
1)Double-Click->Run in terminal (make sure the script is in a new folder). It will download automatically.
2)Double-Click->Display . This will open a text file with the links and you can use a download accl.

Install:
once everything is ready, again start synaptic. Then go to File->"Add Downloaded Packages" and go to the folder where u hav downloaded the files..it will install automatically..

Repeat the install part on any PC, laptop etc. You don't need to download everything again.
NOTE:This will work only if all the downloaded files are in the repositories. That's why you should update them in every computer. Its the only part where you require internet connection in that computer

They usually outdate after a while (which is really irritating) and you can't "add downloaded packages" them any longer.

---

### Post by CatchItBaby on 2010-02-08
Thanks :)

---

