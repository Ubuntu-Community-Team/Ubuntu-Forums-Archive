---
title: "how to create your own mouse pointer"
date: 2010-03-27
forum: General Help
---

### Post by shantiq on 2010-03-27
i have many mouse pointers in the .ico also .ani and .cur format from my old windows days SEE image attached

would also like to make new ones


and really want to turn them into a format which works on ubuntu since the choice of pointers is only 6!!!!!!!!!!!!

i found a way to install X11 cursors from [gnome-look.org]("http://gnome-look.org/index.php?xcontentmode=36&PHPSESSID=e7fdde03d7afbaccb2302c2480f1663e")    download then save to .icons in the hidden part (control H) of my home folder then go system/preference/appearance/customize/pointers   


but even then you have to install a whole lot of files to change one pointer and i see no way of making/installing my own

is there a more straightforward way?
ubuntu/linux are about freedom

and here i am at the moment very restricted


please if you have that knowledge point me ha ha in the right direction    thank you
;);)

---

### Post by shantiq on 2010-03-27
this is from a [pdf]("http://www.mediafire.com/?8zyxnhzm9ta") linked [on this post by CoLeNi]("http://ubuntuforums.org/showthread.php?t=102129&highlight=X11&page=2"). I have also attached it here


SEE BELOW ( there are illustrations which you will find only in the Pdf )


on the plus side i have found an excellent readymade set of X11 cursors at [http://gnome-look.org](http://gnome-look.org) it is called [ComixCursors]("http://gnome-look.org/content/show.php?content=32627&vote=good&tan=22841470") and they are a smart design also with a left handed option   very very professional


As regards creating one's own it looks to me like murder on a stick and the only way !?!! to make your own new mouse pointer. Talk about cumbersome.  At least there is a way



       X11 Mouse Theme Tutorial
       To make a theme you need the picture and/or pictures (PNG format) to make either a static or animated
       cursor respectfully. You also need a configuration file for each picture. This configuration file tells what and
       where the hotspot and refresh rates are for each picture.They all have to be in one directory. You then have to
       run "xcursorgen" (which will read the configuration file and PNG files and output a cursor file. Sounds
       confusing? It's not really. I'll explain each detail below.
       Pictures (must be in PNG format)
       If you make a static cursor (that is a non-animated one) you just need one picture like this:
       Example 1: Static Cursor
       If you want to make an animated cursor you need a picture for every frame you want to animate like this: (All
       these pictures will make one cursor.)
       Example 2: Animated Cursor
       (Below are some quotes from a rough tutorial I found. He couldn't write very good English so it took me a
       while to figure out what he was trying to say. This part though he was very good but sparse on details.
       Hopefully I can fill in the gaps for you.)
       The picture (PNG) files you must make (you don't have to make all of these but if you want a complete theme
       then it is advisable.) are:
          ```
arrow
          based_arrow_up
          bd_double_arrow
          bottom_left_corner
          bottom_right_corner
          bottom_side
          circle
          copy
          crossed_circle
          crosshair
          double_arrow
          draft_large
          draft_small
          fd_double_arrow
          fleur
          h_double_arrow
          hand
          hand1
          hand2
          left_ptr ----->Main Pointer
          left_ptr_watch
          left_side
1 of 8                                                                                                         02/03/2008 04:57 PM
                                                                                                     about:blank
       link
       question_arrow
       right_ptr
       right_side
       sb_down_arrow
       sb_h_double_arrow
       sb_left_arrow
       sb_right_arrow
       sb_up_arrow
       sb_v_double_arrow
       top_left_arrow
       top_left_corner
       top_right_corner
       top_side
       v_double_arrow
       watch
       X_cursor
       xterm ---> I-Beam
```
       ....................................................................
        NOTE:
        If you want make a completely usable theme you must make this xcursors too:
        ```
00008160000006810000408080010102 --> sb_v_double_arrow
        028006030e0e7ebffc7f7070c0600140 --> sb_h_double_arrow
        03b6e0fcb3499374a867c041f52298f0 --> crossed_circle
        08e8e1c95fe2fc01f976f1e063a24ccd --> left_ptr_watch
        14fef782d02440884392942c11205230 --> h_double_arrow
        2870a09082c103050810ffdffffe0204 --> v_double_arrow
        3ecb610c1bf2410f44200f48c40d3599 --> left_ptr_watch
        4498f0e0c1937ffe01fd06f973665830 --> fleur
        6407b0e94181790501fd1e167b474872 --> copy
        640fb0e74195791501fd1ed57b41487f --> link
        9d800788f1b08800ae810202380a0822 --> hand1
        c7088f0f3e6c8088236ef8e1e3e70000 --> top_left_corner
        d9ce0ab605698f320427677b458ad60b --> question_arrow
        e29285e634086352946a0e7090d73106 --> hand
        fcf1c3c7cd4491d801f1e1c78f100000 --> top_right_corner
```
       ...............................................................................
       If you don't make this xcursors you don't hope that your theme work well ...
       You must make this xcursors with the same image that you've maked the action xcursor
       for example ...
       xcursorgen config1.in cursors/question_arrow
       Then you must make this too:
       xcursor config1.in cursors/d9ce0ab605698f320427677b458ad60b
2 of 8                                                                                      02/03/2008 04:57 PM
                                                                                                                        about:blank
       Configuration File
           This file must have some information about the xcursor. The general structure of the config files are:
           [size] [x_cordinate_cursor] [y_cordinate_cursor] [direction_of_image_file] [refresh_task_of_xcursor]
           This is a example of the content of a config file:
```
           34 10 4 png_images/pointer.png 1000
```
           This is a example if you want make a animated xcursor :
           ```
34 10 4 png_images/pointer1.png 100
           34 10 4 png_images/pointer2.png 100
           34 10 4 png_images/pointer3.png 100
           34 10 4 png_images/pointer4.png 100
           34 10 4 png_images/pointer5.png 100
```
       We will take his example from above (34 10 4 png_images/pointer.png 1000) and I will explain each part.
       1. The 34 is the actual size of the picture. This will change depending on the size of your picture. Take for
       example this picture:
       It is 28x28 pixel big so you would enter 28
       If it were 34x34 you would enter 34 etc.
       2. The X,Y coordinates (or HotSpot) looks like this: (This is the point at the end of the cursor you will use to
       select stuff with.) You'll need these for every picture you want to convert.
       To get these open up your picture in Gimp and put you mouse cursor right at the tip of the pointer where the
       red dot is in the picture. Gimp will tell you the X and Y coordinate down in the status bar. In the example
       above where the red spot is it turns out to be 4(X), 2(Y) so now we have "28 4 2 " for our configuration file.
       3. The png_images/pointer.png is the name of your picture. In my example above the name of my PNG file is
       is "cursor.png."
       So now we have "28 4 2 cursor.png"
       4. The 1000 is the refresh rate the cursor will have. This is a good default for static cursors but you might
       have to slow it down or speed it up on an animated cursor because this is what produces your animation
3 of 8                                                                                                         02/03/2008 04:57 PM
                                                                                                                   about:blank
       effect. Are example configuration entry know looks like this: "28 4 2 cursor.png 1000" (Note I used 1000
       because in this example we are making a static cursor.)
       As noted from his quote when you make an animated cursor you need to make a configuration entry for each
       pictures that make up the animated cursor.
       To make a configuration file open GEdit make your configuration entries and save with the extension ".in"
       Remember "static cursors" will only have on entry in there ".in" file. Example: "based_arrow_down"
       28 13 13 based_arrow_down.png 1000
       The ".in" file for an animated cursor looks like this. Example: "background [1-8]"
       ```
32 5 2 background_1.png 100
       28 4 2 background_2.png 100
       28 4 2 background_3.png 100
       28 4 2 background_4.png 100
       28 4 2 background_5.png 100
       28 4 2 background_6.png 100
       28 4 2 background_7.png 100
       28 4 2 background_8.png 100
```
       When you get done your directory should look something like this:
4 of 8                                                                                                    02/03/2008 04:57 PM
                                                                                                                        about:blank
       Xcursorgen File Generation
         The command that we use is "xcursorgen"
         The use of this command is as follows:
         xcursorgen [config_file] [destination_of_xcursor] --->"destination_of_xcursor" This means two-fold.
         First a directory name. It's a good idea always to use "cursors" as this will create a folder inside your
         working folder called "cursors " where you cursor files will be stored on output. The second part means
         one of the predefined cursor names from the list of xcursors above. Basically the cursor your trying to
         make with your pictures. Below in his example he is using the example left_ptr and as I noted above this
         is the main cursor. The easiest way I found of figuring out what is what is to download a theme and see
         which ones correspond to which predefined names.
         for every one cursor.
         This is a example:
5 of 8                                                                                                         02/03/2008 04:57 PM
                                                                                                                      about:blank
          xcursorgen config1.in cursors/left_ptr
       Take for example "xcursorgen circle.in cursors/circle" would output a cursor file called" circle" in the
       directory of "cursor". Notice "circle" is one of the predefined names from the list that we need to make a
       theme.
       You can make a bash script that will automate this process. It looks like this:
          ```
#!/bin/sh
          #This is a shell script for make the xcursor files
          echo This is a script for make the xcursor files of your theme
          echo .
          echo ..
          echo ...
          echo ....
          echo .....
          echo ......
          echo .......
          echo ........
          echo .......
          echo ......
          echo .....
          echo ....
          echo ...
          echo ..
          echo .
          echo Making the files ... please wait ...
          xcursorgen left_ptr_watch.in cursors/left_ptr_watch
          xcursorgen left_ptr_watch.in cursors/08e8e1c95fe2fc01f976f1e063a24ccd
          xcursorgen hand1.in cursors/hand1
          xcursorgen hand1.in cursors/hand2
          xcursorgen left_ptr.in cursors/left_ptr
          xcursorgen xterm.in cursors/xterm
          xcursorgen crossed_circle.in cursors/crossed_circle
          xcursorgen right_ptr.in cursors/right_ptr
          xcursorgen copy.in cursors/copy
          xcursorgen circle.in cursors/circle
          xcursorgen sb_h_double_arrow.in cursors/sb_h_double_arrow
          xcursorgen sb_v_double_arrow.in cursors/sb_v_double_arrow
          xcursorgen top_left_corner.in cursors/top_left_corner
          xcursorgen top_right_corner.in cursors/top_right_corner
          xcursorgen watch.in cursors/watch
          xcursorgen sb_left_arrow.in cursors/sb_left_arrow
          xcursorgen sb_right_arrow.in cursors/sb_right_arrow
          xcursorgen sb_up_arrow.in cursors/sb_up_arrow
          xcursorgen sb_down_arrow.in cursors/sb_down_arrow
6 of 8                                                                                                       02/03/2008 04:57 PM
                                                                                                                        about:blank
          xcursorgen based_arrow_down.in cursors/based_arrow_down
          xcursorgen based_arrow_up.in cursors/based_arrow_up
          xcursorgen fleur.in cursors/fleur
          xcursorgen question_arrow.in cursors/question_arrow
          xcursorgen X_cursor.in cursors/X_cursor
          echo .
          echo ..
          echo ...
          echo ....
          echo .....
          echo ......
          echo .......
          echo ........
          echo .......
          echo ......
          echo .....
          echo ....
          echo ...
          echo ..
          echo .
          echo DONE ...
          echo See in your cursors directory ....
```
       * Notice how we have an xcursorgen command for every set(s) of picture and configuration file we will be
       outputing.
       This bash example comes from two themes. The main part came with that tutorial and it worked but the
       xcursorgen commands are from the entis_mini_cursors which as you can tell is not a complete theme. You
       can call it whatever you want so I called mine "make.sh"
       Make sure this is in the same directory as your pictures and your configuration files. I found the most reliable
       way for this to work is open a Terminal go to your directory and type "./whatever_ your_script_is_called.sh".
       You will then have a directory inside your previous directory called "cursors".
       To load your new cursor set copy that new "cursors" folder we just made now click "Show Hidden Files" in
       your home directory. Go down to ".icons" folder and create a new folder. Call it whatever you want you
       cursor set to be called and then paste the "cursors" folder inside that one. Open up GEdit and paste this in:
          [Icon Theme]
          Name=The_Name_of_Your_ Theme
          Comment= Comments_About_Your_Theme_Author_etc.
          Example=left_ptr
          Inherits=core
       *Note: The text in red depends on you so it will be different for each theme you create.
       Save this as "index.theme" and save it to the folder you just created to put the "cursors" folder in. It should
       look like this:
7 of 8                                                                                                         02/03/2008 04:57 PM
                                                                                                                   about:blank
       Open a Terminal and type" ldconfig" (Not sure if this is important but I do it anyway.) You can now choose
       your pointers from Appearance-->Customize[/COLOR]-->Pointer.
8 of 8                                                                                                    02/03/2008 04:57 PM

---

### Post by Noob Programmer on 2010-05-07
> **shantiq said:**
> 
          left_ptr ----->Main Pointer

Thanks a lot. That was the line I was missing.

---

### Post by qewriusjorj on 2010-12-14
Making static pointer.

Followed PDF meticulously.

System -> Preferences -> Appearance -> Customize -> Pointer does not recognize the new pointer.

Ubuntu 10.10

---

