---
title: "Need  help creating a script to load Flatout 2"
date: 2011-05-11
forum: General Help
---

### Post by AwesomeX on 2011-05-11
Hello, for days i have been try to get a working launcher for the racing game FlatOut 2.

I have tried almost every thing and it always comes up with a error ether the .EXE didn't load its main files from the games folder or it doesn't work at all and i REALLY need some help.

I am on Ubuntu 11.04 with the classic gnome interface.

And i am trying to make a launcher for my gnome main menu to play the game from there.

To make it simple i want it so that i can hit the gnome main menu button up top and go to the category Games and select Flatout 2 and play from there.

Now there are two problems with this.
1. FlatOut 2 needs to load its main data files from its folder.
2. I don't know how to fix that.  :(

So if theres a way to create a shell script or something to load the games folder THEN the .EXE that would be great if you guys could give me a full tutorial or something to help me out.

Thanks!  :)

---

### Post by anaconda on 2011-05-11
```
#!/bin/bash

pushd ~/.wine/drive_c/Program\ Files/flatout/
#cd ~/.wine/drive_c/Program\ Files/flatout/

wine flatout2.exe

popd

```
just (edit and) save this on your home directory as. eg. 
flatout2.sh
then make the file executable with: chmod a+x flatout2.sh
and then you can make a launcher, that launches that script....

Edit:
forgot to say, that edit the "script" and change the directories and the actual wine command to be correct....
for some reason many wine applicatios need to have the "current" folder to be on the windows "disk"

---

### Post by AwesomeX on 2011-05-11
Thanks im gonna try this il let ya know if it works!

---

### Post by AwesomeX on 2011-05-11
THANK YOU THANK YOU THANK YOU!!!
you really saved me man i would kiss ya if i could
but yeah it works one hundred million%%% THANKS!!

---

