---
title: "Help: Sun Java VM?"
date: 2012-10-08
forum: General Help
---

### Post by mwurch on 2012-10-08
Hello everyone,
I just installed ubuntu 11.04(because 12.04 was very slow on my laptop) and I didn't partition or anything. So I erased the windows 7 os that I had before. Well, I need to do my chemistry homework on a site called, [www.aleks.com](www.aleks.com) and they require a certain plug-in for it to run. But I called them and asked them for help to install this plug-in with linux. They got very skittish and basically they told me, " we can direct you to a site that might help, but since we do not officially support linux, we cannot be of any more help" and that was all. So(sorry this is a long explanation) in the end, I'm a super ubuntu noob and I was wondering if there is a "sun java vm" that I can install? Well this is what the first part of the "help" they gave me said: 

To download manually the plug-in on Linux for Netscape 7.1+, or Firefox 1.0+, or Mozilla 1.6+, you will have to download the ALEKS package file and save it on your computer in the "Java VM lib/ext" directory.

For instance, with the Sun Java VM version 1.4.1, this directory is usually:

/usr/java/j2re1.4.1/lib/ext/




I already have the ALEKS jar package but they say i need Sun Java VM. is it even possible to get in ubuntu?

Thanks for your time! :D

---

### Post by mwurch on 2012-10-08
Ok, I think I know how to do it now, but one last question:

I type in the terminal:
>su root //then I hit 'enter' and it says....
>password  //so I type in my password and hit enter but it says..
>su Authentication Failure //why? I tried it 5 times and it still                                     says that!

---

### Post by mwurch on 2012-10-08
Oh and this is the actual site of the "linux help for ALEKS"

[http://www.aleks.com/downloads/linux_jvm](http://www.aleks.com/downloads/linux_jvm)

---

### Post by mwurch on 2012-10-08
OK I figured it out. If anyone has this problem as well, here is what you do:

1. Download the aleksPack10.jar and put it into your home
2. Open terminal and type this command:
sudo cp aleksPack10.jar /usr/lib/jvm/java-1.6.0-openjdk/jre/lib/ext/
3. Restart browser(I use firefox for ALEKS even though I prefer Chromium for everything else) 

This should work out fine :)

NOTE: this answer was a compilation from advice from 3 different threads but I decided to make a complete list of instructions here because I myself could not find a complete list.

---

