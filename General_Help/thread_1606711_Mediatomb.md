---
title: "Mediatomb"
date: 2010-10-26
forum: General Help
---

### Post by dewey_daniels on 2010-10-26
Okay I know this question as been asked alot but I dont understand the Mediatomb Wiki FAQ and the other "solutions" dont work for me either so....How do I make Mediatomb auto start.

I am on 10.10
```
# Defaults for MediaTomb initscript
# sourced by /etc/init.d/mediatomb
# installed at /etc/default/mediatomb by the maintainer scripts

#
# This is a POSIX shell fragment
#

# Set whether the daemon should be started. Set this value to anything
# but 'yes' to enable the daemon
NO_START="no"

# Additional options that are passed to the daemon.
OPTIONS=""

# The network interface for MediaTomb to bind to and for which the multicast
# routing entry should be added; "" if the route shouldn't be added at all.
# For example: INTERFACE="eth0"
INTERFACE=""

# The route command and arguments to be used if INTERFACE is defined.
# These variables should normally be left unmodified.
ROUTE_ADD="/sbin/route add -net 239.0.0.0 netmask 255.0.0.0"
ROUTE_DEL="/sbin/route del -net 239.0.0.0 netmask 255.0.0.0"

# The user and group that MediaTomb should be run as.
USER="mediatomb"
GROUP="mediatomb"
```That is the one from etc>default>

```
<?xml version="1.0" encoding="UTF-8"?>
<config version="2" xmlns="http://mediatomb.cc/config/2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/2 http://mediatomb.cc/config/2.xsd">
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
    <udn>uuid:d74f6c2f-ede0-4262-a3c7-59042f302212</udn>
    <home>/home/derek/.mediatomb</home>
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
        <map from="avi" to="video/x-divx"/>
        <map from="divx" to="video/x-divx"/>
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
        <!-- <map from="avi" to="video/divx"/> -->
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
```There is the Config. What am I doing wrong. Thanks in advance.:popcorn:

Edit This is al for my ps3 if that matters.

Also >     <name>MediaTomb</name> if I change the name do I have to change anything else? Like if I wanted to just call it PS3 for simplicities sake what else would I have to do.

---

### Post by dewey_daniels on 2010-10-27
:popcorn: Sorry I know I should wait longer but I will be gone for little while and I need this fixed.

---

### Post by dewey_daniels on 2010-10-27
bump

---

### Post by dewey_daniels on 2010-10-29
Bump

---

### Post by dewey_daniels on 2010-10-30
bump

---

### Post by Ancanus on 2010-10-30
No idea what Mediatomb is, but is there any reason you can't just create an entry on *System -> Preferences -> Startup Applications* for it?

---

### Post by dewey_daniels on 2010-10-30
If you dont know what it is then why reply?

You start it with a terminal command

---

### Post by Ancanus on 2010-10-30
> **dewey_daniels said:**
> If you dont know what it is then why reply?

You start it with a terminal command

...because you have been bumping this thread for the last 3 days to no avail?

If you start it with a terminal command, you can make an auto-start entry in the Startup Applications I noted above.

---

### Post by dewey_daniels on 2010-10-30
How?

---

### Post by Bealer on 2010-10-31
I've been running into this problem.

As mentioned above, go into the StartUp Applications menu.

Select to "add", and in the window that pops up, give it a name etc...

For the command put "mediatomb -d"

That'll get mediatomb starting upon your system loading up. By doing this it may run via your home directory, ie config.xml will be in and run from /home/_user_/.mediatomb/

---

### Post by dewey_daniels on 2010-10-31
How do I know if it worked. I cant check my ps3 at the moment and terminal appeared

---

### Post by dewey_daniels on 2010-11-01
bump Didn't work

---

### Post by dewey_daniels on 2010-11-03
bump

---

### Post by dewey_daniels on 2010-11-06
[color="red"]bump[/color]

---

### Post by pereclies on 2010-11-11
> **dewey_daniels said:**
> How do I know if it worked. I cant check my ps3 at the moment and terminal appeared

One way I've found out to see if the service is running (I don't know linux that well yet but I've been battling this same problem myself for some time and have gotten to know mediatomb pretty well) is by seeing if you can access the web config.  the link is given when you run mediatomb from the command line.  might want to check your config to see what ip the server will be using, since I think the default is something like 192.168.122.1:[some port number] and if you're like me, and are trying to get this to work over ssh from another computer, then you can't access that page because it's on a different subnet.

try adding the ```
<ip>192.168.1.8</ip>
``` (replacing with your real server ip of course) tag in the ~/.mediatomb/config.xml under the first [HTML]<server>[/HTML] section. 

once you do that, you should be able to access the webpage if the program is running.

one page I've found slightly helpful is [http://mediatomb.cc/pages/documentation](http://mediatomb.cc/pages/documentation)

Good luck and please report back with what progress you make, since, like I said, I'm having trouble with the same thing.

---

