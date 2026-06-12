---
title: "Writing a single shell script to change preview settings and a launcher's icon"
date: 2010-03-22
forum: General Help
---

### Post by gadolinio on 2010-03-22
Hello. I want to write a single shell script that allows me to, once executed from a panel launcher, change the image preview setting between &#8220;local files only&#8221; and &#8220;never&#8221;.
 Right now i have two tiny scripts, one for local files only and another one for never,
 that is:
 

 -----------------------------------------------------------------------------.
 #!/bin/bash 
  
 gconftool-2 --set /apps/nautilus/preferences/show_image_thumbnails --type string "never"
 -----------------------------------------------------------------------------.
 
and the other says string "local_only".


 But that means i need to have two launchers, because i don't know how to write the condition <<when set to &#8220;never&#8221;, change it to &#8220;local only&#8221;>>.
 

 And is it possible to make a script that also changes the launcher's icon when the preview config is set to one or the other value? That way i'd know what it is set to just by looking at it. It would act as a diagnostic and therapeutic tool XD
 

 Thanks in advance...

---

### Post by kaibob on 2010-03-22
> **gadolinio said:**
> But that means i need to have two launchers, because i don't know how to write the condition <<when set to “never”, change it to “local only”>>. 
 
And is it possible to make a script that also changes the launcher's icon when the preview config is set to one or the other value? That way i'd know what it is set to just by looking at it. It would act as a diagnostic and therapeutic tool XD

I have included below a shell script I use that toggles between panel locked and panel unlocked. You can easily insert your commands into this script.

I don't know how to change the panel icon to reflect the current state (neat idea though). Instead I use a zenity info dialog that times out in one second. 

```
#!/bin/sh

LOCKED=$(gconftool-2 --get /apps/panel/global/locked_down)

if [ $LOCKED = true ] ; then
   gconftool-2 --type bool --set /apps/panel/global/locked_down false
   zenity --info --timeout=1 --text="Panel Unlocked"
else
   gconftool-2 --type bool --set /apps/panel/global/locked_down true
   zenity --info --timeout=1 --text="Panel Locked"
fi
```

---

### Post by gadolinio on 2010-03-22
> **kaibob said:**
> I have included below a shell script I use that toggles between panel locked and panel unlocked. You can easily insert your commands into this script.

I don't know how to change the panel icon to reflect the current state (neat idea though). Instead I use a zenity info dialog that times out in one second. 

```
#!/bin/sh

LOCKED=$(gconftool-2 --get /apps/panel/global/locked_down)

if [ $LOCKED = true ] ; then
   gconftool-2 --type bool --set /apps/panel/global/locked_down false
   zenity --info --timeout=1 --text="Panel Unlocked"
else
   gconftool-2 --type bool --set /apps/panel/global/locked_down true
   zenity --info --timeout=1 --text="Panel Locked"
fi
```


Thanks! i'll modify that to adapt it

---

### Post by kaibob on 2010-03-22
> **gadolinio said:**
> Thanks! i'll modify that to adapt it
If you happen to find anything on the icon change, please post here if possible. I'll do a bit of research on this later. It's a good idea.

---

### Post by gadolinio on 2010-03-22
Mmm i can't adapt it because the properties i want to change don't have true/false values.
There are three posible values (never, local_only, and always, which i don't mean to use at all).
I'm stuck here...

---

### Post by gadolinio on 2010-03-22
> **gadolinio said:**
> Mmm i can't adapt it because the properties i want to change don't have true/false values.
There are three posible values (never, local_only, and always, which i don't mean to use at all).
I'm stuck here...

Got it. It needed to change type from "bool" to "string". Sorry for the dumb question.
So now the launcher is ready! THANKS A LOT for that piece of script...
Regarding the icon issue, i'm looking for the place where that info is located. I can't find the value/path of the icon i'm currently using (looked for it in gconf-editor with no success).

---

### Post by gadolinio on 2010-03-22
Did some improvements, but for some reason it's not working yet.
Desktop launchers are stored at /home/user/.gnome2/panel2.d/default/launchers.
My launcher could be "preview.desktop".
Opening it with gedit lets me see its properties, including icon path.
Now the thing is how to make the script modify it, without opening the file (as one wouldn't like to have such a window opened, and even less having to modify it manually, of course).
Well, i found a command that can replace a fragment of text in a file, only by giving the order to the terminal; no need to open nor edit anything else.

```

sed -i 's,text_to_be_replaced,new_text,g' /path/file.extension

```

It does modify the file, but the icon doesn't change...
Ahhh this is soooo close to achieving my primary goal.... :P

---

### Post by kaibob on 2010-03-22
Well, I've gotten to the same place and a bit further, but I don't think this is going to work. 

I created a test panel launcher, and the existing icon in the desktop configuration file was:

> Icon[en_US]=/usr/share/pixmaps/apple-red.png

I used the following sed command to change this entry:

```
sed -i 's/apple-red/apple-green/' /home/kaibob/.gnome2/panel2.d/default/launchers/panel-lock.desktop
```

Unfortunately, as you note, this does not change the icon. One option--which works but is of no help--is to reboot. The other is to use the following command:

```
killall gnome-panel
```

This does change the icon, but it's way too distracting. I spent some time with google, but I don't think there is a usable alternative.

---

### Post by gadolinio on 2010-03-22
Yes, restarting the panel does the job.
Now, all we need is to figure out a way to refresh it in order to make it use the new icon...
Killing the process and then starting it over works, but it's not straightforward nor neat enough...
There has to be a way.... This is almost done!

---

### Post by gadolinio on 2010-03-22
Done.
Didn't find a way to change a launcher's icon, but could do it with a drawer containing the launcher. It requires 2 clicks instead of just one, and it's not the objective i had in mind in the first place (reasons to keep the thread unsolved), but will do the job: change the image preview setting directly from the panel, without opening the nautilus-file-management-properties window, and doesn't take up more than a single element's place in the panel.

In the unlikely case of someone looking for this, i post it  :P

Here's the script:

```

#!/bin/bash

SHOW=$(gconftool-2 --get /apps/nautilus/preferences/show_image_thumbnails)

if [ $SHOW = "never" ] ; then
   gconftool-2 --type string --set /apps/nautilus/preferences/show_image_thumbnails "local_only"
   gconftool-2 --type string --set /apps/panel/objects/DRAWER/custom_icon "/usr/share/icons/hicolor/scalable/actions/jockey-enabled.svg"
else
   gconftool-2 --type string --set /apps/nautilus/preferences/show_image_thumbnails "never"
   gconftool-2 --type string --set /apps/panel/objects/DRAWER/custom_icon "/usr/share/icons/hicolor/scalable/actions/jockey-disabled.svg"
fi

```Add a drawer to the panel, and replace "DRAWER" in the script with its name.
To find its name: change the drawer's icon to one you can recognize, for example one located in your user folder. Then open a terminal, type in "gconf-editor", hit enter. In the tree that appears, go to apps/panel/objects; inside objects you'll have a list of keys called "object_*", where "*" is a number. Search through them to find out which one is the drawer you've just created: it will have your icon path as a value. Make sure that the option "custom_icon" is activated. Note the number after "object_"; and put that "object_*" where the script says "DRAWER".
Then all that is left is to add a launcher to the drawer, in order to execute the script.
Type: application in terminal.
Command: sh /path_to_script_file/script_name

That's it. If someone has a better method (very probable thing), please post it.
Finally, thanks [kaibob]("http://ubuntuforums.org/member.php?u=595193") for participating in this little experiment!

---

### Post by kaibob on 2010-03-23
That's an ingenious solution that would not have occurred to me. I rewrote my panel-lock script as you suggested and changed the panel icon to a drawer. It does take an extra click, but it shows the current status, which is more important. Thanks.

---

### Post by gadolinio on 2010-03-23
Yes, i think it's worth the extra click.
Note that it shows the current status only if the last change in that variable was made by this script. If you happen to lock the panel manually, the icon will remain as "unlocked", because the script isn't executed so it doesn't change the icon. If after that you click the launcher, you unlock it again, and the script will set the icon to unlocked... so it stays as it is. It always shows the last change made by the script.

---

### Post by kaibob on 2010-03-26
It occurred to me that I already have a drawer in my top panel (it contains links to web sites). So, I just use that to indicate panel-lock status, which means the script icon only takes a single click. It's all a bit of a kludge, but it does work quite well.

---

### Post by gadolinio on 2010-03-26
> **kaibob said:**
> It occurred to me that I already have a drawer in my top panel (it contains links to web sites). So, I just use that to indicate panel-lock status, which means the script icon only takes a single click. It's all a bit of a kludge, but it does work quite well.

Smart workaround... Who said that the launcher had to be inside the same drawer it modifies? If you already have a drawer or menu (those can also be used with this method), and you don't need to have a specific icon for it, why not use that? I hadn't thought about it...

---

