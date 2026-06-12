---
title: "install weatherbug"
date: 2011-07-24
forum: General Help
---

### Post by waltwin on 2011-07-24
[SIZE=2]I have been searching for many months for a procedure to install Weatherbug onto ubuntu 10.10. I have asked this forum and have received many recommendations one of the most important was to make sure that Gdebi was installed which it was not on my machine.

I found the following procedure that worked for me:

[COLOR=#FF0000][/COLOR]To install weatherbug issue the following command in the terminal window[/SIZE] (**Applications -> Accessories -> Terminal** )
[SIZE=2][COLOR=#FF0000]
[/COLOR][/SIZE][COLOR=#FF0000][INDENT][SIZE=2]sudo apt-get install sun-java5-jre  libswt3.2-gtk-java [SIZE=1][/SIZE][/SIZE][/INDENT][COLOR=#000000][/COLOR][/COLOR][SIZE=2]
To install weatherbug issue the following command in the terminal window 
[/SIZE][INDENT][SIZE=2]wget [http://wdownload.weatherbug.com/linux/weatherbug-1.0-1.deb](http://wdownload.weatherbug.com/linux/weatherbug-1.0-1.deb)[/SIZE][/INDENT][SIZE=2]

[/SIZE][CENTER][SIZE=2]and
[/SIZE][/CENTER]
[SIZE=2]
[/SIZE][INDENT][SIZE=2]sudo dpkg -i weatherbug-1.0-1.deb[/SIZE][/INDENT][COLOR=#FF0000]
[/COLOR][SIZE=2][COLOR=#FF0000] [/COLOR][/SIZE][COLOR=#FF0000]


[/COLOR][SIZE=2][COLOR=#FF0000][COLOR=#000000]After completing the installation you can launch weatherbug from (**Applications -> Accessories -> Weatherbug **)[/COLOR][/COLOR]
[/SIZE]

---

### Post by ctsdownloads on 2011-07-25
> **waltwin said:**
> [SIZE=2]I have been searching for many months for a procedure to install Weatherbug onto ubuntu 10.10. I have asked this forum and have received many recommendations one of the most important was to make sure that Gdebi was installed which it was not on my machine.

I found the following procedure that worked for me:

[COLOR=#FF0000][/COLOR]To install weatherbug issue the following command in the terminal window[/SIZE] (**Applications -> Accessories -> Terminal** )
[SIZE=2][COLOR=#FF0000]
[/COLOR][/SIZE][COLOR=#FF0000][INDENT][SIZE=2]sudo apt-get install sun-java5-jre  libswt3.2-gtk-java [SIZE=1][/SIZE][/SIZE][/INDENT][COLOR=#000000][/COLOR][/COLOR][SIZE=2]
To install weatherbug issue the following command in the terminal window 
[/SIZE][INDENT][SIZE=2]wget [http://wdownload.weatherbug.com/linux/weatherbug-1.0-1.deb](http://wdownload.weatherbug.com/linux/weatherbug-1.0-1.deb)[/SIZE][/INDENT][SIZE=2]

[/SIZE][CENTER][SIZE=2]and
[/SIZE][/CENTER]
[SIZE=2]
[/SIZE][INDENT][SIZE=2]sudo dpkg -i weatherbug-1.0-1.deb[/SIZE][/INDENT][COLOR=#FF0000]
[/COLOR][SIZE=2][COLOR=#FF0000] [/COLOR][/SIZE][COLOR=#FF0000]


[/COLOR][SIZE=2][COLOR=#FF0000][COLOR=#000000]After completing the installation you can launch weatherbug from (**Applications -> Accessories -> Weatherbug **)[/COLOR][/COLOR]
[/SIZE]

Yeah, the project is defunct as there has been hope by yours truly that we'd see the Linux community build something up around the WeatherBug API. GTK, Qt, whatever works and has its code available to the community.

WeatherBug is actively seeking a new (non-Java) based alternative to be created by the community. They offer a fantastic API and have had examples during API contests built with Python.

Anyone looking to step up to the challenge, willing to take the WeatherBug API for a spin, feel free to PM me here for details. I cannot post anything related to it here as I don't wish to spam, but you can Google "WeatherBug API" and then PM for further details if you like. ;)

Disclosure: I happen work closely with the parent company and would desperately love to see a community project around the API. Evidence of this can be provided to any interested developers via a PM to my user account. Would be in appropriate to post my email, etc, to an open thread.

Also, the Java app "sort of" works with 11.04, although not officially. Reason being it runs really poorly and it sends the CPU into fits with every mouse click. :(

---

