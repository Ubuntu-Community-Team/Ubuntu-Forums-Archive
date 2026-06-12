---
title: "Help with menu , Well kinda :)"
date: 2011-09-13
forum: General Help
---

### Post by josephmills on 2011-09-13
):P 

I would like to thank you for taking the time to read this. 


so I have a menu set up that I would like to play with. But here is the thing.I want to rename some things . 

to give you a sample of what my menu looks like I have a services tab that  I use for starting apache changing ruby versions and ect. After making the menu it did not come out right I mean it works but.... 
 

Here is an example of  Apache 



**/etc/xdg/menus/applications-merged/applications-local.menu**
```


<Menu>
   <Name>Aphche</Name>
   <Layout>
    <Merge type="files"/>
    <Filename>alacarte-made.desktop</Filename>
    <Filename>**alacarte-made-1.desktop**</Filename>
   </Layout>
   <NotDeleted/>
   <Include>
    <Filename>alacarte-made.desktop</Filename>
    <Filename>**alacarte-made-1.desktop**</Filename>
   </Include>
  </Menu>



```



desktop directory for apache 
```

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Directory
Icon[en_US]=folder
Name[en_US]=Apache
[SIZE=2]**Name=Apache**[/SIZE]
Icon=folder



```


Just a sample of 
/usr/share/applications 
```
alacarte-made-195.desktop   alacarte-made-449.desktop  alacarte-made-702.desktop  alacarte-made-957.desktop
alacarte-made-196.desktop   alacarte-made-44.desktop   alacarte-made-703.desktop  alacarte-made-958.desktop
alacarte-made-197.desktop   alacarte-made-450.desktop  alacarte-made-704.desktop  alacarte-made-959.desktop
alacarte-made-198.desktop   alacarte-made-451.desktop  alacarte-made-705.desktop  alacarte-made-95.desktop
alacarte-made-199.desktop   alacarte-made-452.desktop  alacarte-made-706.desktop  alacarte-made-960.desktop
alacarte-made-19.desktop    alacarte-made-453.desktop  alacarte-made-707.desktop  alacarte-made-961.desktop
[SIZE=2]**alacarte-made-1.desktop**[/SIZE]     alacarte-made-454.desktop  alacarte-made-708.desktop  alacarte-made-962.desktop
alacarte-made-200.desktop   alacarte-made-455.desktop  alacarte-made-709.desktop  alacarte-made-963.desktop
alacarte-made-201.desktop   alacarte-made-456.desktop  alacarte-made-70.desktop   alacarte-made-964.desktop
alacarte-made-202.desktop     
```




**/usr/share/applications/alacarte-made-1.desktop **
```

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=stop
Name[en_US]=Stop Apache
Exec=kdesudo stop-apache
**Name=Stop Apache**
Icon=stop


```







Now do you see how everything is called alacarte this is bothersome to me and I would like to fix this. I have been able to fix all the usr/share/applications/


but is I do that first then the menu goes bonkers ;)  because of 
/etc/xdg/menus/applications-merged/applications-local.menu

```
 <Merge type="files"/>
    <Filename>alacarte-made.desktop</Filename>
    <Filename>alacarte-made-1.desktop</Filename>
```





so I have to backed up /usr/share/applications/ <----the good one that is. 

and I figure if I can find a way to make a script that changes it for me 


this is what I came up with  If there is a way to use 

/usr/share/applications/alacarte-made-1.desktop 

with sed or awk to pull the[COLOR=Red] Name=[SIZE=3]Stop Apache [/SIZE] [COLOR=Black]

out of the folder and then replace it with the one from 
[/COLOR][/COLOR]/etc/xdg/menus/applications-merged/applications-local.menu


So basically all I want is for my files not to be named alacarte any more and to have a working menu. that is clean.  Also learning bash is fun :p    

I would like to thank you again for reading this and hope to hear from you soon 

Joseph 
[COLOR=Red][COLOR=Black]
[/COLOR][/COLOR]

---

### Post by josephmills on 2011-09-14
:popcorn::popcorn:BUMP :popcorn::popcorn:

---

