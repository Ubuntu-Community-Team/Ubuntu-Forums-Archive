---
title: "HI whenever I'm trying to install my own theme I get this"
date: 2010-09-02
forum: General Help
---

### Post by Lukasz Tarkowski on 2010-09-02
I followed this tutorial

[http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

Plymouth code

[PHP]    
    [Plymouth Theme]
    Name=DoctorWhoEleventhHour
    Description=Wallpaper only
    ModuleName=script

    [script]
    ImageDir=/lib/plymouth/themes/DoctorWhoEleventhHour/DoctorWhoEleventhHour
    ScriptFile=/lib/plymouth/themes/DoctorWhoEleventhHour/DoctorWhoEleventhHour.script

[/PHP]

Script code
[PHP]wallpaper_image = Image(“theeleventhhour.png”);
screen_width = Window.GetWidth();
screen_height = Window.GetHeight();
resized_wallpaper_image = wallpaper_image.Scale(screen_width,screen_height);
wallpaper_sprite = Sprite(resized_wallpaper_image);
wallpaper_sprite.SetZ(-100);
[/PHP]

Not sure maybe I made a a mistake :P

---

### Post by Lukasz Tarkowski on 2010-09-02
The problem is now my picture won't display on boot It is png 1680x1050
The resolution is set correctly :)

---

