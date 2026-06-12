---
title: "Ubuntu as media server?"
date: 2009-07-10
forum: General Help
---

### Post by Fafnr on 2009-07-10
Hey all, 

I hope this is the right place to ask, if not, please let me know, I'll repost somewhere else!

I find myself with a spare laptop, and I want to use it as a media server (+ a couple of other things - SVN server, maybe webserver too).

When I say media server I mean the following:
- ability to stream MP3's both on the network (via DAAP, I think) and over the internet (this guide tells me how to do it: 
[http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/](http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/))

- ability to stream movies (MP4, divx, xvid, etc.) over LAN but preferably also over the internet. LAN sharing for xbox / ps3 is also covered by the link above, but not other kinds of streaming?
Are there any kind of tutorials for this? And is Ubuntu even the right distro for it? Is my 1mbit upload even enough for it to be realistic to stream video over the internet?

The server will operator in a mixed environment. Currently I have Apple and Windows boxes running, and I'd like for the server to be able to talk to both.
Also, it'll be connected to a few USB harddrives with the material on it.

Really, I'd like to use it as an entertainment hub to serve content both on the LAN and over the internet. The only thing I *don't* need it to be is a mediacenter as it won't be connected to my TV directly.

I hope I've given enough info, if not, please let me know, and I'll post more info!

Thanks in advance!

Regards,

Søren

---

### Post by tgalati4 on 2009-07-10
mediatomb and firefly/fireplay (mt-daap)

Rhythmbox shows up as a media share in iTunes.

---

### Post by Ian_F on 2009-07-12
1mbit does not give you much headroom for streaming video across the internet. It should be fine for audio tho.
Keeping everything secure, whilst allowing you to access your content across the internet, is no trivial task.

If you abandon that strategy and just stick within your own network then life will be a whole lot easier ;)

---

### Post by Neezer on 2009-10-19
So I have been trying to get media files streamed to my ps3. I get to the restart mediatomb part and type

sudo /etc/init.d/mediatomb restart

and all I get is a red [fail]

Then I can't get to the mediatomb engine in my firefox window.

---

### Post by Ian_F on 2009-10-19
> **Neezer said:**
> So I have been trying to get media files streamed to my ps3. I get to the restart mediatomb part and type

sudo /etc/init.d/mediatomb restart

and all I get is a red [fail]

Then I can't get to the mediatomb engine in my firefox window.

What do you mean by a "red (fail)"? Did you install it using the Synaptic Package Manager? Did it install without error?

What error message do you get when you enter [**http://IPAddressOfYourServer:49152/**](**http://IPAddressOfYourServer:49152/**) into Firefox?
Are you using Firefox from the machine itself or from a remote machine?

---

### Post by Neezer on 2009-10-19
> **Ian_F said:**
> What do you mean by a "red (fail)"? Did you install it using the Synaptic Package Manager? Did it install without error?

What error message do you get when you enter [**http://IPAddressOfYourServer:49152/**](**http://IPAddressOfYourServer:49152/**) into Firefox?
Are you using Firefox from the machine itself or from a remote machine?

by "red (fail)" I mean the text of fail was red, and it said [fail]

[[red]fail[/red]]

I used the following as per the instructions on this page: [http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/](http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/)
```

sudo apt-get install mediatomb vlc ubuntu-restricted-extras samba

```


here is my terminal screen:
```

nate@server:~$ sudo /etc/init.d/mediatomb restart
 * Restarting upnp media server mediatomb                                [fail]

```

---

### Post by Ian_F on 2009-10-19
> **Neezer said:**
> by "red (fail)" I mean the text of fail was red, and it said [fail]

[[red]fail[/red]]

I used the following as per the instructions on this page: [http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/](http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/)
```

sudo apt-get install mediatomb vlc ubuntu-restricted-extras samba

```


here is my terminal screen:
```

nate@server:~$ sudo /etc/init.d/mediatomb restart
 * Restarting upnp media server mediatomb                                [fail]

```

Thanks.

I've not used those instructions so am going to have to blag it a bit but I'd look at the config file changes you've made. Perhaps either the instructions are lacking or you've done something wrong.

I just installed it using "sudo apt-get install mediatomb" and that was it.

Perhaps the easiest thing is to purge the install and start over? See whether you can get mediatomb running first and THEN hack the config file. If it fails after the changes then you've got something to focus on.

Just a thought.

---

### Post by Neezer on 2009-10-19
Uh oh!!!

so I tried 
```

sudo apt-get remove mediatomb

```

got the program removed from my system.

then
```

sudo apt-get install mediatomb

```

reinstalled fine.

after trying to restart mediatomb, I get the same fail error message.

So then I went through and removed all of the programs that I installed with the command from that website.

sudo apt-get remove vlc
sudo apt-get remove ubuntu-restricted-extras
sudo apt-get remove samba

I don't know why those might cause a problem, but I did it anyways.

I also removed mediatomb again.

after removeing mediatomb, I looked through my system for any medaitomb files or folders. I found a folder in /etc, and I found something else in /etc/init.d. I removed both of those items with sudo rmdir, and sudo rm respectively.

after that I reinstalled mediatomb with sudo apt-get......

and then I get this when trying to restart the program.

```

nate@server:/etc$ sudo /etc/init.d/mediatomb restart
sudo: /etc/init.d/mediatomb: command not found

```

upon looking through my file system, I indeed don't have a mediatomb program in my init.d file.

I try sudo apt-get install mediatomb again, and it tells me that it is already on my system and there are no new updates for it.

```

nate@server:/etc$ sudo apt-get install mediatomb
Reading package lists... Done
Building dependency tree
Reading state information... Done
mediatomb is already the newest version.
The following packages were automatically installed and are no longer required:
  libqt4-sql-mysql libqt4-dbus libqt4-qt3support libdvbpsi4 libvlc2 vlc-nox libqtcore4 libqt4-sql
  libiso9660-5 libqt4-xml libqt4-network libqt4-designer libqtgui4 liblua5.1-0 vlc-data libtar libqt4-script
  libaudio2 libvlccore0 libvcdinfo0 libebml0 libmatroska0 qt4-qtconfig libsdl-image1.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I hope I didn't really screw things up..

---

### Post by Ian_F on 2009-10-19
Hi Neezer,

Try using "purge" instead of "remove". So, 

```
sudo apt-get purge mediatomb
``` and so on

When it gives you prompts like: "*Use 'apt-get autoremove' to remove them*" then do just that, remove them using **sudo apt-get autoremove**.

You'll be fine, just don't start hacking around too much :)

---

### Post by Neezer on 2009-10-19
I did the purge for all of those programs, and the autoremove for them as well...they were all gone. Then I rebooted the computer. Then sudo apt-get install mediatomb.

Still no mediatomb file in my init.d folder. Do I need to do something to create that?

I tried looking for /etc/mediatomb and i'm not sure if it was there.

```

nate@server:/etc/init.d$ cd ..
nate@server:/etc$ cd mediatomb
nate@server:/etc/mediatomb$ la
.  ..

```

can cd mediatomb create that directory if it isn't there? I have aliased my ls -a to la....just to let you know if you were confused wit my command.

---

### Post by Giblet5 on 2009-10-19
> **Neezer said:**
> I did the purge for all of those programs, and the autoremove for them as well...they were all gone. Then I rebooted the computer. Then sudo apt-get install mediatomb.

Still no mediatomb file in my init.d folder. Do I need to do something to create that?

I tried looking for /etc/mediatomb and i'm not sure if it was there.

```

nate@server:/etc/init.d$ cd ..
nate@server:/etc$ cd mediatomb
nate@server:/etc/mediatomb$ la
.  ..

```

can cd mediatomb create that directory if it isn't there? I have aliased my ls -a to la....just to let you know if you were confused wit my command.

No, cd will not create a directory.

I'm surprised that the mediatomb config.xml is not there, but the default file is kinda useless anyway...

Here's the default:

```
<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <!--
     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    -->
  <server>
    <ui enabled="yes" show-tooltips="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:d0b54289-6201-4af4-8230-e120a6f34550</udn>
    <home>/var/lib/mediatomb</home>
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
    <protocolInfo extend="no"/><!-- For PS3 support change to "yes" -->
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
      </ffmpegthumbnailer>
      <mark-played-items enabled="no" suppress-cds-updates="yes">
        <string mode="prepend">*</string>
      </mark-played-items>
    </extended-runtime-options>
  </server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <common-script>/usr/share/mediatomb/js/common.js</common-script>
      <playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
      <virtual-layout type="builtin">
        <import-script>/usr/share/mediatomb/js/import.js</import-script>
        <dvd-script>/usr/share/mediatomb/js/import-dvd.js</dvd-script>
      </virtual-layout>
    </scripting>
    <mappings>
      <extension-mimetype ignore-unknown="no">
        <map from="mp3" to="audio/mpeg"/>
        <map from="ogg" to="application/ogg"/>
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
        <!-- <map from="avi" to="video/divx"/> -->
        <!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
        <!-- <map from="avi" to="video/avi"/> -->
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
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
        <treat mimetype="video/x-mkv" as="mkv"/>
        <treat mimetype="audio/mp4" as="mp4"/>
        <treat mimetype="application/x-iso9660" as="dvd"/>
        <treat mimetype="application/x-iso9660-image" as="dvd"/>
      </mimetype-contenttype>
    </mappings>
    <online-content>
      <!-- Make sure to setup a transcoding profile for flv -->
      <YouTube enabled="no" refresh="28800" update-at-start="no" purge-after="604800" racy-content="exclude" format="flv" hd="no">
        <favorites user="mediatomb"/>
        <standardfeed feed="most_viewed" time-range="today"/>
        <playlists user="mediatomb"/>
        <uploads user="mediatomb"/>
        <standardfeed feed="recently_featured" time-range="today"/>
      </YouTube>
      <Weborama enabled="no" refresh="28800" update-at-start="no">
        <playlist name="Active" type="playlist" mood="active"/>
        <playlist name="Metal" type="playlist">
          <filter>
            <genres>metal</genres>
          </filter>
        </playlist>
      </Weborama>
      <AppleTrailers enabled="no" refresh="43200" update-at-start="no" resolution="640"/>
    </online-content>
  </import>
  <transcoding enabled="no">
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
```

Just select and copy all of that, then create the file via ```
sudo gedit /etc/mediatomb/config.xml
``` and paste the data in, save it and exit.

As I said, that config file is all but useless and /etc/init.d/mediatomb start will fail because it isn't configured correctly. Yet.

You can debug the config.xml by restarting mediatomb and checking the log (/var/log/mediatomb.log I think).

It's not very polished, but it does work.

---

### Post by Giblet5 on 2009-10-19
The easy way to debug mediatomb:

Run it directly via ```
mediatomb -c /etc/mediatomb/config.xml
```

It'll spew any fatals out and you can fix them directly. Then, once you have a config that doesn't barf at startup, you can switch to checking the logs when things don't work as expected.

I have mediatomb set up against a PS3 and it does everything I need. It took perseverance though.

---

### Post by Ian_F on 2009-10-19
Yeah, what Giblet5 said :)

I was going to suggest manually removing the mediatomb entries from the /etc folder and doing another purge and reinstall but Giblet5's suggestion is better

---

### Post by Neezer on 2009-10-19
> **Giblet5 said:**
> The easy way to debug mediatomb:

Run it directly via ```
mediatomb -c /etc/mediatomb/config.xml
```

It'll spew any fatals out and you can fix them directly. Then, once you have a config that doesn't barf at startup, you can switch to checking the logs when things don't work as expected.

I have mediatomb set up against a PS3 and it does everything I need. It took perseverance though.

Here is what I got:
```

nate@server:/etc/mediatomb$ sudo nano config.xml
nate@server:/etc/mediatomb$ la
.  ..  config.xml
nate@server:/etc/mediatomb$ mediatomb -c /etc/mediatomb/config.xml

MediaTomb UPnP Server version 0.11.0 - http://mediatomb.cc/

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2009-10-19 16:09:00    INFO: Loading configuration from: /etc/mediatomb/config.xml
2009-10-19 16:09:00    INFO: Checking configuration...
2009-10-19 16:09:00    INFO: Setting filesystem import charset to UTF-8
2009-10-19 16:09:00    INFO: Setting metadata import charset to UTF-8
2009-10-19 16:09:00    INFO: Setting playlist charset to UTF-8
2009-10-19 16:09:00    INFO: Configuration check succeeded.

```

not really sure where to go from here though. I don't have a prompt...and I don't know how to get rid of the program....I have ran into this before, and I don't know how to use kill properly. I guess it worked.

On a side note, I am planning on doing the exact same thing...streaming movies and music to a ps3 that is hooked up to my big tv and receiver.

---

### Post by Giblet5 on 2009-10-19
> **Neezer said:**
> Here is what I got:
```

nate@server:/etc/mediatomb$ sudo nano config.xml
nate@server:/etc/mediatomb$ la
.  ..  config.xml
nate@server:/etc/mediatomb$ mediatomb -c /etc/mediatomb/config.xml

MediaTomb UPnP Server version 0.11.0 - http://mediatomb.cc/

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2009-10-19 16:09:00    INFO: Loading configuration from: /etc/mediatomb/config.xml
2009-10-19 16:09:00    INFO: Checking configuration...
2009-10-19 16:09:00    INFO: Setting filesystem import charset to UTF-8
2009-10-19 16:09:00    INFO: Setting metadata import charset to UTF-8
2009-10-19 16:09:00    INFO: Setting playlist charset to UTF-8
2009-10-19 16:09:00    INFO: Configuration check succeeded.

```

not really sure where to go from here though. I don't have a prompt...and I don't know how to get rid of the program....I have ran into this before, and I don't know how to use kill properly. I guess it worked.

On a side note, I am planning on doing the exact same thing...streaming movies and music to a ps3 that is hooked up to my big tv and receiver.


Ctrl-C is interrupt... It will do a graceful shutdown.

Here's my PS3 config file. It WILL break mediatomb, since you almost certainly don't have all of the codecs and other transcoding helper files yet.

```
<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <name>Slo Boxen</name>
    <udn>uuid:30c0d5f5-abaf-458b-9235-d605b630f75f</udn>
    <home>/home/mediahome</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage>
      <sqlite3 enabled="yes">
        <database-file>mediatomb.db</database-file>
      </sqlite3>
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
  </server>
  <autoscan use-inotify="auto">
    <directory location="/samba/Music" mode="timed" interval="7200" level="full" recursive="yes" hidden-files="no"/>
    <directory location="/samba/images" mode="timed" interval="7200" level="full" recursive="yes" hidden-files="no"/>
  </autoscan>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">      
    <common-script>/usr/share/mediatomb/js/common.js</common-script>
    <playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
      <virtual-layout type="js">
         <import-script>/usr/share/mediatomb/js/import.js</import-script>
      </virtual-layout>
    </scripting>
  <mappings>
      <extension-mimetype ignore-unknown="no">
        <map from="mp3" to="audio/mpeg"/>
        <map from="ogg" to="application/ogg"/>
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
        <map from="ts" to="video/mpeg"/>
        <map from="mp4" to="video/mp4"/>
        <map from="m4v" to="video/mp4"/>
        <map from="vob" to="video/mpeg"/>
        <map from="wav" to="audio/wav"/>
        <map from="mpg" to="video/mpeg"/>
        <map from="aac" to="audio/x-aac"/>
        <map from="m4a" to="audio/mp4"/>
        <map from="mkv" to="video/x-matroska"/>
        <map from="mov" to="video/x-quicktime"/> 
        <map from="flv" to="video/x-flv"/>
        <map from="divx" to="video/x-divx"/>
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
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
      </mimetype-contenttype>
    </mappings>
  </import>
  <transcoding enabled="yes">
    <mimetype-profile-mappings>  
      <transcode mimetype="audio/mpeg" using="vlcwav"/>    
      <transcode mimetype="video/x-flv" using="vlcyoutube"/>
      <transcode mimetype="video/mp4" using="transvideo"/>
      <transcode mimetype="video/x-quicktime" using="transvideo"/>
      <transcode mimetype="application/ogg" using="vlcwav"/>
      <transcode mimetype="audio/x-ms-wma" using="vlcwav"/>
      <transcode mimetype="audio/x-ms-asf" using="vlcwav"/>
      <transcode mimetype="audio/x-flac" using="ffmpegwav"/>
      <transcode mimetype="audio/x-aac" using="vlcwav"/>
      <transcode mimetype="audio/mp4" using="vlcwav"/>
      <transcode mimetype="video/x-msvideo" using="transvideo"/>
      <transcode mimetype="video/x-ms-wmv" using="transvideo"/>
      <transcode mimetype="video/mpeg" using="mpeg2trans"/>
      <transcode mimetype="video/x-matroska" using="transvideo"/>
      <transcode mimetype="image/jpeg" using="rescalejpeg"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="transvideo" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <agent command="ffmpegvideo" arguments="%in %out 8300k 256k"/>
        <buffer size="57600000" chunk-size="128000" fill-size="10000000"/>
      </profile>
      <profile name="mpeg2trans" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>yes</hide-original-resource>
        <agent command="ffmpegvideo" arguments="%in %out 8000k 256k"/>
        <buffer size="28800000" chunk-size="512000" fill-size="120000"/>
      </profile>
      <profile name="ffmpegwav" enabled="yes" type="external">
        <use-chunked-encoding>no</use-chunked-encoding>
        <mimetype>audio/wav</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <agent command="ffmpegaudio" arguments="%in %out"/>
        <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>
      <profile name="vlcwav" enabled="yes" type="external">
	<use-chunked-encoding>no</use-chunked-encoding> 
        <mimetype>audio/wav</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <agent command="vlc" arguments="-I dummy %in
           --sout #transcode{acodec=s16l,ab=192,channels=2}:standard{access=file,
                                                      mux=wav,dst=%out} vlc:quit"/>
        <buffer size="512000" chunk-size="32000" fill-size="64000"/>
      </profile>
      <profile name="rescalejpeg" enabled="yes" type="external">
        <mimetype>image/jpeg</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <agent command="/usr/bin/convert" arguments="-size 1080x720 %in -auto-orient
                                           -resize 112.5%x100% +profile '*' %out"/>
        <buffer size="50000" chunk-size="100" fill-size="100"/>
      </profile>
      <profile name="ffyoutube" enabled="no" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="ffmpegyoutube" arguments="%in %out"/>
        <buffer size="14400000" chunk-size="256000" fill-size="80000"/>
      </profile>
      <profile name="vlcyoutube" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="vlc" arguments="-I dummy %in
           --sout #transcode{vcodec=mp2v,vb=4096,canvas-width=448,canvas-height=252,
           acodec=mpga,ab=64,samplerate=44100,channels=1}:standard{access=file,
                                                       mux=ts,dst=%out} vlc:quit"/> 
        <buffer size="14400000" chunk-size="256000" fill-size="80000"/>
      </profile>
    </profiles>
  </transcoding>
</config>
```

The mediatomb web has pointers on getting various codecs to transcode properly and you'll have to play sleuth to figure out what packages you'll need to install.

Some of the helpers in the above config.xml are from the mediatomb web, so prepare to spend time there.

G'luck!

That's running on Karmic, by the way...

---

### Post by fcuk112 on 2009-10-19
if you have a ps3 you can also check out **ps3mediaserver**, it supports mkv files as well (transcoding is done on the PC) which mediatomb doesn't (i think).  still prefer mediatomb though.

cheers, frank.

---

### Post by Neezer on 2009-10-19
Thanks a lot guys!

I am running jaunty.

One thing that is bothering me, I still don't have a mediatomb file in /etc/init.d

I didn't try to run it yet, but it just worries me that it isn't there. pressing ctl+c didn't really work....I just got a ^C in the window and that was it. 

I closed my ssh window and restarted my connection with ssh to get a prompt back. Did a reboot when i got my prompt back just in case....probably not needed though.


EDIT:

As I was afraid of,
```

nate@server:~$ /etc/init.d/mediatomb restart
-bash: /etc/init.d/mediatomb: No such file or directory


```

not sure what to do now...I really don't want to start configuring the .conf file until I get this issue started....I think.

---

### Post by Neezer on 2009-10-20
So did I really screw up my whole notion of running mediatomb on my computer? Why isn't the mediatomb executable showing up in /etc/init.d/??

---

### Post by buntunoob on 2009-10-27
To start mediatomb use Daemon Mode
mediatomb -d
There are some scripts to run this at start up, I cant seem to find them now thou.

---

