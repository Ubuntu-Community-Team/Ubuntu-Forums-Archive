---
title: "No password require for wakeup from suspend??"
date: 2009-08-08
forum: General Help
---

### Post by ysha4171 on 2009-08-08
I have set up the keyboard shortcut for suspend.  The shortcut suspend works fine, however it does not ask for password on resume.   But if i suspend from power-management icon at desktop top right corner,  then it does ask for password on resume. 
Anyone knows why?  :confused:

PS: i have ticked "lock screen when screen saver is active", also ticked "suspend" and "use_screensaver_setting"  in gconf-editor>app>gnome-power-management>lock.

cheers

---

### Post by ysha4171 on 2009-08-08
I have set up the keyboard shortcut for suspend. The shortcut suspend works fine, however it does not ask for password on resume. But if i suspend from power-management icon at desktop top right corner, then it does ask for password on resume. 
Anyone knows why?  :confused:

PS: i have ticked "lock screen when screen saver is active", also ticked "suspend" and "use_screensaver_setting" in gconf-editor>app>gnome-power-management>lock.

cheers

---

### Post by ibuclaw on 2009-08-08
Threads merged. Please don't cross post in the future.


How have you setup the shortcut to suspend up?
That may give a hint as to why this is happening.

Regards
Iain

---

### Post by tgalati4 on 2009-08-08
There are several ways to suspend. What version of Ubuntu?  I can't tell from your post.

What was the precise command that you assigned to the keyboard shortcut?

If you suspend using the icon and you want that behavior, then you need to determine the switch.  I presume you are using Gnome Power Manager 2.24 under Jaunty.

What happens when you run this from the command:

$gnome-power-cmd suspend

If it works the way you want, then assign that command to the shortcut.

---

### Post by ysha4171 on 2009-08-08
It worked now!! Thanks!  But i got this message:   Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Is this a problem at all?

PS:I assigned this command "/usr/sbin/pm-suspend" to  to a keyboard shortcut before.  So why "pm-suspend" and "gnome-power-cmd suspend" have different ways of suspending? 


Again many thanks.

---

### Post by tgalati4 on 2009-08-08
cat /usr/bin/gnome-power-cmd
cat /usr/sbin/pm-suspend

Perhaps you can tell us the differences.

I'm sure the Gnome folks programmed gnome-power-cmd for a reason.  

Like I said, there are several ways to put a machine to sleep.

sudo echo closed > /proc/acpi/button/lid/LID/state

There are several others.

---

### Post by ysha4171 on 2009-08-08
Thanks [tgalati4]("http://ubuntuforums.org/member.php?u=241895")!
 
  It seems "pm-suspend" removes the suspend lock no matter what happens?    

:)

---

### Post by tgalati4 on 2009-08-09
That explains why gnome needed their own suspend script, to add screen security to the desktop/laptop.

---

