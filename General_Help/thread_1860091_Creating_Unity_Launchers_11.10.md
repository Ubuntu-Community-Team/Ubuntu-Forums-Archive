---
title: "Creating Unity Launchers 11.10"
date: 2011-10-14
forum: General Help
---

### Post by NoNameWill on 2011-10-14
I have read the link usually given for 11.04. There is no option when right clicking the desktop to create a laucher. 

The program I want to put in the sidebar is Ganttproject. It must be started with the sh command in terminal. No big deal. However I get a button in the panel that I added. But it won't start the program after I click it. 

A little back ground on the program. It's a cross platform java based program. It doesn't need to be installed in linux to run. The .sh script starts the program. 

I would like to use the graphic button if possible. I don't know where it is though. Not sure how to find it. I looked in the ganttproject folder and the /.local. Nothing that I could equate to the graphic. 

Just looking for a point in the right direction. TIA

---

### Post by talannon on 2011-10-18
I have been looking for an answer to this also but with no success. If I start the program from a terminal and select keep in launcher on the icon. It won't start either. So I have no other choice but to use alt-f2 and run the sh script from the history. I would prefer an icon...

---

### Post by NoNameWill on 2011-10-25
I have not tried this yet. But I found this youtube video yesterday for 11.10. Have to install a program from the repo's. 

```
sudo apt-get install --no-install-recommends gnome-panel
```

[http://youtu.be/GfTfc-DLtpU](http://youtu.be/GfTfc-DLtpU)

As you watch the video you will see that when the launcher is add to the dock. That it will not load the icon image but the launcher icon. 

I have since read the wiki on creating lenses. Dug into the filesystem for locations. Found them all. But felt over whelmed when I couldn't find anything that could at least guide me further; past the generic wiki Ubuntu put out for it. :confused:

---

