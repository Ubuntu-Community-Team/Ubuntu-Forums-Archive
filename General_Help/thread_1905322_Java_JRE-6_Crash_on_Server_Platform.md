---
title: "Java JRE-6 Crash on Server Platform"
date: 2012-01-06
forum: General Help
---

### Post by ffixcollector on 2012-01-06
I have been going nuts trying to fix run ps3mediaserver. Every time I try view certain folders JRE-6 crashes with the following log.

```
    #
    # A fatal error has been detected by the Java Runtime Environment:
    #
    #  SIGSEGV (0xb) at pc=0x00007f91e171abd6, pid=1558, tid=140264498943744
    #
    # JRE version: 6.0_20-b20
    # Java VM: OpenJDK 64-Bit Server VM (19.0-b09 mixed mode linux-amd64 compressed oops)
    # Derivative: IcedTea6 1.9.10
    # Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.10-0ubuntu1~10.04.2
    # Problematic frame:
    # C  [jna8882993865954913672.tmp+0x6bd6]  newJavaString+0x1b6
    #
    # If you would like to submit a bug report, please include
    # instructions how to reproduce the bug and visit:
    #   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
    # The crash happened outside the Java Virtual Machine in native code.
    # See problematic frame for where to report the bug.
    #

    ---------------  T H R E A D  ---------------

    Current thread (0x0000000002758000):  JavaThread "New I/O server worker #1-4" [_thread_in_native, id=1598, stack(0x00007f91df925000,0x00007f91dfa26000)]

    siginfo:si_signo=SIGSEGV: si_errno=0, si_code=2 (SEGV_ACCERR), si_addr=0x00007f91df925000

    Registers:
    RAX=0x000000000000006f, RBX=0x00007f91de681028, RCX=0x0000000000055808, RDX=0x00000000000d4753
    RSP=0x00007f91df879ff0, RBP=0x00007f91dfa22ef0, RSI=0x00007f91df879ff0, RDI=0x0000000000055809
    R8 =0x000000000000000a, R9 =0x000000000000000a, R10=0x0000000000000065, R11=0x000000000000006e
    R12=0x0000000000000000, R13=0x00000000c73069d0, R14=0x00007f91dfa22f88, R15=0x0000000002758000
    RIP=0x00007f91e171abd6, EFL=0x0000000000010206, CSGSFS=0x0000000000000033, ERR=0x0000000000000006
      TRAPNO=0x000000000000000e

    Register to memory mapping:

    RAX=0x000000000000006f
    0x000000000000006f is pointing to unknown location

    RBX=0x00007f91de681028
    0x00007f91de681028 is pointing to unknown location

    RCX=0x0000000000055808
    0x0000000000055808 is pointing to unknown location

    RDX=0x00000000000d4753
    0x00000000000d4753 is pointing to unknown location

    RSP=0x00007f91df879ff0
    0x00007f91df879ff0 is pointing to unknown location

    RBP=0x00007f91dfa22ef0
    0x00007f91dfa22ef0 is pointing into the stack for thread: 0x0000000002758000
    "New I/O server worker #1-4" prio=10 tid=0x0000000002758000 nid=0x63e runnable [0x00007f91dfa22000]
       java.lang.Thread.State: RUNNABLE

    RSI=0x00007f91df879ff0
    0x00007f91df879ff0 is pointing to unknown location

    RDI=0x0000000000055809
    0x0000000000055809 is pointing to unknown location

    R8 =0x000000000000000a
    0x000000000000000a is pointing to unknown location

    R9 =0x000000000000000a
    0x000000000000000a is pointing to unknown location

    R10=0x0000000000000065
    0x0000000000000065 is pointing to unknown location

    R11=0x000000000000006e
    0x000000000000006e is pointing to unknown location

    R12=0x0000000000000000
    0x0000000000000000 is pointing to unknown location

    R13=0x00000000c73069d0
    {method}
    - klass: {other class}

    R14=0x00007f91dfa22f88
    0x00007f91dfa22f88 is pointing into the stack for thread: 0x0000000002758000
    "New I/O server worker #1-4" prio=10 tid=0x0000000002758000 nid=0x63e runnable [0x00007f91dfa22000]
       java.lang.Thread.State: RUNNABLE

    R15=0x0000000002758000
    "New I/O server worker #1-4" prio=10 tid=0x0000000002758000 nid=0x63e runnable [0x00007f91dfa22000]
       java.lang.Thread.State: RUNNABLE


    Top of Stack: (sp=0x00007f91df879ff0)
    0x00007f91df879ff0:   0065006e00650047 000a006c00610072
    0x00007f91df87a000:   006e0075006f0043 0020002000200074
    0x00007f91df87a010:   0020002000200020 0020002000200020
    0x00007f91df87a020:   0020002000200020 0020002000200020
    0x00007f91df87a030:   0020002000200020 0020002000200020
    0x00007f91df87a040:   00320020003a0020 0053000a00380037
    0x00007f91df87a050:   0061006500720074 0075006f0043006d
    0x00007f91df87a060:   002000200074006e 0020002000200020
    0x00007f91df87a070:   0020002000200020 0020002000200020
    0x00007f91df87a080:   0020002000200020 0020002000200020
    0x00007f91df87a090:   000a00310020003a 0065007200740053
    0x00007f91df87a0a0:   0069004b006d0061 002000200064006e
    0x00007f91df87a0b0:   0020002000200020 0020002000200020
    0x00007f91df87a0c0:   0020002000200020 0020002000200020
    0x00007f91df87a0d0:   0020002000200020 00470020003a0020
    0x00007f91df87a0e0:   00720065006e0065 0053000a006c0061
    0x00007f91df87a0f0:   0061006500720074 006e0069004b006d
    0x00007f91df87a100:   00740053002f0064 0067006e00690072
    0x00007f91df87a110:   0020002000200020 0020002000200020
    0x00007f91df87a120:   0020002000200020 0020002000200020
    0x00007f91df87a130:   006500470020003a 006100720065006e
    0x00007f91df87a140:   00740053000a006c 006d006100650072
    0x00007f91df87a150:   0064006e0069004b 0020002000440049
    0x00007f91df87a160:   0020002000200020 0020002000200020
    0x00007f91df87a170:   0020002000200020 0020002000200020
    0x00007f91df87a180:   003a002000200020 0041000a00300020
    0x00007f91df87a190:   006f006900640075 006e0075006f0043
    0x00007f91df87a1a0:   0020002000200074 0020002000200020
    0x00007f91df87a1b0:   0020002000200020 0020002000200020
    0x00007f91df87a1c0:   0020002000200020 0020002000200020
    0x00007f91df87a1d0:   000a00310020003a 0069006400750041
    0x00007f91df87a1e0:   006f0046005f006f 00740061006d0072

    Instructions: (pc=0x00007f91e171abd6)
    0x00007f91e171abc6:   83 e6 f0 85 d2 7e 14 31 ff 31 c9 8b 04 8b ff c7
    0x00007f91e171abd6:   66 89 04 4e 48 ff c1 39 fa 75 f0 48 8b 4d d8 48

    Stack: [0x00007f91df925000,0x00007f91dfa26000],  sp=0x00007f91df879ff0,  free space=18014398509481299k
    Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
    C  [jna8882993865954913672.tmp+0x6bd6]  newJavaString+0x1b6
    j  com.sun.jna.Pointer._getString(JZ)Ljava/lang/String;+0
    j  com.sun.jna.Pointer.getString(JZ)Ljava/lang/String;+7
    j  com.sun.jna.Function.invokeString(I[Ljava/lang/Object;Z)Ljava/lang/String;+24
    j  com.sun.jna.Function.invoke([Ljava/lang/Object;Ljava/lang/Class;Z)Ljava/lang/Object;+557
    j  com.sun.jna.Function.invoke(Ljava/lang/Class;[Ljava/lang/Object;Ljava/util/Map;)Ljava/lang/Object;+214
    j  com.sun.jna.Library$Handler.invoke(Ljava/lang/Object;Ljava/lang/reflect/Method;[Ljava/lang/Object;)Ljava/lang/Object;+341
    j  net.pms.dlna.$Proxy0.Inform(Lcom/sun/jna/Pointer;)Lcom/sun/jna/WString;+16
    j  net.pms.dlna.MediaInfo.Inform()Ljava/lang/String;+7
    j  net.pms.dlna.MediaInfoParser.parse(Lnet/pms/dlna/DLNAMediaInfo;Lnet/pms/dlna/InputFile;I)V+41
    j  net.pms.configuration.FormatConfiguration.parse(Lnet/pms/dlna/DLNAMediaInfo;Lnet/pms/dlna/InputFile;Lnet/pms/formats/Format;I)V+92
    j  net.pms.formats.Format.parse(Lnet/pms/dlna/DLNAMediaInfo;Lnet/pms/dlna/InputFile;ILnet/pms/configuration/RendererConfiguration;)V+22
    j  net.pms.dlna.RealFile.resolve()V+244
    j  net.pms.dlna.DLNAResource.run()V+8
    j  net.pms.dlna.RealFile.isValid()Z+108
    j  net.pms.dlna.DLNAResource.addChild(Lnet/pms/dlna/DLNAResource;)V+68
    j  net.pms.dlna.MapFile.manageFile(Ljava/io/File;)V+354
    j  net.pms.dlna.MapFile.analyzeChildren(I)Z+110
    j  net.pms.dlna.DLNAResource.discoverWithRenderer(Lnet/pms/configuration/RendererConfiguration;I)V+29
    j  net.pms.dlna.DLNAResource.getDLNAResources(Ljava/lang/String;ZIILnet/pms/configuration/RendererConfiguration;)Ljava/util/List;+58
    j  net.pms.network.RequestV2.answer(Lorg/jboss/netty/handler/codec/http/HttpResponse;Lorg/jboss/netty/channel/MessageEvent;ZLnet/pms/external/StartStopListenerDelegate;)Lorg/jboss/netty/channel/ChannelFuture;+2956
    j  net.pms.network.RequestHandlerV2.writeResponse(Lorg/jboss/netty/channel/MessageEvent;Lnet/pms/network/RequestV2;Ljava/net/InetAddress;)V+138
    j  net.pms.network.RequestHandlerV2.messageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/MessageEvent;)V+1517
    j  org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+13
    j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
    j  org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+22
    j  org.jboss.netty.handler.stream.ChunkedWriteHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+82
    j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
    j  org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+22
    j  org.jboss.netty.handler.codec.http.HttpChunkAggregator.messageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/MessageEvent;)V+155
    j  org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+13
    j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
    j  org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+22
    j  org.jboss.netty.channel.Channels.fireMessageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Ljava/lang/Object;Ljava/net/SocketAddress;)V+16
    j  org.jboss.netty.handler.codec.replay.ReplayingDecoder.unfoldAndfireMessageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Ljava/lang/Object;Ljava/net/SocketAddress;)V+114
    j  org.jboss.netty.handler.codec.replay.ReplayingDecoder.callDecode(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/Channel;Lorg/jboss/netty/buffer/ChannelBuffer;Ljava/net/SocketAddress;)V+178
    j  org.jboss.netty.handler.codec.replay.ReplayingDecoder.messageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/MessageEvent;)V+78
    j  org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+13
    j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
    j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+44
    j  org.jboss.netty.channel.Channels.fireMessageReceived(Lorg/jboss/netty/channel/Channel;Ljava/lang/Object;Ljava/net/SocketAddress;)V+16
    j  org.jboss.netty.channel.Channels.fireMessageReceived(Lorg/jboss/netty/channel/Channel;Ljava/lang/Object;)V+3
    j  org.jboss.netty.channel.socket.nio.NioWorker.read(Ljava/nio/channels/SelectionKey;)Z+178
    j  org.jboss.netty.channel.socket.nio.NioWorker.processSelectedKeys(Ljava/util/Set;)V+52
    j  org.jboss.netty.channel.socket.nio.NioWorker.run()V+93
    j  org.jboss.netty.util.ThreadRenamingRunnable.run()V+55
    j  org.jboss.netty.util.internal.DeadLockProofWorker$1.run()V+14
    j  java.util.concurrent.ThreadPoolExecutor.runWorker(Ljava/util/concurrent/ThreadPoolExecutor$Worker;)V+46
    j  java.util.concurrent.ThreadPoolExecutor$Worker.run()V+5
    j  java.lang.Thread.run()V+11
    v  ~StubRoutines::call_stub
    V  [libjvm.so+0x431958]
    V  [libjvm.so+0x4307f8]
    V  [libjvm.so+0x4313b3]
    V  [libjvm.so+0x4314d7]
    V  [libjvm.so+0x482b10]
    V  [libjvm.so+0x6e806b]
    V  [libjvm.so+0x5e42e2]

    Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
    j  com.sun.jna.Pointer._getString(JZ)Ljava/lang/String;+0
    j  com.sun.jna.Pointer.getString(JZ)Ljava/lang/String;+7
    j  com.sun.jna.Function.invokeString(I[Ljava/lang/Object;Z)Ljava/lang/String;+24
    j  com.sun.jna.Function.invoke([Ljava/lang/Object;Ljava/lang/Class;Z)Ljava/lang/Object;+557
    j  com.sun.jna.Function.invoke(Ljava/lang/Class;[Ljava/lang/Object;Ljava/util/Map;)Ljava/lang/Object;+214
    j  com.sun.jna.Library$Handler.invoke(Ljava/lang/Object;Ljava/lang/reflect/Method;[Ljava/lang/Object;)Ljava/lang/Object;+341
    j  net.pms.dlna.$Proxy0.Inform(Lcom/sun/jna/Pointer;)Lcom/sun/jna/WString;+16
    j  net.pms.dlna.MediaInfo.Inform()Ljava/lang/String;+7
    j  net.pms.dlna.MediaInfoParser.parse(Lnet/pms/dlna/DLNAMediaInfo;Lnet/pms/dlna/InputFile;I)V+41
    j  net.pms.configuration.FormatConfiguration.parse(Lnet/pms/dlna/DLNAMediaInfo;Lnet/pms/dlna/InputFile;Lnet/pms/formats/Format;I)V+92
    j  net.pms.formats.Format.parse(Lnet/pms/dlna/DLNAMediaInfo;Lnet/pms/dlna/InputFile;ILnet/pms/configuration/RendererConfiguration;)V+22
    j  net.pms.dlna.RealFile.resolve()V+244
    j  net.pms.dlna.DLNAResource.run()V+8
    j  net.pms.dlna.RealFile.isValid()Z+108
    j  net.pms.dlna.DLNAResource.addChild(Lnet/pms/dlna/DLNAResource;)V+68
    j  net.pms.dlna.MapFile.manageFile(Ljava/io/File;)V+354
    j  net.pms.dlna.MapFile.analyzeChildren(I)Z+110
    j  net.pms.dlna.DLNAResource.discoverWithRenderer(Lnet/pms/configuration/RendererConfiguration;I)V+29
    j  net.pms.dlna.DLNAResource.getDLNAResources(Ljava/lang/String;ZIILnet/pms/configuration/RendererConfiguration;)Ljava/util/List;+58
    j  net.pms.network.RequestV2.answer(Lorg/jboss/netty/handler/codec/http/HttpResponse;Lorg/jboss/netty/channel/MessageEvent;ZLnet/pms/external/StartStopListenerDelegate;)Lorg/jboss/netty/channel/ChannelFuture;+2956
    j  net.pms.network.RequestHandlerV2.writeResponse(Lorg/jboss/netty/channel/MessageEvent;Lnet/pms/network/RequestV2;Ljava/net/InetAddress;)V+138
    j  net.pms.network.RequestHandlerV2.messageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/MessageEvent;)V+1517
    j  org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+13
    j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
    j  org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+22
    j  org.jboss.netty.handler.stream.ChunkedWriteHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+82
    j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
    j  org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+22
    j  org.jboss.netty.handler.codec.http.HttpChunkAggregator.messageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/MessageEvent;)V+155
    j  org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+13
    j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
    j  org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+22
    j  org.jboss.netty.channel.Channels.fireMessageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Ljava/lang/Object;Ljava/net/SocketAddress;)V+16
    j  org.jboss.netty.handler.codec.replay.ReplayingDecoder.unfoldAndfireMessageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Ljava/lang/Object;Ljava/net/SocketAddress;)V+114
    j  org.jboss.netty.handler.codec.replay.ReplayingDecoder.callDecode(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/Channel;Lorg/jboss/netty/buffer/ChannelBuffer;Ljava/net/SocketAddress;)V+178
    j  org.jboss.netty.handler.codec.replay.ReplayingDecoder.messageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/MessageEvent;)V+78
    j  org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+13
    j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
    j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+44
    j  org.jboss.netty.channel.Channels.fireMessageReceived(Lorg/jboss/netty/channel/Channel;Ljava/lang/Object;Ljava/net/SocketAddress;)V+16
    j  org.jboss.netty.channel.Channels.fireMessageReceived(Lorg/jboss/netty/channel/Channel;Ljava/lang/Object;)V+3
    j  org.jboss.netty.channel.socket.nio.NioWorker.read(Ljava/nio/channels/SelectionKey;)Z+178
    j  org.jboss.netty.channel.socket.nio.NioWorker.processSelectedKeys(Ljava/util/Set;)V+52
    j  org.jboss.netty.channel.socket.nio.NioWorker.run()V+93
    j  org.jboss.netty.util.ThreadRenamingRunnable.run()V+55
    j  org.jboss.netty.util.internal.DeadLockProofWorker$1.run()V+14
    j  java.util.concurrent.ThreadPoolExecutor.runWorker(Ljava/util/concurrent/ThreadPoolExecutor$Worker;)V+46
    j  java.util.concurrent.ThreadPoolExecutor$Worker.run()V+5
    j  java.lang.Thread.run()V+11
    v  ~StubRoutines::call_stub

    ---------------  P R O C E S S  ---------------

    Java Threads: ( => current thread )
      0x0000000001e69000 JavaThread "DestroyJavaVM" [_thread_blocked, id=1560, stack(0x00007f91efb18000,0x00007f91efc19000)]
      0x00000000020a8800 JavaThread "Thread-15" [_thread_in_native, id=1600, stack(0x00007f91e2378000,0x00007f91e2479000)]
      0x00000000020a7800 JavaThread "Thread-14" [_thread_blocked, id=1599, stack(0x00007f91e192b000,0x00007f91e1a2c000)]
    =>0x0000000002758000 JavaThread "New I/O server worker #1-4" [_thread_in_native, id=1598, stack(0x00007f91df925000,0x00007f91dfa26000)]
      0x00000000025c8800 JavaThread "New I/O server worker #1-2" [_thread_in_native, id=1597, stack(0x00007f91dfa26000,0x00007f91dfb27000)]
      0x0000000002227000 JavaThread "New I/O server worker #1-1" [_thread_in_native, id=1596, stack(0x00007f91dfb27000,0x00007f91dfc28000)]
      0x000000000268a000 JavaThread "pool-3-thread-1" [_thread_blocked, id=1595, stack(0x00007f91e044d000,0x00007f91e054e000)]
      0x0000000001f9d000 JavaThread "New I/O server worker #1-3" [_thread_in_native, id=1594, stack(0x00007f91e054e000,0x00007f91e064f000)]
      0x0000000002186800 JavaThread "H2 Log Writer MEDIAS" daemon [_thread_blocked, id=1593, stack(0x00007f91e0750000,0x00007f91e0851000)]
      0x000000000201c800 JavaThread "H2 File Lock Watchdog /var/lib/pms-linux/database-ffixcollector/medias.lock.db" daemon [_thread_blocked, id=1592, stack(0x00007f91e0851000,0x00007f91e0952000)]
      0x0000000002595000 JavaThread "New I/O server boss #1 ([id: 0x53371566, /192.168.1.250:5001])" [_thread_in_native, id=1589, stack(0x00007f91e0952000,0x00007f91e0a53000)]
      0x0000000001f64800 JavaThread "Thread-4" daemon [_thread_blocked, id=1583, stack(0x00007f91e182a000,0x00007f91e192b000)]
      0x00007f91e42d6800 JavaThread "TimerQueue" daemon [_thread_blocked, id=1580, stack(0x00007f91e1a2c000,0x00007f91e1b2d000)]
      0x00007f91e41bf000 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=1579, stack(0x00007f91e2176000,0x00007f91e2277000)]
      0x00007f91e41da000 JavaThread "AWT-Shutdown" [_thread_blocked, id=1578, stack(0x00007f91e2277000,0x00007f91e2378000)]
      0x00007f91e417e000 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=1572, stack(0x00007f91e2479000,0x00007f91e257a000)]
      0x00007f91e411b000 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=1571, stack(0x00007f91e80c1000,0x00007f91e81c2000)]
      0x00007f91e4001800 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=1569, stack(0x00007f91e8c8b000,0x00007f91e8d8c000)]
      0x0000000001f00800 JavaThread "CompilerThread1" daemon [_thread_blocked, id=1568, stack(0x00007f91e8d8c000,0x00007f91e8e8d000)]
      0x0000000001efd800 JavaThread "CompilerThread0" daemon [_thread_blocked, id=1567, stack(0x00007f91e8e8d000,0x00007f91e8f8e000)]
      0x0000000001efc000 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=1566, stack(0x00007f91e8f8e000,0x00007f91e908f000)]
      0x0000000001edc000 JavaThread "Finalizer" daemon [_thread_blocked, id=1565, stack(0x00007f91e90ce000,0x00007f91e91cf000)]
      0x0000000001ed4800 JavaThread "Reference Handler" daemon [_thread_blocked, id=1564, stack(0x00007f91e91cf000,0x00007f91e92d0000)]

    Other Threads:
      0x0000000001ecd800 VMThread [stack: 0x00007f91e92d0000,0x00007f91e93d1000] [id=1563]
      0x00007f91e4004000 WatcherThread [stack: 0x00007f91e8b8a000,0x00007f91e8c8b000] [id=1570]

    VM state:not at safepoint (normal execution)

    VM Mutex/Monitor currently owned by a thread: None

    Heap
    PSYoungGen      total 27904K, used 11610K [0x00000000f0000000, 0x00000000f1f20000, 0x0000000100000000)
      eden space 23936K, 31% used [0x00000000f0000000,0x00000000f077a150,0x00000000f1760000)
      from space 3968K, 99% used [0x00000000f1b40000,0x00000000f1f1ca98,0x00000000f1f20000)
      to   space 3968K, 0% used [0x00000000f1760000,0x00000000f1760000,0x00000000f1b40000)
    PSOldGen        total 63872K, used 2531K [0x00000000d0000000, 0x00000000d3e60000, 0x00000000f0000000)
      object space 63872K, 3% used [0x00000000d0000000,0x00000000d0278d68,0x00000000d3e60000)
    PSPermGen       total 32576K, used 32407K [0x00000000c5a00000, 0x00000000c79d0000, 0x00000000d0000000)
      object space 32576K, 99% used [0x00000000c5a00000,0x00000000c79a5f50,0x00000000c79d0000)

    Dynamic libraries:
    00400000-00409000 r-xp 00000000 fb:00 31458211                           /usr/lib/jvm/java-6-openjdk/jre/bin/java
    00608000-00609000 r--p 00008000 fb:00 31458211                           /usr/lib/jvm/java-6-openjdk/jre/bin/java
    00609000-0060a000 rw-p 00009000 fb:00 31458211                           /usr/lib/jvm/java-6-openjdk/jre/bin/java
    01e60000-02a4e000 rw-p 00000000 00:00 0                                  [heap]
    c5a00000-c79d0000 rw-p 00000000 00:00 0
    c79d0000-d0000000 rw-p 00000000 00:00 0
    d0000000-d3e60000 rw-p 00000000 00:00 0
    d3e60000-f0000000 rw-p 00000000 00:00 0
    f0000000-f1f20000 rw-p 00000000 00:00 0
    f1f20000-100000000 rw-p 00000000 00:00 0
    7f91de681000-7f91df121000 rw-p 00000000 00:00 0
    7f91df521000-7f91df524000 ---p 00000000 00:00 0
    7f91df524000-7f91df622000 rw-p 00000000 00:00 0
    7f91df622000-7f91df625000 ---p 00000000 00:00 0
    7f91df625000-7f91df723000 rw-p 00000000 00:00 0
    7f91df723000-7f91df726000 ---p 00000000 00:00 0
    7f91df726000-7f91df824000 rw-p 00000000 00:00 0
    7f91df824000-7f91df827000 ---p 00000000 00:00 0
    7f91df827000-7f91df926000 rw-p 00000000 00:00 0
    7f91df926000-7f91df928000 ---p 00000000 00:00 0
    7f91df928000-7f91dfa26000 rw-p 00000000 00:00 0
    7f91dfa26000-7f91dfa29000 ---p 00000000 00:00 0
    7f91dfa29000-7f91dfb27000 rw-p 00000000 00:00 0
    7f91dfb27000-7f91dfb2a000 ---p 00000000 00:00 0
    7f91dfb2a000-7f91dfc28000 rw-p 00000000 00:00 0
    7f91dfc28000-7f91dfc2a000 r-xp 00000000 fb:00 54136331                   /lib/libnss_mdns4.so.2
    7f91dfc2a000-7f91dfe29000 ---p 00002000 fb:00 54136331                   /lib/libnss_mdns4.so.2
    7f91dfe29000-7f91dfe2a000 r--p 00001000 fb:00 54136331                   /lib/libnss_mdns4.so.2
    7f91dfe2a000-7f91dfe2b000 rw-p 00002000 fb:00 54136331                   /lib/libnss_mdns4.so.2
    7f91dfe2b000-7f91dfe41000 r-xp 00000000 fb:00 54132768                   /lib/libresolv-2.11.1.so
    7f91dfe41000-7f91e0040000 ---p 00016000 fb:00 54132768                   /lib/libresolv-2.11.1.so
    7f91e0040000-7f91e0041000 r--p 00015000 fb:00 54132768                   /lib/libresolv-2.11.1.so
    7f91e0041000-7f91e0042000 rw-p 00016000 fb:00 54132768                   /lib/libresolv-2.11.1.so
    7f91e0042000-7f91e0044000 rw-p 00000000 00:00 0
    7f91e0044000-7f91e0049000 r-xp 00000000 fb:00 54132761                   /lib/libnss_dns-2.11.1.so
    7f91e0049000-7f91e0248000 ---p 00005000 fb:00 54132761                   /lib/libnss_dns-2.11.1.so
    7f91e0248000-7f91e0249000 r--p 00004000 fb:00 54132761                   /lib/libnss_dns-2.11.1.so
    7f91e0249000-7f91e024a000 rw-p 00005000 fb:00 54132761                   /lib/libnss_dns-2.11.1.so
    7f91e024a000-7f91e024c000 r-xp 00000000 fb:00 54136332                   /lib/libnss_mdns4_minimal.so.2
    7f91e024c000-7f91e044b000 ---p 00002000 fb:00 54136332                   /lib/libnss_mdns4_minimal.so.2
    7f91e044b000-7f91e044c000 r--p 00001000 fb:00 54136332                   /lib/libnss_mdns4_minimal.so.2
    7f91e044c000-7f91e044d000 rw-p 00002000 fb:00 54136332                   /lib/libnss_mdns4_minimal.so.2
    7f91e044d000-7f91e0450000 ---p 00000000 00:00 0
    7f91e0450000-7f91e054e000 rw-p 00000000 00:00 0
    7f91e054e000-7f91e0551000 ---p 00000000 00:00 0
    7f91e0551000-7f91e064f000 rw-p 00000000 00:00 0
    7f91e064f000-7f91e0652000 ---p 00000000 00:00 0
    7f91e0652000-7f91e0750000 rw-p 00000000 00:00 0
    7f91e0750000-7f91e0753000 ---p 00000000 00:00 0
    7f91e0753000-7f91e0851000 rw-p 00000000 00:00 0
    7f91e0851000-7f91e0854000 ---p 00000000 00:00 0
    7f91e0854000-7f91e0952000 rw-p 00000000 00:00 0
    7f91e0952000-7f91e0955000 ---p 00000000 00:00 0
    7f91e0955000-7f91e0a53000 rw-p 00000000 00:00 0
    7f91e0a53000-7f91e0a54000 r--p 00000000 fb:00 30674074                   /usr/lib/locale/en_US.utf8/LC_NUMERIC
    7f91e0a54000-7f91e0a55000 r--p 00000000 fb:00 30674075                   /usr/lib/locale/en_US.utf8/LC_TIME
    7f91e0a55000-7f91e0b73000 r--p 00000000 fb:00 30674076                   /usr/lib/locale/en_US.utf8/LC_COLLATE
    7f91e0b73000-7f91e0f99000 r-xp 00000000 fb:00 30543397                   /usr/lib/libmediainfo.so.0.0.0
    7f91e0f99000-7f91e1198000 ---p 00426000 fb:00 30543397                   /usr/lib/libmediainfo.so.0.0.0
    7f91e1198000-7f91e11a2000 r--p 00425000 fb:00 30543397                   /usr/lib/libmediainfo.so.0.0.0
    7f91e11a2000-7f91e11a9000 rw-p 0042f000 fb:00 30543397                   /usr/lib/libmediainfo.so.0.0.0
    7f91e11a9000-7f91e11aa000 rw-p 00000000 00:00 0
    7f91e11aa000-7f91e12a0000 r-xp 00000000 fb:00 30541325                   /usr/lib/libstdc++.so.6.0.13
    7f91e12a0000-7f91e14a0000 ---p 000f6000 fb:00 30541325                   /usr/lib/libstdc++.so.6.0.13
    7f91e14a0000-7f91e14a7000 r--p 000f6000 fb:00 30541325                   /usr/lib/libstdc++.so.6.0.13
    7f91e14a7000-7f91e14a9000 rw-p 000fd000 fb:00 30541325                   /usr/lib/libstdc++.so.6.0.13
    7f91e14a9000-7f91e14be000 rw-p 00000000 00:00 0
    7f91e14be000-7f91e1512000 r-xp 00000000 fb:00 30543395                   /usr/lib/libzen.so.0.0.0
    7f91e1512000-7f91e1712000 ---p 00054000 fb:00 30543395                   /usr/lib/libzen.so.0.0.0
    7f91e1712000-7f91e1713000 r--p 00054000 fb:00 30543395                   /usr/lib/libzen.so.0.0.0
    7f91e1713000-7f91e1714000 rw-p 00055000 fb:00 30543395                   /usr/lib/libzen.so.0.0.0
    7f91e1714000-7f91e1729000 r-xp 00000000 fb:00 1048596                    /tmp/jna8882993865954913672.tmp
    7f91e1729000-7f91e1828000 ---p 00015000 fb:00 1048596                    /tmp/jna8882993865954913672.tmp
    7f91e1828000-7f91e182a000 rw-p 00014000 fb:00 1048596                    /tmp/jna8882993865954913672.tmp
    7f91e182a000-7f91e182d000 ---p 00000000 00:00 0
    7f91e182d000-7f91e192b000 rw-p 00000000 00:00 0
    7f91e192b000-7f91e192e000 ---p 00000000 00:00 0
    7f91e192e000-7f91e1a2c000 rw-p 00000000 00:00 0
    7f91e1a2c000-7f91e1a2f000 ---p 00000000 00:00 0
    7f91e1a2f000-7f91e1b2d000 rw-p 00000000 00:00 0
    7f91e1b2d000-7f91e1b35000 r-xp 00000000 fb:00 31458156                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
    7f91e1b35000-7f91e1d34000 ---p 00008000 fb:00 31458156                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
    7f91e1d34000-7f91e1d35000 r--p 00007000 fb:00 31458156                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
    7f91e1d35000-7f91e1d36000 rw-p 00008000 fb:00 31458156                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
    7f91e1d36000-7f91e1d40000 r-xp 00000000 fb:00 31458142                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjpeg.so
    7f91e1d40000-7f91e1f3f000 ---p 0000a000 fb:00 31458142                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjpeg.so
    7f91e1f3f000-7f91e1f40000 r--p 00009000 fb:00 31458142                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjpeg.so
    7f91e1f40000-7f91e1f41000 rw-p 0000a000 fb:00 31458142                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjpeg.so
    7f91e1f41000-7f91e1f73000 r-xp 00000000 fb:00 31458147                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/liblcms.so
    7f91e1f73000-7f91e2172000 ---p 00032000 fb:00 31458147                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/liblcms.so
    7f91e2172000-7f91e2173000 r--p 00031000 fb:00 31458147                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/liblcms.so
    7f91e2173000-7f91e2174000 rw-p 00032000 fb:00 31458147                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/liblcms.so
    7f91e2174000-7f91e2176000 rw-p 00000000 00:00 0
    7f91e2176000-7f91e2179000 ---p 00000000 00:00 0
    7f91e2179000-7f91e2277000 rw-p 00000000 00:00 0
    7f91e2277000-7f91e227a000 ---p 00000000 00:00 0
    7f91e227a000-7f91e2378000 rw-p 00000000 00:00 0
    7f91e2378000-7f91e237b000 ---p 00000000 00:00 0
    7f91e237b000-7f91e2479000 rw-p 00000000 00:00 0
    7f91e2479000-7f91e247c000 ---p 00000000 00:00 0
    7f91e247c000-7f91e257a000 rw-p 00000000 00:00 0
    7f91e257a000-7f91e257f000 r-xp 00000000 fb:00 30549937                   /usr/lib/libXfixes.so.3.1.0
    7f91e257f000-7f91e277e000 ---p 00005000 fb:00 30549937                   /usr/lib/libXfixes.so.3.1.0
    7f91e277e000-7f91e277f000 r--p 00004000 fb:00 30549937                   /usr/lib/libXfixes.so.3.1.0
    7f91e277f000-7f91e2780000 rw-p 00005000 fb:00 30549937                   /usr/lib/libXfixes.so.3.1.0
    7f91e2780000-7f91e2789000 r-xp 00000000 fb:00 30549941                   /usr/lib/libXcursor.so.1.0.2
    7f91e2789000-7f91e2988000 ---p 00009000 fb:00 30549941                   /usr/lib/libXcursor.so.1.0.2
    7f91e2988000-7f91e2989000 r--p 00008000 fb:00 30549941                   /usr/lib/libXcursor.so.1.0.2
    7f91e2989000-7f91e298a000 rw-p 00009000 fb:00 30549941                   /usr/lib/libXcursor.so.1.0.2
    7f91e298a000-7f91e29a0000 r-xp 00000000 fb:00 54132791                   /lib/libgcc_s.so.1
    7f91e29a0000-7f91e2b9f000 ---p 00016000 fb:00 54132791                   /lib/libgcc_s.so.1
    7f91e2b9f000-7f91e2ba0000 r--p 00015000 fb:00 54132791                   /lib/libgcc_s.so.1
    7f91e2ba0000-7f91e2ba1000 rw-p 00016000 fb:00 54132791                   /lib/libgcc_s.so.1
    7f91e2ba1000-7f91e2c21000 r-xp 00000000 fb:00 30539975                   /usr/lib/libfreetype.so.6.3.22
    7f91e2c21000-7f91e2e21000 ---p 00080000 fb:00 30539975                   /usr/lib/libfreetype.so.6.3.22
    7f91e2e21000-7f91e2e26000 r--p 00080000 fb:00 30539975                   /usr/lib/libfreetype.so.6.3.22
    7f91e2e26000-7f91e2e27000 rw-p 00085000 fb:00 30539975                   /usr/lib/libfreetype.so.6.3.22
    7f91e2e27000-7f91e2e6e000 r-xp 00000000 fb:00 31458113                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libfontmanager.so
    7f91e2e6e000-7f91e306d000 ---p 00047000 fb:00 31458113                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libfontmanager.so
    7f91e306d000-7f91e3070000 r--p 00046000 fb:00 31458113                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libfontmanager.so
    7f91e3070000-7f91e3071000 rw-p 00049000 fb:00 31458113                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libfontmanager.so
    7f91e3071000-7f91e3083000 rw-p 00000000 00:00 0
    7f91e3083000-7f91e3088000 r-xp 00000000 fb:00 30547937                   /usr/lib/libXdmcp.so.6.0.0
    7f91e3088000-7f91e3287000 ---p 00005000 fb:00 30547937                   /usr/lib/libXdmcp.so.6.0.0
    7f91e3287000-7f91e3288000 r--p 00004000 fb:00 30547937                   /usr/lib/libXdmcp.so.6.0.0
    7f91e3288000-7f91e3289000 rw-p 00005000 fb:00 30547937                   /usr/lib/libXdmcp.so.6.0.0
    7f91e3289000-7f91e328b000 r-xp 00000000 fb:00 30547935                   /usr/lib/libXau.so.6.0.0
    7f91e328b000-7f91e348b000 ---p 00002000 fb:00 30547935                   /usr/lib/libXau.so.6.0.0
    7f91e348b000-7f91e348c000 r--p 00002000 fb:00 30547935                   /usr/lib/libXau.so.6.0.0
    7f91e348c000-7f91e348d000 rw-p 00003000 fb:00 30547935                   /usr/lib/libXau.so.6.0.0
    7f91e348d000-7f91e34a8000 r-xp 00000000 fb:00 30547939                   /usr/lib/libxcb.so.1.1.0
    7f91e34a8000-7f91e36a7000 ---p 0001b000 fb:00 30547939                   /usr/lib/libxcb.so.1.1.0
    7f91e36a7000-7f91e36a8000 r--p 0001a000 fb:00 30547939                   /usr/lib/libxcb.so.1.1.0
    7f91e36a8000-7f91e36a9000 rw-p 0001b000 fb:00 30547939                   /usr/lib/libxcb.so.1.1.0
    7f91e36a9000-7f91e36b8000 r-xp 00000000 fb:00 30549283                   /usr/lib/libXi.so.6.1.0
    7f91e36b8000-7f91e38b7000 ---p 0000f000 fb:00 30549283                   /usr/lib/libXi.so.6.1.0
    7f91e38b7000-7f91e38b8000 r--p 0000e000 fb:00 30549283                   /usr/lib/libXi.so.6.1.0
    7f91e38b8000-7f91e38b9000 rw-p 0000f000 fb:00 30549283                   /usr/lib/libXi.so.6.1.0
    7f91e38b9000-7f91e38be000 r-xp 00000000 fb:00 30549285                   /usr/lib/libXtst.so.6.1.0
    7f91e38be000-7f91e3abe000 ---p 00005000 fb:00 30549285                   /usr/lib/libXtst.so.6.1.0
    7f91e3abe000-7f91e3abf000 r--p 00005000 fb:00 30549285                   /usr/lib/libXtst.so.6.1.0
    7f91e3abf000-7f91e3ac0000 rw-p 00006000 fb:00 30549285                   /usr/lib/libXtst.so.6.1.0
    7f91e3ac0000-7f91e3ac9000 r-xp 00000000 fb:00 30549873                   /usr/lib/libXrender.so.1.3.0
    7f91e3ac9000-7f91e3cc8000 ---p 00009000 fb:00 30549873                   /usr/lib/libXrender.so.1.3.0
    7f91e3cc8000-7f91e3cc9000 r--p 00008000 fb:00 30549873                   /usr/lib/libXrender.so.1.3.0
    7f91e3cc9000-7f91e3cca000 rw-p 00009000 fb:00 30549873                   /usr/lib/libXrender.so.1.3.0
    7f91e3cca000-7f91e3dfb000 r-xp 00000000 fb:00 30547941                   /usr/lib/libX11.so.6.3.0
    7f91e3dfb000-7f91e3ffb000 ---p 00131000 fb:00 30547941                   /usr/lib/libX11.so.6.3.0
    7f91e3ffb000-7f91e3ffc000 r--p 00131000 fb:00 30547941                   /usr/lib/libX11.so.6.3.0
    7f91e3ffc000-7f91e4000000 rw-p 00132000 fb:00 30547941                   /usr/lib/libX11.so.6.3.0
    7f91e4000000-7f91e4c4a000 rw-p 00000000 00:00 0
    7f91e4c4a000-7f91e8000000 ---p 00000000 00:00 0
    7f91e8091000-7f91e8092000 r--p 00000000 fb:00 30674077                   /usr/lib/locale/en_US.utf8/LC_MONETARY
    7f91e8092000-7f91e8093000 r--p 00000000 fb:00 30674079                   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
    7f91e8093000-7f91e8094000 r--p 00000000 fb:00 30674080                   /usr/lib/locale/en_US.utf8/LC_PAPER
    7f91e8094000-7f91e8095000 r--p 00000000 fb:00 30674081                   /usr/lib/locale/en_US.utf8/LC_NAME
    7f91e8095000-7f91e8096000 r--p 00000000 fb:00 30674082                   /usr/lib/locale/en_US.utf8/LC_ADDRESS
    7f91e8096000-7f91e809c000 r--s 000fc000 fb:00 31195221                   /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
    7f91e809c000-7f91e80a5000 r--s 00000000 fb:00 12455197                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
    7f91e80a5000-7f91e80ae000 r--s 00000000 fb:00 12457339                   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le64.cache-3
    7f91e80ae000-7f91e80b8000 r--s 00000000 fb:00 12455185                   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le64.cache-3
    7f91e80b8000-7f91e80c1000 r--s 00000000 fb:00 12455197                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
    7f91e80c1000-7f91e80c4000 ---p 00000000 00:00 0
    7f91e80c4000-7f91e81c2000 rw-p 00000000 00:00 0
    7f91e81c2000-7f91e81d3000 r-xp 00000000 fb:00 30548670                   /usr/lib/libXext.so.6.4.0
    7f91e81d3000-7f91e83d2000 ---p 00011000 fb:00 30548670                   /usr/lib/libXext.so.6.4.0
    7f91e83d2000-7f91e83d3000 r--p 00010000 fb:00 30548670                   /usr/lib/libXext.so.6.4.0
    7f91e83d3000-7f91e83d4000 rw-p 00011000 fb:00 30548670                   /usr/lib/libXext.so.6.4.0
    7f91e83d4000-7f91e8420000 r-xp 00000000 fb:00 31458364                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
    7f91e8420000-7f91e8620000 ---p 0004c000 fb:00 31458364                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
    7f91e8620000-7f91e8621000 r--p 0004c000 fb:00 31458364                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
    7f91e8621000-7f91e8624000 rw-p 0004d000 fb:00 31458364                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
    7f91e8624000-7f91e8625000 rw-p 00000000 00:00 0
    7f91e8625000-7f91e86c7000 r-xp 00000000 fb:00 31458110                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libawt.so
    7f91e86c7000-7f91e88c7000 ---p 000a2000 fb:00 31458110                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libawt.so
    7f91e88c7000-7f91e88c8000 r--p 000a2000 fb:00 31458110                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libawt.so
    7f91e88c8000-7f91e88d3000 rw-p 000a3000 fb:00 31458110                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libawt.so
    7f91e88d3000-7f91e88f8000 rw-p 00000000 00:00 0
    7f91e88f8000-7f91e890d000 r-xp 00000000 fb:00 31458154                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
    7f91e890d000-7f91e8b0c000 ---p 00015000 fb:00 31458154                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
    7f91e8b0c000-7f91e8b0d000 r--p 00014000 fb:00 31458154                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
    7f91e8b0d000-7f91e8b0e000 rw-p 00015000 fb:00 31458154                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
    7f91e8b0e000-7f91e8b8a000 r--s 013de000 fb:00 32374825                   /usr/share/pms-linux/pms.jar
    7f91e8b8a000-7f91e8b8b000 ---p 00000000 00:00 0
    7f91e8b8b000-7f91e8c8b000 rw-p 00000000 00:00 0
    7f91e8c8b000-7f91e8c8e000 ---p 00000000 00:00 0
    7f91e8c8e000-7f91e8d8c000 rw-p 00000000 00:00 0
    7f91e8d8c000-7f91e8d8f000 ---p 00000000 00:00 0
    7f91e8d8f000-7f91e8e8d000 rw-p 00000000 00:00 0
    7f91e8e8d000-7f91e8e90000 ---p 00000000 00:00 0
    7f91e8e90000-7f91e8f8e000 rw-p 00000000 00:00 0
    7f91e8f8e000-7f91e8f91000 ---p 00000000 00:00 0
    7f91e8f91000-7f91e908f000 rw-p 00000000 00:00 0
    7f91e908f000-7f91e90ce000 r--p 00000000 fb:00 30674073                   /usr/lib/locale/en_US.utf8/LC_CTYPE
    7f91e90ce000-7f91e90d1000 ---p 00000000 00:00 0
    7f91e90d1000-7f91e91cf000 rw-p 00000000 00:00 0
    7f91e91cf000-7f91e91d2000 ---p 00000000 00:00 0
    7f91e91d2000-7f91e92d0000 rw-p 00000000 00:00 0
    7f91e92d0000-7f91e92d1000 ---p 00000000 00:00 0
    7f91e92d1000-7f91e96d4000 rw-p 00000000 00:00 0
    7f91e96d4000-7f91e96d6000 r--s 0001d000 fb:00 31195189                   /usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar
    7f91e96d6000-7f91e96db000 r--s 00045000 fb:00 31195193                   /usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar
    7f91e96db000-7f91e970e000 rw-p 00000000 00:00 0
    7f91e970e000-7f91e989d000 r--s 038c4000 fb:00 31195290                   /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
    7f91e989d000-7f91e98c5000 rw-p 00000000 00:00 0
    7f91e98c5000-7f91e98c6000 ---p 00000000 00:00 0
    7f91e98c6000-7f91e99c6000 rw-p 00000000 00:00 0
    7f91e99c6000-7f91e99c7000 ---p 00000000 00:00 0
    7f91e99c7000-7f91e9ad7000 rw-p 00000000 00:00 0
    7f91e9ad7000-7f91e9b1a000 rw-p 00000000 00:00 0
    7f91e9b1a000-7f91e9b3a000 rw-p 00000000 00:00 0
    7f91e9b3a000-7f91e9c1a000 rw-p 00000000 00:00 0
    7f91e9c1a000-7f91e9c2a000 rw-p 00000000 00:00 0
    7f91e9c2a000-7f91e9c6d000 rw-p 00000000 00:00 0
    7f91e9c6d000-7f91e9c8d000 rw-p 00000000 00:00 0
    7f91e9c8d000-7f91e9d6d000 rw-p 00000000 00:00 0
    7f91e9d6d000-7f91e9d7d000 rw-p 00000000 00:00 0
    7f91e9d7d000-7f91e9ded000 rw-p 00000000 00:00 0
    7f91e9ded000-7f91e9dee000 rw-p 00000000 00:00 0
    7f91e9dee000-7f91ea05e000 rwxp 00000000 00:00 0
    7f91ea05e000-7f91ecdee000 rw-p 00000000 00:00 0
    7f91ecdee000-7f91ecdf5000 r-xp 00000000 fb:00 31458169                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
    7f91ecdf5000-7f91ecff4000 ---p 00007000 fb:00 31458169                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
    7f91ecff4000-7f91ecff5000 r--p 00006000 fb:00 31458169                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
    7f91ecff5000-7f91ecff6000 rw-p 00007000 fb:00 31458169                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
    7f91ecff6000-7f91ed002000 r-xp 00000000 fb:00 54132762                   /lib/libnss_files-2.11.1.so
    7f91ed002000-7f91ed201000 ---p 0000c000 fb:00 54132762                   /lib/libnss_files-2.11.1.so
    7f91ed201000-7f91ed202000 r--p 0000b000 fb:00 54132762                   /lib/libnss_files-2.11.1.so
    7f91ed202000-7f91ed203000 rw-p 0000c000 fb:00 54132762                   /lib/libnss_files-2.11.1.so
    7f91ed203000-7f91ed20d000 r-xp 00000000 fb:00 54132764                   /lib/libnss_nis-2.11.1.so
    7f91ed20d000-7f91ed40c000 ---p 0000a000 fb:00 54132764                   /lib/libnss_nis-2.11.1.so
    7f91ed40c000-7f91ed40d000 r--p 00009000 fb:00 54132764                   /lib/libnss_nis-2.11.1.so
    7f91ed40d000-7f91ed40e000 rw-p 0000a000 fb:00 54132764                   /lib/libnss_nis-2.11.1.so
    7f91ed40e000-7f91ed416000 r-xp 00000000 fb:00 54132760                   /lib/libnss_compat-2.11.1.so
    7f91ed416000-7f91ed615000 ---p 00008000 fb:00 54132760                   /lib/libnss_compat-2.11.1.so
    7f91ed615000-7f91ed616000 r--p 00007000 fb:00 54132760                   /lib/libnss_compat-2.11.1.so
    7f91ed616000-7f91ed617000 rw-p 00008000 fb:00 54132760                   /lib/libnss_compat-2.11.1.so
    7f91ed617000-7f91ed61f000 r-xp 00000000 fb:00 31458170                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/native_threads/libhpi.so
    7f91ed61f000-7f91ed81e000 ---p 00008000 fb:00 31458170                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/native_threads/libhpi.so
    7f91ed81e000-7f91ed81f000 r--p 00007000 fb:00 31458170                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/native_threads/libhpi.so
    7f91ed81f000-7f91ed820000 rw-p 00008000 fb:00 31458170                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/native_threads/libhpi.so
    7f91ed820000-7f91ed837000 r-xp 00000000 fb:00 54132759                   /lib/libnsl-2.11.1.so
    7f91ed837000-7f91eda36000 ---p 00017000 fb:00 54132759                   /lib/libnsl-2.11.1.so
    7f91eda36000-7f91eda37000 r--p 00016000 fb:00 54132759                   /lib/libnsl-2.11.1.so
    7f91eda37000-7f91eda38000 rw-p 00017000 fb:00 54132759                   /lib/libnsl-2.11.1.so
    7f91eda38000-7f91eda3a000 rw-p 00000000 00:00 0
    7f91eda3a000-7f91eda67000 r-xp 00000000 fb:00 31458132                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
    7f91eda67000-7f91edc66000 ---p 0002d000 fb:00 31458132                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
    7f91edc66000-7f91edc67000 r--p 0002c000 fb:00 31458132                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
    7f91edc67000-7f91edc6a000 rw-p 0002d000 fb:00 31458132                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
    7f91edc6a000-7f91edc79000 r-xp 00000000 fb:00 31458167                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
    7f91edc79000-7f91ede78000 ---p 0000f000 fb:00 31458167                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
    7f91ede78000-7f91ede7a000 r--p 0000e000 fb:00 31458167                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
    7f91ede7a000-7f91ede7b000 rw-p 00010000 fb:00 31458167                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
    7f91ede7b000-7f91ede82000 r-xp 00000000 fb:00 54132769                   /lib/librt-2.11.1.so
    7f91ede82000-7f91ee081000 ---p 00007000 fb:00 54132769                   /lib/librt-2.11.1.so
    7f91ee081000-7f91ee082000 r--p 00006000 fb:00 54132769                   /lib/librt-2.11.1.so
    7f91ee082000-7f91ee083000 rw-p 00007000 fb:00 54132769                   /lib/librt-2.11.1.so
    7f91ee083000-7f91ee105000 r-xp 00000000 fb:00 54132757                   /lib/libm-2.11.1.so
    7f91ee105000-7f91ee304000 ---p 00082000 fb:00 54132757                   /lib/libm-2.11.1.so
    7f91ee304000-7f91ee305000 r--p 00081000 fb:00 54132757                   /lib/libm-2.11.1.so
    7f91ee305000-7f91ee306000 rw-p 00082000 fb:00 54132757                   /lib/libm-2.11.1.so
    7f91ee306000-7f91eeb8c000 r-xp 00000000 fb:00 31458171                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
    7f91eeb8c000-7f91eed8b000 ---p 00886000 fb:00 31458171                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
    7f91eed8b000-7f91eee01000 r--p 00885000 fb:00 31458171                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
    7f91eee01000-7f91eee1c000 rw-p 008fb000 fb:00 31458171                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
    7f91eee1c000-7f91eee55000 rw-p 00000000 00:00 0
    7f91eee55000-7f91eefcf000 r-xp 00000000 fb:00 54132753                   /lib/libc-2.11.1.so
    7f91eefcf000-7f91ef1ce000 ---p 0017a000 fb:00 54132753                   /lib/libc-2.11.1.so
    7f91ef1ce000-7f91ef1d2000 r--p 00179000 fb:00 54132753                   /lib/libc-2.11.1.so
    7f91ef1d2000-7f91ef1d3000 rw-p 0017d000 fb:00 54132753                   /lib/libc-2.11.1.so
    7f91ef1d3000-7f91ef1d8000 rw-p 00000000 00:00 0
    7f91ef1d8000-7f91ef1da000 r-xp 00000000 fb:00 54132756                   /lib/libdl-2.11.1.so
    7f91ef1da000-7f91ef3da000 ---p 00002000 fb:00 54132756                   /lib/libdl-2.11.1.so
    7f91ef3da000-7f91ef3db000 r--p 00002000 fb:00 54132756                   /lib/libdl-2.11.1.so
    7f91ef3db000-7f91ef3dc000 rw-p 00003000 fb:00 54132756                   /lib/libdl-2.11.1.so
    7f91ef3dc000-7f91ef3e0000 r-xp 00000000 fb:00 31458105                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
    7f91ef3e0000-7f91ef5df000 ---p 00004000 fb:00 31458105                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
    7f91ef5df000-7f91ef5e0000 r--p 00003000 fb:00 31458105                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
    7f91ef5e0000-7f91ef5e1000 rw-p 00004000 fb:00 31458105                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
    7f91ef5e1000-7f91ef5f9000 r-xp 00000000 fb:00 54132767                   /lib/libpthread-2.11.1.so
    7f91ef5f9000-7f91ef7f8000 ---p 00018000 fb:00 54132767                   /lib/libpthread-2.11.1.so
    7f91ef7f8000-7f91ef7f9000 r--p 00017000 fb:00 54132767                   /lib/libpthread-2.11.1.so
    7f91ef7f9000-7f91ef7fa000 rw-p 00018000 fb:00 54132767                   /lib/libpthread-2.11.1.so
    7f91ef7fa000-7f91ef7fe000 rw-p 00000000 00:00 0
    7f91ef7fe000-7f91ef814000 r-xp 00000000 fb:00 54132972                   /lib/libz.so.1.2.3.3
    7f91ef814000-7f91efa13000 ---p 00016000 fb:00 54132972                   /lib/libz.so.1.2.3.3
    7f91efa13000-7f91efa14000 r--p 00015000 fb:00 54132972                   /lib/libz.so.1.2.3.3
    7f91efa14000-7f91efa15000 rw-p 00016000 fb:00 54132972                   /lib/libz.so.1.2.3.3
    7f91efa15000-7f91efa35000 r-xp 00000000 fb:00 54132747                   /lib/ld-2.11.1.so
    7f91efa35000-7f91efa36000 r--p 00000000 fb:00 30674083                   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
    7f91efa36000-7f91efa37000 r--p 00000000 fb:00 30674084                   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
    7f91efa37000-7f91efa38000 r--p 00000000 fb:00 30674085                   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
    7f91efa38000-7f91efa39000 r--p 00000000 00:00 0
    7f91efa39000-7f91efa3c000 r--s 0007d000 fb:00 31195185                   /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
    7f91efa3c000-7f91efa45000 r--s 00000000 fb:00 12457339                   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le64.cache-3
    7f91efa45000-7f91efa4f000 r--s 00000000 fb:00 12455185                   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le64.cache-3
    7f91efa4f000-7f91efa58000 r--s 00065000 fb:00 31720907                   /usr/share/java/gnome-java-bridge.jar
    7f91efa58000-7f91efa62000 rw-p 00000000 00:00 0
    7f91efa62000-7f91efb18000 rw-p 00000000 00:00 0
    7f91efb18000-7f91efb1b000 ---p 00000000 00:00 0
    7f91efb1b000-7f91efc1e000 rw-p 00000000 00:00 0
    7f91efc1e000-7f91efc21000 r--s 0000f000 fb:00 31195213                   /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
    7f91efc21000-7f91efc28000 r--s 00000000 fb:00 30542398                   /usr/lib/gconv/gconv-modules.cache
    7f91efc28000-7f91efc30000 rw-s 00000000 fb:00 1048595                    /tmp/hsperfdata_ffixcollector/1558
    7f91efc30000-7f91efc31000 rw-p 00000000 00:00 0
    7f91efc31000-7f91efc32000 r--p 00000000 00:00 0
    7f91efc32000-7f91efc34000 rw-p 00000000 00:00 0
    7f91efc34000-7f91efc35000 r--p 0001f000 fb:00 54132747                   /lib/ld-2.11.1.so
    7f91efc35000-7f91efc36000 rw-p 00020000 fb:00 54132747                   /lib/ld-2.11.1.so
    7f91efc36000-7f91efc37000 rw-p 00000000 00:00 0
    7fff8abbe000-7fff8abd3000 rw-p 00000000 00:00 0                          [stack]
    7fff8abff000-7fff8ac00000 r-xp 00000000 00:00 0                          [vdso]
    ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]

    VM Arguments:
    jvm_args: -Xmx768M -Xss1024k -Dfile.encoding=UTF-8 -Djava.net.preferIPv4Stack=true
    java_command: net.pms.PMS
    Launcher Type: SUN_STANDARD

    Environment Variables:
    PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
    LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server:/usr/lib/jvm/java-6-openjdk/jre/lib/amd64:/usr/lib/jvm/java-6-openjdk/jre/../lib/amd64
    SHELL=/bin/bash
    DISPLAY=localhost:10.0

    Signal Handlers:
    SIGSEGV: [libjvm.so+0x7240c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
    SIGBUS: [libjvm.so+0x7240c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
    SIGFPE: [libjvm.so+0x5e08f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
    SIGPIPE: [libjvm.so+0x5e08f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
    SIGXFSZ: [libjvm.so+0x5e08f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
    SIGILL: [libjvm.so+0x5e08f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
    SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
    SIGUSR2: [libjvm.so+0x5e0000], sa_mask[0]=0x00000000, sa_flags=0x10000004
    SIGHUP: [libjvm.so+0x5e2a70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
    SIGINT: [libjvm.so+0x5e2a70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
    SIGTERM: [libjvm.so+0x5e2a70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
    SIGQUIT: [libjvm.so+0x5e2a70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


    ---------------  S Y S T E M  ---------------

    OS:Ubuntu 10.04 (lucid)
    uname:Linux 2.6.32-37-server #81-Ubuntu SMP Fri Dec 2 20:49:12 UTC 2011 x86_64
    libc:glibc 2.11.1 NPTL 2.11.1
    rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
    load average:0.22 0.32 0.18

    /proc/meminfo:
    MemTotal:        6126024 kB
    MemFree:         5415740 kB
    Buffers:           22736 kB
    Cached:           212224 kB
    SwapCached:            0 kB
    Active:           373732 kB
    Inactive:         168944 kB
    Active(anon):     308096 kB
    Inactive(anon):      644 kB
    Active(file):      65636 kB
    Inactive(file):   168300 kB
    Unevictable:           0 kB
    Mlocked:               0 kB
    SwapTotal:       2994168 kB
    SwapFree:        2994168 kB
    Dirty:                64 kB
    Writeback:             0 kB
    AnonPages:        308024 kB
    Mapped:            40420 kB
    Shmem:               864 kB
    Slab:              25604 kB
    SReclaimable:      11968 kB
    SUnreclaim:        13636 kB
    KernelStack:        2248 kB
    PageTables:         5768 kB
    NFS_Unstable:          0 kB
    Bounce:                0 kB
    WritebackTmp:          0 kB
    CommitLimit:     6057180 kB
    Committed_AS:    1335696 kB
    VmallocTotal:   34359738367 kB
    VmallocUsed:       27592 kB
    VmallocChunk:   34359707040 kB
    HardwareCorrupted:     0 kB
    HugePages_Total:       0
    HugePages_Free:        0
    HugePages_Rsvd:        0
    HugePages_Surp:        0
    Hugepagesize:       2048 kB
    DirectMap4k:        8064 kB
    DirectMap2M:     6283264 kB


    CPU:total 2 (1 cores per cpu, 1 threads per core) family 15 model 4 stepping 10, cmov, cx8, fxsr, mmx, sse, sse2, sse3

    Memory: 4k page, physical 6126024k(5415740k free), swap 2994168k(2994168k free)

    vm_info: OpenJDK 64-Bit Server VM (19.0-b09) for linux-amd64 JRE (1.6.0_20-b20), built on Nov  8 2011 18:27:16 by "buildd" with gcc 4.4.3

    time: Fri Jan  6 07:56:01 2012
    elapsed time: 40 seconds

```

If anyone can help me out, I would appreciate it.

---

### Post by ffixcollector on 2012-01-06
another message was,
```
n irrecoverable stack overflow has occurred.
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fb604c51bd6, pid=1445, tid=140419658548992
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK 64-Bit Server VM (19.0-b09 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea6 1.9.10
# Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.10-0ubuntu1~10.04.2
# Problematic frame:
# C  [jna5446313872804572983.tmp+0x6bd6]  newJavaString+0x1b6
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid1445.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

```

---

