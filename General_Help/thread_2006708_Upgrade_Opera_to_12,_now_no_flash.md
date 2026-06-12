---
title: "Upgrade Opera to 12, now no flash"
date: 2012-06-19
forum: General Help
---

### Post by WildeBeest on 2012-06-19
I was upgraded to Opera 12.0 on the last update. Now the flash plug-in won't load.
I have the last flash. In the proper folder.

Anyone have any ideas?

---

### Post by uylug on 2012-06-19
> **WildeBeest said:**
> I have the last flash. In the proper folder.

What is that supposed to mean? I'm guessing that, in order for flash to work, you need the flashplayer so file to be located under the opera plugins folder.

You might try copying the file from the mozilla plugins one, or doing a reinstall of the flashplugin installer package:

```
sudo apt-get remove flashplugin-installer
sudo apt-get install flashplugin-installer
```

---

### Post by Frogs Hair on 2012-06-19
Try the suggestion  above . I never had to install a separate flash version for Opera on Linux  . After installing flash via Flash Aid in Firefox flash always worked in Opera and I just tested 12 yesterday.  The .macromedia(Flash) folder is independent of the browser folders.

---

### Post by WildeBeest on 2012-06-19
> sudo apt-get remove flashplugin-installer sudo apt-get install flashplugin-installer

Didn't work.

> 
What I meant by"I have the last flash. In the proper folder."
was:I have the latest flash 

When I go to a web site that requires flash, it indicates that flash needs to be installed.

Opera 11.64 was working fine. The update to 12 borked it.

Any over ideas?

---

### Post by Frogs Hair on 2012-06-19
I just downloaded the Opera 12.00 .deb from the site again and tested YouTube and It worked with my current Flash installation .  You could choose to install flash and see what happens.

---

### Post by WildeBeest on 2012-06-20
I've tried installing from there, just hangs.

I'll try the Opera re-install.

---

### Post by Frogs Hair on 2012-06-20
It reads like the path to the flash plugin is not found for some reason. I used Opera as my main browser until recently and have been testing Iron and Chrome and just don't need that many browsers installed.

---

### Post by vasa1 on 2012-06-20
> **WildeBeest said:**
> I've tried installing from there, just hangs.

I'll try the Opera re-install.
I can't understand why you're facing a problem and don't know what to suggest. I installed Opera 12 a couple of days ago and haven't had a problem with Flash on Opera.

If it's of any help, I'm attaching an image.

---

### Post by WildeBeest on 2012-06-21
Re-install didn't work either.

---

### Post by vasa1 on 2012-06-21
> **WildeBeest said:**
> Re-install didn't work either.

Could you put up a list of the plug-ins that Opera sees?

---

### Post by WildeBeest on 2012-06-21
Plug-ins list:
```
 
Shockwave Flash
Description: Shockwave Flash 11.2 r202
Architecture: native
/usr/lib/flashplugin-installer/libflashplayer.soapplication/futuresplash        spl
application/x-shockwave-flash        swf

Adobe Reader 9.5
Description: The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser. 
Architecture: native
/usr/lib/firefox/plugins/npwrapper.nppdf.soapplication/pdf        pdf
application/vnd.adobe.xdp+xml        xdp
application/vnd.adobe.xfd+xml        xfd
application/vnd.fdf        fdf
application/vnd.adobe.xfdf        xfdf

Shockwave Flash
Description: Shockwave Flash 11.2 r202
Architecture: native
/home/willy/.mozilla/plugins/libflashplayer.soapplication/futuresplash        spl
application/x-shockwave-flash        swf

IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 
(6b20-1.9.13-0ubuntu1~10.04.1))
Description: The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)) executes Java applets.
Architecture: native
/usr/lib/mozilla/plugins/libjavaplugin.soapplication/x-java-vm        class,jar
application/x-java-applet        class,jar
application/x-java-applet;version=1.1        class,jar
application/x-java-applet;version=1.1.1        class,jar
application/x-java-applet;version=1.1.2        class,jar
application/x-java-applet;version=1.1.3        class,jar
application/x-java-applet;version=1.2        class,jar
application/x-java-applet;version=1.2.1        class,jar
application/x-java-applet;version=1.2.2        class,jar
application/x-java-applet;version=1.3        class,jar
application/x-java-applet;version=1.3.1        class,jar
application/x-java-applet;version=1.4        class,jar
application/x-java-applet;version=1.4.1        class,jar
application/x-java-applet;version=1.4.2        class,jar
application/x-java-applet;version=1.5        class,jar
application/x-java-applet;version=1.6        class,jar
application/x-java-bean        class,jar
application/x-java-bean;version=1.1        class,jar
application/x-java-bean;version=1.1.1        class,jar
application/x-java-bean;version=1.1.2        class,jar
application/x-java-bean;version=1.1.3        class,jar
application/x-java-bean;version=1.2        class,jar
application/x-java-bean;version=1.2.1        class,jar
application/x-java-bean;version=1.2.2        class,jar
application/x-java-bean;version=1.3        class,jar
application/x-java-bean;version=1.3.1        class,jar
application/x-java-bean;version=1.4        class,jar
application/x-java-bean;version=1.4.1        class,jar
application/x-java-bean;version=1.4.2        class,jar
application/x-java-bean;version=1.5        class,jar
application/x-java-bean;version=1.6        class,jar
application/x-java-vm-npruntime        
application/x-java-applet;jpi-version=1.6.0_20        class,jar
application/x-java-bean;jpi-version=1.6.0_20        class,jar

QuickTime Plug-in 7.6.6
Description: The Totem 2.30.2 plugin handles video and audio streams.
Architecture: native
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.sovideo/mp4        mp4,mpg4
video/quicktime        qt,mov
image/x-quicktime        mov,pict,pict1,pict2
image/x-macpaint        pntg
video/x-m4v        m4v

DivX® Web Player
Description: DivX Web Player version 1.4.0.233
Architecture: native
/usr/lib/mozilla/plugins/libtotem-mully-plugin.sovideo/divx        divx

iTunes Application Detector
Description: This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
Architecture: native
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.soapplication/itunes-plugin        

Windows Media Player Plug-in 10 (compatible; Totem)
Description: The Totem 2.30.2 plugin handles video and audio streams.
Architecture: native
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.sovideo/x-msvideo        avi,asf,wmv
application/asx        asx
video/x-ms-asf-plugin        asf,wmv
application/x-mplayer2        avi,wma,wmv
video/x-ms-wm        wm,wmv
audio/x-ms-wma        wma
video/x-ms-wvx        wvx,wmv
video/x-ms-wmv        wmv,wmx
video/x-ms-asf        asf,asx
video/x-wmv        wmv
video/x-ms-wmp        wmv,wmp
application/x-ms-wms        wms
application/x-ms-wmp        wmp

VLC Multimedia Plugin (compatible Totem 2.30.2)
Description: The Totem 2.30.2 plugin handles video and audio streams.
Architecture: native
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so
```

---

### Post by Frogs Hair on 2012-06-21
You can try the following , but you will have to re-install any themes or extensions and start from scratch. Remove Opera , open home/hidden folders , delete the .opera folder (locate with Ctrl + H) and install Opera again.

---

### Post by vasa1 on 2012-06-21
One difference is that I have ```
/usr/lib/mozilla/plugins/flashplugin-alternative.so
``` You don't. ???

---

### Post by stinkeye on 2012-06-21
I just install the **flash-aid** add-on in firefox.
Update flash using flash-aid in firefox and opera picks it up.

Saying that, when I updated opera to 12.00 flash worked without doing anything. 

Pic shows content of [B]Preferences > advanced > content > plugin options
[/B]

---

### Post by Frogs Hair on 2012-06-22
As above I have used Flash Aid for installation since 10.10 , about the same time as I used Opera for the first time.

---

### Post by WildeBeest on 2012-06-23
I was hoping to avoid that. But it worked.
Thanks for all the help.

---

