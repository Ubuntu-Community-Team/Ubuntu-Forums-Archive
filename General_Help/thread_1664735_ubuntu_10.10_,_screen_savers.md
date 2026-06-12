---
title: "ubuntu 10.10 , screen savers"
date: 2011-01-11
forum: General Help
---

### Post by harlie on 2011-01-11
I want to use one of my photos (a .JPG file) as a screen saver but cant find a way . surely it can be done easily. can someone tell me how?:confused:

I dropped this as not workable and now have not got fspot instead have the new photo manager in 10.10

---

### Post by adeee on 2011-01-11
import your photos into f-spot
then mark those photos as favorites
 ok now go system->preferences->screensaver 

change screensaver to f-spot photos

its work nice with me. another way i quote from 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/GettingStarted](http://ubuntuguide.org/wiki/Ubuntu:Feisty/GettingStarted)


[LIST]
[*]GLSlideshow is a screensaver that shows your images in a slideshow with smooth panning and fading.  To enable it:
[/LIST]
 System-->Preferences-->Screensaver-->GLSlideshow

[LIST]
[*]Feisty doesn't offer a way to edit the directory for the images  graphically. To set the image directory create a file called  .xscreensaver in your home folder (if it doesn't exist allready) and  place the key 'imageDirectory: /path/to/your/pictures' in it. You might  also want to add the key 'chooseRandomImages: True'.
[/LIST]
 If you had a preview running while editing   you'll have to reset  GLSlideshow by selecting another screensaver and the reselecting it.  
 cd ~
echo "imageDirectory:	/path/to/your/pictures" >> .xscreensaver
echo "chooseRandomImages:   True" >> .xscreensaver

[LIST]
[*]You can edit the behaviour of GLSlideshow using the file  /usr/share/applications/screensavers/glslideshow.desktop. Where it  (usually) says 'Exec=glslideshow -root' you can set options by adding  parameters which control things like how long every image should be  shown, how much you want to have it move or how long the transition  between pictures should be. GlSlideshow has it's own manpage where all  the options can be found (man glslideshow). However, these changes can  only be done as root!
[/LIST]
 And again, if you had preview running it will only show these changes after having selected another screensaver and reselecting  
 sudo gedit /usr/share/applications/screensavers/glslideshow.desktop
    find the line where it says Exec=glslideshow -root and replace it with something like
Exec=glslideshow -root -duration 16 -pan 6 -fade 6 -zoom 60

---

### Post by adeee on 2011-01-11
import your photos into f-spot
then mark those photos as favorites
 ok now go system->preferences->screensaver 

change screensaver to f-spot photos

its work nice with me. another way i quote from 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/GettingStarted](http://ubuntuguide.org/wiki/Ubuntu:Feisty/GettingStarted)


[LIST]
[*]GLSlideshow is a screensaver that shows your images in a slideshow with smooth panning and fading.  To enable it:
[/LIST]
 System-->Preferences-->Screensaver-->GLSlideshow

[LIST]
[*]Feisty doesn't offer a way to edit the directory for the images  graphically. To set the image directory create a file called  .xscreensaver in your home folder (if it doesn't exist allready) and  place the key 'imageDirectory: /path/to/your/pictures' in it. You might  also want to add the key 'chooseRandomImages: True'.
[/LIST]
 If you had a preview running while editing   you'll have to reset  GLSlideshow by selecting another screensaver and the reselecting it.  
 cd ~
echo "imageDirectory:	/path/to/your/pictures" >> .xscreensaver
echo "chooseRandomImages:   True" >> .xscreensaver

[LIST]
[*]You can edit the behaviour of GLSlideshow using the file  /usr/share/applications/screensavers/glslideshow.desktop. Where it  (usually) says 'Exec=glslideshow -root' you can set options by adding  parameters which control things like how long every image should be  shown, how much you want to have it move or how long the transition  between pictures should be. GlSlideshow has it's own manpage where all  the options can be found (man glslideshow). However, these changes can  only be done as root!
[/LIST]
 And again, if you had preview running it will only show these changes after having selected another screensaver and reselecting  
 sudo gedit /usr/share/applications/screensavers/glslideshow.desktop
    find the line where it says Exec=glslideshow -root and replace it with something like
Exec=glslideshow -root -duration 16 -pan 6 -fade 6 -zoom 60

---

### Post by adeee on 2011-01-11
import your photos into f-spot
then mark those photos as favorites
 ok now go system->preferences->screensaver 

change screensaver to f-spot photos

its work nice with me. another way i quote from 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/GettingStarted](http://ubuntuguide.org/wiki/Ubuntu:Feisty/GettingStarted)


[LIST]
[*]GLSlideshow is a screensaver that shows your images in a slideshow with smooth panning and fading.  To enable it:
[/LIST]
 System-->Preferences-->Screensaver-->GLSlideshow

[LIST]
[*]Feisty doesn't offer a way to edit the directory for the images  graphically. To set the image directory create a file called  .xscreensaver in your home folder (if it doesn't exist allready) and  place the key 'imageDirectory: /path/to/your/pictures' in it. You might  also want to add the key 'chooseRandomImages: True'.
[/LIST]
 If you had a preview running while editing   you'll have to reset  GLSlideshow by selecting another screensaver and the reselecting it.  
 cd ~
echo "imageDirectory:	/path/to/your/pictures" >> .xscreensaver
echo "chooseRandomImages:   True" >> .xscreensaver

[LIST]
[*]You can edit the behaviour of GLSlideshow using the file  /usr/share/applications/screensavers/glslideshow.desktop. Where it  (usually) says 'Exec=glslideshow -root' you can set options by adding  parameters which control things like how long every image should be  shown, how much you want to have it move or how long the transition  between pictures should be. GlSlideshow has it's own manpage where all  the options can be found (man glslideshow). However, these changes can  only be done as root!
[/LIST]
 And again, if you had preview running it will only show these changes after having selected another screensaver and reselecting  
 sudo gedit /usr/share/applications/screensavers/glslideshow.desktop
    find the line where it says Exec=glslideshow -root and replace it with something like
Exec=glslideshow -root -duration 16 -pan 6 -fade 6 -zoom 60

---

