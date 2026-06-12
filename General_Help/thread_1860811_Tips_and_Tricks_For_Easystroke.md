---
title: "Tips and Tricks For Easystroke"
date: 2011-10-15
forum: General Help
---

### Post by Enterpart on 2011-10-15
Well I want to start this thread because most of Linux users are already familiar with Easystroke and the ones that aren't I feel can benefit greatly with this App. Infact I think Ubuntu should release this as default, its that powerful.

So this thread is about the tricks people have learnt what Easystroke can do and paste them for other users who are interested. If you feel your trick will benefit others and Easystroke has made your computing life easy then contribute to this thread for others.

Start by saying what the trick is and explain it here or post a link to other Ubunutforums that shows the trick.

I'll start and when I have more Tips I'll post them here and if anyone wants to contribute with tips then feel free to do so.

---

### Post by Enterpart on 2011-10-15
***_[COLOR="Red"]TIP Configure 9-button mouse per-application[/COLOR]_***

```
sudo apt get install easystroke
```

located in Applications -> Universal Access

**Now configure Easystroke.**

In Easystroke go to Preferences Tab -> Method to show gestures ->
-> None 

and tick Autostart Easystroke

_**Next add all buttons up to 9**_

In Easystroke go to Preferences Tab -> Additional Buttons ->
-> Add -> click empty box -> Button 1 -> OK 

Repeat process to add the remainder 8 buttons.

**Now match the buttons to send custom keystrokes to each application**

In Easystroke go to Actions Tab -> Add Application

(*Easystroke should get minimised at this point*)

click on the application that your going to set the buttons to work on.

**now to record the keystrokes follow this**

click *Add Action* -> 
-> Choose a name (if your using Alt+Left use the name "Back") ->
-> click Command -> and choose Key (Under Type Column) -> 
-> then press Alt and Left buttons together

-> click Record Stroke and use the button on the mouse that you want to associate with this command - left tilt is it?

**It will prompt you if your sure. Click Yes**

**now repeat the process for the remaining buttons.**

Once your done with that Application.

**Repeat the whole process with adding another application.**

[B]Do not use mouse buttons 1 2 or 3 as the "Record Stroke since they are used already"
[/B]

**_*Easystroke is much more powerful than just recording keystrokes. You can use the buttons to enter commands like you would in terminal.*_**

**ANOTHER TIP**

***_add another 2 scroll wheels_***. yes you can do this like as follows 

For example say you wanted to control zoom level of page with scroll wheel do this

click *Add Action* -> 
-> for name choose "Zoom in" ->
-> click Command -> and choose Key (Under Type Column) -> 
-> then press CTRL and + buttons together
-> click Record Gesture -> now hold Left mouse button down and flick the scroll wheel up

you should see a red [COLOR="red"]4[/COLOR], then 

click *Add Action* -> 
-> for name choose "Zoom out" ->
-> click Command -> and choose Key (Under Type Column) -> 
-> then press CTRL and - buttons together
-> click Record Gesture -> now hold Left mouse button down and flick the scroll wheel down

you should see a red [COLOR="red"]5[/COLOR]


now hold down left mouse button and then use the scroll wheel up or down on the browser. It should zoom in and out.

**you can repeat to get another scroll wheel by holding down the right mouse button instead of the Left to control say Brightness, volume toggle application...**

**You cannot use it on the buttons that you have already assigned to perform an action since as soon as you press that button it will trigger that action!**

***_LAST TIP_***

you can **create 8 extra buttons** by click and hold to create another action for each of your buttons. by doing this..

In Easystroke click Advanced tab -> and tick "Timeout Gestures"

now go back to Actions Tab to create a another Action.

click *Add Action* -> 
-> for name choose "firefox" ->
-> click Command -> and choose Command (Under Type Column) -> 
-> then type "firefox" without the brackets
-> click Record Gesture -> now hold a mouse button (other than left mouse button AND HOLD IT FOR TWO SECONDS then let go.

click yes.

then when you hold down that button a firefox window should pop up? you dont have to use firefox it can be any command or keystrokes.

**you can Repeat the last tip to include other buttons if you wanted**

[COLOR="Red"][B][I][U]You asked to Configure 9-button mouse per-application
I've given you 17 button mouse per application with another two scroll wheels.
[/U][/I][/B][/COLOR]
Peace

---

### Post by Enterpart on 2011-10-15
[COLOR="Red"]***_TIP set up tap zones of touchpad_***[/COLOR]

To chnage the area of Tap zones have a look at this

[ATTACH]204253[/ATTACH]

taken from synaptics manpage

```
man synaptics
```

as you can see we need to change the parameters of LeftEdge RightEdge TopEdge and BottomEdge.

These can be changed with the commands

```
synclient LeftEdge=2196
```

and you need to change all edges i.e. synclient RightEdge=....

You can guess the numbers or use this command

```
synclient -m 100
```

but first you would need to enable SHMConfig

do this by the following method

Enter this command, it will give you access to change files on nautilus

```
sudo nautilus
```

Enter Password -> go to "File System" -> "USR" -> "share" -> "X11" -> "xorg.conf.d" -> "50-synaptics.conf"

now you should see this

Section "InputClass"
        [INDENT]Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"[/INDENT]
EndSection

you want to add **Option "SHMConfig"  "true"** so it looks like this 

[ATTACH]204254[/ATTACH]

save and exit

now enter "synclient -m 100" in terminal 

```
synclient -m 100
```

and you should see this

    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000     1 5855   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0

were interested in the x and y numbers
touch your finger on the touchpad were you want the corner of the area 3 you want (see first picture were the TopEdge meets the RightEdge)
you should see the terminal output numbers with a big number around 5000 on x and a number around 2500 in y
the x cordinate is the RightEdge and the y is the TopEdge
record on a piece of paper
then again tap the touchpad at the bottom left at were you want The Leftedge meet the BottomEdge (see again first picture)

the numbers I get are x=2254 y=3654 (each touchpad has different dimensions and you might want a bigger area for the taps)
now here the x=LeftEdge and y=BottomEdge
again record these down

thats all we need so in the terminal you can use this to change the location of the Edges

```
synclient RightEdge=4905
```
```
synclient TopEdge=2431
```
```
synclient LeftEdge=2196
```
```
synclient BottomEdge=3689
```

(these are my own that Ive calibrated with my touchpad and preference so enter the ones you jotted down)

now thats all and you can use this command to see if you changed them

```
synclient -l
```

lastly you can add these to xorg.conf.d (see above to recap) and you should have them permantley saved

and the way you type them in as follows

Option "RightEdge"  "4905"

dont forget its one space between Option and "RightEdge" and two spaces between "RightEdge" and "4905"

and the same with the other 3 save and reboot and then its complete!

---

### Post by Enterpart on 2011-10-15
***_[COLOR="Red"]TIP 8 tap zones controlling key strokes or any commands plus control firefox chrome[/COLOR]_***

You will need easystroke and thats all

```
sudo apt-get install easystroke
```

youtube video showing how to work easystroke

[www.youtube.com/watch?v=sOWXAyOde18]("http://www.youtube.com/watch?v=sOWXAyOde18")

add an action Name it anything type:command and paste this in the command box

```
#!/bin/sh
#
# Use xinput --list-props "SynPS/2 Synaptics TouchPad" to extract data
#

# Set multi-touch emulation parameters
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

# Disable edge scrolling
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0 

# This will make cursor not to jump if you have two fingers on the touchpad and you list one
# (which you usually do after two-finger scrolling)
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110

synclient tapbutton2=2
synclient CircularScrolling=1
synclient LTCornerButton=9
synclient RTCornerButton=10
synclient RBCornerButton=11
synclient LBCornerButton=12
synclient TopEdge=2431
synclient RightEdge=4700
synclient BottomEdge=3689
synclient LeftEdge=2356


```

this will add 2 finger scrolling, 2 finger tap for middle click and circular scrolling also

now "Record gesture" (see the video) you can set the Gesture button to be left click if you want. Record a circle for this gesture. NOW PERFORM THE GESTURE
your settings will have changed to check use this

```
synclient -l
```

and check what it says at TopEdge it should say 2431

ONLY THEN WILL THE NEXT PART MAKE SENSE

now in easystroke go on Preferences tab and click additional Buttons
then click add
then click the box with no writing on and choose 9 press OK and repeat adding buttons 10 11 12

now your touchpad is configured with the corners as button 9 on top left and it goes clockwise with button 10 top right, button 11 bottom right and button 12 bottom left.

now in easystroke go on "Advanced" tab and check timeout gestures (it should now have a tick next to it)

to set the corner buttons with key strokes do this

"add action" then for type click key record the key (you can press 2 or 3 keys at once and it will record those key strokes
once you click Record Stroke and tap on a corner of the touchpad
(make sure its the corner) it will pop up with 

"You are about to bind an action to a single click.  This might make it difficult to use Button 1 in the future.  Are you sure you want to continue?"

thats why make sure its at the corners and your activating the buttons 9-12 and not button 1

press yes and you should have set one corner as a keystroke such as Alt+left arrow for backpage on internet if you so wish

IF YOU ACCIDENTLY MISS THE CORNER KEY just press "Return" key on keyboard then "right arrow" and "return" key again it will delete the gesture and you can start again.

now in the future you can easily change the keystroke associated with each corner

set the other 3 corners

now for the last four keys all you have to do is double tap on any corner and hold (WHICH YOU USE A GESTURE) for 2 seconds then let go. which will count as another button. each corner can be used like this.

you can also open applications like firefox for example, after you add an action, in the type choose command and then past

```
firefox
```

basically you can do anything since you got control of the terminal this way.

oh and to load easystroke at boot you want to go to preferences and check "autostart easystroke" and at boot you want to perform the initial gesture to activate that big command I gave at the beginning

---

### Post by Enterpart on 2011-10-15
***_[COLOR="Red"]TIP google a highlighted word like scrybe gestures.[/COLOR]_***

Some of you will be familiar with Easystroke and know of its potential, but did you know you can use the main feature of Scrybe using Easystroke that is highlight a word/phrase - perform a gesture and a website of your choice pops up with your search already.

Well you will now. Very simple you will need two applications.
 If you haven't already got Easystroke just download from terminal
```
sudo apt-get install easystroke
```

now download xsel
```
sudo apt-get install xsel
```

now a command that will search a phrase in youtube and just pop up the window with the search completed

```
google-chrome "http://www.youtube.com/results?search_query=`xsel -p | tr [:space:] +`&aq=f"
```

If your using firefox then replace google-chrome with firefox

now use whatever gesture you like lets say a gesture in shape of a y.

then your good to go. Test with this "Never Gonna Give You Up"
Enjoyed that :p

the way it works is using this 
```
`xsel -p | tr [:space:] +`
``` 
in the url
in place of what ever search term you used and xsel stores whatever you highlighted in x selection.

the neat thing is once you highlighted a phrase you can use it to access more websites without having to go back to highlighting the phrase again. but once a new phrase is selected whatever search you perform will use that phrase.

if you dont know how I knew what to type to get that url then its simple. go to youtube.com
then type test
now whatever comes in the url after you typed that copy and past it in your command in easystroke but replace "test" with "`xsel -p | tr [:space:] +`"

you can even use on word documents, you dont have to highlight on internet

for convenience sake I'll give you a list of the ones I use

**Google Search**
```
google-chrome "http://www.google.co.uk/search?sourceid=chrome&ie=UTF-8&q=`xsel -p | tr [:space:] +`"
```

**Wikipedia**
```
google-chrome "http://en.wikipedia.org/w/index.php?title=Special:Search&search=`xsel -p | tr [:space:] +`"
```

**Google Images**
```
google-chrome "http://www.google.co.uk/images?hl=en&source=hp&biw=999&bih=581&q=`xsel -p | tr [:space:] +`&gbv=2&aq=f&aqi=&aql=&oq="
```

**Google News**
google-chrome ```
"http://www.google.co.uk/#hl=en&sugexp=llsfp&xhr=t&q=`xsel -p | tr [:space:] +`&cp=3&um=1&ie=UTF-8&tbo=u&tbs=nws:1&source=og&sa=N&tab=wn&fp=2c94a2341fe34a2f"
```

**Amazon**
```
google-chrome "http://www.amazon.co.uk/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=`xsel -p | tr [:space:] +`&x=0&y=0"
```

**Bing Maps**
```
google-chrome "http://maps.google.co.uk/maps?hl=en&q=`xsel -p | tr [:space:] +`&um=1&ie=UTF-8&sa=N&tab=wl"

```
Easystroke is being developed by Tom Jaeger so thankyou Tom and if you have any more hints anyone please write them here

[http://sourceforge.net/apps/trac/easystroke/wiki/TipsAndTricks](http://sourceforge.net/apps/trac/easystroke/wiki/TipsAndTricks)

---

