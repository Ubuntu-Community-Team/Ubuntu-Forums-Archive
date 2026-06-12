---
title: "Trackman Marble enable scroll lock (3button mouse)"
date: 2010-05-28
forum: General Help
---

### Post by dogafin on 2010-05-28
[IMG]http://www.bluesnews.com/miscimages/tmmarble150.gif[/IMG]  [IMG]http://photos-b.ak.fbcdn.net/hphotos-ak-snc3/hs420.snc3/25309_392217965024_515170024_4202722_257736_s.jpg[/IMG]
im currently using this mouse, which i have painted all red so it isnt as ugly.

i have enabled the scroll lock on this mouse (middle button) before switching to lucid and it continued to work even after the upgrade, however, due to other things that happened to my pc i had to i do a fresh install and had lost the setting in /X11/xmodmap file, i redid the steps onto making xmodmap file and adding 

add mod3 = Scroll_Lock

but unfortunately this no longer works for me.

i wish i had done the fix when i booted up onto 8.10 cd and continue on with the upgrade to 10.4 and see if it keeps the settings but i was more engrossed into upgrading that i didnt do any customization until i was done upgrading to 10.4 - i hope i dont have to resort to that!! cause every upgrade lasted as long as 1-2 hours!

i also have a problem with the ATI driver, and i cannot activate compiz

however i am more worried about my mouse working. i need help in remapping my mouse buttons. middle button only works for opening links in a different tab, and scrolling IF it is clicked right on top of the scrollbar. i want the round icon to appear with directional arrows 

[IMG]http://img.photobucket.com/albums/v102/_H_E_L_/th_Screenshot-Facebook-MozillaFirefox.png[/IMG]
but anyway, for me to scroll the webpage l+r or up+down, id have to click the 2nd button (middle) anywhere in the window then move the marble instead of having to chase for the scrollbar.... i want THAT feature back!

any help would be greatly appreciated since this inconvenience is the most annoying thing!

i duno if this helps
> dogafin@dogafin-desktop:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech USB Keyboard          	id=9	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech TrackMan                  	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard          	id=8	[slave  keyboard (3)]


xev
> ButtonPress event, serial 33, synthetic NO, window 0x7600001,
    root 0x6a, subw 0x0, time 16094699, (128,92), root:(134,156),
    state 0x10, button 2, same_screen YES


---

### Post by dogafin on 2010-05-28
I FOUND IT!! its an easy fix and it isnt about 'remapping' at all!

Type 'about:config' into firefox and press enter to view your Firefox configuration settings

Here is the problem: general.autoScroll set to 'False'. double click the word True/False to toggle the value.

so you should look for
> general.autoScroll default boolean false
then change the value to
> general.autoScroll user set boolean true

[IMG]http://img.photobucket.com/albums/v102/_H_E_L_/Screenshot-aboutconfig-MozillaFi-1.png[/IMG]

:popcorn:

---

