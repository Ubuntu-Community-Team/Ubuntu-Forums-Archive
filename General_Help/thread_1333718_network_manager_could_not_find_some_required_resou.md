---
title: "network manager could not find some required resources."
date: 2009-11-21
forum: General Help
---

### Post by pearldrums on 2009-11-21
I keep getting this message when I load up Kubuntu: "The NetworkManager applet could not find some required resources.  It cannot continue." and as it says NetworkManager doesn't work. I found[ this post]("http://ubuntuforums.org/showthread.php?t=791993") which didn't get me any answers but did say that it might have to do with my icons folder. I was recently modifying /usr/share/icons, and I printed out all the files in case I'm missing something.


```
levi@Yoda:/usr/share/icons$ ls
application-default-icon.png  default.kde        gnome                          Human            redglass    xchat.xpm
cab_extract.png               default.kde4       handhelds                      Humanity         skype.png
cab_view.png                  DMZ-Black          hicolor                        Humanity-Dark    Tangerine
crystalsvg                    DMZ-White          HighContrastInverse            HumanLoginIcons  Tango
default                       elementaryXubuntu  HighContrastLargePrintInverse  oxygen           whiteglass
levi@Yoda:/usr/share/icons$ cd /usr/share/icons/elementaryXubuntu/
levi@Yoda:/usr/share/icons/elementaryXubuntu$ ls
actions  animations  apps  categories  devices  emblems  icon-theme.cache  index.theme  mimes  places  status
levi@Yoda:/usr/share/icons/elementaryXubuntu$ 

```

Any Ideas?

---

