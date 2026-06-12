---
title: "xubuntu: where are the default mount options?"
date: 2012-09-13
forum: General Help
---

### Post by 7bit on 2012-09-13
xubuntu will automount removable drives when plugged into the usb port and I need to change the default for all vfat drives to shortname=lower. Where do I configure this? 

Please don't suggest fstab, this does not seem to play well with the automatic creation and deletion of needed mount points in /media/ there must be a proper way to do this.

TIA,
Bernd

---

### Post by LewisTM on 2012-09-13
There is a way!
Install package **usbmount**. This package will mounts usb devices in a configurable way.
Edit file /etc/usbmount/usbmount.conf
You can change various options in that file to your liking. The important ones are:

FILESYSTEMS="vfat"
FS_MOUNTOPTIONS="-fstype=vfat,shortname=lower,umask=0,utf8=1,showexec,flush,uhelper=udisks"

Also, to safely disconnect a device, you have to run 
```
pumount /media/usb
```
Another way would be to unmount with the device brand name.
```
pumount /var/run/usbmount/<brand name>
```
This could be made into a launcher. 

Cheers!

---

### Post by 7bit on 2012-09-14
I have tried this and while usbmont works on its own as advertised it unfortunately seems to be totally incompatible with xfce: 

When I plug in my camera then usbmount will mount it at /media/usb0 but xfce (thunar) will display an icon on the desktop "KAMERA" (thats the vfat file system label I gave to it after formatting) and when hovering over it it says "not mounted" (it seems thunar thinks it should be mounted at /media/KAMERA/ but instead usbmount already mounted it at /media/usb0/). I can disable the icon on the desktop but inside thunar it will still show me "KAMERA" in the left side bar (and crash if I click it).

The strange thing is also pcmanfm and also nautilus will display this "KAMERA" entry in their sidebars (and in nautilus I can even use it), so this makes me believe that there is something else that is managing these devices that is NOT part of xfce or thunar (because other file managers can see it too), I would like to know what exactly it is that is finding the plugged in devices, giving names to them and making them appear in the side bar of 3 different file managers. Maybe this unknown "something" that is doing this is the correct place to configure the aoutomounting behavior? 

Why is all this automatic voodoo so poorly documented, what exactly is going on behind the scenes if I plug in an usb drive, which part is responsible for creating the item in the sidebar of the file managers and the desktops, which piece of software is attempting to mounting it and why does it not recognize that it actually *is* mounted already?

---

### Post by 7bit on 2012-09-14
Ok, after a lot of googling and experimenting I think I have found a working solution:


[LIST]
[*]remove above mentioned usbmount and also any other automounter script
[*]**disable** auto mounting in thunar
[*]install udisks-glue: ```
sudo apt-get install udisks-glue
```
[*]edit the file /etc/udisks-glue.conf to contain filters for certain devices and commands to execute when they match. Mine now looks like this (only vfat devices will be matched by the filter and automounted for now, can add more filters and matches later):
```

filter vfat {
    partition_table = false
    usage = filesystem
    type = vfat
}

match vfat {
    automount = true
    automount_options = { sync, 'shortname=lower' }
    post_mount_command = "notify-send '%device_file\nhas been mounted at\n%mount_point' --icon=gnome-dev-harddisk-usb"
    post_unmount_command = "notify-send '%device_file\nhas been unmounted' --icon=gnome-dev-harddisk-usb"
}

```
[*]start the daemon udisks-glue as user automatically from within the session autostart or start it manually (as user, not as root!), kill and restart it after config file has changed.
[/LIST]
The above filter will match all devices that have a vfat file system, for each "filter" directive there is also a "match" directive with the same name and the one above will make it use my custom mount options and also display some nice libnotify popups on mount and unmount.


It seems xfce and Thunar already use udisks to detect which devices exist and also would use udisks to mount them with (hardcoded) default options and the above is 100% compatible with it since it would mount them exactly in the same manner and choose the same mount points that thunar would have choosen and I can then also use the icons on the desktop to open them or to unmount them again.

Edit: I have marked this thread as "solved" although the underlying problem is not really solved at all. Thunar is simply missing this functionality and I am now totally bypassing and disabling Thunar's auto-mounting feature, it would be extremely nice if the xfce authors could implement such configurable filters and custom mount options directly in Thunar itself to remove the need for using udisks-glue instead of thunar-volman.

---

### Post by LewisTM on 2012-09-14
Thanks for the info! It's amazing what a determined mind can come up with.

FYI Thunar and Xfce have little to do with disk automounting, it's all managed by Devicekit then passed on to [GIO/GVFS.]("http://en.wikipedia.org/wiki/GVFS") The latter subsystem is an offshoot of GNOME. As seems to be the trend lately, GNOME apps have hardcoded instead of configurable settings. Thunar-volman is just one layer on top that calls those processes.

Cheers!

---

### Post by 7bit on 2012-09-14
> **LewisTM said:**
> 
FYI Thunar and Xfce have little to do with disk automounting, it's all managed by Devicekit then passed on to [GIO/GVFS.]("http://en.wikipedia.org/wiki/GVFS") The latter subsystem is an offshoot of GNOME. 

I just had a quick look into the source code of thunar-volman and it is calling g_volume_mount() when it detects the event. So it is indeed thunar-volman who is actually mounting it (of course it doesn't call mount itself, it does it through a very abstract API but ultimately it is thunar-volman who gets notified and then deciding whether to mount or not to mount and then doing it). So instead of calling the very limited g_volume_mount() which does not allow to pass additional mount options it could be made to use the udisks API directly to initiate the mounting, this way it would be possible to pass mount options.

---

### Post by LewisTM on 2012-09-14
> **7bit said:**
> I just had a quick look into the source code of thunar-volman and it is calling g_volume_mount() when it detects the event. So it is indeed thunar-volman who is actually mounting it (of course it doesn't call mount itself, it does it through a very abstract API but ultimately it is thunar-volman who gets notified and then deciding whether to mount or not to mount and then doing it). So instead of calling the very limited g_volume_mount() which does not allow to pass additional mount options it could be made to use the udisks API directly to initiate the mounting, this way it would be possible to pass mount options.
Yep, g_volume_mount() is a call to GIO.
See [http://developer.gnome.org/gio/2.28/GVolume.html](http://developer.gnome.org/gio/2.28/GVolume.html)
You might take this to the Xfce devs but I fear they will answer that they have limited resources and prefer to reuse well-tested libraries.

---

### Post by Morbius1 on 2012-09-14
How are you disabling automounting in Thunar?

[LIST]
[*]> **disable** auto mounting in thunar
[/LIST]

---

### Post by 7bit on 2012-09-14
> **LewisTM said:**
> Yep, g_volume_mount() is a call to GIO.
See [http://developer.gnome.org/gio/2.28/GVolume.html](http://developer.gnome.org/gio/2.28/GVolume.html)
You might take this to the Xfce devs but I fear they will answer that they have limited resources and prefer to reuse well-tested libraries.

An alternative would be on the"Storage" tab in thunar-volman:

instead of:

[X] mount removable drives when hot-plugged

this could be changed into something like:

when a removable drive is hot-plugged
(*) mount the drive
(_) execute this command: [__________________________][...]
(_) do nothing

Then it would not break any exiting code, would not introduce new dependencies and not require to design a complicated UI to set up filters and mount options but it would enable people like me to write arbitrarily complex scripts to do all kinds of fancy stuff with the device (check what type it is, mount it themselves, do other stuff, etc.)

---

### Post by 7bit on 2012-09-14
> **Morbius1 said:**
> How are you disabling automounting in Thunar?
  

In the options on the advanced tab there is a link to the volume manager settings, there on the "storage" tab you can uncheck the box "mount drives when hot-plugged". Then it will not mount them immediately. It might still try to mount them later when you click on the unmounted device icon but this leaves enough time for udisks-glue to mount it immediately when plugged in.

---

### Post by Morbius1 on 2012-09-15
This is all very interesting. I started playing with this a bit to see if I could "fix" a problem many users have with Samba sharing of an external USB drive. It's easy enough to make it work in Samba itself but ...

These are the steps I took to automount an external **[COLOR=Blue]ntfs[/COLOR]** usb drive so that it mounts with permissions of 777 instead of the default 0700:

** Insted of /etc/udisks-glue.conf I created a file at $HOME/.udisks-glue.conf.
** Then I added the following:
```
filter ntfs {
    partition_table = false
    usage = filesystem
    type = ntfs
}

match ntfs {
    automount = true
    automount_options = { sync, 'umask=0000' }
    post_mount_command = "notify-send '%device_file\nhas been mounted at\n%mount_point' --icon=gnome-dev-harddisk-usb"
    post_unmount_command = "notify-send '%device_file\nhas been unmounted' --icon=gnome-dev-harddisk-usb"

```** Then I started udisks-glue
** I did not disable auto mounting in thunar [COLOR=Blue]only because I forgot to do so[/COLOR] - it seems to work without doing that in my limited tests.

Sure enough it mounted to /media with permissions of 777 just like it should. What I have not been able to do is also launch thunar to that mount point.

I tried many variations:

** I added the following as an separate statement:
```
post_insertion_command = "thunar '%mount_point'"
```** I also added "thunar %mount_point" after an && to the end of the post_mount_command.

But I can't seem to launch thunar for some reason - at least not yet :)

---

### Post by Morbius1 on 2012-09-15
You know what they say about 1000 monkeys in front of typewriters? Well I finally got it:
```
post_mount_command = "notify-send '%device_file\nhas been mounted  at\n%mount_point' --icon=gnome-dev-harddisk-usb | thunar  %mount_point"
```Now it notifies you that the it has mounted and automatically launches thunar to that location.

There's another interesting thing about this. I tried to change permissions to allow access to only members of one group.

This does not work:
```
automount_options = { sync, 'umask=0007', 'gid=46' }
```This does:
```
automount_options = { sync, 'gid=46','umask=0007' }
```Not sure why the relative position of gid should matter but it apparently does.

---

### Post by 7bit on 2012-09-15
> **Morbius1 said:**
> 
** I did not disable auto mounting in thunar [COLOR=Blue]only because I forgot to do so[/COLOR] - it seems to work without doing that in my limited tests.


Its probably a race condition, udisks-glue will get its events directly from udisks and will initiate the mount directly through udisks while in xfce there is GIO on top of udisks and also it first has to start a new thunar-volman process when a device is plugged in which will then request the mount through GIO and by the time thunar-volman's mount request has finally arrived at udisks it is probably already processing the mount request that came from udisks-glue a few milliseconds earlier.

This also means that as a side effect it should still be able to mount those devices for which you have not defined a filter in udisks-glue.

---

### Post by Morbius1 on 2012-09-15
> **7bit said:**
> Its probably a race condition, udisks-glue will get its events directly from udisks and will initiate the mount directly through udisks while in xfce there is GIO on top of udisks and also it first has to start a new thunar-volman process when a device is plugged in which will then request the mount through GIO and by the time thunar-volman's mount request has finally arrived at udisks it is probably already processing the mount request that came from udisks-glue a few milliseconds earlier.

This also means that as a side effect it should still be able to mount those devices for which you have not defined a filter in udisks-glue.
Actually that was my concern about all this. I would rather have the system automount things on it's own and only use udisks-glue as an exception. Are you suggesting that eventually my "ntfs-usb only" approach might fail depending on certain conditions unless I stop auto mounting completely?

---

### Post by 7bit on 2012-09-15
> **Morbius1 said:**
> Actually that was my concern about all this. I would rather have the system automount things on it's own and only use udisks-glue as an exception. Are you suggesting that eventually my "ntfs-usb only" approach might fail depending on certain conditions unless I stop auto mounting completely?

No, theoretically it might work. My theory is that udisks-glue is a little bit faster than thunar (which has to go through all this GIO/gvfs stuff) and so the unintended (but positive) side effect that you are observing is that udisks-glue will have precedence for all devices for which it has a matching filter simply because it comes a little bit earlier. When the mount command from thunar-volman arrives a few milliseconds later it might simply be ignored because the device is already mounted (or in the process of being mounted).

And if there is no matching filter then udisks-glue will simply do nothing at all and thunar-volman can do its mount with default options.

But all this is only a theory based on your observations, I  did not test this myself yet but I think it might make sense.

---

### Post by Morbius1 on 2012-09-15
Understood. This has some interesting possibilities. Do you always find interesting things like this when you try to solve a problem in Linux ;).

Anyway, I appreciate you taking the time to respond.

---

