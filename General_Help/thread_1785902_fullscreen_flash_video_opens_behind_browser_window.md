---
title: "fullscreen flash video opens behind browser window"
date: 2011-06-18
forum: General Help
---

### Post by eival on 2011-06-18
i have this RANDOM issue, altho its more often than not where i try to open a flash video fullscreen while the browser is maximised but it opens behind the browser window.

i know this use to happen if i had a program open(like Gnome ALSA Mixer) and set to "always on top" how ever im now having this issue with just Firefox or Chrome open.

the only workaround i know of is to resize the browser so its not maximized and i can see some of the desktop, then when i click fullscreen i can see the video open behind it, so then i click the video outside of the browser window area but that normally closes the video and starts another glitch where i have to repeat this process about 3-4 times before the fullscreen video finally comes to the front.

this doesnt seem to happen on the very popular sites like Youtube but alot of other sites have this issue.

i would ask this directly to either Mozilla or Adobe but they're community seems to be dead an never respond to any previous posts ive made, so im hoping someone here knows about this issue:popcorn:


im on Ubuntu 10.4 / Firefox 3.6.17 / Chrome 12.0.742.91 / Flash 10.3(latest stable)
but this issue also happened during the entire life of Flash 10.2

i also had Flash-Aid installed and it had an option that seemed to be related to this issue, how ever even with it enabled i still had this issue.

---

### Post by kriukov on 2011-06-19
I have the same problem. It doesn't depend on the browser (present in Firefox 4.0 and Chrome 10). Minimizing the browser sometimes helps, but sometimes does not - the full-screen flash content disappears immediately after minimizing.

---

### Post by lovinglinux on 2011-06-19
Ask the author of [http://ubuntuforums.org/showpost.php?p=10880548&postcount=11](http://ubuntuforums.org/showpost.php?p=10880548&postcount=11)

The post explains how to fix on KDE, but I suppose it also affects Compiz.

---

### Post by christopher.wortman on 2011-06-19
lol thanks for that this answered my question.

---

### Post by theLured on 2011-06-24
Here is my solution for gnome. It works for me on Gnome 3 on Fedora 15 :)

install devilspie
make the directory .devilspie in your home directory
put the below code into a text editor and save the file as /home/your-username/.devilspie/flash-fullscreen-browsername.ds

Firefox - save as flash-fullscreen-firefox.ds
```
(if
    (is (application_name) "npviewer.bin")
    (begin
       (focus)
    )
)
```

Chrome - save as flash-fullscreen-chrome.ds
note that it uses the application name exe. This is all I could find for the windows name. Please do say if you know of a better way to reference it.
```
(if
    (is (application_name) "exe")
    (begin
       (focus)
    )
)
```



This will bring the flash window into focus, just like what happens when you alt+tab to the next window.
That should solve the problem.

Next run the command to test it
devilspie
Test video at [http://espn.go.com/video/](http://espn.go.com/video/)

If it worked then you want the program to auto start. To do this run the command
gnome-session-properties
Click the add button
In the Name box type devilspie
In the Command box type devilspie
Click Add button

Now you're done :D. All that is left to do is to log out and back in again for the auto start to kick in. Or you could just press Alt+F2 and type devilspie, if it's not already loaded.


If for some reason you want the flash video to "Stay Above All Windows" as well, you can just add the new line "(above)", like in the code below.
We still need the "(focus)" line because for me switching to fullscreen didn't give the window any focus without it.

Firefox
```
(if
    (is (application_name) "npviewer.bin")
    (begin
       (focus)
       (above)
    )
)
```

---

### Post by eival on 2011-06-24
> **theLured said:**
> Here is my solution for gnome. It works for me on Gnome 3 on Fedora 15 :)


before i use your changes, im using Ubuntu 10.04 and it has Gnome v2.30.2

would your changes work with previous versions?

---

### Post by theLured on 2011-06-25
Hello Eival,

Yes, the changes should work for gnome on ubuntu.

devilspie is just a program that can let you set properties for each window. All that my config file does is bring the window to the front, just the same as when you click on the flash video.

This page has more details on how to use it, if you are interested.
[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

Don't worry about messing anything up. If you run devilspie in a terminal, you can hold Ctrl and press C and it will stop the program from running. Or you could just run the command
killall devilspie

This way you can just test if it works.

As you can see the config file is said to work on npviewer.bin. This is the name of the window that is created by firefox when you view flash in fullscreen, as said in this thread.
[http://ubuntuforums.org/showthread.php?t=647961](http://ubuntuforums.org/showthread.php?t=647961)


I didn't know this doesn't work with chrome.
There is a way to get it to work with chrome. Just change the name from "npviewer.bin" to "exe" and save it in the file flash-fullscreen-chrome.ds I've added this to my original comment.

---

### Post by netman74501 on 2011-07-27
THANK YOU FOR THIS theLured!

I am using Gnome3 and have suffered from this for several months now. I couldn't figure out how to use the window rules in Compiz Settings Manager to focus the window but, this works wonderfully in it's place. I just had to change the application name to "<unknown>" instead of "npviewer.bin" for it to work.

The first attempt at fullscreen flash always has worked but, subsequent fullscreens would open behind the browser. Therefore, it left me with having to restart the browser every time I wanted to watch more than one flash video fullscreened. Thank you for freeing me from this nuisance!

---

