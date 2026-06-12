---
title: "Help with Startup Bash Script"
date: 2010-08-21
forum: General Help
---

### Post by ngrieb on 2010-08-21
I have written a bash script which I want to run right after all other desktop effects and everything else loads. The script works perfectly fine when I have already logged in fully and run it through the terminal, but it fails when I try to autorun it using the startup programs tool. I really don't know why this would happen. Can anyone help...it is driving me crazy. Thanks in advance.

---

### Post by ScarletWyvern on 2010-08-21
Could you give more details? Or even post the script, too?

---

### Post by M4he on 2010-08-21
[LIST]
[*]Make sure your script is marked as executable
[*]Check if the startup command points to the right location (i.e. if a script called script.sh is located in your personal folder and your user is called ngrieb, the startup command would be /**home**/ngrieb/script.sh)
[*]If you want to start it after all other things are loaded you might consider adding a sleep command to your script like:
[/LIST]
```
sleep 20;
```(this will make the script wait 20 seconds before executing the commands after this line. You can modify the amount of seconds according to your likings)

---

### Post by ngrieb on 2010-08-21
Wow, thanks for the quick replies. Ah yes I knew it was something simple I was missing. I changed it to executable now. I'll get back to you if it works now. 

If this doesn't work alone though, I have the script running out of my home dir right now. Do I have to move it to the usr dir for it to get the proper permissions to execute? I am calling other files from the script as well, should I move them too or just point to them too? Thanks.

---

### Post by M4he on 2010-08-21
> **ngrieb said:**
> If this doesn't work alone though, I have the script running out of my home dir right now. Do I have to move it to the usr dir for it to get the proper permissions to execute? I am calling other files from the script as well, should I move them too or just point to them too? Thanks.

SORRY my fault, this was a mistake which I corrected now in my post! It is /home/ not /usr/ 
...and it's still too early in the morning for me :D
No need to move anything.

---

### Post by ngrieb on 2010-08-21
Ya, still will not execute.... =-( It's early morning for me too, but bordering on the 1 am side of things anyway here is my script:
****************************************************************

#!/bin/sh
txt=$(xrandr);
#echo "${txt}";
res=${txt:37:11};
#echo "${res}";

if [ "${res}" = "1366 x 768," ];
then
    #echo "1366 x 768";
    fdclock -sta 5 -g 150x150+1134+75 &
    gnome-terminal --hide-menubar --window-with-profile="TerminalBar" &
    devilspie -a ~/DevilsDesktop/devilsterminalTV.ds &
    devilspie -a ~/DevilsDesktop/devilsclockTV.ds &
fi
if [ "${res}" = "1280 x 1024" ];
then
    #echo "1280 x 1024";
    fdclock -sta 5 -g 150x150+1062+75 & 
    gnome-terminal --hide-menubar --window-with-profile="TerminalBar" & 
    devilspie -a ~/DevilsDesktop/devilsterminalLCD.ds &
    devilspie -a ~/DevilsDesktop/devilsclockLCD.ds &
else
    #echo "1024 x 600";
    fdclock -sta 5 -g 150x150+850+75 &
    gnome-terminal --hide-menubar --window-with-profile="TerminalBar" &
    devilspie -a ~/DevilsDesktop/devilsterminalNB.ds &
    devilspie -a ~/DevilsDesktop/devilsclockNB.ds &
fi

****************************************************************

I'm trying to execute it like :
bash ~/path/script.sh
in the startup programs applet 

I was just looking at it and should I have /bin/bash ? Perhaps there is the problem...

---

### Post by M4he on 2010-08-21
> **ngrieb said:**
> bash ~/path/script.sh

Try removing the "bash" in front of it just put:
```
~/path/script.sh
```in the startup manager.

---

### Post by ngrieb on 2010-08-21
Nope, nothing. I have tried ~/path/./script.sh also. Is there a separate .bash extension perhaps? I have no idea why this is so hard...works fine from the terminal every time. How about editing the rc.local file? How would I stick the script in there? I'm using Lucid x64 if that has anything to do with it...?

---

### Post by M4he on 2010-08-21
And what about adding a
```
sleep 5;
``` at the top of the script (but after the #!/bin/sh line)?
Maybe the command is started too early...

---

### Post by vince2678 on 2010-08-21
try replaceing
 ```
if [ "${res}" = "1366 x 768," ];
then
```

with
```

if [ "${res}" == "1366 x 768" ]; then
```

and (2)
```
if [ "${res}" = "1280 x 1024" ];
then
```

with
```

if [ "${res}" == "1280 x 1024" ]; then
```

(3)

check if the files:
```
devilspie -a ~/DevilsDesktop/devilsterminalTV.ds
    devilspie -a ~/DevilsDesktop/devilsclockTV.ds
    devilspie -a ~/DevilsDesktop/devilsterminalLCD.ds
    devilspie -a ~/DevilsDesktop/devilsclockLCD.ds
    devilspie -a ~/DevilsDesktop/devilsterminalNB.ds
    devilspie -a ~/DevilsDesktop/devilsclockNB.ds
```

are accessible

(4) 

example script snippet with "if"
```
#!/bin/bash
#Zvikomborero Vincent Zvikaramba
IS_COMPIZ_RUNNING=$(pstree | grep -io compiz) #to see if compiz is running
TEMPFILEGAP=$(tempfile -p 1) #make temporary file and give a prefix of 1
TEMPFILEGAPII=$(tempfile -p 2) #make temporary file and give a prefix of 1
TFCURSOR_THEME=$(gconftool-2 --get /desktop/gnome/peripherals/mouse/cursor_theme) #gconf key that has the current cursor name
USR=/usr/share/icons/compiz-cursors
echo $TFCURSOR_THEME > $TEMPFILEGAP # check waaaay below
/usr/bin/gnome-appearance-properties-compiz-cursors %F #gnome-appearance-properties
CURSOR_SIZE=$(gconftool-2 --get /desktop/gnome/peripherals/mouse/cursor_size) #Cursor size
gconftool-2 --type integer  --set  /apps/compiz/general/allscreens/options/cursor_size $CURSOR_SIZE
CURSOR_THEME=$(gconftool-2 --get /desktop/gnome/peripherals/mouse/cursor_theme)
echo $CURSOR_THEME > $TEMPFILEGAPII #check below
cp $USR/$CURSOR_THEME /usr/share/icons/default/index.theme #update the theme
cp $USR/$CURSOR_THEME $HOME/.compiz-cursors-index.theme #gdm purposes

if [ "$IS_COMPIZ_RUNNING" == "compiz" ]; then #check if compiz is running
	diff $TEMPFILEGAP $TEMPFILEGAPII || /usr/bin/compiz --replace; #if so, check if theme has changed. If it has, restart. If not, compiz keeps going
else exit; #if not, continue as normal, ie if metacity, xfwm or other window manager is running, dont restart wm
fi

rm $TEMPFILEGAP $TEMPFILEGAPII # remove temporary files
```

this is from [compiz-cursors.deb]("http://www.4shared.com/file/HbZ0DCac/compiz-cursors-03.html") for making cursor themes work properly
in compiz.

---

### Post by ngrieb on 2010-08-21
Thanks, I have tried sleeping the script already to no avail, but the double equals was questionable to me because I looked at bash scripts and never saw it in that manner, but I will give it a try.

Nope, nothing. still does not work. The thing is that the script does not even seem to run at all on startup. The terminal and fdclock apps never open at all which means that the script is totally being ignored. Any more ideas as to why this wouldn't run? 

I'm going to try and move the scripts to a dir that has some privileges and see if that works.

Yes that did it, just moved the script to /opt/ and it worked.

---

