---
title: "Need Help with Blender"
date: 2010-04-25
forum: General Help
---

### Post by trucker33377 on 2010-04-25
First off let me say thanks to all those who help in here, your the greatest! 
I guess I'm a junkie for these free OP SYS. Ive had my Ubuntu tweaked and working I don't know how many times just to flub it up when a new release comes out. I started with 7.04 and now have 10.04. If I ever get this one tweaked I swear I will find the AAA for PC user's group and go threw the 12 step plan to recovery.
Just a little humor folks.
heres my deal I want to install Blender to be used to import sculpties into the game Second Life, at one time i had it done, but have lost that install. So if anyone could and would help me work threw this i would forever be in your debt.
Blender is installed Second Life uses a program called Primstar to be placed into the scripts folder ive done this but I get errors that have to do with python. This has caused me to lose 2 Ubuntu installs by fooling with python. Im just not that good at it and tend to try things hoping for the best. So Please help if know how to set this up.
Here are the errors from the term.

badboy@badboy-desktop:~$ blender
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Compiled with Python version 2.6.5.
Checking for installed Python... got it!
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/home/badboy/.blender/scripts/primstar/import_sculptie.py", line 53, in <module>
    from primstar import sculpty
  File "/home/badboy/.blender/scripts/primstar/sculpty.py", line 36, in <module>
    from primstar.uv_tools import add_map_uv, snap_to_pixels
  File "/home/badboy/.blender/scripts/primstar/uv_tools.py", line 44, in <module>
    from uvcalc_follow_active_coords import extend
ImportError: No module named uvcalc_follow_active_coords


Thank You

---

### Post by HenryCrun on 2010-05-22
Hi trucker33377,
Afraid it's not a solution to your python script problems but i may have found a solution to the:
'bt_audio_service_open: connect() failed: Connection refused (111)'
It seems to contribute to problems with my current game engine project (blender 2.49b + Ubuntu 9.10), sound would stop after some running time and this would make game engine freeze on escape key and make blender interface crash.
Adding 'DRIVERS = oss' to the file '/etc/openal/alsoft.conf' seems to remove these errors. I'm hoping it will cure the crashes, currently running a test..
Cheers.

---

