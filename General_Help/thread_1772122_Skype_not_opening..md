---
title: "Skype not opening."
date: 2011-05-31
forum: General Help
---

### Post by OldLes on 2011-05-31
Ubuntu 10.04

2 days ago Skype crashed. since then I can no longer open it from "Applications  ---   Internet  ---   Skype". I get this error message:----
Failed to execute child process "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so" (No such file or directory)
I can open it using terminal and typing "Skype" and return.
I have checked the main menu, where the command is:--
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

I suspect the problem lies here.
HELP.
Les.

---

### Post by timgood on 2011-05-31
Go to your home folder and press Ctrl + H to view hidden files. Navigate to the .Skype directory and delete the file shared.xml and then restart Skype. You will need to sign in again, but Skype will now work. 

Hope this helps.

---

### Post by OldLes on 2011-05-31
Timgood, thanks, but I have been there and done that earlier, but it did not work.
I suspect the command may be wrong.
I know there was a common problem yesterday, but mine started the day before.
I was having camera problems (that has now cured itself), but when I tested it in "Options   Video " within Skype, the camera second request, via a double click, caused the crash.
That is the current situation, exactly as described in my original question.
Les.

---

### Post by mastablasta on 2011-05-31
command should be
 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
 
try putting this in the terminal and see if it works. 
 
if not then check in Synaptic if you have libv4l installed.

---

### Post by OldLes on 2011-05-31
Mastablasta, right, with terminal, I can open skype OK simply by typing "Skype".
Similarly, it will open from terminal with your command:-- 

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

I then tried to put that command in the main menu (simply deleting   /usr/bin   )
but still does not open normally from    applications   internet   skype

Obviously once I get this working again, I can have it opening automatically whenever I switch the PC on.

Still confused OldLes.

---

### Post by OldLes on 2011-05-31
SOLVED!!!
I just put "Skype" in the main menu command.

De-confused (for now) OldLes.

---

### Post by mastablasta on 2011-05-31
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so is only needed in front of skype if the camera (video) doesn't load propperly.
 
to make it it always start you need to make a short script with this command and then save it as executable file.
 
however if only 
 
skype
 
commands works nicelly then there is no need for it. i have to use the preload command, so i f oyu need the short script you can pm me and i will tell you how to do it (it's easy) or just send you mine.

---

### Post by pfbray on 2011-06-12
Hello! I am compeltely new to Ubuntu so very basic instructions would be appreciated greatly. My skype aborts on logging in. Running from terminal this is what comes up
```
skype
philip@ubuntu:~$ skype
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:11430): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:11430): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:11430): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:11430): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:11430): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:11430): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:11430): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:11430): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:11430): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:11430): Gtk-WARNING **: Loading IM context type 'ibus' failed
Aborted

```

Could someone help? What should I do to make it work? I'v tried uninstalling and reinstalling via Software Centre.

---

