---
title: "java error"
date: 2011-08-23
forum: General Help
---

### Post by gringo8217 on 2011-08-23
java error message can anybody advise plz.....


#
#  SIGSEGV (0xb) at pc=0xb59bc913, pid=4566, tid=3033164656
#
# JRE version: 6.0_22-b22
# Java VM: OpenJDK Client VM (20.0-b11 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.10.2
# Distribution: Ubuntu 11.04, package 6b22-1.10.2-0ubuntu1~11.04.1
# Problematic frame:
# J  org.eclipse.swt.graphics.GC.textExtent(Ljava/lang/String;I)Lorg/eclipse/swt/graphics/Point;
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#

---------------  T H R E A D  ---------------

Current thread (0xb4e5a000):  JavaThread "MainRunner" [_thread_in_Java, id=4578, stack(0xb4c56000,0xb4ca7000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=128 (), si_addr=0x00000000

Registers:
EAX=0x00000006, EBX=0x00000004, ECX=0x6fc63048, EDX=0x00000004
ESP=0xb4ca3ed0, EBP=0xb4ca3f48, ESI=0x6fc63048, EDI=0xfffffffd
EIP=0xb59bc913, EFLAGS=0x00010246, CR2=0xb782d100

Top of Stack: (sp=0xb4ca3ed0)
0xb4ca3ed0:   00000006 00000000 8feb7330 00000000
0xb4ca3ee0:   b4ca3f04 b4ca3f38 b57c7e21 00000000
0xb4ca3ef0:   00000000 00000000 6fceec08 6fc63048
0xb4ca3f00:   00000000 00000007 b4ca3f48 b57c7f87
0xb4ca3f10:   00000006 6fc63048 b57c7f87 00000006
0xb4ca3f20:   6fceec08 6fc63048 b4ca3f28 8febc5e4
0xb4ca3f30:   b4ca3f54 8febcc28 00000000 8febc5f0
0xb4ca3f40:   b4ca3f1c b4ca3f50 b4ca3f78 b57c7f87 

Instructions: (pc=0xb59bc913)
0xb59bc8f3:   ff 8b 4c 24 2c 8b 71 14 8b 76 58 83 fe ff 0f 84
0xb59bc903:   07 00 00 00 8b d9 e9 0e 00 00 00 8b f1 8b ce 90
0xb59bc913:   e8 48 07 00 00 8b 5c 24 2c ba 80 a6 dc 8f 8b cc
0xb59bc923:   c1 e9 0c 8b 0c 8d c0 4d 0c 01 8b 41 34 8d 78 10 

Register to memory mapping:

EAX=0x00000006 is an unknown value
EBX=0x00000004 is an unknown value
ECX=0x6fc63048 is an oop

[error occurred during error reporting (printing register info), id 0xb]

Stack: [0xb4c56000,0xb4ca7000],  sp=0xb4ca3ed0,  free space=311k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
J  org.eclipse.swt.graphics.GC.textExtent(Ljava/lang/String;I)Lorg/eclipse/swt/graphics/Point;
j  org.gudy.azureus2.ui.swt.shells.GCStringPrinter.drawText(Lorg/eclipse/swt/graphics/GC;Ljava/lang/String;IIILjava/util/List;Z)Lorg/eclipse/swt/graphics/Point;+661
j  org.gudy.azureus2.ui.swt.shells.GCStringPrinter.drawLine(Lorg/eclipse/swt/graphics/GC;Lorg/gudy/azureus2/ui/swt/shells/GCStringPrinter$LineInfo;ILorg/eclipse/swt/graphics/Rectangle;Z)V+724
J  org.gudy.azureus2.ui.swt.shells.GCStringPrinter.__printString()Z
j  org.gudy.azureus2.ui.swt.shells.GCStringPrinter.printString()Z+1
j  org.gudy.azureus2.ui.swt.shells.MessageSlideShell$13.handleEvent(Lorg/eclipse/swt/widgets/EventV+116
J  org.eclipse.swt.widgets.EventTable.sendEvent(Lorg/eclipse/swt/widgets/EventV
j  org.eclipse.swt.widgets.Widget.sendEvent(ILorg/eclipse/swt/widgets/Event;Z)V+73
j  org.eclipse.swt.widgets.Widget.sendEvent(ILorg/eclipse/swt/widgets/EvenV+4
j  org.eclipse.swt.widgets.Control.gtk_expose_event(II)I+182
j  org.eclipse.swt.widgets.Composite.gtk_expose_event(II)I+41
j  org.eclipse.swt.widgets.Canvas.gtk_expose_event(II)I+49
J  org.eclipse.swt.widgets.Widget.windowProc(III)I
v  ~StubRoutines::call_stub
V  [libjvm.so+0x20a6d2]  JavaCalls::call_helper(JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x262
V  [libjvm.so+0x3044e9]  os:s_exception_wrapper(void (*)(JavaValue*, methodHandle*, JavaCallArguments*, Thread*), JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x19
V  [libjvm.so+0x209bcf]  JavaCalls::call(JavaValue*, methodHandle, JavaCallArguments*, Thread*)+0x2f
V  [libjvm.so+0x214995]  jni_invoke_nonstatic(JNIEnv_*, JavaValue*, _jobject*, JNICallType, _jmethodID*, JNI_ArgumentPusher*, Thread*)+0x235
V  [libjvm.so+0x220768]  jni_CallIntMethodV+0xb8
C  [libswt-gtk-3659.so+0x27bb]  callback+0x2eb
C  0x007332d5
C  [libgtk-x11-2.0.so.0+0x135a04]  gtk_marshal_VOID__UINT_STRING+0x154
C  [libgobject-2.0.so.0+0xc372]  g_closure_invoke+0x192
C  [libgobject-2.0.so.0+0x1f273]  g_signal_handler_disconnect+0x1a73
C  [libgobject-2.0.so.0+0x278d7]  g_signal_emit_valist+0x557
C  [libgobject-2.0.so.0+0x27cc2]  g_signal_emit+0x32
C  [libgtk-x11-2.0.so.0+0x26a836]  gtk_widget_get_realized+0x276
C  [libgtk-x11-2.0.so.0+0x134259]  gtk_main_do_event+0x5e9
C  [libswt-pi-gtk-3659.so+0x44b1d]  Java_org_eclipse_swt_internal_gtk_OS__1gtk_1main_1do_1event+0x1d
J  org.eclipse.swt.internal.gtk.OS._gtk_main_do_event(I)V
J  org.eclipse.swt.widgets.Display.eventProc(II)I
V  [libjvm.so+0x20a6d2]  JavaCalls::call_helper(JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x262
V  [libjvm.so+0x3044e9]  os:s_exception_wrapper(void (*)(JavaValue*, methodHandle*, JavaCallArguments*, Thread*), JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x19
V  [libjvm.so+0x209bcf]  JavaCalls::call(JavaValue*, methodHandle, JavaCallArguments*, Thread*)+0x2f
V  [libjvm.so+0x214995]  jni_invoke_nonstatic(JNIEnv_*, JavaValue*, _jobject*, JNICallType, _jmethodID*, JNI_ArgumentPusher*, Thread*)+0x235
V  [libjvm.so+0x220768]  jni_CallIntMethodV+0xb8
C  [libswt-gtk-3659.so+0x27bb]  callback+0x2eb
C  0x00733192
C  [libgdk-x11-2.0.so.0+0x3ba78]  gdk_window_end_paint+0x6e8
C  [libgdk-x11-2.0.so.0+0x3ba27]  gdk_window_end_paint+0x697
C  [libgdk-x11-2.0.so.0+0x3ba27]  gdk_window_end_paint+0x697
C  [libgdk-x11-2.0.so.0+0x3ba27]  gdk_window_end_paint+0x697
C  [libgdk-x11-2.0.so.0+0x6e184]  gdk_window_set_opacity+0x274
C  [libgdk-x11-2.0.so.0+0x3698c]  gdk_window_is_viewable+0x3cc
C  [libgdk-x11-2.0.so.0+0x38b1c]  gdk_window_process_updates+0x15c
C  [libswt-pi-gtk-3659.so+0x3ec95]  Java_org_eclipse_swt_internal_gtk_OS__1gdk_1window_1process_1updates+0x25
j  org.eclipse.swt.internal.gtk.OS._gdk_window_process_updates(IZ)V+0
j  org.eclipse.swt.internal.gtk.OS.gdk_window_process_updates(IZ)V+9
j  org.eclipse.swt.widgets.Control.update(ZZ)V+45
j  org.eclipse.swt.widgets.Control.update()V+7
j  org.gudy.azureus2.ui.swt.shells.ShellSlider$3.runSupport()V+317
j  org.gudy.azureus2.core3.util.AERunnable.run()V+1
j  org.eclipse.swt.widgets.RunnableLock.run()V+11
j  org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Z)Z+29
j  org.eclipse.swt.widgets.Display.runAsyncMessages(Z)Z+5
j  org.eclipse.swt.widgets.Display.readAndDispatch()Z+58
j  org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(Lcom/aelitis/azureus/ui/IUIIntializerV+546
j  org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(Lcom/aelitis/azureus/ui/IUIIntializerV+19
j  org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Lcom/aelitis/azureus/core/AzureusCore;Lorg/gudy/azureus2/ui/swt/StartServer;[Ljava/lang/StringV+114
j  org.gudy.azureus2.ui.swt.Main.<init>([Ljava/lang/StringV+127
j  org.gudy.azureus2.ui.swt.Main.main([Ljava/lang/StringV+32
v  ~StubRoutines::call_stub
V  [libjvm.so+0x20a6d2]  JavaCalls::call_helper(JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x262
V  [libjvm.so+0x3044e9]  os:s_exception_wrapper(void (*)(JavaValue*, methodHandle*, JavaCallArguments*, Thread*), JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x19
V  [libjvm.so+0x209bcf]  JavaCalls::call(JavaValue*, methodHandle, JavaCallArguments*, Thread*)+0x2f
V  [libjvm.so+0x33761c]  Reflection::invoke(instanceKlassHandle, methodHandle, Handle, bool, objArrayHandle, BasicType, objArrayHandle, bool, Thread*)+0x40c
V  [libjvm.so+0x33a641]  Reflection::invoke_method(oopDesc*, Handle, objArrayHandle, Thread*)+0x161
V  [libjvm.so+0x24b66d]  JVM_InvokeMethod+0x10d
C  [libjava.so+0x149a2]  Java_sun_reflect_NativeMethodAccessorImpl_invoke0+0x32
j  sun.reflect.NativeMethodAccessorImpl.invoke0(Ljava/lang/reflect/Method;Ljava/lang/Object;[Ljava/lang/ObjectLjava/lang/Object;+0
j  sun.reflect.NativeMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/ObjectLjava/lang/Object;+87
j  sun.reflect.DelegatingMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/ObjectLjava/lang/Object;+6
j  java.lang.reflect.Method.invoke(Ljava/lang/Object;[Ljava/lang/ObjectLjava/lang/Object;+161
j  org.gudy.azureus2.ui.common.Main.directLaunch([Ljava/lang/String;Lorg/apache/commons/cli/CommandLineZ+104
j  org.gudy.azureus2.ui.common.Main.main([Ljava/lang/StringV+54
v  ~StubRoutines::call_stub
V  [libjvm.so+0x20a6d2]  JavaCalls::call_helper(JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x262
V  [libjvm.so+0x3044e9]  os:s_exception_wrapper(void (*)(JavaValue*, methodHandle*, JavaCallArguments*, Thread*), JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x19
V  [libjvm.so+0x209bcf]  JavaCalls::call(JavaValue*, methodHandle, JavaCallArguments*, Thread*)+0x2f
V  [libjvm.so+0x33761c]  Reflection::invoke(instanceKlassHandle, methodHandle, Handle, bool, objArrayHandle, BasicType, objArrayHandle, bool, Thread*)+0x40c
V  [libjvm.so+0x33a641]  Reflection::invoke_method(oopDesc*, Handle, objArrayHandle, Thread*)+0x161
V  [libjvm.so+0x24b66d]  JVM_InvokeMethod+0x10d
C  [libjava.so+0x149a2]  Java_sun_reflect_NativeMethodAccessorImpl_invoke0+0x32
j  sun.reflect.NativeMethodAccessorImpl.invoke0(Ljava/lang/reflect/Method;Ljava/lang/Object;[Ljava/lang/ObjectLjava/lang/Object;+0
j  sun.reflect.NativeMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/ObjectLjava/lang/Object;+87
j  sun.reflect.DelegatingMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/ObjectLjava/lang/Object;+6
j  java.lang.reflect.Method.invoke(Ljava/lang/Object;[Ljava/lang/ObjectLjava/lang/Object;+161
j  com.aelitis.azureus.launcher.MainExecutor$1.run()V+40
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub
V  [libjvm.so+0x20a6d2]  JavaCalls::call_helper(JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x262
V  [libjvm.so+0x3044e9]  os:s_exception_wrapper(void (*)(JavaValue*, methodHandle*, JavaCallArguments*, Thread*), JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x19
V  [libjvm.so+0x209bcf]  JavaCalls::call(JavaValue*, methodHandle, JavaCallArguments*, Thread*)+0x2f
V  [libjvm.so+0x20a04a]  JavaCalls::call_virtual(JavaValue*, KlassHandle, symbolHandle, symbolHandle, JavaCallArguments*, Thread*)+0xea
V  [libjvm.so+0x20a1a8]  JavaCalls::call_virtual(JavaValue*, Handle, KlassHandle, symbolHandle, symbolHandle, Thread*)+0x58
V  [libjvm.so+0x23b60f]  thread_entry(JavaThread*, Thread*)+0x7f
V  [libjvm.so+0x3af19c]  JavaThread::thread_main_inner()+0x6c
V  [libjvm.so+0x3af279]  JavaThread::run()+0xc9
V  [libjvm.so+0x3025d1]  java_start(Thread*)+0x121
C  [libpthread.so.0+0x5e99]  start_thread+0xd9


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x09155800 JavaThread "Cell Refresher" daemon [_thread_blocked, id=4643, stack(0xacce9000,0xacd3a000)]
  0x09154000 JavaThread "PeerControlScheduler" daemon [_thread_blocked, id=4642, stack(0xacd3a000,0xacd8b000)]
  0x08edf800 JavaThread "ConcurrentHasher:scheduler" daemon [_thread_blocked, id=4641, stack(0xacd8b000,0xacddc000)]
  0x08ede400 JavaThread "DiskAccessController:dispatch(core/read)[0/0]" daemon [_thread_blocked, id=4640, stack(0xace5e000,0xaceaf000)]
  0x08edcc00 JavaThread "DM:ListenAggregatorDispatcher" daemon [_thread_blocked, id=4639, stack(0xaceaf000,0xacf00000)]
  0x08edc400 JavaThread "DMCiskListenAgregatorDispatcher" daemon [_thread_blocked, id=4638, stack(0xad02f000,0xad080000)]
  0x08ec0400 JavaThread "AWT-XAWT" daemon [_thread_blocked, id=4632, stack(0xad080000,0xad0d1000)]
  0xb2f5f000 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=4631, stack(0xad0d1000,0xad122000)]
  0x0903dc00 JavaThread "Slidey" daemon [_thread_blocked, id=4630, stack(0xad122000,0xad173000)]
  0xb2f62c00 JavaThread "Keep-Alive-Timer" daemon [_thread_blocked, id=4629, stack(0xad173000,0xad1c4000)]
  0x0924d000 JavaThread "TRTrackerServer:accept.loop" daemon [_thread_in_native, id=4628, stack(0xaddf2000,0xade43000)]
  0x0922fc00 JavaThread "TrackerServer:timer.loop" daemon [_thread_blocked, id=4627, stack(0xade43000,0xade94000)]
  0xb2f45400 JavaThread "TiVo:CtrlListener" daemon [_thread_in_native, id=4626, stack(0xae58a000,0xae5db000)]
  0x0924cc00 JavaThread "VCC:init" daemon [_thread_blocked, id=4625, stack(0xade94000,0xadee5000)]
  0x09250400 JavaThread "Local RSS etc.::SSDP:queryLoop" daemon [_thread_blocked, id=4623, stack(0xadee5000,0xadf36000)]
  0x0924e800 JavaThread "MCGroup:CtrlListener" daemon [_thread_in_native, id=4622, stack(0xadf36000,0xadf87000)]
  0x09245000 JavaThread "MCGroup:MCListener" daemon [_thread_in_native, id=4621, stack(0xadf87000,0xadfd8000)]
  0x09242800 JavaThread "processReady" daemon [_thread_in_vm, id=4620, stack(0xadfd8000,0xae029000)]
  0xb3089800 JavaThread "DiskM:ListenAggregatorDispatcher" daemon [_thread_blocked, id=4619, stack(0xae11c000,0xae16d000)]
  0x09240400 JavaThread "NetstatusPlugin:init" daemon [_thread_blocked, id=4618, stack(0xae029000,0xae07a000)]
  0x0923ec00 JavaThread "MagnetPlugin:init" daemon [_thread_blocked, id=4617, stack(0xae07a000,0xae0cb000)]
  0xb2f6d400 JavaThread "DHTPlugin.init" daemon [_thread_blocked, id=4616, stack(0xae0cb000,0xae11c000)]
  0xb2e8e800 JavaThread "AZInstanceManager:initialSearch" daemon [_thread_in_native, id=4614, stack(0xae16d000,0xae1be000)]
  0xb2e7cc00 JavaThread "MCGroup:CtrlListener" daemon [_thread_in_native, id=4613, stack(0xae1be000,0xae20f000)]
  0xb2f43800 JavaThread "UPnPMediaServer:closer" daemon [_thread_blocked, id=4612, stack(0xae20f000,0xae260000)]
  0xb2f48c00 JavaThread "UPnPMediaServer:accepter" daemon [_thread_in_native, id=4611, stack(0xae260000,0xae2b1000)]
  0x0920a800 JavaThread "Timerlugin azupnpav:eventDispatch" daemon [_thread_blocked, id=4610, stack(0xae2b1000,0xae302000)]
  0x0920f800 JavaThread "IPToHostNameResolver" daemon [_thread_in_native, id=4609, stack(0xae302000,0xae353000)]
  0x09215000 JavaThread "Global Status Checker" [_thread_blocked, id=4608, stack(0xae353000,0xae3a4000)]
  0x09211800 JavaThread "TRHost::stats.loop" daemon [_thread_blocked, id=4607, stack(0xae3a4000,0xae3f5000)]
  0x091fe800 JavaThread "Timer:Tracker Timer" daemon [_thread_blocked, id=4606, stack(0xae3f5000,0xae446000)]
  0x091f3000 JavaThread "FMFileManager::closeQueueDispatcher" daemon [_thread_blocked, id=4605, stack(0xae446000,0xae497000)]
  0x09215c00 JavaThread "MCGroup:MCListener" daemon [_thread_in_native, id=4604, stack(0xae497000,0xae4e8000)]
  0x091e9c00 JavaThread "GM:ListenDispatcher" daemon [_thread_blocked, id=4603, stack(0xae4e8000,0xae539000)]
  0x091dc400 JavaThread "MagnetURIHandler" daemon [_thread_in_native, id=4602, stack(0xae539000,0xae58a000)]
  0xb2f49800 JavaThread "Utilities:delayedTask" daemon [_thread_blocked, id=4600, stack(0xb314e000,0xb319f000)]
  0xb44bd400 JavaThread "UI Updater" daemon [_thread_blocked, id=4598, stack(0xb32ab000,0xb32fc000)]
  0xb4417800 JavaThread "TRHost:ListenDispatcher" daemon [_thread_blocked, id=4595, stack(0xb42fe000,0xb434f000)]
  0xb47e8800 JavaThread "Timerrocess Data Sources" daemon [_thread_blocked, id=4594, stack(0xb43af000,0xb4400000)]
  0xb47e7000 JavaThread "AsyncDispatcher" daemon [_thread_blocked, id=4593, stack(0xb4543000,0xb4594000)]
  0xb47e2800 JavaThread "ResourceDownloader:asyncDownload - http://vrpc.vuze.com/vzrpc/rpc.php" daemon [_thread_in_native, id=4592, stack(0xb4594000,0xb45e5000)]
  0xb47e9800 JavaThread "Timer:v3.PlatformMessenger.queue" daemon [_thread_blocked, id=4591, stack(0xb4876000,0xb48c7000)]
  0xb4eea400 JavaThread "Start Server" daemon [_thread_in_native, id=4589, stack(0xb48c7000,0xb4918000)]
  0x09010800 JavaThread "AsyncDispatcher" daemon [_thread_blocked, id=4588, stack(0xb4918000,0xb4969000)]
  0x09000c00 JavaThread "WriteController:WriteSelector" daemon [_thread_blocked, id=4587, stack(0xb4969000,0xb49ba000)]
  0x09004000 JavaThread "ReadController:ReadSelector" daemon [_thread_blocked, id=4586, stack(0xb49ba000,0xb4a0b000)]
  0x09003800 JavaThread "VServerSelectorort47498" daemon [_thread_in_native, id=4585, stack(0xb4a0b000,0xb4a5c000)]
  0x08fcf800 JavaThread "WriteController:WriteProcessor" daemon [_thread_blocked, id=4584, stack(0xb4a5c000,0xb4aad000)]
  0x08fcac00 JavaThread "ReadController:ReadProcessor" daemon [_thread_blocked, id=4583, stack(0xb4aad000,0xb4afe000)]
  0x08fb5000 JavaThread "AEThreadMonitor" daemon [_thread_blocked, id=4582, stack(0xb4afe000,0xb4b4f000)]
  0xb4e6c000 JavaThread "Timer:Simple Timer" daemon [_thread_blocked, id=4581, stack(0xb4b4f000,0xb4ba0000)]
  0x08f88c00 JavaThread "ConnectDisconnectManager" daemon [_thread_in_native, id=4580, stack(0xb4ba0000,0xb4bf1000)]
  0x08f4ec00 JavaThread "SystemTime" daemon [_thread_blocked, id=4579, stack(0xb4bf1000,0xb4c42000)]
  0xb4e41000 JavaThread "DestroyJavaVM" [_thread_blocked, id=4570, stack(0xb77c5000,0xb7816000)]
=>0xb4e5a000 JavaThread "MainRunner" [_thread_in_Java, id=4578, stack(0xb4c56000,0xb4ca7000)]
  0xb4e00800 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=4576, stack(0xb4f3d000,0xb4f8e000)]
  0x08ea0c00 JavaThread "C1 CompilerThread0" daemon [_thread_blocked, id=4575, stack(0xb4f8e000,0xb500f000)]
  0x08e9f000 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=4574, stack(0xb500f000,0xb5060000)]
  0x08e9ac00 JavaThread "Finalizer" daemon [_thread_blocked, id=4573, stack(0xb5260000,0xb52b1000)]
  0x08e96000 JavaThread "Reference Handler" daemon [_thread_blocked, id=4572, stack(0xb52b1000,0xb5302000)]

Other Threads:
  0x08e94400 VMThread [stack: 0xb5302000,0xb5383000] [id=4571]
  0xb4e03000 WatcherThread [stack: 0xb4d7f000,0xb4e00000] [id=4577]

VM state:synchronizing (normal execution)

VM Mutex/Monitor currently owned by a thread:  ([mutex/lock_event])
[0x08e65ff8] Safepoint_lock - owner thread: 0x08e94400
[0x08e66060] Threads_lock - owner thread: 0x08e94400
[0x08e66470] Heap_lock - owner thread: 0x09154000

Heap
 def new generation   total 4992K, used 4991K [0x6f8b0000, 0x6fe10000, 0x7a350000)
  eden space 4480K,  99% used [0x6f8b0000, 0x6fd0fe08, 0x6fd10000)
  from space 512K, 100% used [0x6fd10000, 0x6fd90000, 0x6fd90000)
  to   space 512K,   0% used [0x6fd90000, 0x6fd90000, 0x6fe10000)
 tenured generation   total 10944K, used 4055K [0x7a350000, 0x7ae00000, 0x8f8b0000)
   the space 10944K,  37% used [0x7a350000, 0x7a745e78, 0x7a746000, 0x7ae00000)
 compacting perm gen  total 17920K, used 17903K [0x8f8b0000, 0x90a30000, 0x938b0000)
   the space 17920K,  99% used [0x8f8b0000, 0x90a2bf70, 0x90a2c000, 0x90a30000)
    ro space 10240K,  73% used [0x938b0000, 0x9400fa00, 0x9400fa00, 0x942b0000)
    rw space 12288K,  60% used [0x942b0000, 0x949f9700, 0x949f9800, 0x94eb0000)

Code Cache  [0xb57c5000, 0xb59c5000, 0xb77c5000)
 total_blobs=931 nmethods=661 adapters=205 free_code_cache=31488832 largest_free_block=192

Dynamic libraries:
00110000-0026a000 r-xp 00000000 08:05 34079553   /lib/i386-linux-gnu/libc-2.13.so
0026a000-0026b000 ---p 0015a000 08:05 34079553   /lib/i386-linux-gnu/libc-2.13.so
0026b000-0026d000 r--p 0015a000 08:05 34079553   /lib/i386-linux-gnu/libc-2.13.so
0026d000-0026e000 rw-p 0015c000 08:05 34079553   /lib/i386-linux-gnu/libc-2.13.so
0026e000-00271000 rw-p 00000000 00:00 0 
00271000-00278000 r-xp 00000000 08:05 34079622   /lib/i386-linux-gnu/librt-2.13.so
00278000-00279000 r--p 00006000 08:05 34079622   /lib/i386-linux-gnu/librt-2.13.so
00279000-0027a000 rw-p 00007000 08:05 34079622   /lib/i386-linux-gnu/librt-2.13.so
0027a000-00280000 r-xp 00000000 08:05 34079595   /lib/i386-linux-gnu/libnss_compat-2.13.so
00280000-00281000 r--p 00005000 08:05 34079595   /lib/i386-linux-gnu/libnss_compat-2.13.so
00281000-00282000 rw-p 00006000 08:05 34079595   /lib/i386-linux-gnu/libnss_compat-2.13.so
00282000-00284000 r-xp 00000000 08:05 13373628   /usr/lib/libplds4.so
00284000-00285000 r--p 00001000 08:05 13373628   /usr/lib/libplds4.so
00285000-00286000 rw-p 00002000 08:05 13373628   /usr/lib/libplds4.so
00286000-00289000 r-xp 00000000 08:05 14421332   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00289000-0028a000 r--p 00002000 08:05 14421332   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
0028a000-0028b000 rw-p 00003000 08:05 14421332   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
0028b000-002af000 r-xp 00000000 08:05 34079590   /lib/i386-linux-gnu/libm-2.13.so
002af000-002b0000 r--p 00023000 08:05 34079590   /lib/i386-linux-gnu/libm-2.13.so
002b0000-002b1000 rw-p 00024000 08:05 34079590   /lib/i386-linux-gnu/libm-2.13.so
002b1000-002bc000 r-xp 00000000 08:05 14423843   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
002bc000-002bd000 ---p 0000b000 08:05 14423843   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
002bd000-002be000 r--p 0000b000 08:05 14423843   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
002be000-002bf000 rw-p 0000c000 08:05 14423843   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
002bf000-002d2000 r-xp 00000000 08:05 34079593   /lib/i386-linux-gnu/libnsl-2.13.so
002d2000-002d3000 r--p 00012000 08:05 34079593   /lib/i386-linux-gnu/libnsl-2.13.so
002d3000-002d4000 rw-p 00013000 08:05 34079593   /lib/i386-linux-gnu/libnsl-2.13.so
002d4000-002d6000 rw-p 00000000 00:00 0 
002d6000-002df000 r-xp 00000000 08:05 34079603   /lib/i386-linux-gnu/libnss_nis-2.13.so
002df000-002e0000 r--p 00008000 08:05 34079603   /lib/i386-linux-gnu/libnss_nis-2.13.so
002e0000-002e1000 rw-p 00009000 08:05 34079603   /lib/i386-linux-gnu/libnss_nis-2.13.so
002e1000-002eb000 r-xp 00000000 08:05 34079599   /lib/i386-linux-gnu/libnss_files-2.13.so
002eb000-002ec000 r--p 00009000 08:05 34079599   /lib/i386-linux-gnu/libnss_files-2.13.so
002ec000-002ed000 rw-p 0000a000 08:05 34079599   /lib/i386-linux-gnu/libnss_files-2.13.so
002ed000-003f8000 r-xp 00000000 08:05 13373574   /usr/lib/libnss3.so
003f8000-003fb000 r--p 0010a000 08:05 13373574   /usr/lib/libnss3.so
003fb000-003fd000 rw-p 0010d000 08:05 13373574   /usr/lib/libnss3.so
003fd000-00434000 r-xp 00000000 08:05 13376959   /usr/lib/nss/libsoftokn3.so
00434000-00435000 r--p 00036000 08:05 13376959   /usr/lib/nss/libsoftokn3.so
00435000-00436000 rw-p 00037000 08:05 13376959   /usr/lib/nss/libsoftokn3.so
00436000-004bd000 r-xp 00000000 08:05 13375846   /usr/lib/i386-linux-gnu/libsqlite3.so.0.8.6
004bd000-004be000 ---p 00087000 08:05 13375846   /usr/lib/i386-linux-gnu/libsqlite3.so.0.8.6
004be000-004bf000 r--p 00087000 08:05 13375846   /usr/lib/i386-linux-gnu/libsqlite3.so.0.8.6
004bf000-004c0000 rw-p 00088000 08:05 13375846   /usr/lib/i386-linux-gnu/libsqlite3.so.0.8.6
004c0000-004c1000 rw-p 00000000 00:00 0 
004c1000-004c7000 r-xp 00000000 08:05 14423846   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libmanagement.so
004c7000-004c8000 r--p 00005000 08:05 14423846   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libmanagement.so
004c8000-004c9000 rw-p 00006000 08:05 14423846   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libmanagement.so
004ca000-004d0000 r-xp 00000000 08:05 14421328   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
004d0000-004d1000 r--p 00005000 08:05 14421328   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
004d1000-004d2000 rw-p 00006000 08:05 14421328   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
004d2000-004e5000 r-xp 00000000 08:05 14423851   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
004e5000-004e6000 r--p 00013000 08:05 14423851   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
004e6000-004e7000 rw-p 00014000 08:05 14423851   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
004e7000-004ea000 r-xp 00000000 08:05 17439212   /usr/lib/jni/libswt-gtk-3659.so
004ea000-004eb000 r--p 00002000 08:05 17439212   /usr/lib/jni/libswt-gtk-3659.so
004eb000-004ec000 rw-p 00003000 08:05 17439212   /usr/lib/jni/libswt-gtk-3659.so
004ec000-004ed000 rw-p 00000000 00:00 0 
004ed000-004f0000 r-xp 00000000 08:05 13375798   /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.2800.6
004f0000-004f1000 r--p 00003000 08:05 13375798   /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.2800.6
004f1000-004f2000 rw-p 00004000 08:05 13375798   /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.2800.6
004f2000-004f4000 r-xp 00000000 08:05 13375719   /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
004f4000-004f5000 r--p 00001000 08:05 13375719   /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
004f5000-004f6000 rw-p 00002000 08:05 13375719   /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
004f6000-004f8000 r-xp 00000000 08:05 13375723   /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
004f8000-004f9000 r--p 00001000 08:05 13375723   /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
004f9000-004fa000 rw-p 00002000 08:05 13375723   /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
004fa000-00504000 r-xp 00000000 08:05 13375828   /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2800.4
00504000-00505000 r--p 00009000 08:05 13375828   /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2800.4
00505000-00506000 rw-p 0000a000 08:05 13375828   /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2800.4
00506000-0050a000 r-xp 00000000 08:05 13375729   /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
0050a000-0050b000 r--p 00003000 08:05 13375729   /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
0050b000-0050c000 rw-p 00004000 08:05 13375729   /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
0050c000-00525000 r-xp 00000000 08:05 13375747   /usr/lib/i386-linux-gnu/libatk-1.0.so.0.9.1
00525000-00526000 ---p 00019000 08:05 13375747   /usr/lib/i386-linux-gnu/libatk-1.0.so.0.9.1
00526000-00527000 r--p 00019000 08:05 13375747   /usr/lib/i386-linux-gnu/libatk-1.0.so.0.9.1
00527000-00528000 rw-p 0001a000 08:05 13375747   /usr/lib/i386-linux-gnu/libatk-1.0.so.0.9.1
00528000-00543000 r-xp 00000000 08:05 13373239   /usr/lib/libgdk_pixbuf-2.0.so.0.2300.3
00543000-00544000 r--p 0001a000 08:05 13373239   /usr/lib/libgdk_pixbuf-2.0.so.0.2300.3
00544000-00545000 rw-p 0001b000 08:05 13373239   /usr/lib/libgdk_pixbuf-2.0.so.0.2300.3
00545000-00547000 r-xp 00000000 08:05 13375784   /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.2800.6
00547000-00548000 r--p 00002000 08:05 13375784   /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.2800.6
00548000-00549000 rw-p 00003000 08:05 13375784   /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.2800.6
00549000-0054b000 r-xp 00000000 08:05 13375735   /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
0054b000-0054c000 r--p 00001000 08:05 13375735   /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
0054c000-0054d000 rw-p 00002000 08:05 13375735   /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
0054f000-0056b000 r-xp 00000000 08:05 34079540   /lib/i386-linux-gnu/ld-2.13.so
0056b000-0056c000 r--p 0001b000 08:05 34079540   /lib/i386-linux-gnu/ld-2.13.so
0056c000-0056d000 rw-p 0001c000 08:05 34079540   /lib/i386-linux-gnu/ld-2.13.so
0056d000-00592000 r-xp 00000000 08:05 13375830   /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2800.4
00592000-00593000 ---p 00025000 08:05 13375830   /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2800.4
00593000-00594000 r--p 00025000 08:05 13375830   /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2800.4
00594000-00595000 rw-p 00026000 08:05 13375830   /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2800.4
00595000-005a9000 r-xp 00000000 08:05 13373576   /usr/lib/libnssutil3.so
005a9000-005aa000 ---p 00014000 08:05 13373576   /usr/lib/libnssutil3.so
005aa000-005ad000 r--p 00014000 08:05 13373576   /usr/lib/libnssutil3.so
005ad000-005ae000 rw-p 00017000 08:05 13373576   /usr/lib/libnssutil3.so
005ae000-005b0000 r-xp 00000000 08:05 13375863   /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
005b0000-005b1000 r--p 00001000 08:05 13375863   /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
005b1000-005b2000 rw-p 00002000 08:05 13375863   /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
005b2000-005b3000 r-xp 00000000 08:05 13375713   /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
005b3000-005b4000 r--p 00000000 08:05 13375713   /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
005b4000-005b5000 rw-p 00001000 08:05 13375713   /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
005b5000-005d8000 r-xp 00000000 08:05 14421323   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
005d8000-005d9000 r--p 00022000 08:05 14421323   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
005d9000-005db000 rw-p 00023000 08:05 14421323   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
005db000-005e8000 r-xp 00000000 08:05 13375727   /usr/lib/i386-linux-gnu/libXext.so.6.4.0
005e8000-005e9000 r--p 0000c000 08:05 13375727   /usr/lib/i386-linux-gnu/libXext.so.6.4.0
005e9000-005ea000 rw-p 0000d000 08:05 13375727   /usr/lib/i386-linux-gnu/libXext.so.6.4.0
005ea000-005f2000 r-xp 00000000 08:05 13375739   /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
005f2000-005f3000 r--p 00007000 08:05 13375739   /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
005f3000-005f4000 rw-p 00008000 08:05 13375739   /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
005f4000-00601000 r-xp 00000000 08:05 13372276   /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00601000-00602000 r--p 0000c000 08:05 13372276   /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00602000-00603000 rw-p 0000d000 08:05 13372276   /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00603000-00605000 r-xp 00000000 08:05 13375717   /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00605000-00606000 r--p 00001000 08:05 13375717   /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00606000-00607000 rw-p 00002000 08:05 13375717   /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00608000-0060c000 r-xp 00000000 08:05 13373010   /usr/lib/libXtst.so.6.1.0
0060c000-0060d000 r--p 00003000 08:05 13373010   /usr/lib/libXtst.so.6.1.0
0060d000-0060e000 rw-p 00004000 08:05 13373010   /usr/lib/libXtst.so.6.1.0
0060e000-00614000 r-xp 00000000 08:05 13375737   /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
00614000-00615000 r--p 00005000 08:05 13375737   /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
00615000-00616000 rw-p 00006000 08:05 13375737   /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
00616000-0061e000 r-xp 00000000 08:05 13375721   /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
0061e000-0061f000 r--p 00007000 08:05 13375721   /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
0061f000-00620000 rw-p 00008000 08:05 13375721   /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00620000-00626000 r-xp 00000000 08:05 13375859   /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00626000-00627000 r--p 00005000 08:05 13375859   /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00627000-00628000 rw-p 00006000 08:05 13375859   /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00628000-0062c000 r-xp 00000000 08:05 13375725   /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
0062c000-0062d000 r--p 00003000 08:05 13375725   /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
0062d000-0062e000 rw-p 00004000 08:05 13375725   /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
0062e000-0062f000 r-xp 00000000 08:05 13375037   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
0062f000-00630000 r--p 00000000 08:05 13375037   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
00630000-00631000 rw-p 00001000 08:05 13375037   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
00631000-0064b000 r-xp 00000000 08:05 34079581   /lib/i386-linux-gnu/libgcc_s.so.1
0064b000-0064c000 r--p 00019000 08:05 34079581   /lib/i386-linux-gnu/libgcc_s.so.1
0064c000-0064d000 rw-p 0001a000 08:05 34079581   /lib/i386-linux-gnu/libgcc_s.so.1
0064d000-006b3000 r-xp 00000000 08:05 17439213   /usr/lib/jni/libswt-pi-gtk-3659.so
006b3000-006b4000 r--p 00065000 08:05 17439213   /usr/lib/jni/libswt-pi-gtk-3659.so
006b4000-006b6000 rw-p 00066000 08:05 17439213   /usr/lib/jni/libswt-pi-gtk-3659.so
006b6000-006b7000 rw-p 00000000 00:00 0 
006b7000-006ce000 r-xp 00000000 08:05 13375865   /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
006ce000-006cf000 r--p 00016000 08:05 13375865   /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
006cf000-006d0000 rw-p 00017000 08:05 13375865   /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
006d0000-006d4000 r-xp 00000000 08:05 13375642   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
006d4000-006d5000 r--p 00003000 08:05 13375642   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
006d5000-006d6000 rw-p 00004000 08:05 13375642   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
006d9000-006ec000 r-xp 00000000 08:05 34079636   /lib/i386-linux-gnu/libz.so.1.2.3.4
006ec000-006ed000 r--p 00012000 08:05 34079636   /lib/i386-linux-gnu/libz.so.1.2.3.4
006ed000-006ee000 rw-p 00013000 08:05 34079636   /lib/i386-linux-gnu/libz.so.1.2.3.4
006ee000-006ff000 r-xp 00000000 08:05 34079620   /lib/i386-linux-gnu/libresolv-2.13.so
006ff000-00700000 r--p 00010000 08:05 34079620   /lib/i386-linux-gnu/libresolv-2.13.so
00700000-00701000 rw-p 00011000 08:05 34079620   /lib/i386-linux-gnu/libresolv-2.13.so
00701000-00703000 rw-p 00000000 00:00 0 
00703000-0070b000 r-xp 00000000 08:05 13369892   /usr/lib/liboverlay-scrollbar-0.1.so.0.0.12
0070b000-0070c000 r--p 00007000 08:05 13369892   /usr/lib/liboverlay-scrollbar-0.1.so.0.0.12
0070c000-0070d000 rw-p 00008000 08:05 13369892   /usr/lib/liboverlay-scrollbar-0.1.so.0.0.12
0070f000-0071c000 r-xp 00000000 08:05 14421324   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
0071c000-0071d000 r--p 0000c000 08:05 14421324   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
0071d000-0071e000 rw-p 0000d000 08:05 14421324   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
0071e000-00721000 r-xp 00000000 08:05 13373082   /usr/lib/libcanberra-gtk.so.0.1.8
00721000-00722000 r--p 00002000 08:05 13373082   /usr/lib/libcanberra-gtk.so.0.1.8
00722000-00723000 rw-p 00003000 08:05 13373082   /usr/lib/libcanberra-gtk.so.0.1.8
00723000-00731000 r-xp 00000000 08:05 13373084   /usr/lib/libcanberra.so.0.2.5
00731000-00732000 r--p 0000d000 08:05 13373084   /usr/lib/libcanberra.so.0.2.5
00732000-00733000 rw-p 0000e000 08:05 13373084   /usr/lib/libcanberra.so.0.2.5
00733000-00737000 rwxp 00000000 00:00 0 
00737000-00766000 r-xp 00000000 08:05 13373573   /usr/lib/libnspr4.so
00766000-00767000 r--p 0002e000 08:05 13373573   /usr/lib/libnspr4.so
00767000-00768000 rw-p 0002f000 08:05 13373573   /usr/lib/libnspr4.so
00768000-0076a000 rw-p 00000000 00:00 0 
0076a000-007ff000 r-xp 00000000 08:05 13373237   /usr/lib/libgdk-x11-2.0.so.0.2400.4
007ff000-00800000 ---p 00095000 08:05 13373237   /usr/lib/libgdk-x11-2.0.so.0.2400.4
00800000-00802000 r--p 00095000 08:05 13373237   /usr/lib/libgdk-x11-2.0.so.0.2400.4
00802000-00803000 rw-p 00097000 08:05 13373237   /usr/lib/libgdk-x11-2.0.so.0.2400.4
00803000-00841000 r-xp 00000000 08:05 13375826   /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2800.4
00841000-00842000 r--p 0003e000 08:05 13375826   /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2800.4
00842000-00843000 rw-p 0003f000 08:05 13375826   /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2800.4
00843000-0085c000 r-xp 00000000 08:05 34079624   /lib/i386-linux-gnu/libselinux.so.1
0085c000-0085d000 r--p 00018000 08:05 34079624   /lib/i386-linux-gnu/libselinux.so.1
0085d000-0085e000 rw-p 00019000 08:05 34079624   /lib/i386-linux-gnu/libselinux.so.1
0085e000-00860000 r-xp 00000000 08:05 13376205   /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
00860000-00861000 r--p 00001000 08:05 13376205   /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
00861000-00862000 rw-p 00002000 08:05 13376205   /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
00863000-00866000 r-xp 00000000 08:05 13373627   /usr/lib/libplc4.so
00866000-00867000 r--p 00002000 08:05 13373627   /usr/lib/libplc4.so
00867000-00868000 rw-p 00003000 08:05 13373627   /usr/lib/libplc4.so
00868000-00895000 r-xp 00000000 08:05 13375773   /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
00895000-00896000 r--p 0002c000 08:05 13375773   /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
00896000-00897000 rw-p 0002d000 08:05 13375773   /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
00897000-0089e000 r-xp 00000000 08:05 13373826   /usr/lib/libvorbisfile.so.3.3.4
0089e000-0089f000 r--p 00006000 08:05 13373826   /usr/lib/libvorbisfile.so.3.3.4
0089f000-008a0000 rw-p 00007000 08:05 13373826   /usr/lib/libvorbisfile.so.3.3.4
008a0000-008a7000 r-xp 00000000 08:05 13373510   /usr/lib/libltdl.so.7.2.1
008a7000-008a8000 r--p 00006000 08:05 13373510   /usr/lib/libltdl.so.7.2.1
008a8000-008a9000 rw-p 00007000 08:05 13373510   /usr/lib/libltdl.so.7.2.1
008ab000-008b2000 r-xp 00000000 08:05 14421327   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
008b2000-008b3000 r--p 00006000 08:05 14421327   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
008b3000-008b4000 rw-p 00007000 08:05 14421327   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
008b4000-00935000 r-xp 00000000 08:05 13369532   /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
00935000-00939000 r--p 00080000 08:05 13369532   /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
00939000-0093a000 rw-p 00084000 08:05 13369532   /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
0093a000-0093c000 r-xp 00000000 08:05 34078788   /lib/libnss_mdns4_minimal.so.2
0093c000-0093d000 r--p 00001000 08:05 34078788   /lib/libnss_mdns4_minimal.so.2
0093d000-0093e000 rw-p 00002000 08:05 34078788   /lib/libnss_mdns4_minimal.so.2
0093e000-00953000 r-xp 00000000 08:05 34079618   /lib/i386-linux-gnu/libpthread-2.13.so
00953000-00954000 r--p 00015000 08:05 34079618   /lib/i386-linux-gnu/libpthread-2.13.so
00954000-00955000 rw-p 00016000 08:05 34079618   /lib/i386-linux-gnu/libpthread-2.13.so
00955000-00957000 rw-p 00000000 00:00 0 
00957000-0095c000 r-xp 00000000 08:05 13373589   /usr/lib/libogg.so.0.7.0
0095c000-0095d000 r--p 00004000 08:05 13373589   /usr/lib/libogg.so.0.7.0
0095d000-0095e000 rw-p 00005000 08:05 13373589   /usr/lib/libogg.so.0.7.0
0095e000-0095f000 r-xp 00000000 00:00 0          [vdso]
0095f000-009a4000 r-xp 00000000 08:05 13375792   /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.2800.6
009a4000-009a5000 r--p 00044000 08:05 13375792   /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.2800.6
009a5000-009a6000 rw-p 00045000 08:05 13375792   /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.2800.6
009a6000-009e3000 r-xp 00000000 08:05 34079615   /lib/i386-linux-gnu/libpcre.so.3.12.1
009e3000-009e4000 r--p 0003c000 08:05 34079615   /lib/i386-linux-gnu/libpcre.so.3.12.1
009e4000-009e5000 rw-p 0003d000 08:05 34079615   /lib/i386-linux-gnu/libpcre.so.3.12.1
009e6000-00ac5000 r-xp 00000000 08:05 13375848   /usr/lib/i386-linux-gnu/libstdc++.so.6.0.14
00ac5000-00ac9000 r--p 000de000 08:05 13375848   /usr/lib/i386-linux-gnu/libstdc++.so.6.0.14
00ac9000-00aca000 rw-p 000e2000 08:05 13375848   /usr/lib/i386-linux-gnu/libstdc++.so.6.0.14
00aca000-00ad1000 rw-p 00000000 00:00 0 
00ad1000-00be7000 r-xp 00000000 08:05 13375715   /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00be7000-00be8000 ---p 00116000 08:05 13375715   /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00be8000-00be9000 r--p 00116000 08:05 13375715   /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00be9000-00beb000 rw-p 00117000 08:05 13375715   /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00beb000-00bec000 rw-p 00000000 00:00 0 
00bec000-00bf3000 r-xp 00000000 08:05 13375620   /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
00bf3000-00bf4000 ---p 00007000 08:05 13375620   /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
00bf4000-00bf5000 r--p 00007000 08:05 13375620   /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
00bf5000-00bf6000 rw-p 00008000 08:05 13375620   /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
00bf6000-00bfa000 r-xp 00000000 08:05 13375033   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
00bfa000-00bfb000 r--p 00003000 08:05 13375033   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
00bfb000-00bfc000 rw-p 00004000 08:05 13375033   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
00bfc000-00c46000 r-xp 00000000 08:05 13376954   /usr/lib/nss/libfreebl3.so
00c46000-00c47000 r--p 0004a000 08:05 13376954   /usr/lib/nss/libfreebl3.so
00c47000-00c48000 rw-p 0004b000 08:05 13376954   /usr/lib/nss/libfreebl3.so
00c48000-00c4c000 rw-p 00000000 00:00 0 
00c4f000-00c51000 r-xp 00000000 08:05 34079563   /lib/i386-linux-gnu/libdl-2.13.so
00c51000-00c52000 r--p 00001000 08:05 34079563   /lib/i386-linux-gnu/libdl-2.13.so
00c52000-00c53000 rw-p 00002000 08:05 34079563   /lib/i386-linux-gnu/libdl-2.13.so
00c53000-0108d000 r-xp 00000000 08:05 17043893   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
0108d000-010a4000 r--p 0043a000 08:05 17043893   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
010a4000-010b1000 rw-p 00451000 08:05 17043893   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
010b1000-014c9000 rw-p 00000000 00:00 0 
014c9000-01503000 r-xp 00000000 08:05 13373436   /usr/lib/libibus.so.2.0.0
01503000-01504000 r--p 00039000 08:05 13373436   /usr/lib/libibus.so.2.0.0
01504000-01505000 rw-p 0003a000 08:05 13373436   /usr/lib/libibus.so.2.0.0
01505000-01510000 r-xp 00000000 08:05 34079630   /lib/i386-linux-gnu/libudev.so.0.11.1
01510000-01511000 r--p 0000a000 08:05 34079630   /lib/i386-linux-gnu/libudev.so.0.11.1
01511000-01512000 rw-p 0000b000 08:05 34079630   /lib/i386-linux-gnu/libudev.so.0.11.1
01512000-01518000 r-xp 00000000 08:05 13375711   /usr/lib/i386-linux-gnu/libSM.so.6.0.1
01518000-01519000 r--p 00005000 08:05 13375711   /usr/lib/i386-linux-gnu/libSM.so.6.0.1
01519000-0151a000 rw-p 00006000 08:05 13375711   /usr/lib/i386-linux-gnu/libSM.so.6.0.1
0151a000-01564000 r-xp 00000000 08:05 13372961   /usr/lib/libFLAC.so.8.2.0
01564000-01565000 r--p 00049000 08:05 13372961   /usr/lib/libFLAC.so.8.2.0
01565000-01566000 rw-p 0004a000 08:05 13372961   /usr/lib/libFLAC.so.8.2.0
01566000-015ef000 r-xp 00000000 08:05 14421326   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
015ef000-015f0000 r--p 00088000 08:05 14421326   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
015f0000-015f7000 rw-p 00089000 08:05 14421326   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
015f7000-0161b000 rw-p 00000000 00:00 0 
0161b000-0165e000 r-xp 00000000 08:05 17432837   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
0165e000-0165f000 r--p 00042000 08:05 17432837   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
0165f000-01661000 rw-p 00043000 08:05 17432837   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
01661000-01662000 rw-p 00000000 00:00 0 
01662000-0169a000 r-xp 00000000 08:05 14423853   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
0169a000-0169b000 ---p 00038000 08:05 14423853   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
0169b000-0169c000 r--p 00038000 08:05 14423853   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
0169c000-0169d000 rw-p 00039000 08:05 14423853   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
0169d000-016bc000 r-xp 00000000 08:05 13373138   /usr/lib/libdbus-glib-1.so.2.1.0
016bc000-016bd000 r--p 0001e000 08:05 13373138   /usr/lib/libdbus-glib-1.so.2.1.0
016bd000-016be000 rw-p 0001f000 08:05 13373138   /usr/lib/libdbus-glib-1.so.2.1.0
016be000-016cc000 r-xp 00000000 08:05 13375749   /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
016cc000-016cd000 r--p 0000d000 08:05 13375749   /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
016cd000-016ce000 rw-p 0000e000 08:05 13375749   /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
016ce000-0175f000 r-xp 00000000 08:05 13375790   /usr/lib/i386-linux-gnu/libgnutls.so.26.14.12
0175f000-01763000 r--p 00090000 08:05 13375790   /usr/lib/i386-linux-gnu/libgnutls.so.26.14.12
01763000-01764000 rw-p 00094000 08:05 13375790   /usr/lib/i386-linux-gnu/libgnutls.so.26.14.12
01764000-017ab000 r-xp 00000000 08:05 13372985   /usr/lib/libORBit-2.so.0.1.0
017ab000-017b3000 r--p 00047000 08:05 13372985   /usr/lib/libORBit-2.so.0.1.0
017b3000-017b5000 rw-p 0004f000 08:05 13372985   /usr/lib/libORBit-2.so.0.1.0
017b5000-017ca000 r-xp 00000000 08:05 13373033   /usr/lib/libart_lgpl_2.so.2.3.21
017ca000-017cb000 r--p 00014000 08:05 13373033   /usr/lib/libart_lgpl_2.so.2.3.21
017cb000-017cc000 rw-p 00015000 08:05 13373033   /usr/lib/libart_lgpl_2.so.2.3.21
017cc000-017e6000 r-xp 00000000 08:05 13373289   /usr/lib/libgnome-keyring.so.0.1.1
017e6000-017e7000 r--p 0001a000 08:05 13373289   /usr/lib/libgnome-keyring.so.0.1.1
017e7000-017e8000 rw-p 0001b000 08:05 13373289   /usr/lib/libgnome-keyring.so.0.1.1
017e8000-017eb000 r-xp 00000000 08:05 13372989   /usr/lib/libORBitCosNaming-2.so.0.1.0
017eb000-017ec000 r--p 00003000 08:05 13372989   /usr/lib/libORBitCosNaming-2.so.0.1.0
017ec000-017ed000 rw-p 00004000 08:05 13372989   /usr/lib/libORBitCosNaming-2.so.0.1.0
01899000-018be000 r-xp 00000000 08:05 13373822   /usr/lib/libvorbis.so.0.4.5
018be000-018bf000 r--p 00025000 08:05 13373822   /usr/lib/libvorbis.so.0.4.5
018bf000-018c0000 rw-p 00026000 08:05 13373822   /usr/lib/libvorbis.so.0.4.5
018dd000-018ec000 r-xp 00000000 08:05 13373760   /usr/lib/libtdb.so.1.2.9
018ec000-018ed000 r--p 0000e000 08:05 13373760   /usr/lib/libtdb.so.1.2.9
018ed000-018ee000 rw-p 0000f000 08:05 13373760   /usr/lib/libtdb.so.1.2.9
01966000-019a5000 r-xp 00000000 08:05 13370232   /usr/lib/libpulse.so.0.12.3
019a5000-019a6000 r--p 0003e000 08:05 13370232   /usr/lib/libpulse.so.0.12.3
019a6000-019a7000 rw-p 0003f000 08:05 13370232   /usr/lib/libpulse.so.0.12.3
024e0000-02645000 r-xp 00000000 08:05 13373824   /usr/lib/libvorbisenc.so.2.0.8
02645000-02646000 ---p 00165000 08:05 13373824   /usr/lib/libvorbisenc.so.2.0.8
02646000-02657000 r--p 00165000 08:05 13373824   /usr/lib/libvorbisenc.so.2.0.8
02657000-02658000 rw-p 00176000 08:05 13373824   /usr/lib/libvorbisenc.so.2.0.8
02710000-02712000 r-xp 00000000 08:05 34078787   /lib/libnss_mdns4.so.2
02712000-02713000 r--p 00001000 08:05 34078787   /lib/libnss_mdns4.so.2
02713000-02714000 rw-p 00002000 08:05 34078787   /lib/libnss_mdns4.so.2
0293a000-02967000 r-xp 00000000 08:05 13373299   /usr/lib/libgnomecanvas-2.so.0.3000.3
02967000-02968000 ---p 0002d000 08:05 13373299   /usr/lib/libgnomecanvas-2.so.0.3000.3
02968000-02969000 r--p 0002d000 08:05 13373299   /usr/lib/libgnomecanvas-2.so.0.3000.3
02969000-0296a000 rw-p 0002e000 08:05 13373299   /usr/lib/libgnomecanvas-2.so.0.3000.3
02def000-02df2000 r-xp 00000000 08:05 34079587   /lib/i386-linux-gnu/libgpg-error.so.0.8.0
02df2000-02df3000 r--p 00002000 08:05 34079587   /lib/i386-linux-gnu/libgpg-error.so.0.8.0
02df3000-02df4000 rw-p 00003000 08:05 34079587   /lib/i386-linux-gnu/libgpg-error.so.0.8.0
03023000-03036000 r-xp 00000000 08:05 13373420   /usr/lib/libgvfscommon.so.0.0.0
03036000-03037000 r--p 00012000 08:05 13373420   /usr/lib/libgvfscommon.so.0.0.0
03037000-03038000 rw-p 00013000 08:05 13373420   /usr/lib/libgvfscommon.so.0.0.0
0320e000-0323d000 r-xp 00000000 08:05 13373699   /usr/lib/librsvg-2.so.2.32.1
0323d000-0323e000 r--p 0002e000 08:05 13373699   /usr/lib/librsvg-2.so.2.32.1
0323e000-0323f000 rw-p 0002f000 08:05 13373699   /usr/lib/librsvg-2.so.2.32.1
03351000-03398000 r-xp 00000000 08:05 13370240   /usr/lib/libpulsecommon-0.9.22.so
03398000-03399000 r--p 00046000 08:05 13370240   /usr/lib/libpulsecommon-0.9.22.so
03399000-0339a000 rw-p 00047000 08:05 13370240   /usr/lib/libpulsecommon-0.9.22.so
034eb000-0350e000 r-xp 00000000 08:05 13375151   /usr/lib/gio/modules/libgvfsdbus.so
0350e000-0350f000 r--p 00023000 08:05 13375151   /usr/lib/gio/modules/libgvfsdbus.so
0350f000-03510000 rw-p 00024000 08:05 13375151   /usr/lib/gio/modules/libgvfsdbus.so
0361a000-039eb000 r-xp 00000000 08:05 13373379   /usr/lib/libgtk-x11-2.0.so.0.2400.4
039eb000-039ef000 r--p 003d0000 08:05 13373379   /usr/lib/libgtk-x11-2.0.so.0.2400.4
039ef000-039f1000 rw-p 003d4000 08:05 13373379   /usr/lib/libgtk-x11-2.0.so.0.2400.4
039f1000-039f3000 rw-p 00000000 00:00 0 
03c1e000-03c22000 r-xp 00000000 08:05 13375627   /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
03c22000-03c23000 r--p 00003000 08:05 13375627   /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
03c23000-03c24000 rw-p 00004000 08:05 13375627   /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
03ca1000-03dc4000 r-xp 00000000 08:05 13370293   /usr/lib/libxml2.so.2.7.8
03dc4000-03dc8000 r--p 00123000 08:05 13370293   /usr/lib/libxml2.so.2.7.8
03dc8000-03dc9000 rw-p 00127000 08:05 13370293   /usr/lib/libxml2.so.2.7.8
03dc9000-03dca000 rw-p 00000000 00:00 0 
03e83000-03e97000 r-xp 00000000 08:05 13375709   /usr/lib/i386-linux-gnu/libICE.so.6.3.0
03e97000-03e98000 r--p 00013000 08:05 13375709   /usr/lib/i386-linux-gnu/libICE.so.6.3.0
03e98000-03e99000 rw-p 00014000 08:05 13375709   /usr/lib/i386-linux-gnu/libICE.so.6.3.0
03e99000-03e9b000 rw-p 00000000 00:00 0 
045d0000-045e2000 r-xp 00000000 08:05 13373054   /usr/lib/libbonobo-activation.so.4.0.0
045e2000-045e3000 r--p 00012000 08:05 13373054   /usr/lib/libbonobo-activation.so.4.0.0
045e3000-045e4000 rw-p 00013000 08:05 13373054   /usr/lib/libbonobo-activation.so.4.0.0
045e4000-045e5000 rw-p 00000000 00:00 0 
04c61000-04c63000 r-xp 00000000 08:05 13375755   /usr/lib/i386-linux-gnu/libavahi-glib.so.1.0.2
04c63000-04c64000 r--p 00001000 08:05 13375755   /usr/lib/i386-linux-gnu/libavahi-glib.so.1.0.2
04c64000-04c65000 rw-p 00002000 08:05 13375755   /usr/lib/i386-linux-gnu/libavahi-glib.so.1.0.2
04d2a000-04d39000 r-xp 00000000 08:05 13375850   /usr/lib/i386-linux-gnu/libtasn1.so.3.1.9
04d39000-04d3a000 r--p 0000e000 08:05 13375850   /usr/lib/i386-linux-gnu/libtasn1.so.3.1.9
04d3a000-04d3b000 rw-p 0000f000 08:05 13375850   /usr/lib/i386-linux-gnu/libtasn1.so.3.1.9
0532b000-053d9000 r-xp 00000000 08:05 13373074   /usr/lib/libcairo.so.2.11000.2
053d9000-053da000 ---p 000ae000 08:05 13373074   /usr/lib/libcairo.so.2.11000.2
053da000-053db000 r--p 000ae000 08:05 13373074   /usr/lib/libcairo.so.2.11000.2
053db000-053dc000 rw-p 000af000 08:05 13373074   /usr/lib/libcairo.so.2.11000.2
053dc000-053de000 rw-p 00000000 00:00 0 
05436000-0543a000 r-xp 00000000 08:05 13375636   /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
0543a000-0543b000 r--p 00003000 08:05 13375636   /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
0543b000-0543c000 rw-p 00004000 08:05 13375636   /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
059d7000-059dd000 r-xp 00000000 08:05 13373225   /usr/lib/libgailutil.so.18.0.1
059dd000-059de000 r--p 00005000 08:05 13373225   /usr/lib/libgailutil.so.18.0.1
059de000-059df000 rw-p 00006000 08:05 13373225   /usr/lib/libgailutil.so.18.0.1
05ab4000-05b04000 r-xp 00000000 08:05 13373052   /usr/lib/libbonobo-2.so.0.0.0
05b04000-05b05000 ---p 00050000 08:05 13373052   /usr/lib/libbonobo-2.so.0.0.0
05b05000-05b08000 r--p 00050000 08:05 13373052   /usr/lib/libbonobo-2.so.0.0.0
05b08000-05b0f000 rw-p 00053000 08:05 13373052   /usr/lib/libbonobo-2.so.0.0.0
05cc1000-05cc8000 r-xp 00000000 08:05 34078824   /lib/libwrap.so.0.7.6
05cc8000-05cc9000 r--p 00006000 08:05 34078824   /lib/libwrap.so.0.7.6
05cc9000-05cca000 rw-p 00007000 08:05 34078824   /lib/libwrap.so.0.7.6
05d11000-05d1b000 r-xp 00000000 08:05 17439210   /usr/lib/jni/libswt-atk-gtk-3659.so
05d1b000-05d1c000 r--p 00009000 08:05 17439210   /usr/lib/jni/libswt-atk-gtk-3659.so
05d1c000-05d1d000 rw-p 0000a000 08:05 17439210   /usr/lib/jni/libswt-atk-gtk-3659.so
05f54000-05f82000 r-xp 00000000 08:05 13373229   /usr/lib/libgconf-2.so.4.1.5
05f82000-05f83000 ---p 0002e000 08:05 13373229   /usr/lib/libgconf-2.so.4.1.5
05f83000-05f84000 r--p 0002e000 08:05 13373229   /usr/lib/libgconf-2.so.4.1.5
05f84000-05f86000 rw-p 0002f000 08:05 13373229   /usr/lib/libgconf-2.so.4.1.5
06024000-06084000 r-xp 00000000 08:05 13369976   /usr/lib/libsndfile.so.1.0.23
06084000-06085000 ---p 00060000 08:05 13369976   /usr/lib/libsndfile.so.1.0.23
06085000-06086000 r--p 00060000 08:05 13369976   /usr/lib/libsndfile.so.1.0.23
06086000-06087000 rw-p 00061000 08:05 13369976   /usr/lib/libsndfile.so.1.0.23
06087000-0608b000 rw-p 00000000 00:00 0 
0618a000-0620e000 r-xp 00000000 08:05 13373305   /usr/lib/libgnomeui-2.so.0.2400.5
0620e000-06210000 r--p 00083000 08:05 13373305   /usr/lib/libgnomeui-2.so.0.2400.5
06210000-06212000 rw-p 00085000 08:05 13373305   /usr/lib/libgnomeui-2.so.0.2400.5
06459000-0652e000 r-xp 00000000 08:05 34079585   /lib/i386-linux-gnu/libglib-2.0.so.0.2800.6
0652e000-0652f000 r--p 000d4000 08:05 34079585   /lib/i386-linux-gnu/libglib-2.0.so.0.2800.6
0652f000-06530000 rw-p 000d5000 08:05 34079585   /lib/i386-linux-gnu/libglib-2.0.so.0.2800.6
0656a000-065db000 r-xp 00000000 08:05 34079583   /lib/i386-linux-gnu/libgcrypt.so.11.6.0
065db000-065dc000 r--p 00070000 08:05 34079583   /lib/i386-linux-gnu/libgcrypt.so.11.6.0
065dc000-065de000 rw-p 00071000 08:05 34079583   /lib/i386-linux-gnu/libgcrypt.so.11.6.0
06618000-06670000 r-xp 00000000 08:05 13373307   /usr/lib/libgnomevfs-2.so.0.2400.4
06670000-06672000 r--p 00057000 08:05 13373307   /usr/lib/libgnomevfs-2.so.0.2400.4
06672000-06674000 rw-p 00059000 08:05 13373307   /usr/lib/libgnomevfs-2.so.0.2400.4
06691000-066c2000 r-xp 00000000 08:05 13373114   /usr/lib/libcroco-0.6.so.3.0.1
066c2000-066c3000 r--p 00030000 08:05 13373114   /usr/lib/libcroco-0.6.so.3.0.1
066c3000-066c5000 rw-p 00031000 08:05 13373114   /usr/lib/libcroco-0.6.so.3.0.1
072d6000-07311000 r-xp 00000000 08:05 34079637   /lib/i386-linux-gnu/libdbus-1.so.3.5.4
07311000-07312000 r--p 0003a000 08:05 34079637   /lib/i386-linux-gnu/libdbus-1.so.3.5.4
07312000-07313000 rw-p 0003b000 08:05 34079637   /lib/i386-linux-gnu/libdbus-1.so.3.5.4
07376000-073ce000 r-xp 00000000 08:05 13373056   /usr/lib/libbonoboui-2.so.0.0.0
073ce000-073cf000 r--p 00057000 08:05 13373056   /usr/lib/libbonoboui-2.so.0.0.0
073cf000-073d1000 rw-p 00058000 08:05 13373056   /usr/lib/libbonoboui-2.so.0.0.0
0744a000-0744d000 r-xp 00000000 08:05 17439215   /usr/lib/jni/libswt-gnome-gtk-3659.so
0744d000-0744e000 r--p 00002000 08:05 17439215   /usr/lib/jni/libswt-gnome-gtk-3659.so
0744e000-0744f000 rw-p 00003000 08:05 17439215   /usr/lib/jni/libswt-gnome-gtk-3659.so
0745d000-0745f000 r-xp 00000000 08:05 34079631   /lib/i386-linux-gnu/libutil-2.13.so
0745f000-07460000 r--p 00001000 08:05 34079631   /lib/i386-linux-gnu/libutil-2.13.so
07460000-07461000 rw-p 00002000 08:05 34079631   /lib/i386-linux-gnu/libutil-2.13.so
074db000-074ed000 r-xp 00000000 08:05 13373283   /usr/lib/libgnome-2.so.0.3200.1
074ed000-074ee000 r--p 00011000 08:05 13373283   /usr/lib/libgnome-2.so.0.3200.1
074ee000-074ef000 rw-p 00012000 08:05 13373283   /usr/lib/libgnome-2.so.0.3200.1
076d0000-076e5000 r-xp 00000000 08:05 13373140   /usr/lib/libdbusmenu-glib.so.3.0.14
076e5000-076e6000 r--p 00014000 08:05 13373140   /usr/lib/libdbusmenu-glib.so.3.0.14
076e6000-076e7000 rw-p 00015000 08:05 13373140   /usr/lib/libdbusmenu-glib.so.3.0.14
07933000-0799a000 r-xp 00000000 08:05 13373626   /usr/lib/libpixman-1.so.0.20.2
0799a000-0799b000 ---p 00067000 08:05 13373626   /usr/lib/libpixman-1.so.0.20.2
0799b000-0799e000 r--p 00067000 08:05 13373626   /usr/lib/libpixman-1.so.0.20.2
0799e000-0799f000 rw-p 0006a000 08:05 13373626   /usr/lib/libpixman-1.so.0.20.2
07c11000-07c1b000 r-xp 00000000 08:05 34078807   /lib/libpopt.so.0.0.0
07c1b000-07c1c000 r--p 00009000 08:05 34078807   /lib/libpopt.so.0.0.0
07c1c000-07c1d000 rw-p 0000a000 08:05 34078807   /lib/libpopt.so.0.0.0
07cb0000-07cb5000 r-xp 00000000 08:05 13376369   /usr/lib/libcanberra-0.28/libcanberra-pulse.so
07cb5000-07cb6000 r--p 00005000 08:05 13376369   /usr/lib/libcanberra-0.28/libcanberra-pulse.so
07cb6000-07cb7000 rw-p 00006000 08:05 13376369   /usr/lib/libcanberra-0.28/libcanberra-pulse.so
07cc6000-07dc4000 r-xp 00000000 08:05 13375782   /usr/lib/i386-linux-gnu/libgio-2.0.so.0.2800.6
07dc4000-07dc5000 ---p 000fe000 08:05 13375782   /usr/lib/i386-linux-gnu/libgio-2.0.so.0.2800.6
07dc5000-07dc7000 r--p 000fe000 08:05 13375782   /usr/lib/i386-linux-gnu/libgio-2.0.so.0.2800.6
07dc7000-07dc8000 rw-p 00100000 08:05 13375782   /usr/lib/i386-linux-gnu/libgio-2.0.so.0.2800.6
07dc8000-07dc9000 rw-p 00000000 00:00 0 
07e84000-07e8f000 r-xp 00000000 08:05 13375618   /usr/lib/gtk-2.0/2.10.0/engines/libmist.so
07e8f000-07e90000 r--p 0000a000 08:05 13375618   /usr/lib/gtk-2.0/2.10.0/engines/libmist.so
07e90000-07e91000 rw-p 0000b000 08:05 13375618   /usr/lib/gtk-2.0/2.10.0/engines/libmist.so
08048000-08051000 r-xp 00000000 08:05 14289431   /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 08:05 14289431   /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 08:05 14289431   /usr/lib/jvm/java-6-openjdk/jre/bin/java
081ce000-081d2000 r-xp 00000000 08:05 34079597   /lib/i386-linux-gnu/libnss_dns-2.13.so
081d2000-081d3000 r--p 00004000 08:05 34079597   /lib/i386-linux-gnu/libnss_dns-2.13.so
081d3000-081d4000 rw-p 00005000 08:05 34079597   /lib/i386-linux-gnu/libnss_dns-2.13.so
0857f000-08582000 r-xp 00000000 08:05 34079634   /lib/i386-linux-gnu/libuuid.so.1.3.0
08582000-08583000 r--p 00002000 08:05 34079634   /lib/i386-linux-gnu/libuuid.so.1.3.0
08583000-08584000 rw-p 00003000 08:05 34079634   /lib/i386-linux-gnu/libuuid.so.1.3.0
0869d000-086c3000 r-xp 00000000 08:05 34079576   /lib/i386-linux-gnu/libexpat.so.1.5.2
086c3000-086c4000 ---p 00026000 08:05 34079576   /lib/i386-linux-gnu/libexpat.so.1.5.2
086c4000-086c6000 r--p 00026000 08:05 34079576   /lib/i386-linux-gnu/libexpat.so.1.5.2
086c6000-086c7000 rw-p 00028000 08:05 34079576   /lib/i386-linux-gnu/libexpat.so.1.5.2
087fc000-08807000 r-xp 00000000 08:05 17439214   /usr/lib/jni/libswt-cairo-gtk-3659.so
08807000-08808000 r--p 0000a000 08:05 17439214   /usr/lib/jni/libswt-cairo-gtk-3659.so
08808000-08809000 rw-p 0000b000 08:05 17439214   /usr/lib/jni/libswt-cairo-gtk-3659.so
089a3000-089ad000 r-xp 00000000 08:05 13375751   /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
089ad000-089ae000 r--p 00009000 08:05 13375751   /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
089ae000-089af000 rw-p 0000a000 08:05 13375751   /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
08b57000-08b5a000 r-xp 00000000 08:05 13373851   /usr/lib/libxcb-atom.so.1.0.0
08b5a000-08b5b000 r--p 00002000 08:05 13373851   /usr/lib/libxcb-atom.so.1.0.0
08b5b000-08b5c000 rw-p 00003000 08:05 13373851   /usr/lib/libxcb-atom.so.1.0.0
08dc1000-08de4000 r-xp 00000000 08:05 34078887   /lib/i386-linux-gnu/libpng12.so.0.44.0
08de4000-08de5000 r--p 00022000 08:05 34078887   /lib/i386-linux-gnu/libpng12.so.0.44.0
08de5000-08de6000 rw-p 00023000 08:05 34078887   /lib/i386-linux-gnu/libpng12.so.0.44.0
08e32000-08e40000 r-xp 00000000 08:05 13373142   /usr/lib/libdbusmenu-gtk.so.3.0.14
08e40000-08e41000 r--p 0000d000 08:05 13373142   /usr/lib/libdbusmenu-gtk.so.3.0.14
08e41000-08e42000 rw-p 0000e000 08:05 13373142   /usr/lib/libdbusmenu-gtk.so.3.0.14
08e61000-092a9000 rw-p 00000000 00:00 0          [heap]
6f8b0000-6fe10000 rw-p 00000000 00:00 0 
6fe10000-7a350000 rw-p 00000000 00:00 0 
7a350000-7ae00000 rw-p 00000000 00:00 0 
7ae00000-8f8b0000 rw-p 00000000 00:00 0 
8f8b0000-90a30000 rw-p 00000000 00:00 0 
90a30000-938b0000 rw-p 00000000 00:00 0 
938b0000-94010000 r--s 00001000 08:05 17043895   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94010000-942b0000 rw-p 00000000 00:00 0 
942b0000-949fa000 rw-p 00761000 08:05 17043895   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
949fa000-94eb0000 rw-p 00000000 00:00 0 
94eb0000-94fac000 rw-p 00eab000 08:05 17043895   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94fac000-952b0000 rw-p 00000000 00:00 0 
952b0000-952b8000 r-xs 00fa7000 08:05 17043895   /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
952b8000-956b0000 rw-p 00000000 00:00 0 
acb00000-acb90000 rw-p 00000000 00:00 0 
acb90000-acc00000 ---p 00000000 00:00 0 
acce9000-accec000 ---p 00000000 00:00 0 
accec000-acd3a000 rw-p 00000000 00:00 0 
acd3a000-acd3d000 ---p 00000000 00:00 0 
acd3d000-acd8b000 rw-p 00000000 00:00 0 
acd8b000-acd8e000 ---p 00000000 00:00 0 
acd8e000-ace5e000 rw-p 00000000 00:00 0 
ace5e000-ace61000 ---p 00000000 00:00 0 
ace61000-aceaf000 rw-p 00000000 00:00 0 
aceaf000-aceb2000 ---p 00000000 00:00 0 
aceb2000-acf00000 rw-p 00000000 00:00 0 
acf00000-acffe000 rw-p 00000000 00:00 0 
acffe000-ad000000 ---p 00000000 00:00 0 
ad02f000-ad032000 ---p 00000000 00:00 0 
ad032000-ad080000 rw-p 00000000 00:00 0 
ad080000-ad083000 ---p 00000000 00:00 0 
ad083000-ad0d1000 rw-p 00000000 00:00 0 
ad0d1000-ad0d4000 ---p 00000000 00:00 0 
ad0d4000-ad122000 rw-p 00000000 00:00 0 
ad122000-ad125000 ---p 00000000 00:00 0 
ad125000-ad173000 rw-p 00000000 00:00 0 
ad173000-ad176000 ---p 00000000 00:00 0 
ad176000-ad1c4000 rw-p 00000000 00:00 0 
ad1c4000-add08000 r--p 00000000 08:05 15467084   /usr/share/icons/hicolor/icon-theme.cache
add08000-addf2000 r--p 00000000 08:05 15468160   /usr/share/icons/Humanity/icon-theme.cache
addf2000-addf5000 ---p 00000000 00:00 0 
addf5000-ade43000 rw-p 00000000 00:00 0 
ade43000-ade46000 ---p 00000000 00:00 0 
ade46000-ade94000 rw-p 00000000 00:00 0 
ade94000-ade97000 ---p 00000000 00:00 0 
ade97000-adee5000 rw-p 00000000 00:00 0 
adee5000-adee8000 ---p 00000000 00:00 0 
adee8000-adf36000 rw-p 00000000 00:00 0 
adf36000-adf39000 ---p 00000000 00:00 0 
adf39000-adf87000 rw-p 00000000 00:00 0 
adf87000-adf8a000 ---p 00000000 00:00 0 
adf8a000-adfd8000 rw-p 00000000 00:00 0 
adfd8000-adfdb000 ---p 00000000 00:00 0 
adfdb000-ae029000 rw-p 00000000 00:00 0 
ae029000-ae02c000 ---p 00000000 00:00 0 
ae02c000-ae07a000 rw-p 00000000 00:00 0 
ae07a000-ae07d000 ---p 00000000 00:00 0 
ae07d000-ae0cb000 rw-p 00000000 00:00 0 
ae0cb000-ae0ce000 ---p 00000000 00:00 0 
ae0ce000-ae11c000 rw-p 00000000 00:00 0 
ae11c000-ae11f000 ---p 00000000 00:00 0 
ae11f000-ae16d000 rw-p 00000000 00:00 0 
ae16d000-ae170000 ---p 00000000 00:00 0 
ae170000-ae1be000 rw-p 00000000 00:00 0 
ae1be000-ae1c1000 ---p 00000000 00:00 0 
ae1c1000-ae20f000 rw-p 00000000 00:00 0 
ae20f000-ae212000 ---p 00000000 00:00 0 
ae212000-ae260000 rw-p 00000000 00:00 0 
ae260000-ae263000 ---p 00000000 00:00 0 
ae263000-ae2b1000 rw-p 00000000 00:00 0 
ae2b1000-ae2b4000 ---p 00000000 00:00 0 
ae2b4000-ae302000 rw-p 00000000 00:00 0 
ae302000-ae305000 ---p 00000000 00:00 0 
ae305000-ae353000 rw-p 00000000 00:00 0 
ae353000-ae356000 ---p 00000000 00:00 0 
ae356000-ae3a4000 rw-p 00000000 00:00 0 
ae3a4000-ae3a7000 ---p 00000000 00:00 0 
ae3a7000-ae3f5000 rw-p 00000000 00:00 0 
ae3f5000-ae3f8000 ---p 00000000 00:00 0 
ae3f8000-ae446000 rw-p 00000000 00:00 0 
ae446000-ae449000 ---p 00000000 00:00 0 
ae449000-ae497000 rw-p 00000000 00:00 0 
ae497000-ae49a000 ---p 00000000 00:00 0 
ae49a000-ae4e8000 rw-p 00000000 00:00 0 
ae4e8000-ae4eb000 ---p 00000000 00:00 0 
ae4eb000-ae539000 rw-p 00000000 00:00 0 
ae539000-ae53c000 ---p 00000000 00:00 0 
ae53c000-ae58a000 rw-p 00000000 00:00 0 
ae58a000-ae58d000 ---p 00000000 00:00 0 
ae58d000-ae5db000 rw-p 00000000 00:00 0 
ae5db000-ae5fe000 r--p 00000000 08:05 12583047   /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
ae5fe000-ae5ff000 ---p 00000000 00:00 0 
ae5ff000-aedff000 rw-p 00000000 00:00 0 
aedff000-b2e00000 rw-s 00000000 00:10 31708      /dev/shm/pulse-shm-3286848286
b2e00000-b2efc000 rw-p 00000000 00:00 0 
b2efc000-b2f00000 ---p 00000000 00:00 0 
b2f00000-b3000000 rw-p 00000000 00:00 0 
b3000000-b3100000 rw-p 00000000 00:00 0 
b313f000-b3147000 r--s 00000000 08:05 25168124   /home/gringo/.local/share/gvfs-metadata/root-589f3e00.log
b3147000-b314e000 r--s 000fb000 08:05 13500541   /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
b314e000-b3151000 ---p 00000000 00:00 0 
b3151000-b319f000 rw-p 00000000 00:00 0 
b319f000-b31f8000 r--p 00000000 08:05 14419635   /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-BI.ttf
b31f8000-b3258000 r--p 00000000 08:05 14419639   /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-RI.ttf
b3258000-b32ab000 r--p 00000000 08:05 14419634   /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf
b32ab000-b32ae000 ---p 00000000 00:00 0 
b32ae000-b32fc000 rw-p 00000000 00:00 0 
b32fc000-b32fd000 ---p 00000000 00:00 0 
b32fd000-b3afd000 rw-p 00000000 00:00 0 
b3afd000-b3afe000 ---p 00000000 00:00 0 
b3afe000-b42fe000 rw-p 00000000 00:00 0 
b42fe000-b4301000 ---p 00000000 00:00 0 
b4301000-b434f000 rw-p 00000000 00:00 0 
b434f000-b43af000 rw-s 00000000 00:04 1933342    /SYSV00000000 (deleted)
b43af000-b43b2000 ---p 00000000 00:00 0 
b43b2000-b4400000 rw-p 00000000 00:00 0 
b4400000-b4500000 rw-p 00000000 00:00 0 
b4503000-b4504000 r--s 00000000 08:05 25168122   /home/gringo/.local/share/gvfs-metadata/root
b4504000-b4521000 r--s 00000000 08:05 13767775   /usr/share/mime/mime.cache
b4521000-b4527000 r--s 00000000 08:05 25427984   /home/gringo/.local/share/mime/mime.cache
b4527000-b4532000 r--p 00000000 08:05 15475548   /usr/share/icons/Humanity-Dark/icon-theme.cache
b4532000-b4535000 rw-s 00000000 00:04 1966111    /SYSV00000000 (deleted)
b4535000-b4543000 r--s 00351000 08:05 13500506   /usr/lib/jvm/java-6-openjdk/jre/lib/charsets.jar
b4543000-b4546000 ---p 00000000 00:00 0 
b4546000-b4594000 rw-p 00000000 00:00 0 
b4594000-b4597000 ---p 00000000 00:00 0 
b4597000-b45e5000 rw-p 00000000 00:00 0 
b45e5000-b4634000 r--p 00000000 08:05 14419596   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b4634000-b468c000 r--p 00000000 08:05 14419638   /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
b468c000-b468d000 r--s 00000000 08:05 16257400   /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b468d000-b468e000 r--s 00000000 08:05 16256753   /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b468e000-b4694000 r--s 00000000 08:05 16256750   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4694000-b4696000 r--s 00000000 08:05 16256751   /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4696000-b4699000 r--s 00000000 08:05 16256761   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4699000-b469e000 r--s 00000000 08:05 16257407   /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b469e000-b46a0000 r--s 00000000 08:05 16256738   /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
b46a0000-b46a1000 r--s 00000000 08:05 16257408   /var/cache/fontconfig/52728cdc49031813f272d4aa720952ff-le32d4.cache-3
b46a1000-b46a2000 r--s 00000000 08:05 16256762   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b46a2000-b46a4000 r--s 00000000 08:05 16252935   /var/cache/fontconfig/b5ea634b0fb353b8ea17632d1f9ef766-le32d4.cache-3
b46a4000-b46a7000 r--s 00000000 08:05 16256747   /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b46a7000-b46a8000 r--s 00000000 08:05 16256742   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b46a8000-b46a9000 r--s 00000000 08:05 16256735   /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b46a9000-b46aa000 r--s 00000000 08:05 16256745   /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b46aa000-b46ae000 r--s 00000000 08:05 16256752   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b46ae000-b46b2000 r--s 00000000 08:05 16258124   /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b46b2000-b46b9000 r--s 00000000 08:05 16256817   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b46b9000-b46c4000 r--s 00000000 08:05 16256736   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b46c4000-b46c7000 r--s 00000000 08:05 16256758   /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b46c7000-b46c8000 r--s 00000000 08:05 16256818   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b46c8000-b46ea000 r--s 00000000 08:05 16252937   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
b46ea000-b46f2000 r--s 00000000 08:05 16256757   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b46f2000-b4700000 r--s 00000000 08:05 16257409   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4700000-b4800000 rw-p 00000000 00:00 0 
b4800000-b4801000 r--p 00000000 00:00 0 
b4801000-b4805000 r--s 00032000 08:05 25168621   /home/gringo/.azureus/plugins/azupnpav/azupnpav_0.2.23.jar
b4805000-b4808000 r--s 00000000 08:05 16257384   /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4808000-b4816000 r--s 00000000 08:05 16257406   /var/cache/fontconfig/865f88548240fee46819705c6468c165-le32d4.cache-3
b4816000-b4876000 rw-s 00000000 00:04 1900573    /SYSV00000000 (deleted)
b4876000-b4879000 ---p 00000000 00:00 0 
b4879000-b48c7000 rw-p 00000000 00:00 0 
b48c7000-b48ca000 ---p 00000000 00:00 0 
b48ca000-b4918000 rw-p 00000000 00:00 0 
b4918000-b491b000 ---p 00000000 00:00 0 
b491b000-b4969000 rw-p 00000000 00:00 0 
b4969000-b496c000 ---p 00000000 00:00 0 
b496c000-b49ba000 rw-p 00000000 00:00 0 
b49ba000-b49bd000 ---p 00000000 00:00 0 
b49bd000-b4a0b000 rw-p 00000000 00:00 0 
b4a0b000-b4a0e000 ---p 00000000 00:00 0 
b4a0e000-b4a5c000 rw-p 00000000 00:00 0 
b4a5c000-b4a5f000 ---p 00000000 00:00 0 
b4a5f000-b4aad000 rw-p 00000000 00:00 0 
b4aad000-b4ab0000 ---p 00000000 00:00 0 
b4ab0000-b4afe000 rw-p 00000000 00:00 0 
b4afe000-b4b01000 ---p 00000000 00:00 0 
b4b01000-b4b4f000 rw-p 00000000 00:00 0 
b4b4f000-b4b52000 ---p 00000000 00:00 0 
b4b52000-b4ba0000 rw-p 00000000 00:00 0 
b4ba0000-b4ba3000 ---p 00000000 00:00 0 
b4ba3000-b4bf1000 rw-p 00000000 00:00 0 
b4bf1000-b4bf4000 ---p 00000000 00:00 0 
b4bf4000-b4c42000 rw-p 00000000 00:00 0 
b4c42000-b4c56000 r--s 00183000 08:05 17958602   /usr/lib/java/swt-gtk-3.6.2.jar
b4c56000-b4c59000 ---p 00000000 00:00 0 
b4c59000-b4ca7000 rw-p 00000000 00:00 0 
b4ca7000-b4d7f000 r--s 00ba1000 08:05 13769545   /usr/share/java/Azureus2.jar
b4d7f000-b4d80000 ---p 00000000 00:00 0 
b4d80000-b4e00000 rw-p 00000000 00:00 0 
b4e00000-b4efc000 rw-p 00000000 00:00 0 
b4efc000-b4f00000 ---p 00000000 00:00 0 
b4f00000-b4f04000 r--s 00038000 08:05 13500528   /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar
b4f04000-b4f06000 r--s 00013000 08:05 13500505   /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
b4f06000-b4f09000 r--s 00031000 08:05 13500530   /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar
b4f09000-b4f0d000 r--s 0007c000 08:05 13500504   /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
b4f0d000-b4f0f000 r--s 00007000 08:05 13769295   /usr/share/java/commons-cli-1.2.jar
b4f0f000-b4f17000 r--s 00053000 08:05 13769411   /usr/share/java/log4j-1.2-1.2.15.jar
b4f17000-b4f2b000 r--s 00183000 08:05 17958602   /usr/lib/java/swt-gtk-3.6.2.jar
b4f2b000-b4f33000 r--s 00053000 08:05 13769411   /usr/share/java/log4j-1.2-1.2.15.jar
b4f33000-b4f35000 r--s 00007000 08:05 13769295   /usr/share/java/commons-cli-1.2.jar
b4f35000-b4f3d000 r--s 00066000 08:05 13769058   /usr/share/java/gnome-java-bridge.jar
b4f3d000-b4f40000 ---p 00000000 00:00 0 
b4f40000-b4f8e000 rw-p 00000000 00:00 0 
b4f8e000-b4f91000 ---p 00000000 00:00 0 
b4f91000-b500f000 rw-p 00000000 00:00 0 
b500f000-b5012000 ---p 00000000 00:00 0 
b5012000-b5060000 rw-p 00000000 00:00 0 
b5060000-b5260000 r--p 00000000 08:05 13376930   /usr/lib/locale/locale-archive
b5260000-b5263000 ---p 00000000 00:00 0 
b5263000-b52b1000 rw-p 00000000 00:00 0 
b52b1000-b52b4000 ---p 00000000 00:00 0 
b52b4000-b5302000 rw-p 00000000 00:00 0 
b5302000-b5303000 ---p 00000000 00:00 0 
b5303000-b53b6000 rw-p 00000000 00:00 0 
b53b6000-b5546000 r--s 037af000 08:05 13500543   /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
b5546000-b5556000 rw-p 00000000 00:00 0 
b5556000-b556e000 rw-p 00000000 00:00 0 
b556e000-b5574000 rw-p 00000000 00:00 0 
b5574000-b5619000 rw-p 00000000 00:00 0 
b5619000-b561c000 rw-p 00000000 00:00 0 
b561c000-b566e000 rw-p 00000000 00:00 0 
b566e000-b5674000 rw-p 00000000 00:00 0 
b5674000-b5719000 rw-p 00000000 00:00 0 
b5719000-b5722000 rw-p 00000000 00:00 0 
b5722000-b5739000 rw-p 00000000 00:00 0 
b5739000-b574d000 rw-p 00000000 00:00 0 
b574d000-b57c5000 rw-p 00000000 00:00 0 
b57c5000-b59c5000 rwxp 00000000 00:00 0 
b59c5000-b77c5000 rw-p 00000000 00:00 0 
b77c5000-b77c8000 ---p 00000000 00:00 0 
b77c8000-b7819000 rw-p 00000000 00:00 0 
b7819000-b781a000 r--s 00000000 08:05 25168701   /home/gringo/.azureus/plugins/azupdater/azupdaterpatcher_1.8.10.jar
b781a000-b781d000 r--s 0000f000 08:05 13500533   /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b781d000-b781e000 r--p 002a1000 08:05 13376930   /usr/lib/locale/locale-archive
b781e000-b7824000 rw-p 00000000 00:00 0 
b7824000-b782c000 rw-s 00000000 08:05 12582977   /tmp/hsperfdata_gringo/4566
b782c000-b782d000 rw-p 00000000 00:00 0 
b782d000-b782e000 ---p 00000000 00:00 0 
b782e000-b7830000 rw-p 00000000 00:00 0 
bfbec000-bfc0d000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Dazureus.install.path=/home/gringo/.azureus 
java_command: org.gudy.azureus2.ui.common.Main
Launcher Type: SUN_STANDARD

Environment Variables:
JAVA_HOME=/usr/lib/jvm/java-6-openjdk
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=gringo
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3de6f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3de6f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x2fef90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x2fef90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x2fef90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x2fee00], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x301bf0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x301bf0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x301bf0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x301bf0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 11.04 (natty)
uname:Linux 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686
libc:glibc 2.13 NPTL 2.13 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 4096, AS infinity
load average:0.27 0.16 0.15

/proc/meminfo:
MemTotal:        1801488 kB
MemFree:          895764 kB
Buffers:           64932 kB
Cached:           412980 kB
SwapCached:        27424 kB
Active:           350940 kB
Inactive:         472920 kB
Active(anon):     118968 kB
Inactive(anon):   235820 kB
Active(file):     231972 kB
Inactive(file):   237100 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:        925640 kB
HighFree:         163688 kB
LowTotal:         875848 kB
LowFree:          732076 kB
SwapTotal:       1832956 kB
SwapFree:        1765932 kB
Dirty:              1404 kB
Writeback:             0 kB
AnonPages:        327404 kB
Mapped:            77044 kB
Shmem:              8704 kB
Slab:              40628 kB
SReclaimable:      28752 kB
SUnreclaim:        11876 kB
KernelStack:        2928 kB
PageTables:         6456 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2733700 kB
Committed_AS:    1662780 kB
VmallocTotal:     122880 kB
VmallocUsed:       30368 kB
VmallocChunk:      81784 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       20472 kB
DirectMap4M:      888832 kB


CPU:total 2 (2 cores per cpu, 1 threads per core) family 6 model 15 stepping 13, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3

Memory: 4k page, physical 1801488k(895764k free), swap 1832956k(1765932k free)

vm_info: OpenJDK Client VM (20.0-b11) for linux-x86 JRE (1.6.0_22-b22), built on Jun 11 2011 05:57:52 by "buildd" with gcc 4.5.2

time: Tue Aug 23 23:02:11 2011
elapsed time: 13 seconds

---

