---
title: "Start script at startup"
date: 2009-07-10
forum: General Help
---

### Post by bertles86 on 2009-07-10
Hi folks

I've made the script from the wiki to switch the arrow keys and right shift key. can someone walk me through how to make it work at startup?

The wiki is quite clear but is still beyond me...

edit - the script i made is exactly like this

```
 #!/bin/sh
 # set up keyboard to exchange the Shift and Up keys, and the Down and Right keys
 xmodmap -e "keycode 62 = Up"        # Shift       => Up
 xmodmap -e "keycode 109 = Prior"    # Shift-shift => PgUp
 xmodmap -e "keycode 98 = Shift_R"   # Up          => Shift
 xmodmap -e "keycode 99 = Control_R" # PgUp        => Shift-shift
 xmodmap -e "keycode 104 = Right"    # Down        => Right
 xmodmap -e "keycode 105 = End"      # PgDn        => End
 xmodmap -e "keycode 102 = Down"     # Right       => Down
 xmodmap -e "keycode 103 = Next"     # End         => PgDn
 xmodmap -e "add shift = Shift_R"    # Make the new Shift key actually do shifting
 xset r 62                           # Make the new Up key autorepeat
 xset r 109                          # Make the new PgUp autorepeat
 xset -r 98                          # Prevent the new Shift key from autorepeating

```

will that map up arrow and shift as well as down arrow and right arrow?

---

### Post by t4thfavor on 2009-07-10
Put it in your System -> Preferences -> Startup Programs. Then it will run when you login to gnome.

If you want it to run at system boot, you will have to put it into rc.d or init.d somehow.

---

### Post by bertles86 on 2009-07-10
ok so in startup apps if i add my script, then when i login it'll run? is the code ok for the key setup i want?

edit: i copie the script from the wiki for a US keyboard, but I have UK qwerty!

---

### Post by t4thfavor on 2009-07-10
Does it work when you run it from the terminal after loggin in? If so it's pretty safe top say it will be just fine on login.

One way to find out.

---

### Post by bertles86 on 2009-07-10
Well from the terminal I entered the dir that my script was in and typed "./setupkbd.sh"

No errors came up and it just returned the prompt. On test the newly placed keys acted like this:

Up arrow = Up arrow and Shift
Down arrow = Right arrow (should be down)
Shift = Up arrow
Right arrow = Down arrow

So it doesn't work!

---

### Post by t4thfavor on 2009-07-10
You must have your keycodes incorrectly set. Im not much for changing my keymap, as I have grown accustomed to it. I just know how to run a script at login. 

I will do some playiong with thexmodmap command and let you know.

Pretty close to what you are doing, and it solves your startup issue.

[http://forum.eeeuser.com/viewtopic.php?id=58019](http://forum.eeeuser.com/viewtopic.php?id=58019)

---

### Post by bertles86 on 2009-07-10
thanks i appreciate your help!

---

### Post by bertles86 on 2009-07-11
How can we work out the UK Qwerty keymap? If we work that out, and alter the strings surely my script will work, then all we'll need is to get it running at startup!

---

### Post by bertles86 on 2009-07-12
Right I've made progress, I've run Xev and discovered by default my values are:

Up Arrow: 111
R Shift: 62
Down Arrow: 116
Right Arrow: 114

And I want it to be:

Up Arrow: 62
R Shift: 111
Down Arrow: 114
Right Arrow: 116

So can I just edit xmodmap to reflect these changes and it'll work automatically at startup?

---

### Post by bertles86 on 2009-07-12
Right I've got my script working! Below is the UK Qwerty script for the Right Shift alteration:

```
 #!/bin/sh
 # set up keyboard to exchange the Shift and Up keys, and the Down and Right keys
 xmodmap -e "keycode 62 = Up"        # Shift       => Up
 xmodmap -e "keycode 105 = Prior"    # Shift-shift => PgUp
 xmodmap -e "keycode 111 = Shift_R"  # Up          => Shift
 xmodmap -e "keycode 99 = Control_R" # PgUp        => Shift-shift
 xmodmap -e "keycode 116 = Right"    # Down        => Right
 xmodmap -e "keycode 117 = End"      # PgDn        => End
 xmodmap -e "keycode 114 = Down"     # Right       => Down
 xmodmap -e "keycode 115 = Next"     # End         => PgDn
 xmodmap -e "add shift = Shift_R"    # Make the new Shift key actually do shifting
 xset r 62                           # Make the new Up key autorepeat
 xset r 105                          # Make the new PgUp autorepeat
 xset -r 111                         # Prevent the new Shift key from autorepeating
 echo "All Done setting up keyboard."
```

Now any chance of bit of help getting this to run at startup please? :p

---

### Post by bertles86 on 2009-07-12
Ok I followed the wiki on how to get it to run at startup:

```
   1.
      Save the script to /home/YourUserName/ExampleName.sh ( the first line of the script must be #!/bin/sh )
   2.
      Give the script execute permission chmod 0755 /home/YourUserName/ExampleName.sh
   3.
      Select from your main menu: Preferences –> Startup Applications
          *
            Select Startup Programs tab if it is not already selected.
          *
            Click Add
          *
            Name the application e.g.: Example Script
          *
            Command: enter the path to the script: i.e.: /home/YourUserName/ExampleName.sh (Or use the Browse… button for the file chooser to find the script.)
          *
            Click Add
          *
            Make sure that the new entry in the Startup Programs tab of the Sessions dialog is checked.
          *
            Click Close
   4.
      Reboot

```

I restarted, and now all I get is a blank desktop showing the icon for my SDHC card and nothing else...ideas?

P.S. I put my script in /usr

---

### Post by bertles86 on 2009-07-12
Well I right clicked the desktop and created a launcher, with the command xterm, opened up the terminal and typed "gnome-panel" and it all came back. 

I restarted and the panels had gone again...

---

