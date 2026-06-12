---
title: "Devilspie question"
date: 2011-01-01
forum: General Help
---

### Post by daqron on 2011-01-01
Howdy.

I have a devilspie script that is intended to close windows that match a certain title. The script works fine if I run devilspie manually from terminal AFTER the window is open, but it doesn't work if devilspie is already running when the window opens.

The documentation indicates that devilspie can be configured to detect windows as they are opened, but I can't figure out how to make it do that. Any suggestions?

---

### Post by dodo3773 on 2011-01-24
> **daqron said:**
> Howdy.

I have a devilspie script that is intended to close windows that match a certain title. The script works fine if I run devilspie manually from terminal AFTER the window is open, but it doesn't work if devilspie is already running when the window opens.

The documentation indicates that devilspie can be configured to detect windows as they are opened, but I can't figure out how to make it do that. Any suggestions?

Have you tried "devilspie -a"

My startup script looks like this

```
#! /bin/bash

sleep 10 && evolution & firefox-4.0 & sleep 20 && devilspie -a &  sleep 25 && pkill -f "devilspie -a"



exit
```That way after the program has enough time to load devilspie will apply itself afterwards. I like to kill devilspie after because I do not want it constantly running. I might want to open another window on a different viewport etc..

---

### Post by Ol' Craig on 2011-03-30
@ dodo, 
this looks like just the thing i am looking for.
i'm really new to this linux stuff.
i just recently got devilspie working, so that it automatically opens matlab on workspace 3
i was about to set it up to open a terminal window and browser in another workspace, when i realized that the "rules" would always apply.
i am now trying to write a script that will open all this on startup, using devilspie to direct things to the proper workspaces, and then kill devilspie
this is all i've found so far:
[http://rusteddev.wordpress.com/2011/03/05/unix-rails-environment-start-script-quick/](http://rusteddev.wordpress.com/2011/03/05/unix-rails-environment-start-script-quick/)
i can't imagine adapting this will be difficult, but this is my first attempt at a linux script
any help would be appreciated
cheers

---

### Post by dodo3773 on 2011-03-30
> **Ol' Craig said:**
> @ dodo, 
this looks like just the thing i am looking for.
i'm really new to this linux stuff.
i just recently got devilspie working, so that it automatically opens matlab on workspace 3
i was about to set it up to open a terminal window and browser in another workspace, when i realized that the "rules" would always apply.
i am now trying to write a script that will open all this on startup, using devilspie to direct things to the proper workspaces, and then kill devilspie
this is all i've found so far:
[http://rusteddev.wordpress.com/2011/03/05/unix-rails-environment-start-script-quick/](http://rusteddev.wordpress.com/2011/03/05/unix-rails-environment-start-script-quick/)
i can't imagine adapting this will be difficult, but this is my first attempt at a linux script
any help would be appreciated
cheers

Where are you running into problems? Is it in the kill option (devilspie is not getting killed)?

---

### Post by Ol' Craig on 2011-03-30
> **dodo3773 said:**
> Where are you running into problems? Is it in the kill option (devilspie is not getting killed)?

i'm not quite sure. i started using the gdevilspie gui, and had pretty good luck with it to start. also, i could check a box to set it to start automatically. this is the script i've been running:

#! /bin/bash

sleep 5 && /usr/local/matlab/bin/matlab -glnx86 -desktop & gnome-terminal -t "Do you have any idea what you're doing?" & firefox & sleep 30 && pkill -f devilspie

exit


it's essentially the same thing you have, and it does what it's supposed to. at this point, my problems seem to be with the gdevilspie gui. I keep adjusting the settings for where the windows should open, but they don't seem to stick :/

---

### Post by dodo3773 on 2011-03-30
> **Ol' Craig said:**
> i'm not quite sure. i started using the gdevilspie gui, and had pretty good luck with it to start. also, i could check a box to set it to start automatically. this is the script i've been running:

#! /bin/bash

sleep 5 && /usr/local/matlab/bin/matlab -glnx86 -desktop & gnome-terminal -t "Do you have any idea what you're doing?" & firefox & sleep 30 && pkill -f devilspie

exit


it's essentially the same thing you have, and it does what it's supposed to. at this point, my problems seem to be with the gdevilspie gui. I keep adjusting the settings for where the windows should open, but they don't seem to stick :/

I have never used the devilspie gui. But unless devilspie is already loaded when you run that script then it will not load because you did not call on it in the script. A couple of things to keep in mind are: If it is a startup script then make sure that you give the OS enough time to load. Make sure that you give the applications enough time to load also before you run devilspie (that is why I like to use the "devilspie -a" option after). Why do you sleep the script for 5 seconds at the beginning? Also, you can go line by line instead of using &&. Like this

```

#! /bin/bash

sleep 5
/usr/local/matlab/bin/matlab -glnx86 -desktop &
gnome-terminal -t "Do you have any idea what you're doing?" & 
firefox & 
sleep 30
pkill -f devilspie

exit
```I am still not completely sure as to your question though. What do you mean by "but they don't seem to stick"?

---

### Post by Ol' Craig on 2011-03-31
The devilspie gui has a setting to start the devilspie daemon upon login. The script seems to work properly, but i will continue to tweak it as i go.
The comment i made about the windows not sticking is in regards to the behaviour of the windows.
I figure this has to do with the .ds files created for each application. 
I'll keep working at it.
I haven't been to sure as what my questions are either.
At this point:
What does the -a option do after devilspie?
The man page says, "-a --apply-to-existing
              Apply to all existing windows instead of just new windows."
This means it will position the windows "retroactively", for lack of a better word?

Also, the reason I started using && was to wait to execute a command until the previous command was executed. I started thinking that something like devilspie or opening an application might not immediately return an exit status.

I apologize for the "skatter braindedness" of my posts. 
Even while writing it, I am still researching. ie. the -a option question and probably the answer. lol

Thank you for helping though

---

### Post by dodo3773 on 2011-03-31
> **Ol' Craig said:**
> The devilspie gui has a setting to start the devilspie daemon upon login. The script seems to work properly, but i will continue to tweak it as i go.
The comment i made about the windows not sticking is in regards to the behaviour of the windows.
I figure this has to do with the .ds files created for each application. 
I'll keep working at it.
I haven't been to sure as what my questions are either.
At this point:
What does the -a option do after devilspie?
The man page says, "-a --apply-to-existing
              Apply to all existing windows instead of just new windows."
This means it will position the windows "retroactively", for lack of a better word?

Also, the reason I started using && was to wait to execute a command until the previous command was executed. I started thinking that something like devilspie or opening an application might not immediately return an exit status.

I apologize for the "skatter braindedness" of my posts. 
Even while writing it, I am still researching. ie. the -a option question and probably the answer. lol

Thank you for helping though


I am pretty sure that all your rules are suppost to go into one .ds file. The -a option is exactly like you said. It moves and rearranges the windows that are already open. As far as the && the process has to finish like you said for the next one to start. But, on that same note if you were to go "gedit && firefox" then firefox would not open until gedit was closed. One "&" is to run multiple processes at once. Also, each line is a new command so 
```

gedit & baobab

```is the same as 
```

gedit &
baobab

```and 
```

gedit && baobab

```is the same as
```

gedit
baobab
```Hope that helps.

---

### Post by Ol' Craig on 2011-03-31
Ok, here is some of the print out from running debug.ds:

> 
Window Title: 'MATLAB'; Application Name: 'MATLAB'; Class: 'MATLAB'; Geometry: 396x424+443+214
Window Title: '<Student Version> MATLAB  7.8.0 (R2009a)'; Application Name: '<Student Version> MATLAB  7.8.0 (R2009a)'; Class: 'com-mathworks-util-PostVMInit'; Geometry: 1262x1039+96+138

** (devilspie:4440): WARNING **: Workspace number 3 does not exist

(devilspie:4440): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed
Window Title: '<Student Version> Command Window'; Application Name: '<Student Version> Command Window'; Class: 'com-mathworks-util-PostVMInit'; Geometry: 1280x970+0+24

** (devilspie:4440): WARNING **: Workspace number 3 does not exist

(devilspie:4440): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed
Window Title: 'Workspace Switcher Preferences'; Application Name: 'wnck-applet'; Class: 'Wnck-applet'; Geometry: 202x174+1996+23
Window Title: 'Mozilla Firefox'; Application Name: 'Firefox'; Class: 'Firefox'; Geometry: 1280x980+1280+23

My matlab desktop is setup as two large windows, each occupying a display. My intent is to have the program open to workspace 3.
This debug output says the workspace doesn't exit, but it does.
I just recently changed the .ds from "set_viewport 3" to "set_workspace 3"
I'll post my .ds files

---

### Post by Ol' Craig on 2011-03-31
These are the .ds configuration files i'm using

```

; generated_rule matlab
( if 
    ( begin
        ( is ( application_name ) "<Student Version> MATLAB  7.8.0 (R2009a)" )
    ) 

    ( begin 
        ( maximize )
        ( maximize_vertically )
        ( maximize_horizontally )
        ( set_workspace 3 )
        
    )
)


``````

; generated_rule matlab_command_window
( if 
    ( begin 
        ( is ( application_name ) "<Student Version> Command Window" )
    ) 
    ( begin 
        ( maximize )
        ( maximize_vertically )
        ( maximize_horizontally )
        ( set_workspace 3 )
        
    )
)


```

---

### Post by dodo3773 on 2011-03-31
> **Ol' Craig said:**
> These are the .ds configuration files i'm using

```

; generated_rule matlab
( if 
    ( begin
        ( is ( application_name ) "<Student Version> MATLAB  7.8.0 (R2009a)" )
    ) 

    ( begin 
        ( maximize )
        ( maximize_vertically )
        ( maximize_horizontally )
        ( set_workspace 3 )
        
    )
)


``````

; generated_rule matlab_command_window
( if 
    ( begin 
        ( is ( application_name ) "<Student Version> Command Window" )
    ) 
    ( begin 
        ( maximize )
        ( maximize_vertically )
        ( maximize_horizontally )
        ( set_workspace 3 )
        
    )
)


```


I just tried this

```
(if
(is (application_name) "Firefox")
(begin
(set_workspace 2)
(maximize)
)
)
```In metacity and it worked for me (on compiz I use viewport).  Are all of your rules in the same file? That is all I can think of. Other than that I am not sure.

---

### Post by Ol' Craig on 2011-03-31
Hmm...I'll try putting them all in one file.

Have you ever used the command "kstart" ?

It seems to be better suited for writing a startup script, but i'm having some troubles with it as well

---

### Post by dodo3773 on 2011-03-31
> **Ol' Craig said:**
> Hmm...I'll try putting them all in one file.

Have you ever used the command "kstart" ?

It seems to be better suited for writing a startup script, but i'm having some troubles with it as well

kstart? Do you use kde?

---

### Post by Ol' Craig on 2011-03-31
no.
i tried to edit that last post.
kstart worked, in that it started the program,
but it rearranged everything i had open
ehh...time to call it a night
thanks again for your time
i'll post again later on my progress

---

### Post by Ol' Craig on 2011-03-31
ok, i've got my .ds files working properly
the script works well on startup if i have devilspie set to run automatically, by the gui, in which case i remove the devilspie command at the beginning of the script.
i have tried it as presented below, but nothing happens.
when run, as below, the devilspie daemon and the running script both appear in the system monitor.
i'm a bit confused as to why the script would open the programs and then kill the already running devilspie, but not start devilspie itself, open the programs and kill devilspie.
is there a command that should be included to "run" devilspie?

```


#! /bin/bash
devilspie
sleep 5
/usr/local/matlab/bin/matlab -glnx86 -desktop -r "edit %f" & 
sleep 45 
pkill -f devilspie
exit


```Got it working!
I added an ampersand after the devilspie command....it was waiting till devilspie was "done" before executing the remaining commands.

```


#! /bin/bash

devilspie &
/usr/local/matlab/bin/matlab -glnx86 -desktop -r "edit %f" &
evolution &
firefox &
gnome-terminal &
sleep 45 
pkill -f devilspie

exit


```The only other problem I have, is getting firefox to open in the proper place when there are multiple tabs to be restored. if it's just opening a blank browser window it works fine. weird!!

Thanks again for all your help d

---

### Post by Ol' Craig on 2011-04-01
Also, for reference, here are my devilspie .ds configurations. I found a good balance of using the gdevilspie gui and adjusting the files by hand worked best.

```

; generated_rule email
( if 
    ( begin 
        ( is ( window_class ) "evolution" )
        ( is ( application_name ) "evolution" )
        ( contains ( window_name ) "Evolution" )
    )
    ( begin 
        ( maximize )
        ( geometry "1280x980+1280+23" )
        ( set_viewport 2 )
    )
)

```

```

; generated_rule firefox
( if 
    ( begin 
        ( is ( window_class ) "Firefox" )
        ( is ( application_name ) "Firefox" )
    ) 
    ( begin 
        ( maximize )
        ( geometry "1280x979+0+24" )
        ( set_viewport 4 )
    )
)

```

```

; generated_rule matlab
( if 
    ( begin 
        ( is ( window_class ) "com-mathworks-util-PostVMInit" )
        ( is ( application_name ) "<Student Version> MATLAB  7.8.0 (R2009a)" )
        ( is ( window_name ) "<Student Version> MATLAB  7.8.0 (R2009a)" )
    ) 
    ( begin 
        ( maximize )
        ( set_viewport 3 )
    )
)

```

```

; generated_rule matlab_editor
( if 
    ( begin 
        ( is ( window_class ) "com-mathworks-util-PostVMInit" )
        ( is ( application_name ) "Editor" )
        ( contains ( window_name ) "Editor" )
    ) 
    ( begin 
        ( maximize )
        ( geometry "1280x980+1280+23" )
        ( set_viewport 3 )
    )
)

```

```

; generated_rule terminal
( if 
    ( begin 
        ( is ( window_class ) "Terminal" )
        ( is ( application_name ) "Terminal" )
        ( is ( window_name ) "Terminal" )
    ) 
    ( begin 
        ( geometry "657x465+1591+97" )
        ( set_viewport 4 )
    )
)

```

Hope this will be helpful

---

