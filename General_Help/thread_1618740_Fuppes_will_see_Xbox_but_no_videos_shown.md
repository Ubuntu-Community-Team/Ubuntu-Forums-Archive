---
title: "Fuppes will see Xbox but no videos shown"
date: 2010-11-11
forum: General Help
---

### Post by Frosty91 on 2010-11-11
ok so i had fuppes all configured on mint 10 and everything worked fine and then i deleted a couple folders from my video folder and now fuppes wont show anything 

heres my fuppes cfg:
[HTML]
<pre class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 498px;
		text-align: left;
		overflow: auto"><pre class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 498px;
		text-align: left;
		overflow: auto">ben@weka:~$ sudo apt-get install ffmpeg build-essential libavutil-dev libavformat-dev libavcodec-dev subversion libtool automake autoconf libsqlite3-dev libpcre3-dev libxml2-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
libavutil-dev is already the newest version.
libavutil-dev set to manual installed.
libavformat-dev is already the newest version.
libavcodec-dev is already the newest version.
libavcodec-dev set to manual installed.
subversion is already the newest version.
libtool is already the newest version.
automake is already the newest version.
autoconf is already the newest version.
autoconf set to manual installed.
libsqlite3-dev is already the newest version.
libpcre3-dev is already the newest version.
libxml2-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodeccvs51 (&gt;= 3:20071206) but it is not going to be installed
          Depends: libavdevicecvs52 (&gt;= 3:20071206) but it is not going to be installed
          Depends: libavformatcvs52 (&gt;= 3:20071206) but it is not going to be installed
          Depends: libavutilcvs49 (&gt;= 3:20071206) but it is not going to be installed
          Depends: libc6 (&gt;= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
          Depends: libswscalecvs0 (&gt;= 3:20071206) but it is not going to be installed
E: Broken packages
</pre></pre>[/HTML]

and here's my vfolder.cfg:

[HTML]<pre class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 498px;
		text-align: left;
		overflow: auto"><?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="false">

    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder>

    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem" />
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
       
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)" />
      </vfolder>      
    </vfolder>

    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
    
    <vfolder name="shared dirs">
      <shared_dirs full_extend="true" />
    </vfolder>
    
  </vfolder_layout>

 <vfolder_layout device="Xbox 360" enabled="true" create_references="true">

    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album" type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
            
      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>
      
      <vfolder name="Artist" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>
      
      <vfolder name="Genre" id="5">
        <vfolders property="genre" type="container.genre.musicGenre">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Playlist" id="15" />
    </vfolder>
   
    <vfolder name="Pictures" id="3">
      <vfolder name="Album" id="13" />
      
      <vfolder name="All Pictures" id="11">
        <items type="imageItem" />
      </vfolder>
      
      <vfolder name="Date Taken" id="12" />
      
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19" />
      <vfolder name="Folders" id="23" />
    </vfolder>

    <vfolder name="Video" id="2">
      <vfolder name="Actor" id="10">
        <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
				<items type="videoItem" />
			</vfolder>
      <vfolder name="Folders" id="21">
			   <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Genre" id="9" />
    </vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>
</pre>[/HTML]

---

