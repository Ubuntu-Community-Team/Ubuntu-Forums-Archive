---
title: "GIMP crashes"
date: 2010-07-04
forum: General Help
---

### Post by HomoGleek on 2010-07-04
Hello..

Everytime I try use the eraser of text tools in GIMP it crashes, the application instantly disappears of the screen. I have uninstalled and reinstalled via the SC but no luck. Any ideas?

---

### Post by HomoGleek on 2010-07-05
bump :/

---

### Post by khelben1979 on 2010-07-05
What version of GIMP are you using?

Have you tried the same thing with other applications closed down? It can be a RAM issue, so giving us a list of the computer hardware will also help diagnosing the problem.

---

### Post by lukeiamyourfather on 2010-07-05
Not enough information is given to troubleshoot. What version of GIMP, what version of Ubuntu, 64-bit or 32-bit, any plugins or modifications to GIMP? Have you checked for the bug on the GIMP project?

---

### Post by HomoGleek on 2010-07-05
Default version in 10.04, no extensions.

EeePC900, 1GB Ram.

---

### Post by lukeiamyourfather on 2010-07-05
> **HomoGleek said:**
> Default version in 10.04, no extensions.

EeePC900, 1GB Ram.

No issues with using the eraser in GIMP from what I can tell in Ubuntu 10.04. Maybe try submitting and issue/bug to the GIMP project and specifically mention the hardware. Cheers!

---

### Post by HomoGleek on 2010-07-05
It did work until a couple of days ago, so I think hardware is rules out?

---

### Post by HomoGleek on 2010-07-05
Error code that appears in terminal

```


darren@EeePC900:~$ gimp
VANISH
gimp: fatal error: Failed to register GObject with DBusConnection

(script-fu:9598): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error

```

---

### Post by AlphaLexman on 2010-07-05
Is it a particular file you're working on? does gimp crash only on erase or can you draw anything. Check that nothing is selected on any layers.

---

### Post by HomoGleek on 2010-07-05
> **AlphaLexman said:**
> Is it a particular file you're working on? does gimp crash only on erase or can you draw anything. Check that nothing is selected on any layers.
Thanks, but it happens regardless of the image, even if I create a new blank image.

---

### Post by AlphaLexman on 2010-07-05
from the command line try:
```
gimp --stack-trace-mode always
```
and post the output

---

### Post by HomoGleek on 2010-07-05
```


darren@EeePC900:~$ gimp --stack-trace-mode always
gimp: fatal error: Failed to register GObject with DBusConnection
#0  0x003ba422 in __kernel_vsyscall ()
#1  0x0015ede3 in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x00ca2be3 in g_on_error_stack_trace () from /lib/libglib-2.0.so.0
#3  0x080a6213 in ?? ()
#4  0x080a6279 in gimp_fatal_error ()
#5  0x080a6291 in ?? ()
#6  0x00cd1bea in g_logv () from /lib/libglib-2.0.so.0
#7  0x00cd2056 in g_log () from /lib/libglib-2.0.so.0
#8  0x001ca1c2 in dbus_g_connection_register_g_object ()
#9  0x051816bd in ?? () from /usr/lib/libdbusmenu-glib.so.1
#10 0x004bbb06 in ?? () from /usr/lib/libgobject-2.0.so.0
#11 0x004bcc4c in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#12 0x004bd90c in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#13 0x004bda27 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#14 0x05181041 in dbusmenu_server_new () from /usr/lib/libdbusmenu-glib.so.1
#15 0x00fc9e43 in ?? () from /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
#16 0x004c34e8 in g_cclosure_marshal_VOID__PARAM ()
#17 0x004b6252 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#18 0x004ca99d in ?? () from /usr/lib/libgobject-2.0.so.0
#19 0x004cbdb4 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#20 0x004cc256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#21 0x004ba631 in ?? () from /usr/lib/libgobject-2.0.so.0
#22 0x004b6f8f in ?? () from /usr/lib/libgobject-2.0.so.0
#23 0x004bc873 in g_object_notify () from /usr/lib/libgobject-2.0.so.0
#24 0x00b28b1f in gtk_widget_set_parent () from /usr/lib/libgtk-x11-2.0.so.0
#25 0x0092d19a in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#26 0x081e4173 in ?? ()
#27 0x004c32d8 in g_cclosure_marshal_VOID__OBJECT ()
#28 0x004b6252 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#29 0x004ca99d in ?? () from /usr/lib/libgobject-2.0.so.0
#30 0x004cbdb4 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#31 0x004cc256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#32 0x082989c0 in gimp_context_tool_changed ()
#33 0x08298ae9 in ?? ()
#34 0x004c3dcc in g_cclosure_marshal_VOID__VOID ()
#35 0x004b6252 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#36 0x004ca99d in ?? () from /usr/lib/libgobject-2.0.so.0
#37 0x004cbdb4 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#38 0x004cc256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#39 0x00ac45ea in gtk_toggle_button_toggled ()
#40 0x00a319ca in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#41 0x004c3dcc in g_cclosure_marshal_VOID__VOID ()
#42 0x004b48b9 in ?? () from /usr/lib/libgobject-2.0.so.0
#43 0x004b6252 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#44 0x004ca23a in ?? () from /usr/lib/libgobject-2.0.so.0
#45 0x004cbdb4 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#46 0x004cc256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#47 0x00935dca in gtk_button_clicked () from /usr/lib/libgtk-x11-2.0.so.0
#48 0x00ac4338 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#49 0x004c3dcc in g_cclosure_marshal_VOID__VOID ()
#50 0x004b48b9 in ?? () from /usr/lib/libgobject-2.0.so.0
#51 0x004b6252 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#52 0x004ca23a in ?? () from /usr/lib/libgobject-2.0.so.0
#53 0x004cbdb4 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#54 0x004cc256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#55 0x00935e6a in gtk_button_released () from /usr/lib/libgtk-x11-2.0.so.0
#56 0x00935eb3 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#57 0x009f34b4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#58 0x004b48b9 in ?? () from /usr/lib/libgobject-2.0.so.0
#59 0x004b6252 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#60 0x004ca5e6 in ?? () from /usr/lib/libgobject-2.0.so.0
#61 0x004cbc33 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#62 0x004cc256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#63 0x00b210e6 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#64 0x009ebaed in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#65 0x009ece97 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#66 0x007c139a in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#67 0x00cc75e5 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#68 0x00ccb2d8 in ?? () from /lib/libglib-2.0.so.0
#69 0x00ccb817 in g_main_loop_run () from /lib/libglib-2.0.so.0
#70 0x080a5b1a in app_run ()
#71 0x080a6b8a in main ()

(script-fu:10307): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error

```

---

### Post by AlphaLexman on 2010-07-05
WOW!

I would try removing and reinstalling gimp.

---

### Post by HomoGleek on 2010-07-05
Hi,

Thanks, but I've already tried  sudo apt-get remove --purge gimp, shame because I really need to use GIMP just now :/

---

### Post by lukeiamyourfather on 2010-07-05
> **HomoGleek said:**
> Hi,

Thanks, but I've already tried  sudo apt-get remove --purge gimp, shame because I really need to use GIMP just now :/

Not sure if the --purge option does anything, I think it should be "sudo apt-get purge gimp" instead of --purge. Cheers!

---

### Post by HomoGleek on 2010-07-05
> **lukeiamyourfather said:**
> Not sure if the --purge option does anything, I think it should be "sudo apt-get purge gimp" instead of --purge. Cheers!
Hi

Tried that, no luck after reinstall :/

---

### Post by AlphaLexman on 2010-07-05
When exactly does gimp crash, at startup, or when you try to do something?
I found this bug: [https://bugzilla.gnome.org/show_bug.cgi?id=622608](https://bugzilla.gnome.org/show_bug.cgi?id=622608)

---

### Post by Irony on 2010-07-05
Have you tried deleting the config folder;

```
~/.gimp-2.6
```

---

### Post by HomoGleek on 2010-07-05
> **Irony said:**
> Have you tried deleting the config folder;

```
~/.gimp-2.6
```

Ye I tried that... no luck.


> **AlphaLexman said:**
> When exactly does gimp crash, at startup, or when you try to do something?
I found this bug: [https://bugzilla.gnome.org/show_bug.cgi?id=622608](https://bugzilla.gnome.org/show_bug.cgi?id=622608)

Only when I click on the eraser or the add text tool...

---

### Post by AlphaLexman on 2010-07-05
Try rolling back to an older version maybe.

---

### Post by climber117 on 2010-07-05
I had a similar problem. On a tip from here: [http://alexsleat.co.uk/2010/07/04/gimp-2-6-8-crashing-on-some-toolbox-icons-lucid/]("http://alexsleat.co.uk/2010/07/04/gimp-2-6-8-crashing-on-some-toolbox-icons-lucid/"), I removed the appmenu-gtk package:

```
sudo apt-get remove appmenu-gtk
```

It worked for me. Hope that helps.

---

### Post by HomoGleek on 2010-07-05
> **climber117 said:**
> I had a similar problem. On a tip from here: [http://alexsleat.co.uk/2010/07/04/gimp-2-6-8-crashing-on-some-toolbox-icons-lucid/]("http://alexsleat.co.uk/2010/07/04/gimp-2-6-8-crashing-on-some-toolbox-icons-lucid/"), I removed the appmenu-gtk package:

```
sudo apt-get remove appmenu-gtk
```

It worked for me. Hope that helps.

Yes it worked.... thanks!

Any idea what appmenu-gtk does? Will it be missed?

---

### Post by MastroPino on 2010-07-07
> **climber117 said:**
> I had a similar problem. On a tip from here: [http://alexsleat.co.uk/2010/07/04/gimp-2-6-8-crashing-on-some-toolbox-icons-lucid/]("http://alexsleat.co.uk/2010/07/04/gimp-2-6-8-crashing-on-some-toolbox-icons-lucid/"), I removed the appmenu-gtk package:

```
sudo apt-get remove appmenu-gtk
```

It worked for me. Hope that helps.

Thanks mate u save my work today ;)

---

### Post by satismo on 2010-07-08
> **climber117 said:**
> I had a similar problem. On a tip from here: [http://alexsleat.co.uk/2010/07/04/gimp-2-6-8-crashing-on-some-toolbox-icons-lucid/]("http://alexsleat.co.uk/2010/07/04/gimp-2-6-8-crashing-on-some-toolbox-icons-lucid/"), I removed the appmenu-gtk package:

```
sudo apt-get remove appmenu-gtk
```

It worked for me. Hope that helps.

bless you!:KS

---

