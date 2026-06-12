---
title: "understanding dbus"
date: 2011-04-30
forum: General Help
---

### Post by jesuisbenjamin on 2011-04-30
Hello there,

i'm playing around with dbus-monitor to try and understand how dbus is working and how Ubuntu functions too.
I'd like some help understanding few things, so if you feel like and have the patience please teach me some :)

Could you please let me know how to read the following properly? I understand the big idea, but not the details. > signal sender=:1.1948 -> dest=(null destination) serial=1829990 path=/org/ayatana/menu/DA00003; interface=org.ayatana.dbusmenu; member=ItemPropertyUpdated
   int32 23
   string "enabled"
   variant       boolean true
method call sender=:1.6 -> dest=org.freedesktop.Notifications serial=1399 path=/org/freedesktop/Notifications; interface=org.freedesktop.Notifications; member=GetCapabilities
 I get that the first one is a signal whereas the second is a method. Does destination mean there can be a specific receiver/slot for a signal? What's a member? And are the items of the list following the signal the arguments passed in the signal? What are sender and serials?

How can i spy on dbus methods and signals using the dbus module in python? I've seen [the dbus-python tutorial]("http://dbus.freedesktop.org/doc/dbus-python/doc/tutorial.html") and it teaches how to listen to all signals (by specifying neither interface nor path etc.) But how to track methods when triggered?

Finally, i noticed something about the relationship between volume-control and notifications. From what i read from the dbus-monitor output > method call sender=:1.6 -> dest=org.freedesktop.Notifications serial=1400 path=/org/freedesktop/Notifications; interface=org.freedesktop.Notifications; member=Notify
   string "gnome-settings-daemon"
   uint32 0
   string "notification-audio-volume-medium"
   string " "
   string ""
   array [
   ]
   array [
      dict entry(
         string "value"
         variant             int32 38
      )
      dict entry(
         string "x-canonical-private-synchronous"
         variant             string "volume"
      )
   ]
   int32 -1

It seems that the notification is triggered by its method. In my view it would make more sense if there was a signal emitted "notification-audio-volume-medium" while the notification would listen for this signal and react accordingly. If the sending / receiving would be public rather than private, it would allow for more flexibility in the OS or am i wrong? For instance if there was a public signal for "volume-medium" then several notification applications could exist and also new applications would just have to bother sending a signal while picking up and handling the signal would be the notifying application's business.

I'm just new to dbus and perhaps i am confused about it. So if you have any knowledge to share i'd appreciate it.

Thanks.
Benjamin

---

