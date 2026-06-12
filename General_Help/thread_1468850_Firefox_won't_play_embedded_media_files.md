---
title: "Firefox won't play embedded media files"
date: 2010-05-01
forum: General Help
---

### Post by oldtraveler on 2010-05-01
Using Ubuntu 10.04 LTS and 64 bit.

Trying to play embedded video or audio files in Firefox. Nothing happens.
If I select play with "Movie Player" the file will play. Why can't I get Firefox to do it?

---

### Post by oldtraveler on 2010-05-02
Is this so difficult that nobody has any ideas?

Please.

---

### Post by oldtraveler on 2010-05-03
This problem includes You Tube.  When I try to view You Tube all I get is a black video screen with a message stating "An error occured, please try again later."

---

### Post by sunk8 on 2010-05-03
Definitely a flash issue...
Why dont u install flash plugin from the adobe site...
Do tell if this solves the issue...

---

### Post by oldtraveler on 2010-05-03
Using Synaptic to try to install whatever is missing I keep getting this error message - "E: postfix: subprocess installed post-installation script returned error exit status 75
E: bsd-mailx: dependency problems - leaving unconfigured"

Could this have something to do with the problem?


Since some of the files that will not embed are mp4 files, I question whether flash has anything to do with it. I am trying the adobe flash plugin and get this same error.

---

### Post by sunk8 on 2010-05-03
Ah! Dependency issue...
Go, resolve it in the terminal...
Try sudo apt-get upgrade
The Terminal commands are better than any GUI package manager...

---

### Post by sunk8 on 2010-05-03
Also, do check the software sources before you do that...
Have only the official ones checked...
Some app didn't get installed fully and is creating trouble...

---

### Post by oldtraveler on 2010-05-03
Here is what I get on the "upgrade"

phil@ubuntu10:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up postfix (2.7.0-1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: numeric hostname: 04
newaliases: fatal: file /etc/postfix/main.cf: parameter mydomain: bad parameter value: 04
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
 bsd-mailx
E: Sub-process /usr/bin/dpkg returned an error code (1)
phil@ubuntu10:~$

---

### Post by philinux on 2010-05-03
> **oldtraveler said:**
> Using Ubuntu 10.04 LTS and 64 bit.

Trying to play embedded video or audio files in Firefox. Nothing happens.
If I select play with "Movie Player" the file will play. Why can't I get Firefox to do it?

Working fine here so lets check what you got.
```

sudo updatedb

This updates the locate database with no message returned.

locate libflashplayer.so
```

Post back what locate finds.

Also look in Tools>addons>plugins and tell us what it says for Flash.

---

### Post by oldtraveler on 2010-05-03
> **sunk8 said:**
> Also, do check the software sources before you do that...
Have only the official ones checked...
Some app didn't get installed fully and is creating trouble...

Which ones are "official"?  If listed in Synaptic aren't they official?

How might I tell which app didn't get installed fully and is creating trouble?

---

### Post by oldtraveler on 2010-05-03
phil@ubuntu10:~$ sudo updatedb
phil@ubuntu10:~$ locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
phil@ubuntu10:~$ 



Located the following plugin:

Shockwave Flash

    File: libgnashplugin.so
    Version: 
    Shockwave Flash 10.1 r999. Gnash 0.8.7, the GNU SWF Player. Copyright (C) 2006, 2007, 2008, 2009, 2010 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 10.1 r999.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes

---

### Post by philinux on 2010-05-03
> **oldtraveler said:**
> phil@ubuntu10:~$ sudo updatedb
phil@ubuntu10:~$ locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
phil@ubuntu10:~$ 



Located the following plugin:

Shockwave Flash

    File: libgnashplugin.so
    Version: 
    Shockwave Flash 10.1 r999. Gnash 0.8.7, the GNU SWF Player. Copyright (C) 2006, 2007, 2008, 2009, 2010 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 10.1 r999.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes

Got to synaptic and mark for complete removal gnash and flashplugin-installer.

Go here and download the 64 bit plugin.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Right click to Extract here. Inside the archive is libflashplayer.so

Move or copy this file to ~/.mozilla/plugins

You have to create the plugins directory first.

Restart Firefox.

---

### Post by oldtraveler on 2010-05-03
Some additional puzzling info.

The following URL contains embedded video which does play - except for having the sound muted.  All I needed to do was increase the volume.  Why does this default to no volume?

[http://philsden.com/09/entertainment132.html](http://philsden.com/09/entertainment132.html)

---

### Post by oldtraveler on 2010-05-03
Removed gnash and flashplugin-installer

Extracted libflashplayer.so to my desktop since I don't know where the ~/.mozilla/plugins folder is or how to create it.

---

### Post by sunk8 on 2010-05-03
> **oldtraveler said:**
> Extracted libflashplayer.so to my desktop since I don't know where the ~/.mozilla/plugins folder is or how to create it.

Copy it here:
usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by philinux on 2010-05-03
> **oldtraveler said:**
> Removed gnash and flashplugin-installer

Extracted libflashplayer.so to my desktop since I don't know where the ~/.mozilla/plugins folder is or how to create it.

Open Places>Home Folder then ctrl+h to view hidden files. (Those stating with a dot.)

Navigate to .mozilla open that, right click and create folder plugins.

If you are the only user then it will do there.

If there are more users then the place to put it is in here.
usr/lib/mozilla/plugins/

---

### Post by oldtraveler on 2010-05-03
Found the mozilla/plugins folder.  Moved the libflashplayer.so into it.  Also there is a libnpjp2.so file in there.  Do I leave it or delete it?

---

### Post by Taus on 2010-05-03
not sure what exactly your problem is, but i had trouble clicking control objects in flash such as play, stop pause etc

i noticed that i could work it around by holding down the right mousebutton on the flash object and then left click the flash button i wanted to click while still holding down the right mouse button.

i then found out i could completely fix it by doing this from the terminal:

sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this before the last line of text “export GDK_NATIVE_WINDOWS=1&#8243;, then save and restart the application that uses flash.

it worked for me  this is only for 64 bit version of ubuntu. I hope it works for you as well..

cheers

---

### Post by philinux on 2010-05-03
> **oldtraveler said:**
> Found the mozilla/plugins folder.  Moved the libflashplayer.so into it.  Also there is a libnpjp2.so file in there.  Do I leave it or delete it?

Leave it for now.

---

### Post by oldtraveler on 2010-05-03
Now all I get at You Tube is a blank white video window.  No more error message.  No nothing.

---

### Post by oldtraveler on 2010-05-03
> **Taus said:**
> not sure what exactly your problem is, but i had trouble clicking control objects in flash such as play, stop pause etc

i noticed that i could work it around by holding down the right mousebutton on the flash object and then left click the flash button i wanted to click while still holding down the right mouse button.

i then found out i could completely fix it by doing this from the terminal:

sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this before the last line of text “export GDK_NATIVE_WINDOWS=1&#8243;, then save and restart the application that uses flash.

it worked for me  this is only for 64 bit version of ubuntu. I hope it works for you as well..

cheers

Now I get the video window with error telling me that I need to download and install the latest Adobe Flash Player.

---

### Post by oldtraveler on 2010-05-03
After installing the flash player I now have You Tube Video.  Hurray!

But Firefox still won't play [http://philsden.com/Howdy02.mp3](http://philsden.com/Howdy02.mp3).  Nor will this now open with "Movie Player"

---

### Post by taminrob on 2010-05-03
I would be interested in a solution for this as well.  I seem to be having the same problem on my 32 bit system.  I can play youtube videos no problem, but when trying to view videos from charter.net all I get is the outline of a player showing a blank screen where the video should play.  What is doubly frustrating, is that I had this problem when I installed (fresh) 10.04 and I did something or other, installed User agent switch I think (though I never changed from default agent), and it fixed it.  Now after about a day and an update of some kind regarding flash from the Update Manager, my system is back to not playing embedded videos.

When trying to view the link above, I get audio, but no video.

---

### Post by Dilutu on 2010-05-03
This link does not work for me neither.(no audio,no vdo).totem tells me "could not determine type of stream". Lucid 32bit here.

---

### Post by oldtraveler on 2010-05-03
> **Dilutu said:**
> This link does not work for me neither.(no audio,no vdo).totem tells me "could not determine type of stream". Lucid 32bit here.

It's odd.  That link ([http://philsden.com/Howdy02.mp3](http://philsden.com/Howdy02.mp3)) works in Windows just fine. Also the file on my Windows partition which was uploaded to make the link  plays in Movie Player in Ubuntu.

---

### Post by oldtraveler on 2010-05-13
> **philinux said:**
> Working fine here so lets check what you got.
```

sudo updatedb

This updates the locate database with no message returned.

locate libflashplayer.so
```

Post back what locate finds.

Also look in Tools>addons>plugins and tell us what it says for Flash.
Here's what I get after using your code in the terminal:

phil@ubuntu10:~$ locate libflashplayer.so
/home/phil/.mozilla/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
phil@ubuntu10:~$ 
 

In tools;addons;plugins it shows Shockwave Flash 10.0 r45

---

### Post by oldtraveler on 2010-05-16
Discovered a partial solution.  I found that when I used the following html coding, the embedded file and player are shown BUT the default volume is muted.  How can I set the default volume to not be muted?
[html]
<html>
<head>
<body>

Test

<OBJECT ID="MediaPlayer1" CLASSID="CLSID:22d6f312-b0f6-11d0-94ab-0080c74c7e95" CODEBASE="http://activex.microsoft.com/activex/controls/mplayer/en/nsmp2inf.cab# Version=5,1,52,701" STANDBY="Loading Microsoft Windows® Media Player components..." TYPE="application/x-oleobject" width="230" height="70">
<PARAM NAME="fileName" VALUE="http://www.wtv-zone.com/Anastasia/Reflections/nightsinwhitesatin.mid">

<PARAM NAME="animationatStart" VALUE="true">
<PARAM NAME="transparentatStart" VALUE="true">
<PARAM NAME="autoStart" VALUE="true">
<PARAM NAME="showControls" VALUE="true">
<PARAM NAME="Volume" value="-100">
<EMBED type="application/x-mplayer2" pluginspage="http://www.microsoft.com/Windows/MediaPlayer/" SRC="http://www.wtv-zone.com/Anastasia/Reflections/nightsinwhitesatin.mid" name="MediaPlayer1" width=230 height=70 autostart=1 showcontrols=1 volume=-100>
</OBJECT>

<NOEMBED> <bgsound src="http://www.wtv-zone.com/Anastasia/Reflections/nightsinwhitesatin.mid" autostart=true hidden=false volume=75%></NOEMBED>


</body>
</html>
[/html]

But oddly using the same html and sustituting [http://philsden.com/Howdy02.mp3](http://philsden.com/Howdy02.mp3) for the sound file does not work.

---

### Post by hou5ton on 2010-05-26
Thank you very much Philinux.  This seems to have worked for me.   The only thing ... after restarting Firefox, it only worked one time and from that point forward, Firefox would immediately crash upon trying to open an embedded video.  I restarted the whole system, and since then it has worked perfectly.

---

### Post by rogerdean on 2010-06-08
same problem here hou5ton, on a clean install...

---

### Post by sunk8 on 2010-06-08
I installed Ubuntu Tweak, and installed the flash player from there...
Now it works like a charm...

---

### Post by jimmyisland on 2010-06-08
I have this problem too, but i don't think the problem is with Flash - Chrome plays embedded videos without problem.

output of updatedb and locate below
james@james-laptop:~$ sudo updatedb
james@james-laptop:~$ locate libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
james@james-laptop:~$

---

### Post by oldtraveler on 2010-06-08
> **sunk8 said:**
> I installed Ubuntu Tweak, and installed the flash player from there...
Now it works like a charm...

Thank you for this suggestion.  After I figured out where to find Ubuntu Tweak (had to go to Google), I installed it.  Then went to Applications; System Tools; Ubuntu Tweak and installed all of the audio programs it listed.  One of them did the trick and now have embedded media files playing as well as You Tube.

---

