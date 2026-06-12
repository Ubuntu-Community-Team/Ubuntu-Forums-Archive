---
title: "Moving/Resetting the Cheese Webcam folder"
date: 2010-10-11
forum: General Help
---

### Post by kolo-01 on 2010-10-11
Every time I start up my webcam in cheese, a folder is created called 'Webcam' in my home folder, and if this folder is deleted, it will be recreated when another session is started, i would ideally like to just have this folder hidden but if i do that then it will be recreated, so is there anyway of having the folder created as a hidden .Webcam? there is no option for this in the cheese menu.. thanks

---

### Post by tornadof3 on 2010-10-11
Yes there is an easy way to do this. 

From the command line, type 
```

gedit ~/.gconf/apps/cheese/%gconf.xml
```

and edit the video_path and photo_path entries to your desired location. I found the "Webcam" folder issue equally annoying!

---

### Post by kolo-01 on 2010-10-11
> **tornadof3 said:**
> Yes there is an easy way to do this. 

From the command line, type 
```

gedit ~/.gconf/apps/cheese/%gconf.xml
```

and edit the video_path and photo_path entries to your desired location. I found the "Webcam" folder issue equally annoying!


<?xml version="1.0"?>
<gconf>
	<entry name="selected_effects" mtime="1285073362" type="list" ltype="string">
	</entry>
	<entry name="webcam" mtime="1283423451" type="string">
		<stringvalue>/dev/video0</stringvalue>
	</entry>
	<entry name="countdown" mtime="1286848108" type="bool" value="true"/>
</gconf>


this is the script i get when i open that file, i cant see anywhere to edit the location paths in it so do you think that you have a different version of cheese or something or am i missing something?

---

### Post by tornadof3 on 2010-10-13
Hello. Here is my config file:

```
<?xml version="1.0"?>
<gconf>
    <entry name="saturation" mtime="1275499805" type="float" value="1.1309523582458496"/>
    <entry name="camera" mtime="1272753325" type="string">
        <stringvalue>/dev/video0</stringvalue>
    </entry>
    <entry name="contrast" mtime="1275499797" type="float" value="1.1785714626312256"/>
    <entry name="brightness" mtime="1275499812" type="float" value="0"/>
    <entry name="wide_mode" mtime="1286824948" type="bool" value="true"/>
    <entry name="burst_repeat" mtime="1262789496" type="int" value="5"/>
    <entry name="video_path" mtime="1256752478" type="string">
        <stringvalue>/home/USERNAME/Media/Webcam</stringvalue>
    </entry>
    <entry name="photo_path" mtime="1256752470" type="string">
        <stringvalue>/home/USERNAME/Media/Webcam</stringvalue>
    </entry>
    <entry name="selected_effects" mtime="1286824979" type="list" ltype="string">
    </entry>
    <entry name="y_resolution" mtime="1245957018" type="int" value="480"/>
    <entry name="x_resolution" mtime="1245957018" type="int" value="640"/>
    <entry name="webcam" mtime="1240159780" type="string">
        <stringvalue>/dev/video0</stringvalue>
    </entry>
    <entry name="countdown" mtime="1286824879" type="bool" value="true"/>
</gconf>

```
So I guess if you copy/paste the photo_path and video_path keys from above to yours and change the path to your desired location that should work. I just like anything to do with vid, photos or sound to be under a "Media" folder!

---

### Post by kolo-01 on 2010-10-14
thanks for your help but ive tried pasting all and parts of your script in a few times now and it isn't working for me, its just reverting to the old script and the webcam folder stays the same. the cheese help says exactly what you did and says that your script is what i should be finding, but im not sure where the shorter script i get is coming from, think i'll just delete cheese and try to find an alternative

---

### Post by rbc on 2010-10-14
kolo-01,

I have the same .xml file for Cheese that you do. I was able, however, to edit where Cheese saves things bu opening gconf-editor, then navigating to apps--> cheese. Then edit the photo_path and video_path key values. I do not know if this is exactly what you are after, but I hope it’s a start

---

### Post by kolo-01 on 2010-10-16
> **rbc said:**
> kolo-01,

I have the same .xml file for Cheese that you do. I was able, however, to edit where Cheese saves things bu opening gconf-editor, then navigating to apps--> cheese. Then edit the photo_path and video_path key values. I do not know if this is exactly what you are after, but I hope it’s a start


editing the values in the gconf-editor worked, thanks a lot

---

