---
title: "Samba / Mediatomb Question"
date: 2009-10-20
forum: General Help
---

### Post by barnacles on 2009-10-20
Alright I got a two parter but thought I'd keep it to one post. First, I just set up a network drive so I could store videos from my computer over the network. My question is am I able to share these files for streaming thru mediatomb? 

Also, I am setting up mediatomb so I can stream to my ps3. Heres my mediatomb config 

> <?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:98a7c80e-8370-436d-a6dc-790e445a9f85</udn>
    <home>/home/dave/.mediatomb</home>
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
  </server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <common-script>/usr/share/mediatomb/js/common.js</common-script>
      <playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
      <virtual-layout type="builtin">
        <import-script>/usr/share/mediatomb/js/import.js</import-script>
      </virtual-layout>
    </scripting>
    <mappings>
      <extension-mimetype ignore-unknown="no">
	<map from="avi" to="video/x-divx"/>
	<map from="divx" to="video/x-divx"/>
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
      </mimetype-contenttype>
    </mappings>
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
        <agent command="ogg123" arguments="-d raw -f %out %in"/>
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
</config> <mappings><extension-mimetype ignore-unknown="no">

After trying to run it in terminal though I get an error message as follows..

> Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2009-10-20 16:45:09    INFO: Loading configuration from: /home/dave/.mediatomb/config.xml
2009-10-20 16:45:09   ERROR: Error parsing config file: /home/dave/.mediatomb/config.xml line 115:
junk after document element


It ran before I made a few changes which were setting "<protocolInfo extend="no"/>" to yes and adding "<map from="avi" to="video/x-divx"/>" and 
"<map from="divx" to="video/x-divx"/>"

---

### Post by buntunoob on 2009-10-24
If that’s all of your .cfg then you’re missing the last of it.
I pulled this from [http://juliensimon.blogspot.com](http://juliensimon.blogspot.com)
And Mediatomb Streams Extreamly well, At least to a PS3 it does
Here's the howto I compiled mine to [http://juliensimon.blogspot.com/2008/12/mediatomb-012-on-ps3-video-thumbnails.html](http://juliensimon.blogspot.com/2008/12/mediatomb-012-on-ps3-video-thumbnails.html)


<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
 <server>
   <ui enabled="yes" show-tooltips="yes">
     <accounts enabled="no" session-timeout="30">
       <account user="YouTube_Username" password="YouTube_Password"/>
     </accounts>
   </ui>
   <name>MediaTomb</name>
   <udn>uuid:b8b13d59-378e-4cb8-9a87-14f70c70f847</udn>
   <home>/home/julien/.mediatomb</home>
   <webroot>/usr/local/share/mediatomb/web</webroot>
   <storage>
     <sqlite3 enabled="yes">
       <database-file>mediatomb.db</database-file>
     </sqlite3>
   </storage>
   <protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->
  
   <extended-runtime-options>
     <ffmpegthumbnailer enabled="yes">
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
     <common-script>/usr/local/share/mediatomb/js/common.js</common-script>
     <playlist-script>/usr/local/share/mediatomb/js/playlists.js</playlist-script>
     <virtual-layout type="builtin">
       <import-script>/usr/local/share/mediatomb/js/import.js</import-script>
       <dvd-script>/usr/local/share/mediatomb/js/import-dvd.js</dvd-script>
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
       <map from="avi" to="video/divx"/>
 <map from="mkv" to="video/x-matroska"/>
 <map from="mts" to="video/mpeg"/>
 <map from="ts" to="video/mpeg"/>
 <map from="m2ts" to="video/mpeg"/>

 <map from="flac" to="audio/x-flac"/>
 <map from="mov" to="video/x-quicktime"/>
 <map from="vob" to="video/mpeg"/>
 <map from="m4v" to="video/mp4"/>
 <map from="iso" to="application/x-iso9660-image"/>

     </extension-mimetype>
     <mimetype-upnpclass>
       <map from="audio/*" to="object.item.audioItem.musicTrack"/>
       <map from="video/*" to="object.item.videoItem"/>
       <map from="application/x-iso9660-image" to="object.item.videoItem"/>
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
       <treat mimetype="video/x-msvideo" as="avi"/>
       <treat mimetype="video/divx" as="avi"/>
       <treat mimetype="video/mp4" as="mp4"/>
       <treat mimetype="audio/mp4" as="mp4"/>

       <treat mimetype="video/quicktime" as="mov"/>
       <treat mimetype="video/x-quicktime" as="mov"/>

       <treat mimetype="application/x-iso9660-image" as="dvd"/>

     </mimetype-contenttype>
   </mappings>
   <online-content>
     <!-- Make sure to setup a transcoding profile for flv -->
     <YouTube enabled="yes" refresh="28800" update-at-start="yes" purge-after="604800" racy-content="exclude">
       <favorites user="YouTube_Username"/>
       <playlists user="YouTube_Username"/>
       <uploads user="YouTube_Username"/>
       <standardfeed feed="most_viewed" time-range="today"/>
       <standardfeed feed="top_rated" time-range="this_week"/>
     </YouTube>
     <AppleTrailers enabled="yes" refresh="43200" update-at-start="yes" resolution="640"/>
   </online-content>
 </import>

 <transcoding enabled="yes">
   <mimetype-profile-mappings>
 <transcode mimetype="application/ogg"   using="audio-generic"/>
 <transcode mimetype="audio/x-flac"      using="audio-generic"/>
 <transcode mimetype="video/x-ms-asf"    using="video-generic"/>
 <transcode mimetype="video/x-flv"       using="video-generic"/>
 <transcode mimetype="video/x-matroska"  using="video-generic"/>
 <transcode mimetype="video/x-quicktime" using="video-generic"/>
 <transcode mimetype="video/quicktime"   using="video-generic"/>
   </mimetype-profile-mappings>
   <profiles>

      <profile name="audio-generic" enabled="yes" type="external" >
       <mimetype>audio/L16</mimetype>
       <first-resource>yes</first-resource>
       <accept-url>yes</accept-url>
       <sample-frequency>44100</sample-frequency>
       <audio-channels>2</audio-channels>
       <hide-original-resource>yes</hide-original-resource>
       <agent command="ffmpeg" arguments="-ac 2 -ar 44100 -y -i %in -f s16be %out"/>
       <buffer size="1048576" chunk-size="4096" fill-size="1024"/>
      </profile>

     <profile name="video-generic" enabled="yes" type="external">
       <avi-fourcc-list mode="ignore">
            <fourcc>DX50</fourcc>
            <fourcc>DM4V</fourcc>
            <fourcc>M4S2</fourcc>
       </avi-fourcc-list>
       <mimetype>video/mpeg</mimetype>
       <accept-url>yes</accept-url>
       <first-resource>yes</first-resource>
 <hide-original-resource>yes</hide-original-resource>
       <accept-ogg-theora>yes</accept-ogg-theora>
       <agent command="/usr/local/bin/mediatomb-video-generic" arguments="%in %out"/>
       <buffer size="1048576" chunk-size="26214" fill-size="52428"/>
     </profile>

   </profiles>
 </transcoding>
 
 <lastfm enabled="yes"> 
 <username>LastFM_Username</username> 
 <password>LastFM_Password</password> 
 </lastfm> 

</config>

---

