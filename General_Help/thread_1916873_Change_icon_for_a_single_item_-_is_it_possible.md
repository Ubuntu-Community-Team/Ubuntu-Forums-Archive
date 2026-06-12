---
title: "Change icon for a single item - is it possible?"
date: 2012-01-28
forum: General Help
---

### Post by dwasifar on 2012-01-28
I'm using Xubuntu 11.10.  I've got a couple of script files on the desktop and would like to assign them different icons than the default "page" icon that shell scripts usually have.  I don't want the icon to change for ALL shell scripts; only these two.  Is it possible to change the icon for a particular item in this way?

I feel obliged to state the obvious: This is Xubuntu, so Gnome or Unity-related answers will not help.  Also, there is a good reason why the scripts themselves (and not launchers pointed at them) must live on the desktop.  I will explain this if asked, but it is not strictly relevant to the issue  :)

---

### Post by dwasifar on 2012-02-05
Nobody?

---

### Post by ankspo71 on 2012-02-06
Hi,
If you place the scripts in a directory with bin in the name (~/.local/bin/, /usr/bin/, etc) then they should have no problems running automatically when being called upon by a shortcut, because they will be in your 'paths'. Paths are directories that allow files to be run as executable files. To see your paths open a terminal and paste the following:
```
echo $PATH
```

After you move the scripts you will be able to create application launchers (shortcuts) for them on the desktop, where they can each have their own icons.

Hope this helps.

---

### Post by dwasifar on 2012-02-06
> **ankspo71 said:**
> Hi,
After you move the scripts you will be able to create application launchers (shortcuts) for them on the desktop, where they can each have their own icons.

Thank you, but as I said originally, I cannot use launchers.  The scripts must actually be located on the desktop to function.

There is a good reason for this.  These scripts are designed to act as drag-and-drop targets.  XFCE desktop launchers do not pass the full path and filename of an item dropped onto them.  

If I drag and drop an item onto the script itself, the $1 variable inside the script receives the full path and filename of the dropped object.  This does not work if I drop the item onto an XFCE launcher pointed at that script.  (It does work in Gnome's launchers.)  

So for the scripts to work as intended, they have to live on the desktop, and I want to give them icons that better reflect their function.

---

### Post by BenB1 on 2012-02-07
> **File/Launcher Icons**

         **xfdesktop** can also display on the desktop the contents of the          $XDG_DESKTOP_DIR folder, which can be set in         the $XDG_CONFIG_HOME/user-dirs.dirs file (if you         do not have this file, it will use $HOME/Desktop).         Files can be arranged, copied, moved,          and linked to and from a file manager, and opened using          preferred applications.  Application and URL launchers can          also be created on the desktop.  The file icon view is modeled          to have a similar look and feel as the         [Thunar]("http://thunar.xfce.org/") file         manager. 



file:///usr/share/xfce4/doc/C/xfdesktop.html#xfdesktop-file-icons



It sounds to me that XFCE's default file manager, Thunar, chooses icons. Which then makes it an overall system issue.

> 
My Xfce Desktop doesn't have any shortcut icons, why?  
[LIST]
[*] **Xfce 4.2**: You will  need a third party program to provide you the icons. Suggestions are:  pcmanfm, rox, nautilus etc etc… Beware that those programs will kill  xfdesktop and the ability to use the right click menu.
[*] **Xfce 4.4**: You can  enable the icons in : Settings > Desktop Preferences > Behavior  > Desktop Icons. You will need to build xfdesktop with thunar-vfs and  dbus support. (./configure –enable-thunar-vfs –enable-exo)
[/LIST]
  
  ****


[http://wiki.xfce.org/faq](http://wiki.xfce.org/faq)


And finally, [this]("http://forum.xfce.org/viewtopic.php?id=6587") may provide a decent answer for you. It is a link to a posting explaining how to alter mime type icon associations for Thunar. That does seem to be what you're looking to achieve. If not my apologies.

---

### Post by LewisTM on 2012-02-07
I'm a bit curious as to how you cannot pass the full path and filename to Xfce launchers.

It works perfectly here, both on desktop and panel launchers.
Make sure you include %f in your command to pass the path/filename of the dropped item.

I just ran a simple test with a desktop launcher running
```
sh -c "echo %f > ~/file.txt"
```
and the resulting file.txt contains the full path/name of any dropped item.

---

### Post by dwasifar on 2012-02-07
> **BenB1 said:**
> And finally, [this]("http://forum.xfce.org/viewtopic.php?id=6587") may provide a decent answer for you. It is a link to a posting explaining how to alter mime type icon associations for Thunar. That does seem to be what you're looking to achieve. If not my apologies.

Well, almost.  The problem with that is that changing the mime type icon association would change the icons for ALL shell scripts, not just the particular ones I'm interested in altering.

> **LewisTM said:**
> I'm a bit curious as to how you cannot pass the full path and filename to Xfce launchers.

It works perfectly here, both on desktop and panel launchers.
Make sure you include %f in your command to pass the path/filename of the dropped item.

I just ran a simple test with a desktop launcher running
```
sh -c "echo %f > ~/file.txt"
```
and the resulting file.txt contains the full path/name of any dropped item.

Aha.  That may do it.  I'm not on my XFCE box right now, but I will try it with %f in the config when I get back there and see if that helps.

Thanks.  :)

---

### Post by dwasifar on 2012-02-08
> **dwasifar said:**
> Aha.  That may do it.  I'm not on my XFCE box right now, but I will try it with %f in the config when I get back there and see if that helps.

Thanks.  :)

That solves my problem.  Marking thread solved.  Thanks!

---

### Post by LewisTM on 2012-02-09
I guess you didn't ask the right question to begin with :)
About you initial question, I don't think it's possible to change icons at the single file level. 
The closest thing would be emblems. However I am just realizing to my surprise that emblems are not shown on the desktop. So there's a bug for you! I won't make a big case, the days of xfdesktop are numbered anyways.

Cheers!

---

### Post by dwasifar on 2012-02-09
> **LewisTM said:**
> I guess you didn't ask the right question to begin with :)
I guess I didn't.  :)  In hindsight that seems obvious.  But I'm a Gnome refugee, and in Gnome you don't have to add %f to get the launcher to pass that info, so it never occurred to me to try that in XFCE.  I set up a launcher, dropped an object onto it, discovered by experimentation that the path wasn't getting passed to the script, and thought it was simply a limitation of XFCE.

I keep being surprised by XFCE; sometimes when something that should be easy turns out strangely difficult to do, but mostly the other way around.  For a low-resource DE it's really robust and configurable.

> **LewisTM said:**
> About you initial question, I don't think it's possible to change icons at the single file level. 
The closest thing would be emblems. However I am just realizing to my surprise that emblems are not shown on the desktop. So there's a bug for you! I won't make a big case, the days of xfdesktop are numbered anyways.

Yes, I tried emblems too, and found out the same.  Why do you say xfdesktop's days are numbered?

---

### Post by LewisTM on 2012-02-09
You are right, the %f (and others like %u and %d) should be better documented. They do allow more powerful possibilities like inserting a filename in the middle of a command, not just at the end.

Xfdesktop will be replaced by an extension of Thunar in the next version of Xfce, a bit like Nautilus for GNOME. Which makes sense, it's just a directory window in icon view with a pretty wallpaper. That will solve issues like single-click launching, operations on multiple items, pasting items and emblems.

---

