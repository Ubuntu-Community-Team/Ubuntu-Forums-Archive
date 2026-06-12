---
title: "[Fix] Karmic: Automaticly unmount CIFS shares at shutdown &amp; restart with no errors!"
date: 2009-12-06
forum: General Help
---

### Post by ubradford on 2009-12-06
**Updated: 12/12/09**
I've found that the following works on Ubuntu 9.10 Karmic while using wireless and WPA2 on my laptop:

After hours of beating my head against the wall trying to figure out how to get rid of those time-consuming **CIFS VFS **errors during shutdown, I cobbled together this (ugly) fix.

I take no credit for this script. I found it [here]("http://www.linuxquestions.org/questions/showthread.php?p=3560301#post3560301").  I simply put two and two together, as I guessed this script may execute before Network Manager is killed.  I just plugged in the umountnfs.sh portion.
[LIST]
[*]Save the script somewhere safe.  I saved it in ~/Scripts, and gave it root-only permissions.
[*]sudo chmod +x /path/to/script/scriptname
[*]Add the script to your Start-up Applications. (System > Preferences > Startup Applications)
[/LIST]
```
#!/usr/bin/env python

#Author: Seamus Phelan

#This program runs a custom command/script just before gnome shuts 
#down.  This is done the same way that gedit does it (listening for 
#the 'save-yourself' event).  This is different to placing scipts 
#in /etc/rc#.d/ as the script will be run before gnome exits.
#If the custom script/command fails with a non-zero return code, a 
#popup dialog box will appear offering the chance to cancel logout
#
#Usage: 1 - change the command in the 'subprocess.call' in 
#           function 'session_save_yourself' below to be what ever
#           you want to run at logout.
#       2 - Run this program at every gnome login (add via menu System 
#           -> Preferences -> Session)
# 
#

import sys
import subprocess
import datetime

import gnome
import gnome.ui
import gtk


class Namespace: pass
ns = Namespace()
ns.dialog = None


def main():
    prog = gnome.init ("gnome_save_yourself", "1.0", gnome.libgnome_module_info_get(), sys.argv, [])
    client = gnome.ui.master_client()
    #set up call back for when 'logout'/'Shutdown' button pressed
    client.connect("save-yourself", session_save_yourself)
    client.connect("shutdown-cancelled", shutdown_cancelled)


def session_save_yourself( *args):
    #Unmount those CIFS shares!
    retcode = subprocess.call("sudo /etc/init.d/umountnfs.sh", shell=True)
    if retcode != 0:
        #command failed  
        show_error_dialog()
    return True

def shutdown_cancelled( *args):
    if ns.dialog != None:
        ns.dialog.destroy()
    return True


def show_error_dialog():
    ns.dialog = gtk.Dialog("There was a problem running your pre-shutdown script",
                           None,
                           gtk.DIALOG_MODAL | gtk.DIALOG_DESTROY_WITH_PARENT,
                           ("There was a problem running your pre-shutdown script - continue logout", gtk.RESPONSE_ACCEPT))
    if ns.test_mode == True:
        response = ns.dialog.run()
        ns.dialog.destroy()
    else:
        #when in shutdown mode gnome will only allow you to open a window using master_client().save_any_dialog()
        #It also adds the 'Cancel logout' button
        gnome.ui.master_client().save_any_dialog(ns.dialog)



#Find out if we are in test mode???
if len(sys.argv) >=2 and sys.argv[1] == "test":
    ns.test_mode = True
else:
    ns.test_mode = False

if ns.test_mode == True:
    main()
    session_save_yourself()
else:
    main()
    gtk.main()
```
[LIST]
[*]Run in terminal: ```
sudo visudo
```
[*] Add the following to the bottom of the file:```
%admin ALL=NOPASSWD: /etc/init.d/umountnfs.sh
```
[/LIST]

[LIST]
[*]Press *Ctrl-X* to exit, press *Y* to save changes, and hit *[Enter]* to write the file.
[/LIST]
 
I hope this helps!  I'm a linux noob, so apologies if my guide wasn't perfect. ;)
[B][COLOR=Black] (Credit to stevo1982 for the sudo password workaround!)
[/COLOR][/B]

---

### Post by Ian Ferguson on 2009-12-06
Thanks, ubradford. This worked for me! :D

It should be possible to fix the security issue by having the script refer to a credentials file instead of putting your password in plain text in the script?

---

### Post by ubradford on 2009-12-07
> **Ian Ferguson said:**
> Thanks, ubradford. This worked for me! :D

It should be possible to fix the security issue by having the script refer to a credentials file instead of putting your password in plain text in the script?

[FONT=Courier New][FONT=Verdana]I'll play around with it and try to figure out how to echo the contents of a file into sudo[/FONT][/FONT]. I never thought of that, I'm just a noob. lol :D

---

### Post by Ian Ferguson on 2009-12-07
Just one curious thing. I tested this by clicking "Restart" in the shutdown menu, and my ststem shut down and restarted cleanly, but when I click "Shut Down" it gets as far as a blank screen with a flashing cursor, but doesn't power off as it used to.

Also, it doesnt work when I change ownership of the script to root. I have to keep ownership of it myself.

---

### Post by ubradford on 2009-12-08
> **Ian Ferguson said:**
> Just one curious thing. I tested this by clicking "Restart" in the shutdown menu, and my ststem shut down and restarted cleanly, but when I click "Shut Down" it gets as far as a blank screen with a flashing cursor, but doesn't power off as it used to.

Also, it doesnt work when I change ownership of the script to root. I have to keep ownership of it myself.

The ownership and permissions of my script from "ls -la" are as follows:
```
-rwxr-xr-x  1 root     root       2496 2009-12-06 04:00 gnomelogout
```I've tried "Restart" and "Shut Down" from both gnome-panel and from the "Shut Down the Computer" dialogue box when pressing the power button on my machine.  It is working cleanly in all situations. I do however notice that the shut-down splash screen will break from time to time and let a login prompt flash up on the screen for just a second before the machine powers off entirely.

Maybe another script / program running during logout is conflicting somehow? Or have you played around with the order of script execution in /etc/rc0.d/ and /etc/rc6.d/ ?  Maybe one of those could be causing a problem for you at shut-down?  Both are just guesses, I'm by far not an expert.

Also, it looks like shutting down from terminal with either:
```
sudo shutdown -r 0
``` or ```
sudo shutdown -P 0
```will break the script.  I'd have to guess that gnome never gets a chance to send out the "save-yourself" event the script is listening for when the computer is shut down in that manner.

---

### Post by Ian Ferguson on 2009-12-08
All working now. Turns out that in trying out different fixes, I'd messed up rc0.d, so that's why it wasn't shutting down properly.

Just as well I'd already learned the lesson about making backups before editing system and config files!;)

I've also found this script doesn't work when I shut down or restart from command line. I guess that must bypass the Gnome shutdown sequence.

It occurs to me that this script would be useful if there are other tasks (e.g. backup or synchronize files) that you want to perform automatically on shutdown, but which need the network connection to still be up.

---

### Post by stevo1982 on 2009-12-10
Hi folks.

> Thanks, ubradford. This worked for me!

It should be possible to fix the security issue by having the script refer to a credentials file instead of putting your password in plain text in the script?

I changed the line:
```
retcode = subprocess.call("echo SUDOPASSWORD | sudo -S /etc/init.d/umountnfs.sh", shell=True)

```
to
```
retcode = subprocess.call("sudo /etc/init.d/umountnfs.sh", shell=True)

```
and added this to the bottom of my /etc/sudoers file:
```
%admin ALL=NOPASSWD: /etc/init.d/umountnfs.sh
```
that way I don't need to put the password in the script.

Works just as good for me.

---

### Post by ubradford on 2009-12-12
> 
that way I don't need to put the password in the script.

Works just as good for me.

 Thanks stevo1982!  I'll update the original post with your information. :D

---

### Post by chipbennett on 2009-12-19
Anyone know how to modify this script for KDE?

I'm assuming all of those GNOME/GTK references aren't applicable for KDE/Kubuntu?

Thanks in advance!

---

### Post by Quimby on 2009-12-21
I'm also looking for a fix which works in KDE4.

What i already tried:
- Putting the umountscript in ~/.kde/shutdown/
/etc/network/if-down.d
/etc/Networkmanager/dispatcher.d

- Adding the command in /etc/kde4/kdm/XReset

In all cases the shutdown hangs for several minutes just at different places of the shutdown process.
I thought the script in ~/.kde/Shutdown should do the trick, but it seems even those scripts are executed AFTER the networkmanager kills the connection.

I'm using wireless and WPA2 on kubuntu karmic amd64.

---

### Post by robbuntista on 2009-12-26
It only works for users who have "Administer the system" checked in the "User Privileges" tab in User Settings properties. The other ones cannot use the sudo command.

So, if you have multiple users on a computer and only one has the admin rights, the problem is still opened.

Any idea?

---

### Post by Turpin on 2009-12-29
I'm using Jaunty with LXDE, getting the errors at shutdown caused by shares not unmounting.  Would your script have any chance of working in a non-gnome environment?  I have no clue if it makes a difference, but using GDM for login.

---

### Post by impolo on 2010-01-11
> **ubradford said:**
> **Updated: 12/12/09**
I've found that the following works on Ubuntu 9.10 Karmic while using wireless and WPA2 on my laptop:

After hours of beating my head against the wall trying to figure out how to get rid of those time-consuming **CIFS VFS **errors during shutdown, I cobbled together this (ugly) fix.

I take no credit for this script. I found it [here]("http://www.linuxquestions.org/questions/showthread.php?p=3560301#post3560301").  I simply put two and two together, as I guessed this script may execute before Network Manager is killed.  I just plugged in the umountnfs.sh portion.
[LIST]
[*]Save the script somewhere safe.  I saved it in ~/Scripts, and gave it root-only permissions.
[*]sudo chmod +x /path/to/script/scriptname
[*]Add the script to your Start-up Applications. (System > Preferences > Startup Applications)
[/LIST]
```
#!/usr/bin/env python

#Author: Seamus Phelan

#This program runs a custom command/script just before gnome shuts 
#down.  This is done the same way that gedit does it (listening for 
#the 'save-yourself' event).  This is different to placing scipts 
#in /etc/rc#.d/ as the script will be run before gnome exits.
#If the custom script/command fails with a non-zero return code, a 
#popup dialog box will appear offering the chance to cancel logout
#
#Usage: 1 - change the command in the 'subprocess.call' in 
#           function 'session_save_yourself' below to be what ever
#           you want to run at logout.
#       2 - Run this program at every gnome login (add via menu System 
#           -> Preferences -> Session)
# 
#

import sys
import subprocess
import datetime

import gnome
import gnome.ui
import gtk


class Namespace: pass
ns = Namespace()
ns.dialog = None


def main():
    prog = gnome.init ("gnome_save_yourself", "1.0", gnome.libgnome_module_info_get(), sys.argv, [])
    client = gnome.ui.master_client()
    #set up call back for when 'logout'/'Shutdown' button pressed
    client.connect("save-yourself", session_save_yourself)
    client.connect("shutdown-cancelled", shutdown_cancelled)


def session_save_yourself( *args):
    #Unmount those CIFS shares!
    retcode = subprocess.call("sudo /etc/init.d/umountnfs.sh", shell=True)
    if retcode != 0:
        #command failed  
        show_error_dialog()
    return True

def shutdown_cancelled( *args):
    if ns.dialog != None:
        ns.dialog.destroy()
    return True


def show_error_dialog():
    ns.dialog = gtk.Dialog("There was a problem running your pre-shutdown script",
                           None,
                           gtk.DIALOG_MODAL | gtk.DIALOG_DESTROY_WITH_PARENT,
                           ("There was a problem running your pre-shutdown script - continue logout", gtk.RESPONSE_ACCEPT))
    if ns.test_mode == True:
        response = ns.dialog.run()
        ns.dialog.destroy()
    else:
        #when in shutdown mode gnome will only allow you to open a window using master_client().save_any_dialog()
        #It also adds the 'Cancel logout' button
        gnome.ui.master_client().save_any_dialog(ns.dialog)



#Find out if we are in test mode???
if len(sys.argv) >=2 and sys.argv[1] == "test":
    ns.test_mode = True
else:
    ns.test_mode = False

if ns.test_mode == True:
    main()
    session_save_yourself()
else:
    main()
    gtk.main()
```
[LIST]
[*]Run in terminal: ```
sudo visudo
```
[*] Add the following to the bottom of the file:```
%admin ALL=NOPASSWD: /etc/init.d/umountnfs.sh
```
[/LIST]

[LIST]
[*]Press *Ctrl-X* to exit, press *Y* to save changes, and hit *[Enter]* to write the file.
[/LIST]
 
I hope this helps!  I'm a linux noob, so apologies if my guide wasn't perfect. ;)
[B][COLOR=Black] (Credit to stevo1982 for the sudo password workaround!)
[/COLOR][/B]

Unfortunately this is solution still doesn't work for me :S, I'm using Ubuntu 9.10.

You just added this script in the autostart application? You didn't add anything to /etc/rc0.d or rc6.d directory  ??


EDIT:
It works if I shutdown from the gnome menu, it fail if I shutdown from th termina.
Is there a solution for that issue?

---

### Post by datman on 2010-01-12
Thanks, this worked nicely for me :)

---

### Post by ubradford on 2010-01-16
> **impolo said:**
> Unfortunately this is solution still doesn't work for me :S, I'm using Ubuntu 9.10.

You just added this script in the autostart application? You didn't add anything to /etc/rc0.d or rc6.d directory  ??


EDIT:
It works if I shutdown from the gnome menu, it fail if I shutdown from th termina.
Is there a solution for that issue?

No solution I am aware of.  See [post #5 in this thread]("http://ubuntuforums.org/showpost.php?p=8460466&postcount=5") for an explanation.

---

### Post by ubradford on 2010-01-16
> **robbuntista said:**
> It only works for users who have "Administer the system" checked in the "User Privileges" tab in User Settings properties. The other ones cannot use the sudo command.

So, if you have multiple users on a computer and only one has the admin rights, the problem is still opened.

Any idea?

There is likely a way to do this by embedding the admin's username and sudo password into the script. (Which is the way I originally had it set up.) Of course this comprimises security, so I wouldn't recommend it if you are worried about your normal users finding the script. Something like this may work:

Replace line:
```
retcode = subprocess.call("sudo /etc/init.d/umountnfs.sh", shell=True)
```With:
```
retcode = subprocess.call("echo admin's_sudo_password | sudo -u admin's_username -S /etc/init.d/umountnfs.sh", shell=True)
```Replace admin's_sudo_password and admin's_username with your sudo password and username.

---

### Post by ubradford on 2010-01-16
> **chipbennett said:**
> Anyone know how to modify this script for KDE?

I'm assuming all of those GNOME/GTK references aren't applicable for KDE/Kubuntu?

Thanks in advance!

The script will not work for KDE users, since the script is listening for a specific Gnome event. If someone can find a similar KDE event at shutdown, creating a script to listen for the event and execute commands may work. The trick is to run umountnfs.sh before network managers are killed.

---

### Post by akhilbehl on 2010-01-18
Hey All,

I have had this problem too. I am working presently on Karmic and access network from wireless and wired connections at different times.

I tried three different solutions for this problem:
1. The one given here: [http://ubuntuforums.org/showthread.php?t=1347340](http://ubuntuforums.org/showthread.php?t=1347340)
2. The one given by dmizer here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
3. And the one given here: [http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

However none of the solutions fixed my problem. I read in one of the posts that the real problem was to run the /etc/init.d/umountnfs.sh before the system is killed.

This gave me the simple idea, since I always have a terminal open, I wrote this bash function:

function bringdown()
    {
        sudo /etc/init.d/umountnfs.sh && sudo shutdown -h now
    }

This simply solves my problem.

However I was thinking of a more generic solution. I have never tried scripting. I was wondering if there can be a more elegant and generic solution to this. I have an idea, someone please let me know if this is feasible.

We  can create a script which runs this function `bringdown' as given above (preferable without the need for a sudo password prompt [perhaps using a credentials file or editing visudo]) and put this in the $PATH of each user, so that one can simply call the run dialog and bring the system down.

Please let me know if writing such a script is possible and easy. I am willing to learn and do homework if any is needed.

Thanks for reading the long post. Hoping for some replies.

---

### Post by Tybion on 2010-01-22
This fixes the problem for Xubuntu -

Make links in the rc folders to umountnfs.sh that are earlier in the alphabet than the existing link to umountnfs.sh.

> # For shutdowns ..
cd /etc/rc0.d
sudo ln -s ../init.d/umountnfs.sh K02umountnfs

# For reboots ..
cd /etc/rc6.d
sudo ln -s ../init.d/umountnfs.sh K02umountnfs


(This doesn't work if you use '-n' with the smbmount command because umountnfs.sh reads the /etc/mtab file to find mounts.)

---

### Post by solbot on 2010-02-02
I was also having the same issue using Karmic but have fixed it.
You can see my post [here]("http://ubuntuforums.org/showthread.php?t=1396770").

Not certain, but it *should* work for kubuntu, xubuntu, etc as well.
It also doesn't require any messing around with permissions.

---

### Post by in8sworld on 2010-10-21
I just wanted to say thanks to Ian Ferguson for describing the problem and pointing me to the solution here, ubradford for figuring out a solution which has been annoying me for months, and stevo1982 for the password fix. My Ubuntu 10.04 install now reboots and shuts down cleanly and immediately!

I do have a different problem now though: none of my CIFS mounted Windows shares listed in fstab are being mounted at startup anymore.  If I manually run mount -a they all mount fine.  Any ideas why that may have changed?

Nate

---

### Post by in8sworld on 2010-10-22
> **in8sworld said:**
> I do have a different problem now though: none of my CIFS mounted Windows shares listed in fstab are being mounted at startup anymore.  If I manually run mount -a they all mount fine.  Any ideas why that may have changed?

Everything came up fine this morning, so... never mind :)

---

### Post by tipiglen on 2011-03-20
THANKS!!!
[http://tipiglen.co.uk/loveandpeace3.gif](http://tipiglen.co.uk/loveandpeace3.gif)
ed

---

### Post by bobwyajnr on 2011-05-08
Hi

Sorry to butt into an old thread - especially as I am a complete noob! Found this thread linked to in another thread I was reading...

Perhaps someone could correct me, if I am wrong, but couldn't a simple [Upstart]("http://upstart.ubuntu.com/getting-started.html") script provide a more elegant solution to this problem that applies to all more recent Ubuntu (>=10.04??) flavours (Xubuntu, LXDE, Kubuntu, etc.)??

I'm (theoretically :-k) a big fan of the Upstart model - since it allows  service dependencies to be expressed (so startup and shutdown can be asynchronous).

Any comments?

Bob

---

### Post by tipiglen on 2011-11-10
Just a note to say that I recently found myself with my RAM almost filled, and after a long puzzling period discovered multiple orphan copies of the 'save yourself' "ShutdownCIFS" unmount script in my task list, each claiming around 6Mb....

After killing off a couple hundred of these poor wee orphans, my memory situation (and performance) is fully restored.

The script would seem to be unsatisfied because the external FS is at times not mounted because the server running it isn't online.

If anyone knows contact details for Seamus Phelan, the script's author, I'd appreciate a pointer.

Salaaaams
ed
__________________

---

