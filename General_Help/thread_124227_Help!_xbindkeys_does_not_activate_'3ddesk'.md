---
title: "Help! xbindkeys does not activate '3ddesk'"
date: 2006-02-01
forum: General Help
---

### Post by ahood on 2006-02-01
HI All,

I have installed 3ddesk and it is a super application. I now want to bind it to a key on the keyboard (Super_L). 

I installed xbindkeys and created a default configuration file. I also installed the xbindkeys-config gui editor. I am able to make a new entry that should 'activate' 3ddesk so that I can switch desktops in 3D. However, nothing happens. 

More specifically in the 'action' box of xbindkeys-config I simply type '3ddesk' and then click on the Save&Apply&Exit button. 

When I launch xbindkeys daemon (xbindkeys &), pressing the Super_L key does nothing. 

I then go back into xbindkeys-config and test out the Super_L key and it works!, but it won't work after I close out the xbindkeys-config application. 

I must be missing something, but don't know what it is.....

Can anyone make a suggestion?

Dr. Hood

---

### Post by onesojourner on 2006-02-01
when you type 3ddesk in terminal what happens? does it "do its thing"?

---

### Post by audax321 on 2006-02-01
Can you open a terminal and type: gedit $HOME/.xbindkeysrc and then copy paste the file contents here.

Also, check to see if xbindkeys is even running by typing: pidof xbindkeys (you should get a number)... 

Also to launch xbindkeys you don't need to do "xbindkeys &". Try simply "xbindkeys" because the program does not take over control of the terminal.

---

### Post by onesojourner on 2006-02-01
you can also go apps>system tools>config editor>Apps>metacity>keybindings_commands and then global keybindings.

---

### Post by ahood on 2006-02-01
Thank you all for replying. Here are my responses....

(1) When I type 3ddesk in a terminal, 3ddesk does it thing. It works great!

(2) Yes, 3ddesk and xbindkeys are running. I verify this through Applications --> System Tools --> System Monitor -->Processes and both 3ddesk and xbindkeys are running.

In a terminal, when I do 'pidof xbindkeys' the number 17359 is returned.

(3) The contents of .xbindkeysrc is.....

> ###########################
# xbindkeys configuration #
###########################
#
# Version: 0.1.3
#
# If you edit this, do not forget to uncomment any lines that you change.
# The pound(#) symbol may be used anywhere for comments.
#
# A list of keys is in /usr/include/X11/keysym.h and in
# /usr/include/X11/keysymdef.h 
# The XK_ is not needed. 
#
# List of modifier (on my keyboard): 
#   Control, Shift, Mod1 (Alt), Mod2 (NumLock), 
#   Mod3 (CapsLock), Mod4, Mod5 (Scroll). 
#
# Another way to specifie a key is to use 'xev' and set the 
# keycode with c:nnn or the modifier with m:nnn where nnn is 
# the keycode or the state returned by xev 
#
# This file is created by xbindkey_config 
# The structure is : 
# # Remark 
# "command" 
# m:xxx + c:xxx 
# Shift+... 




#keystate_numlock = enable
#keystate_scrolllock = enable
#keystate_capslock = enable



#show keys
"xbindkeys_show"
   control+shift + q

# set directly keycode (here control + f with my keyboard)
"xterm"
   c:41 + m:0x4

# specify a mouse button
"xterm"
   control + b:2

#switch desktop
"3ddesk"
    m:0x50 + c:115
    Mod2+Mod4 + Super_L 

#
# End of xbindkeys configuration

(4) I will have to check out the metakeys option, if xbindkeys won't work.

Do I have to press 2 keys to get this to work? One to load up an xterm and another for the '3ddesk' command?

Thanks again for replying. Please give more input, it is fantastic!

Dr. Hood

---

### Post by audax321 on 2006-02-01
Okay, to get it to work:

Change "m:0x50" to "m:0x10" and then restart xbindkeys.

---

### Post by ahood on 2006-02-01
Thanks audax321!

Changing "m:0x50" to "m:0x10" and then restarting xbindkeys did the trick. It works now!! 

I wonder why the key was different than what xbindkeys output gave with the command 'xbindkeys -k'?

I would never have guessed to make that kind of change.

Dr. Hood

---

### Post by audax321 on 2006-02-02
Yeah, xev was giving me 0x50 as well. But, 99.9% of the time that m: part should be 0x10. I actually ended up binding 3ddesk to a key as well, but I bound it to my scroll lock key since I never use it for anything anyway :)

Also, it really is much easier to just manually edit .xbindkeysrc. All the commands just take the format:

"command goes here"
  m:0x10 + c:KEY_CODE

where KEY_CODE is the number returned using xev. I never did really like that configuration editor... seemed to buggy for me.

---

