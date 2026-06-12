---
title: "Problem with X session....I think...."
date: 2009-07-15
forum: General Help
---

### Post by Gio24 on 2009-07-15
I have just installed Ubuntu 9.04 on my old PC together with WinXP with a dual boot. Everything went smooth but when I start Ubuntu I receive a message saying that my session has lasted less than 10 secs and  I need to logout. Below I have posted the error message I get, for a newbie as me difficult to understand, I would appreciate very much if somebody could spend few minutes to read it through and give me some advices. Just for information my video card is Nvidia Riva TNT2 model64/Model64Pro Bios 2.05.1903.

Many thanks!

/etc/gdm/Xsession: Beginning session setup... 
Setting IM through im-switch for locale=en_US. 
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default. 
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE. 
I: caps.c: Dropping root privileges. 
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE. 
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the 
configuration. However, we lack the necessary privileges: 
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we 
have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits. 
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit 
privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO 
resource limits for this user. 
GNOME_KEYRING_SOCKET=/tmp/keyring-vWRUSK/socket 
SSH_AUTH_SOCK=/tmp/keyring-vWRUSK/socket.ssh 
GNOME_KEYRING_PID=3995 
(gnome-settings-daemon:3991): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' 
failed 
(gnome-settings-daemon:3991): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' 
failed 
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/giordano/.config/metacity/sessions/
1011a0d5ae9350d94f124690628036547200000039010020.ms: Failed to open file 
'/home/giordano/.config/metacity/sessions/1011a0d5ae9350d94f124690628036547200000039010020.
ms': No such file or directory 
x-session-manager[3901]: WARNING: Unable to parse command '(null)': Key file contains key 
'Terminal' which has value that cannot be interpreted. 
x-session-manager[3901]: ******************* START ******************************** 
x-session-manager[3901]: Frame 0: x-session-manager [0x8061015] 
x-session-manager[3901]: Frame 1: x-session-manager [0x80611c4] 
x-session-manager[3901]: Frame 2: [0xb80b1400] 
x-session-manager[3901]: Frame 3: /usr/lib/libglib-2.0.so.0(g_free+0x36) [0xb7a31126] 
x-session-manager[3901]: Frame 4: /usr/lib/libglib-2.0.so.0(g_strfreev+0x20) [0xb7a4a090] 
x-session-manager[3901]: Frame 5: x-session-manager [0x806eba5] 
x-session-manager[3901]: Frame 6: x-session-manager [0x806f337] 
x-session-manager[3901]: Frame 7: x-session-manager [0x8052b77] 
x-session-manager[3901]: Frame 8: x-session-manager [0x8065606] 
x-session-manager[3901]: Frame 9: /usr/lib/libglib-2.0.so.0(g_hash_table_find+0x5c) [0xb7a1a29c] 
x-session-manager[3901]: Frame 10: x-session-manager [0x8065b47] 
x-session-manager[3901]: Frame 11: x-session-manager [0x8065de6] 
x-session-manager[3901]: Frame 12: /usr/lib/libgobject-
2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84) [0xb7abf3a4] 
x-session-manager[3901]: Frame 13: /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab) 
[0xb7ab1c7b] 
x-session-manager[3901]: Frame 14: /usr/lib/libgobject-2.0.so.0 [0xb7ac7e57] 
x-session-manager[3901]: Frame 15: /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9) 
[0xb7ac94b9] 
x-session-manager[3901]: Frame 16: /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb7ac9936] 
x-session-manager[3901]: Frame 17: x-session-manager [0x8051761] 
x-session-manager[3901]: Frame 18: x-session-manager [0x8069f2e] 
x-session-manager[3901]: Frame 19: x-session-manager [0x80589b6] 
x-session-manager[3901]: Frame 20: /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab) 
[0xb7ab1c7b] 
x-session-manager[3901]: Frame 21: /usr/lib/libgobject-2.0.so.0 [0xb7ac7e57] 
x-session-manager[3901]: Frame 22: /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f) 
[0xb7ac934f] 
x-session-manager[3901]: Frame 23: /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb7ac9936] 
x-session-manager[3901]: Frame 24: x-session-manager [0x805603c] 
x-session-manager[3901]: Frame 25: /usr/lib/libSM.so.6(_SmsProcessMessage+0xd5a) [0xb809a9fa] 
x-session-manager[3901]: Frame 26: /usr/lib/libICE.so.6(IceProcessMessages+0x31a) [0xb808f9fa] 
x-session-manager[3901]: Frame 27: x-session-manager [0x8056c11] 
x-session-manager[3901]: Frame 28: /usr/lib/libglib-2.0.so.0 [0xb7a5fdad] 
x-session-manager[3901]: Frame 29: /usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e
[0xb7a28b88] 
x-session-manager[3901]: Frame 30: /usr/lib/libglib-2.0.so.0 [0xb7a2c0eb] 
x-session-manager[3901]: Frame 31: /usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca) [0xb7a2c5ba] 
x-session-manager[3901]: Frame 32: /usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0xb7d7b7d9] 
x-session-manager[3901]: Frame 33: x-session-manager [0x8062a09] 
x-session-manager[3901]: Frame 34: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) 
[0xb7789775] 
x-session-manager[3901]: Frame 35: x-session-manager [0x80511e1] 
x-session-manager[3901]: ******************* END ********************************** 
(nautilus:4020): EggSMClient-WARNING **: Failed to connect to the session manager: IO error 
occured opening connection 

:confused:

---

