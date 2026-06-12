---
title: "Shutdown PC without root privileges"
date: 2010-09-06
forum: General Help
---

### Post by hakermania on 2010-09-06
All of as now the add-to-panel item that via it you can shutdown the PC without the need of typing any password to gain root privileges.
[CENTER][IMG]http://img842.imageshack.us/img842/9819/screenshot2vy.png[/IMG]
[/CENTER]
How is this possible? I know that fro default the login screen is run by root but how do this app sends the signal to the login-screen to shutdown?
I mean, this app is run without root privileges by me, the simple user, and when clicked the PC shutdowns via a signal from this app to the login screen....
How can I call this signal to an app of mine?

---

### Post by sgosnell on 2010-09-06
I don't think the login screen needs to be involved.  You can shut down from a script with "shutdown".

---

### Post by ender4 on 2010-09-06
The shutdown command will not work without root permissions, at least it doesn't for me.

My guess is that the shutdown applet uses the setuser bit.

---

### Post by sgosnell on 2010-09-06
You need to modify the sudoers file.  There are also a couple of other ways to do it.  Putting "shutdown linux non-root" into Google will give you a number of hits with ways to do what the OP wants.

---

### Post by MooPi on 2010-09-06
Using visudo to edit sudoers file.
Add: ```
# Members of admin group may gain root privileges
%admin ALL=(ALL) ALL
[COLOR="Red"]%username ALL=(ALL)NOPASSWD:/sbin/shutdown[/COLOR]
```

Your user name plugged in. Be careful with this because if you screw this up the system may not boot and you'll end up using a recovery CD or like system to repair.

---

### Post by hakermania on 2010-09-07
NO, I won't edit ANYTHING!
This applet does it, yes, it does, it does shutdown the PC without any prompt requesting for password or without editing any file or something similar. About the setuser bit, how to I use it? Has it to do with chmod/chown ?

---

### Post by hakermania on 2010-09-08
*bump*

---

### Post by shaon3343 on 2010-09-08
Are you asking about a desktop launcher to shutdown ubuntu ? then it may help : 

> 
#!/usr/bin/env python

import os
import sys
import pygtk
import gtk

class power:
    
    def restart(self, event):
            command = "sudo shutdown -r now"
            os.system(command)
        
    def shutdown(self, event):
        command = "sudo shutdown -h now"
        os.system(command)
        
    def cancel(self, event):
        import sys
        sys.exit()
        
    def delete_event(self, widget, event, data=None):
            gtk.main_quit()
            return False
    
    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_title("Power Options")
        self.window.connect("delete_event", self.delete_event)
        self.window.set_border_width(10)
        
        self.box1 = gtk.HBox(False, 0)
            self.window.add(self.box1)
    
        self.button1 = gtk.Button("Restart")
        self.button1.connect("clicked", self.restart)
        self.box1.pack_start(self.button1, True, True, 0)
        
        self.button2 = gtk.Button("Shutdown")
        self.button2.connect("clicked", self.shutdown)
        self.box1.pack_start(self.button2, True, True, 0)
        
        self.button3 = gtk.Button("Cancel")
        self.button3.connect("clicked", self.cancel)
        self.box1.pack_start(self.button3, True, True, 0)
        
                self.window.set_position(gtk.WIN_POS_CENTER)
        self.button1.show()
        self.button2.show()
        self.button3.show()
        self.box1.show()
        self.window.show()
def main():
    gtk.main()
    
if __name__=="__main__":
    pwr = power() 
    main()


save this script in an empty document file ( guess the file name is shut_down) and allow this executing as a program.
 ( properties --> permission --> allow executing ) 
move the file to home folder (/home/your_username)
now go to the terminal and enter this commamd :
>   cd Desktop 
>  cp power_options /home/<your user name> 
Now that the file is in your /home directory we will now make a desktop 
launcher (shortcut) to it.
 

Right click a blank area of your desktop and choose "Create Launcher..".

In the resulting dialog box make sure "application" is selected in the **type:**
 dropdown menu.

In the **name:** field name then launcher anything you want, I chose 
Quit.

In the **command:** field type python /home/<your user 
name>/power_options, again using your actual user name without 
<> where it says <your user name>.
 

In the upper left corner of the launcher dialog box is a generic icon.

Click this icon to change the icon to a more acceptable one from the 
list.

If you have an icon of your own then place it in your /home directory 
and navigate to it using the browse feature.

Click ok when done and you should have a brand new launcher on your 
desktop with

the icon of your choice.
 

Right click the new launcher and choose properties>permissions and 
make sure "allow executing file as a program" is selected, close the 
properties box and you launcher is ready for use.
 

When clicked your new shutdown button will open a small dialog box where
 you can select shutdown, restart or cancel.

HAVE FUN . :)

---

### Post by shaon3343 on 2010-09-08
[SIZE=2]Sorry, forget about my previous post. you can do it simply!! just open terminal and enter:
>  sudo visudo 
and do as the post below: 

> **MooPi said:**
> Using visudo to edit sudoers file.
Add: ```
# Members of admin group may gain root privileges
%admin ALL=(ALL) ALL
[/SIZE] [SIZE=2][COLOR=Red]%username ALL=(ALL)NOPASSWD:/sbin/shutdown[/COLOR][/SIZE][SIZE=2]
```Your user name plugged in. Be careful with this because if you screw this up the system may not boot and you'll end up using a recovery CD or like system to repair.
(   save it with ctrl+X and hit Y )
then create a launcher anywhere you want. and in the command text box enter following command : 
 
>  sudo halt 
it can shutdown your ubuntu with a single click !! :) [/SIZE]

---

### Post by rnerwein on 2010-09-08
hi
what's about this solution:
add your own script to the panel - lets call it: game_over.sh
# aks for shutdown the system
/usr/bin/gnome-session-save --shutdown-dialog
exit 0

ciao

---

