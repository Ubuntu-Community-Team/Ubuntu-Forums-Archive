---
title: "MediaTomb UI is disabled. Check your configuration."
date: 2010-11-11
forum: General Help
---

### Post by GonZo1323 on 2010-11-11
Every time I try and open MediaTomb I get this message.  Can anyone please help?

---

### Post by Gtank on 2010-11-20
Using this site:
[ubuntu10.10 MediaTomb UI is disabled. Check your configuration]("http://forum.ubuntu-fr.org/viewtopic.php?id=418229") in french

and [Google Translate]("http://translate.google.com/#")

I came up with this fix.

You have to change the Media Tomb settings which are located in a config (xml) file.... so to do this you have to. 
1.  Open up a terminal session, it's in Applications > Accessories > Terminal 

2. Type:    sudo gedit /etc/mediatomb/config.xml

3. When the editor is opened change ui enabled and transcoding enabled settings to yes.  (the effected lines should look like this)
 
<ui enabled="**_yes_**" show-tooltips="yes">

<transcoding enabled="**_yes_**"> 

4.  save your changes and close the editor


5. in the terminal window type:  sudo /etc/init.d/mediatomb restart

(this will restart the media tomb server in order for the changes you just did to to take effect.)  

6. Sit back and enjoy your media streaming.

---

### Post by shohnt on 2010-11-28
Thanks Gtank for the help but when I open up the terminal and type in this command sudo gedit /etc/mediatomb/config.xml
 it tells me sudo: gedit: command not found  . How do I fix this! F.Y.I I'm running kubuntu 10.10 if that makes any difference.

---

### Post by matt_symes on 2010-11-28
Hi

> **shohnt said:**
> Thanks Gtank for the help but when I open up the terminal and type in this command sudo gedit /etc/mediatomb/config.xml
 it tells me sudo: gedit: command not found  . How do I fix this! F.Y.I I'm running kubuntu 10.10 if that makes any difference.

gedit should be located in /usr/bin/gedit

so you can type

 gksudo /usr/bin/gedit /etc/mediatomb/config.xml

However it's installed in Gnome and not in Kubuntu. If you really want it 

sudo apt-get install gedit

However why not use Kate in Kubuntu?

sudo kate /etc/mediatomb/config.xml

Also you can use nano from the terminal

sudo nano /etc/mediatomb/config.xml

Kind regards

---

### Post by shohnt on 2010-11-29
Thanks [matt_symes]("http://ubuntuforums.org/member.php?u=1067998")! I used the kate method and it worked perfectly. Now I'm enjoying streaming my HD videos on my WD Live TV.

---

### Post by Wacky Dan on 2010-12-15
Thanks Gtank, just what I needed.

---

### Post by nigel23 on 2011-01-21
> **Gtank said:**
> Using this site:
[ubuntu10.10 MediaTomb UI is disabled. Check your configuration]("http://forum.ubuntu-fr.org/viewtopic.php?id=418229") in french

and [Google Translate]("http://translate.google.com/#")

I came up with this fix.

You have to change the Media Tomb settings which are located in a config (xml) file.... so to do this you have to. 
1.  Open up a terminal session, it's in Applications > Accessories > Terminal 

2. Type:    sudo gedit /etc/mediatomb/config.xml

3. When the editor is opened change ui enabled and transcoding enabled settings to yes.  (the effected lines should look like this)
 
<ui enabled="**_yes_**" show-tooltips="yes">

<transcoding enabled="**_yes_**"> 

4.  save your changes and close the editor


5. in the terminal window type:  sudo /etc/init.d/mediatomb restart

(this will restart the media tomb server in order for the changes you just did to to take effect.)  

6. Sit back and enjoy your media streaming.


I tried this but i keep getting: command not found
I tried kate also
I'm using Desktop 10.10. Any other options to enable?

---

### Post by axept on 2011-01-21
> **nigel23 said:**
> I tried this but i keep getting: command not found
I tried kate also
I'm using Desktop 10.10. Any other options to enable?

On my computer the config file is at /home/USER/.mediatomb

You can find where the config file is with this command in terminal:

```
mediatomb --cfgdir
```

I got that msg even if the UI was enable. I forgot to start the MediaTomb server from terminal. It doesn't start from the menu.

Go to terminal and write

```
mediatomb
```

Then you can start MediaTomb from the menu. (Applications -> Sound & Video)

---

### Post by nigel23 on 2011-01-21
i dont understand. i did what u said and mine is in /home/... but what do i do then?

---

### Post by axept on 2011-01-22
> **nigel23 said:**
> i dont understand. i did what u said and mine is in /home/... but what do i do then?

Then you can 

```
sudo gedit /home/.mediatomb/config.xml
```

If the config-file is called config.xml, and in that file you see this:

```
<server>
      <ui enabled="yes" show-tooltips="yes">
```

Allmost at the beginning of the file, line 8.
Make sure "ui enabled" is "yes", if so save and exit.

Then go to terminal (Applications -> Accessories -> Terminal).

When you're in a terminal, do this:

```
mediatomb
```

When this is done, go to "Application -> Sound & Video -> MediaTomb", now you should have a working MediaTomb. 

You can read more about MediaToomb her: [http://mediatomb.cc/]("http://mediatomb.cc/")

---

### Post by nigel23 on 2011-01-23
THanks, will let u know if it worked.

---

### Post by ncpokrt on 2011-01-26
I am having the same problem, also with 10.10.  I think I have made all of the changes required to the config.xml I changed:
transcoding enabled to yes
protocolInfo extend to yes
accounts enabled to yes
and I uncommented <map from "avi" to "video/divx"/>

My default browser is Chrome which the documentation did not list as tested.  So I tried loading the UI with Firefox. Same error.

The program starts fine in the terminal.  Here is the output:

# mediatomb -d
2011-01-26 09:15:54    INFO: Loading configuration from: /home/nancy/.mediatomb/config.xml
2011-01-26 09:15:54    INFO: Checking configuration...
2011-01-26 09:15:54    INFO: Setting filesystem import charset to UTF-8
2011-01-26 09:15:54    INFO: Setting metadata import charset to UTF-8
2011-01-26 09:15:54    INFO: Setting playlist charset to UTF-8
2011-01-26 09:15:54 WARNING: You enabled the YouTube feature, which allows you
                             to watch YouTube videos on your UPnP device!
                             Please check [http://www.youtube.com/t/terms](http://www.youtube.com/t/terms)
                             By using this feature you may be violating YouTube
                             service terms and conditions!

2011-01-26 09:15:54    INFO: Configuration check succeeded.

Here is the config.xml:

<?xml version="1.0" encoding="UTF-8"?>
<config version="2" xmlns="http://mediatomb.cc/config/2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/2 http://mediatomb.cc/config/2.xsd">
  <!--
     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    -->
  <server>
    <ui enabled="yes" show-tooltips="yes">
      <accounts enabled="yes" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:9b03da87-9af3-4a07-bc45-a6e66b61e2fb</udn>
    <home>/home/nancy/.mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage>
      <sqlite3 enabled="yes">
        <database-file>mediatomb.db</database-file>
      </sqlite3>
      <mysql enabled="no">
        <host>localhost</host>
        <username>mediatomb</username>
        <database>mediatomb</database>
      </mysql>
    </storage>
    <protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->
    <!--
       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    -->
    <!--
    <custom-http-headers>
      <add header="X-User-Agent: redsonic"/>
    </custom-http-headers>

    <manufacturerURL>redsonic.com</manufacturerURL>
    <modelNumber>105</modelNumber>
    -->
    <!-- Uncomment the line below if you have a Telegent TG100 -->
    <!--
       <upnp-string-limit>101</upnp-string-limit>
    -->
    <extended-runtime-options>
      <ffmpegthumbnailer enabled="no">
        <thumbnail-size>128</thumbnail-size>
        <seek-percentage>5</seek-percentage>
        <filmstrip-overlay>yes</filmstrip-overlay>
        <workaround-bugs>no</workaround-bugs>
        <image-quality>8</image-quality>
      </ffmpegthumbnailer>
      <mark-played-items enabled="no" suppress-cds-updates="yes">
        <string mode="prepend">*</string>
        <mark>
          <content>video</content>
        </mark>
      </mark-played-items>
    </extended-runtime-options>
  </server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <virtual-layout type="builtin"/>
    </scripting>
    <mappings>
      <extension-mimetype ignore-unknown="no">
        <map from="mp3" to="audio/mpeg"/>
        <map from="ogx" to="application/ogg"/>
        <map from="ogv" to="video/ogg"/>
        <map from="oga" to="audio/ogg"/>
        <map from="ogg" to="audio/ogg"/>
        <map from="ogm" to="video/ogg"/>
        <map from="asf" to="video/x-ms-asf"/>
        <map from="asx" to="video/x-ms-asf"/>
        <map from="wma" to="audio/x-ms-wma"/>
        <map from="wax" to="audio/x-ms-wax"/>
        <map from="wmv" to="video/x-ms-wmv"/>
        <map from="wvx" to="video/x-ms-wvx"/>
        <map from="wm" to="video/x-ms-wm"/>
        <map from="wmx" to="video/x-ms-wmx"/>
        <map from="m3u" to="audio/x-mpegurl"/>
        <map from="pls" to="audio/x-scpls"/>
        <map from="flv" to="video/x-flv"/>
        <map from="mkv" to="video/x-matroska"/>
        <map from="mka" to="audio/x-matroska"/>
        <!-- Uncomment the line below for PS3 divx support -->
        <map from="avi" to="video/divx"/>
        <!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
        <!-- <map from="avi" to="video/avi"/> -->
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
        <map from="application/ogg" to="object.item.audioItem.musicTrack"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
        <treat mimetype="audio/mpeg" as="mp3"/>
        <treat mimetype="application/ogg" as="ogg"/>
        <treat mimetype="audio/x-flac" as="flac"/>
        <treat mimetype="image/jpeg" as="jpg"/>
        <treat mimetype="audio/x-mpegurl" as="playlist"/>
        <treat mimetype="audio/x-scpls" as="playlist"/>
        <treat mimetype="audio/x-wav" as="pcm"/>
        <treat mimetype="audio/L16" as="pcm"/>
        <treat mimetype="video/x-msvideo" as="avi"/>
        <treat mimetype="video/mp4" as="mp4"/>
        <treat mimetype="audio/mp4" as="mp4"/>
        <treat mimetype="application/x-iso9660" as="dvd"/>
        <treat mimetype="application/x-iso9660-image" as="dvd"/>
        <treat mimetype="video/x-matroska" as="mkv"/>
        <treat mimetype="audio/x-matroska" as="mka"/>
      </mimetype-contenttype>
    </mappings>
    <online-content>
      <YouTube enabled="no" refresh="28800" update-at-start="no" purge-after="604800" racy-content="exclude" format="mp4" hd="no">
        <favorites user="mediatomb"/>
        <standardfeed feed="most_viewed" time-range="today"/>
        <playlists user="mediatomb"/>
        <uploads user="mediatomb"/>
        <standardfeed feed="recently_featured" time-range="today"/>
      </YouTube>
    </online-content>
  </import>
  <transcoding enabled="yes">
    <mimetype-profile-mappings>
      <transcode mimetype="video/x-flv" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="oggflac2raw"/>
      <transcode mimetype="audio/x-flac" using="oggflac2raw"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="oggflac2raw" enabled="no" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <agent command="ogg123" arguments="-d raw -o byteorder:big -f %out %in"/>
        <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>
      <profile name="vlcmpeg" enabled="no" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
        <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
      </profile>
    </profiles>
  </transcoding>
</config>

---

### Post by ncpokrt on 2011-01-26
I figured it out.  You need to run mediaTomb in the terminal with sudo

# sudo mediatomb

and then all is well.

It asked me for a username and password which are by default 
user: mediatomb
password: mediatomb

I recommend you change that to something more secure by editing the ~/.mediatomb/config.xml file

---

### Post by nigel23 on 2011-01-27
PS3 media server is much easier to install for beginners (like me). But as the name hints, it only works for ps3.[http://ps3mediaserver.blogspot.com/]("http://ps3mediaserver.blogspot.com/")

---

### Post by axept on 2011-01-28
> **ncpokrt said:**
> I figured it out.  You need to run mediaTomb in the terminal with sudo

# sudo mediatomb

and then all is well.

It asked me for a username and password which are by default 
user: mediatomb
password: mediatomb

I recommend you change that to something more secure by editing the ~/.mediatomb/config.xml file

Good for you that it worked!

I dont have to use sudo to start it, but anyway...

---

### Post by axept on 2011-01-28
> **nigel23 said:**
> PS3 media server is much easier to install for beginners (like me). But as the name hints, it only works for ps3.[http://ps3mediaserver.blogspot.com/]("http://ps3mediaserver.blogspot.com/")

Did it work for you?? MediaTomb I mean, not ps3 mediaserver...

---

### Post by nigel23 on 2011-02-17
> **axept said:**
> Did it work for you?? MediaTomb I mean, not ps3 mediaserver...

nope, gave up.

---

### Post by matt_symes on 2011-02-17
Hi

Funally enough, i just installed mediatomb today and i have got it working through the browser. I have just watched some streamed test content so i know it works.

Steps to take to enable the UI from the browser.

1. Install media tomb from the repositories.
2. Edit the configuration file. It is located in /etc/mediatomb/config.xml.

From the terminal....

```
sudo nano /etc/mediatomb/config.xml
```

Enter your password. It will not be echoed to the screen. This is the start of the config.xml file.

```
<?xml version="1.0" encoding="UTF-8"?>
<config version="2" xmlns="http://mediatomb.cc/config/2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schem$
     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    -->
  <server>
    <**ui enabled="no"** show-tooltips="yes">
      <**accounts enabled="no"** session-timeout="30">
        <**account user="mediatomb" password="mediatomb"**/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:c88910cd-15d4-41c8-9f74-4050b78cddb0</udn>
    <home>/var/lib/mediatomb</home>.
....
...
```

The entries highlighted on bold are the entries you want to change. This is an example

```
<**ui enabled="yes"** show-tooltips="yes">
      <**accounts enabled="yes"** session-timeout="30">
        <**account user="user1" password="password1"**/>
      </accounts>
    </ui>
```

Save the file with ctrl + o and exit the file with ctrl + x.

Restart mediatomb if it is running. To check if it is running

```
ps aux | grep [m]ediatomb
```

If it's running

```
sudo /etc/init.d/mediatomb restart
```
 
There are other options in the config file that you may need to change for your set up but that will enable the UI from a web browser. Firefox works well (but elinks doesn't). I have not tried other browsers.

From the local or a remote machine (on same LAN) try to access the page. It will be something along the lines of (assuming no port change) ...

for local

```
http://12.0.0.1:49152/
```

on same lan

```
http://192.168.1.5:49152/

```

That IP address (192.168.1.5) will obviously be changed to your servers ip address.

I hope this helps.

Kind regards

---

### Post by Digram_seth on 2011-11-27
Thanks 
it plays like a charm with viewsonic VMP72 :popcorn:

---

### Post by Justin Buser on 2012-10-16
> **GonZo1323 said:**
> Every time I try and open MediaTomb I get this message.  Can anyone please help?

I had this problem and I ended up needing to give read/write permissions for /etc/mediatomb to the mediatomb user and then editing the config.xml file found there. If you are running mediatomb as a daemon and using sqlite for instance and don't see mediatomb.db being created in that dir then you most likely won't be able to use the UI or browse the server via upnp (not sure why there are no errors in the log re: this).

Also if you are using the system menu link under sound/video or any link other than the one found at the end of /var/log/mediatomb.log you may be trying to pull up the UI using the wrong port. In my case for example my meu link was pointing to [http://10.0.0.1:49152](http://10.0.0.1:49152) but the server was actually running on [http://10.0.0.1:49153](http://10.0.0.1:49153)

---

### Post by wheelsmanx on 2012-10-23
so i was able to make my mediatomb show me the ui one time- and then i edited the user name and pass word in the config file and it went back to disabled so i changed them back restarted the server and they are still disabled 

```
<config version="2" xsi:schemaLocation="http://mediatomb.cc/config/2 http://mediatomb.cc/config/2.xsd"><!--
     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    --><server><ui enabled="no" show-tooltips="yes"><accounts enabled="no" session-timeout="30"><account user="mediatomb" password="mediatomb"/></accounts></ui><name>MediaTomb</name><udn>uuid:cb0f1b23-129c-462b-b4c3-78c1107d1ae1</udn><home>/var/lib/mediatomb</home><webroot>/usr/share/mediatomb/web</webroot><storage caching="yes"><sqlite3 enabled="yes"><database-file>mediatomb.db</database-file></sqlite3><mysql enabled="no"><host>localhost</host><username>mediatomb</username><database>mediatomb</database></mysql></storage><protocolInfo extend="no"/><!-- For PS3 support change to "yes" --><!--
       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    --><!--
    <custom-http-headers>
      <add header="X-User-Agent: redsonic"/>
    </custom-http-headers>

    <manufacturerURL>redsonic.com</manufacturerURL>
    <modelNumber>105</modelNumber>
    --><!-- Uncomment the line below if you have a Telegent TG100 --><!--
       <upnp-string-limit>101</upnp-string-limit>
    --><extended-runtime-options><ffmpegthumbnailer enabled="no"><thumbnail-size>128</thumbnail-size><seek-percentage>5</seek-percentage><filmstrip-overlay>yes</filmstrip-overlay><workaround-bugs>no</workaround-bugs></ffmpegthumbnailer><mark-played-items enabled="no" suppress-cds-updates="yes"><string mode="prepend">*</string></mark-played-items></extended-runtime-options></server><import hidden-files="no"><scripting script-charset="UTF-8"><common-script>/usr/share/mediatomb/js/common.js</common-script><playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script><virtual-layout type="builtin"><import-script>/usr/share/mediatomb/js/import.js</import-script><dvd-script>/usr/share/mediatomb/js/import-dvd.js</dvd-script></virtual-layout></scripting><mappings><extension-mimetype ignore-unknown="no"><map from="mp3" to="audio/mpeg"/><map from="ogg" to="application/ogg"/><map from="asf" to="video/x-ms-asf"/><map from="asx" to="video/x-ms-asf"/><map from="wma" to="audio/x-ms-wma"/><map from="wax" to="audio/x-ms-wax"/><map from="wmv" to="video/x-ms-wmv"/><map from="wvx" to="video/x-ms-wvx"/><map from="wm" to="video/x-ms-wm"/><map from="wmx" to="video/x-ms-wmx"/><map from="m3u" to="audio/x-mpegurl"/><map from="pls" to="audio/x-scpls"/><map from="flv" to="video/x-flv"/><map from="mkv" to="video/x-matroska"/><map from="mka" to="audio/x-matroska"/><!-- Uncomment the line below for PS3 divx support --><!-- <map from="avi" to="video/divx"/> --><!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 --><!-- <map from="avi" to="video/avi"/> --></extension-mimetype><mimetype-upnpclass><map from="audio/*" to="object.item.audioItem.musicTrack"/><map from="video/*" to="object.item.videoItem"/><map from="image/*" to="object.item.imageItem"/><map from="application/ogg" to="object.item.audioItem.musicTrack"/></mimetype-upnpclass><mimetype-contenttype><treat mimetype="audio/mpeg" as="mp3"/><treat mimetype="application/ogg" as="ogg"/><treat mimetype="audio/x-flac" as="flac"/><treat mimetype="image/jpeg" as="jpg"/><treat mimetype="audio/x-mpegurl" as="playlist"/><treat mimetype="audio/x-scpls" as="playlist"/><treat mimetype="audio/x-wav" as="pcm"/><treat mimetype="audio/L16" as="pcm"/><treat mimetype="video/x-msvideo" as="avi"/><treat mimetype="video/mp4" as="mp4"/><treat mimetype="audio/mp4" as="mp4"/><treat mimetype="application/x-iso9660" as="dvd"/><treat mimetype="application/x-iso9660-image" as="dvd"/><treat mimetype="video/x-matroska" as="mkv"/><treat mimetype="audio/x-matroska" as="mka"/></mimetype-contenttype></mappings><online-content><!-- Make sure to setup a transcoding profile for flv --><YouTube enabled="no" refresh="28800" update-at-start="no" purge-after="604800" racy-content="exclude" format="flv" hd="no"><favorites user="mediatomb"/><standardfeed feed="most_viewed" time-range="today"/><playlists user="mediatomb"/><uploads user="mediatomb"/><standardfeed feed="recently_featured" time-range="today"/></YouTube><Weborama enabled="no" refresh="28800" update-at-start="no"><playlist name="Active" type="playlist" mood="active"/><playlist name="Metal" type="playlist"><filter><genres>metal</genres></filter></playlist></Weborama><AppleTrailers enabled="no" refresh="43200" update-at-start="no" resolution="640"/></online-content></import><transcoding enabled="no"><mimetype-profile-mappings><transcode mimetype="video/x-flv" using="vlcmpeg"/><transcode mimetype="application/ogg" using="vlcmpeg"/><transcode mimetype="application/ogg" using="oggflac2raw"/><transcode mimetype="audio/x-flac" using="oggflac2raw"/></mimetype-profile-mappings><profiles><profile name="oggflac2raw" enabled="no" type="external"><mimetype>audio/L16</mimetype><accept-url>no</accept-url><first-resource>yes</first-resource><accept-ogg-theora>no</accept-ogg-theora><agent command="ogg123" arguments="-d raw -o byteorder:big -f %out %in"/><buffer size="1048576" chunk-size="131072" fill-size="262144"/></profile><profile name="vlcmpeg" enabled="no" type="external"><mimetype>video/mpeg</mimetype><accept-url>yes</accept-url><first-resource>yes</first-resource><accept-ogg-theora>yes</accept-ogg-theora><agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/><buffer size="14400000" chunk-size="512000" fill-size="120000"/></profile></profiles></transcoding></config>
```

---

