---
title: "Frequent segfaults in various programs"
date: 2010-05-31
forum: General Help
---

### Post by Exp HP on 2010-05-31
In LMMS, pretty much any time where pressing a key or button is supposed to  do something, it can crash.  Regardless of what made it crash, it always dies in the exact same way:  The window just disappears, and I get the line "Segmentation fault" in the console.  Usually it crashes within 15 minutes of normal use.
Not even 6 hours after I downloaded the program, I had given up trying to use it.

Over the next week, a couple other programs crashed with segfaults.  Most of them only crashed once (among those was Firefox).  So, of course, I'm now beginning to think that maybe the problem is not with LMMS, but rather with Ubuntu.

I've had very little luck getting most of these programs to crash a second time, but I did find reliable ways to reproduce the crash in LMMS and Golly, so I got debug logs of those (with backtraces and steps I took to reproduce):
```
WHAT I DID TO MAKE LMMS CRASH:
1. After starting LMMS, created an instrument track using the Oh Synth preset (under LB302)
2. Opened the tool window for the track.
3. Dragged my cursor back and forth across the keys on the virtual piano at the bottom of said window to play them.
4. Within 3 seconds, it crashed.

Starting program: /usr/bin/lmms 
[Thread debugging using libthread_db enabled]
[New Thread 0xb7d62b70 (LWP 4674)]
[New Thread 0xb2c18b70 (LWP 4677)]
[New Thread 0xb2417b70 (LWP 4678)]
[New Thread 0xb195ab70 (LWP 4680)]
[New Thread 0xb1159b70 (LWP 4681)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb195ab70 (LWP 4680)]
0x00fe5ae6 in QObjectPrivate::resetCurrentSender(QObject*, QObjectPrivate::Sender*, QObjectPrivate::Sender*) () from /usr/lib/libQtCore.so.4
#0  0x00fe5ae6 in QObjectPrivate::resetCurrentSender(QObject*, QObjectPrivate::Sender*, QObjectPrivate::Sender*) () from /usr/lib/libQtCore.so.4
#1  0x00fea41f in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#2  0x081af7c3 in automatableModel::destroyed(unsigned int) ()
#3  0x081b1949 in automatableModel::~automatableModel() ()
#4  0x081b4d3e in detuningHelper::~detuningHelper() ()
#5  0x081b3df8 in note::~note() ()
#6  0x0817668c in notePlayHandle::~notePlayHandle() ()
#7  0x0818c736 in mixer::renderNextBuffer() ()
#8  0x0818cf81 in mixer::fifoWriter::run() ()
#9  0x00ed432e in ?? () from /usr/lib/libQtCore.so.4
#10 0x00dd596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0x01398a0e in clone () from /lib/tls/i686/cmov/libc.so.6
Kill the program being debugged? (y or n)
``````
WHAT I DID TO MAKE GOLLY CRASH:
1. After starting Golly, loaded the example file "Still-Lifes/eaters.rle".
2. Alternated between Space (Next Generation) and Ctrl+Z (Undo), holding each for about 1 second.
3. Within 15 seconds, it crashed.

Starting program: /usr/games/golly 
[Thread debugging using libthread_db enabled]

Program received signal SIGSEGV, Segmentation fault.
0x080fd47c in UndoRedo::RememberGenFinish() ()
#0  0x080fd47c in UndoRedo::RememberGenFinish() ()
#1  0x080f855c in MainFrame::NextGeneration(bool) ()
#2  0x081124f5 in MainFrame::OnMenu(wxCommandEvent&) ()
#3  0x00621a9f in wxAppConsole::HandleEvent(wxEvtHandler*, void (wxEvtHandler::*)(wxEvent&), wxEvent&) const () from /usr/lib/libwx_baseu-2.8.so.0
#4  0x006c0379 in wxEvtHandler::ProcessEventIfMatches(wxEventTableEntryBase const&, wxEvtHandler*, wxEvent&) () from /usr/lib/libwx_baseu-2.8.so.0
#5  0x006c1424 in wxEventHashTable::HandleEvent(wxEvent&, wxEvtHandler*) ()
   from /usr/lib/libwx_baseu-2.8.so.0
#6  0x006c1523 in wxEvtHandler::ProcessEvent(wxEvent&) ()
   from /usr/lib/libwx_baseu-2.8.so.0
#7  0x009897a9 in ?? () from /usr/lib/libwx_gtk2u_core-2.8.so.0
#8  0x00f67dcc in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#9  0x00f5a252 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#10 0x00f6e99d in ?? () from /usr/lib/libgobject-2.0.so.0
#11 0x00f6fdb4 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#12 0x00f70256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#13 0x03eb8d1f in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#14 0x00f5a252 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#15 0x00f6e99d in ?? () from /usr/lib/libgobject-2.0.so.0
#16 0x00f6fc33 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#17 0x00f70256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#18 0x03caa8d1 in gtk_accel_group_activate () from /usr/lib/libgtk-x11-2.0.so.0
#19 0x03caa9d5 in gtk_accel_groups_activate ()
   from /usr/lib/libgtk-x11-2.0.so.0
#20 0x03ec94f4 in gtk_window_activate_key () from /usr/lib/libgtk-x11-2.0.so.0
#21 0x03ec957c in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#22 0x03d872f4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#23 0x00f588b9 in ?? () from /usr/lib/libgobject-2.0.so.0
#24 0x00f5a252 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#25 0x00f6e5e6 in ?? () from /usr/lib/libgobject-2.0.so.0
#26 0x00f6fc33 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#27 0x00f70256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#28 0x03eb4306 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#29 0x03d7fa03 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#30 0x03d80cd7 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#31 0x00b9435a in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#32 0x01a9c5e5 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#33 0x01aa02d8 in ?? () from /lib/libglib-2.0.so.0
#34 0x01aa0817 in g_main_loop_run () from /lib/libglib-2.0.so.0
#35 0x03d81299 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#36 0x00912c78 in wxEventLoop::Run() () from /usr/lib/libwx_gtk2u_core-2.8.so.0
#37 0x009a5e3e in wxAppBase::MainLoop() ()
   from /usr/lib/libwx_gtk2u_core-2.8.so.0
#38 0x009a5a31 in wxAppBase::OnRun() () from /usr/lib/libwx_gtk2u_core-2.8.so.0
#39 0x0065b7aa in wxEntry(int&, wchar_t**) ()
   from /usr/lib/libwx_baseu-2.8.so.0
#40 0x0065b987 in wxEntry(int&, char**) () from /usr/lib/libwx_baseu-2.8.so.0
#41 0x08125910 in main ()
Kill the program being debugged? (y or n) 
```I've tried using different governors for CPU (Conservative, Ondemand, etc.), and these crashes continued to occur.
I also tried using a different kernel to no avail; the crashes occur both on **2.6.32-21-generic** and **2.6.31-17-generic**.

Please help me fix whatever's causing these segfaults.

---

### Post by sdennie on 2010-05-31
It's possible that you've just stumbled upon bugs in various applications.  The stack traces don't indicate any shared point of failure like libc, libQT or libgtk and, if one of those were corrupt/invalid, you'd see catastrophic failures instead of reproducible failures.

---

### Post by Exp HP on 2010-05-31
I really wouldn't be surprised if that were the case.

I'm still tempted to believe that there is something wrong with my computer, and that simply one or both of the logs I provided is of a bug in the program.  Both of those logs were procured by doing something that I knew put a good deal of stress on the program, because knew it made it crash before, and I needed quick results.  Many of the crashes I have been experiencing were of a different nature: They occurred during periods of normal or even infrequent use, and could result from just about anything (even just bringing up the File menu).
Furthermore, I could not find others experiencing similar issues to mine for any of the programs.

I'm going to start running everything from within gdb so I can catch the call stack if and when a program implodes.  I'll post back when I get a few.  If there is a pattern to be seen, hopefully it will show up then.

---

### Post by sdennie on 2010-05-31
Another thing to test would be your hardware.  Failing RAM or disks could also account for what you are seeing.  You could try running the memtest from the grub menu overnight for the RAM and maybe see if smartctl can tell you anything interesting about your disk.

---

### Post by cha0s on 2010-06-01
This isn't a Ubuntu bug. LMMS definitly has a crash issue, that somehow has to do with using the virtual keyboard. It's easily reproducible if you click and hold, and move around on the keyboard quickly. It crashes within 5 seconds consistently here, on my 64-bit Xubuntu and my mom's 32-bit Ubuntu. Also, this bug is reported on the LMMS site as well as Red Hat bug lists... etc.

I am currently doing my best to track down any information, and I'm going to take a look at the code later to see if I can figure it out. My first glance guess is that somewhere LMMS is using stack-allocated child objects and then when the parent gets free'd, there are bad things happening.

I don't know about GOLLY, because I haven't tried that app at this point. *buntu is quite stable though, you're just running into apps with some problems... which is a shame because LMMS is really frickin cool from what I can see. I'm hoping to patch that issue... I've already patched the 'tooltips are impossible to see because it's white on yellow' issue locally. I'm still learning where to go to report this stuff. :)

---

