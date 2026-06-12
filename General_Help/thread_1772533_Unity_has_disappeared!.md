---
title: "Unity has disappeared?!"
date: 2011-05-31
forum: General Help
---

### Post by jespdj on 2011-05-31
When logging in, I suddenly got a message saying "It appears you do not have the hardware to run Unity", and it initialized the old GNOME 2 desktop.

Ofcourse I have the hardware to run Unity (an NVIDIA GTX 580), and it has worked normally until now...

Now Unity won't come back, even after logging out / in or rebooting. The video driver works normally and NVIDIA X Server Settings does not show that there's anything wrong with my video card or drivers.

Is this a bug? Did this happen to anyone else? How do I get the Unity desktop back?

---

### Post by jespdj on 2011-05-31
I noticed I have a file named .xsession-errors in my home directory which contains the following.

What's the problem?
> 
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  138 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x1ff
  Serial number of failed request:  32
  Current serial number in output stream:  32
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  138 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x1ff
  Serial number of failed request:  32
  Current serial number in output stream:  32
GNOME_KEYRING_CONTROL=/tmp/keyring-yCkqEg
SSH_AUTH_SOCK=/tmp/keyring-yCkqEg/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-yCkqEg
SSH_AUTH_SOCK=/tmp/keyring-yCkqEg/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-yCkqEg
SSH_AUTH_SOCK=/tmp/keyring-yCkqEg/ssh
Initializing nautilus-gdu extension

(nautilus:3055): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (nm-applet:3056): DEBUG: old state indicates that this was not a disconnect 0

(nautilus:3055): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:3055): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:3055): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:3055): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:3055): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:3055): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:3062): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x2e00024 (jesper@neu); these messages lack timestamps and therefore suck.


---

### Post by jespdj on 2011-05-31
I have no idea what went wrong, but I reinstalled the NVIDIA driver and now everything seems to work normally again.

---

