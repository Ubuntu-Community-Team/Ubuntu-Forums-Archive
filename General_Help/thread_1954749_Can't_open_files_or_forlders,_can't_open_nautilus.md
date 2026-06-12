---
title: "Can't open files or forlders, can't open nautilus"
date: 2012-04-08
forum: General Help
---

### Post by nana126 on 2012-04-08
Hi, this is my first post, hope you can help me!
I use ubuntu 11.10. I was using Inkscape a few days ago and suddenly the computer froze, so I turned it off, and then when I turned it on again, I couldn't open any of the files on my desktop, and I can't open my Personal Folder or any of the folders either.
I can open the programs and the internet browser, it's just the files and the folders. If I search for an specific file on the left pannel I can open some of them, but if I search for a folder, they don't appear.

I read I could open them with nautilus, but when I write nautilus on the terminal it says: "Could not register the application: Timeout was reached". If I search for nautilus on my guest account it opens my personal folder, but on the administrator account, nothing happens. When I try to open a file or a folder, it doesnt appear any error message, it doesn't happen anything at all. 
I tried to create a new administrator account, and copy the files and the folders, but it doesn't let me, so I guess I have to fix this account. 

Im new to Ubuntu so please, if you can help, explain me step by step :) thanks!

---

### Post by Frogs Hair on 2012-04-08
Try to to restart Nautilus with the following command before trying to open it  . ```
nautilus -q
```

---

### Post by nana126 on 2012-04-08
It says "Could not register the application: Timeout was reached" again.

---

### Post by forrestcupp on 2012-04-08
also, after you enter the **nautilus -q** code, try starting it again from the terminal by typing
```
nautilus
```and see if it gives any errors or output in the terminal. If it still doesn't work, post the output you get when you try starting Nautilus from the terminal this way, so we can see what's going on.

---

### Post by nana126 on 2012-04-08
It gives me this output: "Could not register the application: Timeout was reached"

---

### Post by forrestcupp on 2012-04-08
What do you get if you type
```
sudo nautilus
```

---

### Post by labinnsw on 2012-04-28
Having the same problem after upgrading to 12.04. "sudo nautilus" works but "nautilus" does not. 

Error message: > Could not register the application: Timeout was reached

---

### Post by evernacotola on 2012-05-02
I have the same problem, but only if I log in with a Active Directory account via centrifydc express, after the upgrade to ubuntu 12.04.

local accunt -> gnome or ubuntu session: works
AD account -> gnome session: starts, but no nautilus
AD account -> unity session: no desktop at all

With AD account and gnome session:

> ~$ nautilus /tmp/
Could not register the application: È stato raggiunto il timeout
> ~$ sudo nautilus /tmp/
Initializing nautilus-gdu extension
.. nautilus starts

The same thing appens with marlin and thunar.

dbus-monitor reports a endless loop doing:

```


method call sender=:1.285 -> dest=:1.41 serial=5701 path=/org/gtk/vfs/Daemon; interface=org.gtk.vfs.Daemon; member=GetConnection
method return sender=:1.41 -> dest=:1.285 reply_serial=5701
   string "unix:abstract=/dbus-vfs-daemon/socket-IHaHWoUL"
   string "unix:abstract=/dbus-vfs-daemon/socket-OcmPF6yl"
method call sender=:1.285 -> dest=org.gtk.vfs.Daemon serial=5702 path=/org/gtk/vfs/mounttracker; interface=org.gtk.vfs.MountTracker; member=lookupMount
   struct {
      array of bytes "/"
      array [
         struct {
            string "type"
            array of bytes "trash"
         }
      ]
   }
method return sender=:1.2 -> dest=:1.285 reply_serial=5702
   struct {
      string ":1.41"
      object path "/org/gtk/vfs/mount/1"
      string "Cestino"
      string "Cestino"
      string ""
      string ". GThemedIcon user-trash user"
      string ""
      boolean false
      array [
      ]
      struct {
         array of bytes "/"
         array [
            struct {
               string "type"
               array of bytes "trash"
            }
         ]
      }
      array [
      ]
   }

```[FONT=Courier New]

[/FONT]These three processes use more cpu than usual

```

[FONT=Courier New]  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                       
 2571 evernaco  20   0  9084 3100 2620 R   42  0.1  10:34.35 gvfsd-trash                                                                                   
 2474 evernaco  20   0 32684 4620  940 R   29  0.1   7:12.41 dbus-daemon                                                                                   
 2536 evernaco  20   0 1235m 514m  13m R   24 13.2   6:09.55 nautilus                                                                                    [/FONT]

```Killing the gvfsd-trash process now the loop is around gvfsd-burn:

```

[FONT=Courier New]method call sender=:1.37 -> dest=:1.99 serial=222959 path=/org/gtk/vfs/Daemon; interface=org.gtk.vfs.Daemon; member=GetConnection
method return sender=:1.99 -> dest=:1.37 reply_serial=222959
   string "unix:abstract=/dbus-vfs-daemon/socket-SRtlZExF"
   string "unix:abstract=/dbus-vfs-daemon/socket-30wUDUOg"
method call sender=:1.37 -> dest=org.gtk.vfs.Daemon serial=222960 path=/org/gtk/vfs/mounttracker; interface=org.gtk.vfs.MountTracker; member=lookupMount
   struct {
      array of bytes "/"
      array [
         struct {
            string "type"
            array of bytes "burn"
         }
      ]
   }
method return sender=:1.2 -> dest=:1.37 reply_serial=222960
   struct {
      string ":1.99"
      object path "/org/gtk/vfs/mount/1"
      string "Masterizzazione"
      string "Masterizzazione"
      string ""
      string "computer"
      string ""
      boolean false
      array [
      ]
      struct {
         array of bytes "/"
         array [
            struct {
               string "type"
               array of bytes "burn"
            }
         ]
      }
      array [
      ]
   }
[/FONT]

```killing again gvfsd-burn nautilus starts !!!

Workaround:

Renaming /usr/lib/gvfs/gvfsd-trash to /usr/lib/gvfs/gvfsd-trash.save and /usr/lib/gvfs/gvfsd-burn to /usr/lib/gvfs/gvfsd-burn.save now, after three days, finally have my unity session again with ubuntu 12.04

---

### Post by Oceola on 2012-05-04
I have a similar issue going on as well with 10.4.4LTS
I was trying to rectify the en@shaw errors and must have hit something, or at least I'm willing to take the blame for the error.
I can only open Nautilu using "sudo nautilus"
However the error I get is:
** ERROR **: boolean metadata with value other than true or false

I've searched several dozen files I considered might be the culprit but to no avail. Using both Gvim and Gedit for any edit or view.

It seems there's also a disconnect of some kind between the local trash and admin trash. If I open nautilus usin sudo and dump to trash anything from the user home file tree it winds up in the admin trash can but isn't indicated by a darkening of "empty trash.

There also seems to be some problem with holding files on the desktop, which don't show up until I open nautilus???

---

### Post by Oceola on 2012-05-07
Tried using the "rm -rf .gconf/apps/nautilus"
and the rm -rf .conf/nautilus and re-installing nautilus and nautilus-data.
It worked only temporarily. Once I tried to change the settings to list from icons it closed and would not open again.

There seems to be something which slams the door shut unless I use "sudo nautilus."
I keep getting the same error as before.
I removed a lot of Google data, is that tied into nautilus now?

---

### Post by aelmahmoudy on 2012-05-10
I installed nscd package to fix the problem.

---

### Post by Oceola on 2012-05-10
Problem fixed on this end as well.
Removed Lucid Lynx entirely and wiped disc.
Somehow there were a great many other issues along with not maintaining settings, histories for things like nettools, synaptic or the nautilus settings.
Created an unnecessary serial console.
Disc was screwed up from the factory as it had wrong locale setup, andall sorts of huge improprieties. 
Spent several weeks trying to stablize, find problems, remove pulse and other unwanted conditions with deep searches. Remove/reinstalls, editing with Gvim, Gedit or even dpkg-reconfigure wasn't resolving issues.
Last RKhunter scan had several dozen un-named, un-locatable hidden processes.
I've thrown in the towel.
It was a good ride since 2005, not a troll comment, just the way it is.
I'll stick it out with 8.04LTS as long as possible to find something which will have a better backwards compatibility.

Be well.

---

