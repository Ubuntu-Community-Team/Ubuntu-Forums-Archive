---
title: "Emesene conky script"
date: 2011-04-15
forum: General Help
---

### Post by diev47 on 2011-04-15
Hello guys, I'm new here, although lurking ubuntuforums helped me a lot in the past... :D

I'm using **Emesene** as MSN alternative on Ubuntu and I wanted something to **display my online contacts on conky**  (pretty much like what you can do with this amazing script for Pidgin: [http://ubuntuforums.org/showthread.php?t=969933](http://ubuntuforums.org/showthread.php?t=969933)). Fact is that I could not find anything like that and I didn't want to switch back to pidgin. However I found a screenlet app that does the same task ([http://gnome-look.org/content/show.php/Emesene+Screenlet?content=76441](http://gnome-look.org/content/show.php/Emesene+Screenlet?content=76441)) so I tried to port it on conky.

The code that I'm posting does produce a list of your online contacts formatted according to a template file that is exactly the one for the ConkyPidgin script mentioned before.

As my code is actually a grand work of cut-paste-strip-optimize to merge the screenlet app (eliminating any need for screenlets) and conkypidgin, it is still somehow beta ( not all the features of conkypidgin are implemented) and requires a lot of testing and cleanup. Anyway it's a start and it actually works on my system.... ;)

I'm reporting a sample conky configuration file (conkyrc) calling the script and attached you find the script itself and a sample template:

###############
# - EMESENE - #
###############
${voffset 4}${font Droid Sans:style=Bold:size=8}EMESENE $stippled_hr${font}${if_running emesene}
${voffset 4}${execpi 10 ~/.conkycolors/bin/EmeseneConky_v2.py -o -l 10 -t /home/diev47/.conkycolors/templates/pidgin.template}${else}
${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Emesene is not running${endif}

---

