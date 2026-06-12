---
title: "Add system menu to top panel?"
date: 2010-11-05
forum: General Help
---

### Post by cabse7en on 2010-11-05
I've just installed the xubuntu GUI on my ubuntu server and by default I only see Applications and Places on my top panel. There is no option to add the system menu under "Add new items", so I'm curious as to how to go about it.

On a side note, is there a way I can have the system boot into the original command prompt by default, and how can I enable and disable the GUI at my convenience?

Appreciate the help, I'm a bit of a Linux newbie, but very interested in getting away from the shackles of Microsoft. Thanks!

---

### Post by Brandon Williams on 2010-11-07
Others might suggest methods that use a GUI app, but I do these things with the command line and/or vim. Here's what I would do for each of the tasks you mention.

1. creating a system menu
First, cp /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu ~/.config/menus/xfce-system.menu. Then use your preferred editor to open ~/.config/menus/xfce-system.menu. This is an XML file, and you want to find the <Menu> block the includes <Name>System</Name>. Edit the file so that this is the only <Menu> block in the file, and make sure that you include both <DefaultAppDirs/> and <DefaultDirectoryDirs/> inside the <Menu> block. When I do this, the resulting file looks like this:```
<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
  "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">
  <Menu>
    <Name>System</Name>
    <DefaultAppDirs/>
    <DefaultDirectoryDirs/>
    <Directory>xfce-system.directory</Directory>
    <Include>
      <Category>System</Category>
    </Include>
    <Exclude>
      <Filename>ubuntu-software-center.desktop</Filename>
    </Exclude>
  </Menu>
```
After creating that file, right click on the panel, select "Add New Items ...", and then select "Xfce Menu". In the dialog, select "Use custom menu file" and then specify your new xfce-system.menu file.

2. disable gdm and boot to a console login prompt instead
Use sudo and your favorite console editor to open /etc/X11/default-display-manager (e.g. sudo vim /etc/X11/default-display-manager). If you are using gdm as your graphical login manager, it will say "/usr/sbin/gdm". Simply delete that line and save the file. If the file is empty, then the system will not use a graphical login manager and present a console prompt for login instead. From within a text-mode session, if you wish to start an X session, simply run the command 'startx' on the command line.

---

