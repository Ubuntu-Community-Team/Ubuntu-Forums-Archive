---
title: "Bumblebee UI won't work and onboard will only run unity 2d"
date: 2012-09-06
forum: General Help
---

### Post by rasmus91 on 2012-09-06
Hello there!

as the title says bumblebee ui wont work for me, its a small python script that allows for some UI control over bumblebee (which works just fine for me)

it gives me this when run from terminal:
```
Traceback (most recent call last):
  File "./bumblebee-app-settings", line 356, in <module>
    Appset = Applications_settings()	
  File "./bumblebee-app-settings", line 91, in __init__
    self.build_app_list()
  File "./bumblebee-app-settings", line 189, in build_app_list
    for app_info in self.file_set.get_apps_info():
  File "/usr/share/bumblebee-ui/DesktopFile.py", line 63, in get_apps_info
    app_config = desktop_file.get_app_config()
  File "/usr/share/bumblebee-ui/DesktopFile.py", line 144, in get_app_config
    self.app_exec= self.config.get('Desktop Entry','Exec')
  File "/usr/lib/python2.7/ConfigParser.py", line 618, in get
    raise NoOptionError(option, section)
ConfigParser.NoOptionError: No option 'Exec' in section: 'Desktop Entry'

```

i heard that bumblebee UI needs the folder ~/.local/share/applications
and thats there (in active use by other programs it seems) any help or suggestions?

oh, and also, when using my onboard intel card, it seems like the computer will only run ubuntu's unity 2d mode, and i was wondering if i could get it to run in 3D mode?
(It has done that before)

thanks :)

and on a sidenote, very nice work bumblebee team, you guys are have done a nice job.

Update: some stuff went  down and now my intel onboard card seems to run ubity 3d just fine. Im still puzzled as to why, but happy none the less. Im still trying to get a solution for the other thing though.

---

### Post by kwan7zero on 2012-09-22
Hey

after some python code investigation, I think my solution may be the solution to your problem! (hopefully...)

So in Config.py, we will notice and confirm that ~/.local/share/applications directory is indeed depended on by bumblebee-ui.

Furthermore, this error: File "/usr/lib/python2.7/ConfigParser.py", line 618, in get
    raise NoOptionError(option, section)
ConfigParser.NoOptionError: No option 'Exec' in section: 'Desktop Entry'

tells us that in a .desktop file, there seems to be no 'Exec' in the 'Desktop Entry' section within that directory.

So my solution was, I looked into ~/.local/share/applications directory and found that indeed, there was a .desktop file without the 'Exec' option in the 'Desktop Entry' section, which was a custom script that I had installed for mounting my Galaxy Nexus phone.

I added "Exec=" under the Desktop Entry section and voila! It works!


Hope this helps!

---

