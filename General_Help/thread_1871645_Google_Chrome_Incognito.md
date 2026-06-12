---
title: "Google Chrome Incognito"
date: 2011-10-29
forum: General Help
---

### Post by crutch145 on 2011-10-29
Does anyone know how to open the Chrome browser so that it is automatically in Incognito mode?  I know I can press Ctrl+Shift+N to open a window if in normal mode.  But I want to just click the icon and have it open incognito each time.  In Windows you can do this by adding --incognito after the shortcut target path.  Does Ubuntu allow a similar ability.  

Thanks,

Justin

---

### Post by vasa1 on 2011-10-29
> **crutch145 said:**
> Does anyone know how to open the Chrome browser so that it is automatically in Incognito mode?  I know I can press Ctrl+Shift+N to open a window if in normal mode.  But I want to just click the icon and have it open incognito each time.  In Windows you can do this by adding --incognito after the shortcut target path.  Does Ubuntu allow a similar ability.  

Thanks,

Justin

Just a wild newbie guess but maybe you have to modify the command to```
/opt/google/chrome/google-chrome --incognito
```

That works when entered in a terminal. Someone else may explain how to get stuff like that into the Launcher!

---

### Post by crutch145 on 2011-10-29
Do I just do that through the terminal?  If so, what is the command I need to enter?  I right clicked on the Chrome icon and it did not have anything for me to modify command code.  Need to break those Windows habits, lol.

---

### Post by New00Folder on 2011-10-29
[LIST=1]
[*]Right click on the panel and select "Add to panel".
[*]Select "Custom application launcher" and click "add".
[*]Fill "Name" and "Comment" field as desired.
[*]In command field type in "/opt/google/chrome/google-chrome --incognito" without quotes.
[*]Click on the spring icon.
[*]Browse to /opt/google/chrome and select "product_logo_24.png" to select it as the icon.
[*]Click close.
[/LIST]

---

### Post by Gillingham on 2011-10-29
If you are using unity then to alter the command you run when you click on the icon you will need to edit the google-chrome.desktop file.

The safest way I have come across is first to copy the file from
/opt/google/chrome/google-chrome.desktop
to ~/.local/share/applications/ 
```
cp /opt/google/chrome/google-chrome.desktop ~/.local/share/applications/ 
```

then you will need edit the .desktop file
and find the line that has exec in it, for me this is:
```
Exec=/opt/google/chrome/google-chrome %U
```
and replace it with
```
Exec=/opt/google/chrome/google-chrome --incognito
```

and make the file executable
```
chmod +x google-chrome.desktop
```

This will of course only work for the user in whose home directory you have the saved file.

Corrected typo in the copy command.

---

### Post by crutch145 on 2011-10-29
I am using version 11.10.  Is the Panel you are referring to the taskbar on the left side of the screen?  If I right click on that, nothing comes up unless I right click closer to one of the icons (but then the right click only applies to the icon I am right clicking on/near).

---

### Post by crutch145 on 2011-10-29
Gillingham - Here is the error I get when running the first command in the terminal: cp: missing destination file operand after `/opt/google/chrome/google-chrome.desktop~/.local/share/applications'

---

### Post by Gentoo64 on 2011-10-29
You forgot a space.

---

### Post by crutch145 on 2011-10-29
The only spaces in the fist command shown above is between cp and /opt

---

### Post by pricen2 on 2011-10-29
You need a space between the p of desktop and the ~.
The code after and including the ~ becomes the destination.

---

### Post by crutch145 on 2011-10-29
Thanks, Gentoo64 and pricen2!

---

### Post by Gillingham on 2011-10-29
Thank you all for spotting my mistake, I've now edited my original reply.

David

---

