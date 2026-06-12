---
title: "In Ubuntu 12.04 Guitar pro 6 files associates with guitar pro 6 program (.gp? opens)"
date: 2012-05-12
forum: General Help
---

### Post by Finn bjerke on 2012-05-12
[[IMG]http://getsatisfaction.com/assets/user_default_medium.png[/IMG]]("http://getsatisfaction.guitar-pro.com/people/finn_bjerke")        [Edit]("http://getsatisfaction.guitar-pro.com/arobas_music/topics/ubuntu_12_04_guitar_pro_6_assocciating_gp_guitar_pro_files/edit") 
  [Delete]("http://getsatisfaction.guitar-pro.com/arobas_music/topics/ubuntu_12_04_guitar_pro_6_assocciating_gp_guitar_pro_files") 
 
  [Finn Bjerke]("http://getsatisfaction.guitar-pro.com/people/finn_bjerke")    [a minute ago]("http://getsatisfaction.guitar-pro.com/arobas_music/topics/ubuntu_12_04_guitar_pro_6_assocciating_gp_guitar_pro_files#topic_3939863") 
   [B] Ubuntu 12.04 Guitar pro 6 associate .gp?  files (guitar pro files)     
 
 
 [/B]

 
  1. copy Into terminal  
> gksudo gedit '/usr/share/applications/GuitarPro6.desktop'2. Enter password


you want to add  %u 

This  
-------------------------------------------------------- 
    [Desktop Entry] 
    Encoding=UTF-8 
    Name=Guitar Pro 6 
    Comment=Tablature Edition Software 
    Exec=/opt/GuitarPro6/launcher.sh 
    Terminal=false 
    X-MultipleArgs=false 
    Type=Application 
    Icon=guitarpro6.png 
    Categories=Application;AudioVideo; 
--------------------------------------------------------------- 

Should be changed to this  (changing line 5) 
--------------------------------------------------------- 
    [Desktop Entry] 
    Encoding=UTF-8 
    Name=Guitar Pro 6 
    Comment=Tablature Edition Software 
    Exec=/opt/GuitarPro6/launcher.sh %U 
    Terminal=false 
    X-MultipleArgs=false 
    Type=Application 
    Icon=guitarpro6.png 
    Categories=Application;AudioVideo; 

------------------------------------------------------------- 

adding  %U 

save file, exit.  

log out log in  

Now you can right click .gp? files and attach them to guitar pro 6. Så you can start guitar pro 6 with any guitarpro file.  

Et voila (swedish expression??)

---

### Post by benlebowski on 2013-04-17
> **Finn bjerke said:**
> [[IMG]http://getsatisfaction.com/assets/user_default_medium.png[/IMG]]("http://getsatisfaction.guitar-pro.com/people/finn_bjerke")        [Edit]("http://getsatisfaction.guitar-pro.com/arobas_music/topics/ubuntu_12_04_guitar_pro_6_assocciating_gp_guitar_pro_files/edit") 
  [Delete]("http://getsatisfaction.guitar-pro.com/arobas_music/topics/ubuntu_12_04_guitar_pro_6_assocciating_gp_guitar_pro_files") 
 
  [Finn Bjerke]("http://getsatisfaction.guitar-pro.com/people/finn_bjerke")    [a minute ago]("http://getsatisfaction.guitar-pro.com/arobas_music/topics/ubuntu_12_04_guitar_pro_6_assocciating_gp_guitar_pro_files#topic_3939863") 
   [B] Ubuntu 12.04 Guitar pro 6 associate .gp?  files (guitar pro files)     
 
 
 [/B]

 
  1. copy Into terminal  
2. Enter password


you want to add  %u 

This  
-------------------------------------------------------- 
    [Desktop Entry] 
    Encoding=UTF-8 
    Name=Guitar Pro 6 
    Comment=Tablature Edition Software 
    Exec=/opt/GuitarPro6/launcher.sh 
    Terminal=false 
    X-MultipleArgs=false 
    Type=Application 
    Icon=guitarpro6.png 
    Categories=Application;AudioVideo; 
--------------------------------------------------------------- 

Should be changed to this  (changing line 5) 
--------------------------------------------------------- 
    [Desktop Entry] 
    Encoding=UTF-8 
    Name=Guitar Pro 6 
    Comment=Tablature Edition Software 
    Exec=/opt/GuitarPro6/launcher.sh %U 
    Terminal=false 
    X-MultipleArgs=false 
    Type=Application 
    Icon=guitarpro6.png 
    Categories=Application;AudioVideo; 

------------------------------------------------------------- 

adding  %U 

save file, exit.  

log out log in  

Now you can right click .gp? files and attach them to guitar pro 6. Så you can start guitar pro 6 with any guitarpro file.  

Et voila (swedish expression??)

Thanks, it works on 12.10 too :) I don't know if we can get a nice guitar pro icon instead of the default one ;) for the gpx files
Voila is a french expression by the way :)

---

