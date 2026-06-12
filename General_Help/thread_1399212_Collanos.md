---
title: "Collanos"
date: 2010-02-05
forum: General Help
---

### Post by ventolt on 2010-02-05
Hello. I'm asked to use *Collanos* but it runs using Java and it is problematic as I know. The problem is that by default it has it's own Java interpretor or something which cause me to get such errors: ```
pijus@pijus-desktop:~/CollanosWorkplace$ sudo ./Workplace

(<unknown>:6007): GLib-WARNING **: g_set_prgname() called multiple times
[DEFAULT] WARN: [PlatformFactory] problems with platform org.apache.ojb.broker.platforms.PlatformDerbyImpl: org.apache.ojb.broker.platforms.PlatformDerbyImpl
[DEFAULT] WARN: [PlatformFactory] OJB will use PlatformDefaultImpl instead

P2P Transport Layer. (C) Collanos Software AG. All rights reserved.

Feb 5, 2010 5:04:35 PM net.jxta.platform.NetworkManager configure
INFO: Loading existing configuration. mode = EDGE
Feb 5, 2010 5:04:35 PM net.jxta.platform.NetworkManager startNetwork
INFO: Starting JXTA Network! MODE = EDGE,  HOME = file:/root/share/CollanosWorkplace/EFBFBDEFBFBDEFBFBDEFBFBD4246EFBFBDEFBFBDEFBFBD06EFBFBDEFBFBDEFBFBD36EFBFBDEFBFBD/Data/
Feb 5, 2010 5:04:35 PM net.jxta.impl.loader.RefJxtaLoader findModuleImplAdvertisement
WARNING: Failed to find class for urn:jxta:uuid-DEADBEEFDEAFBABAFEEDBABE0000000C0206
java.lang.ClassNotFoundException: No matching class for : urn:jxta:uuid-DEADBEEFDEAFBABAFEEDBABE0000000C0206
   at net.jxta.impl.loader.RefJxtaLoader.findClass(RefJxtaLoader.java:240)
   at net.jxta.impl.loader.RefJxtaLoader.findModuleImplAdvertisement(RefJxtaLoader.java:350)
   at net.jxta.impl.peergroup.StdPeerGroup.getDefaultModuleImplAdvertisement(StdPeerGroup.java:353)
   at net.jxta.impl.peergroup.StdPeerGroup.<clinit>(StdPeerGroup.java:143)
   at net.jxta.peergroup.WorldPeerGroupFactory.getDefaultWorldPeerGroupClass(WorldPeerGroupFactory.java:237)
   at net.jxta.peergroup.WorldPeerGroupFactory.<init>(WorldPeerGroupFactory.java:178)
   at net.jxta.peergroup.NetPeerGroupFactory.<init>(NetPeerGroupFactory.java:205)
   at net.jxta.platform.NetworkManager.startNetwork(NetworkManager.java:410)
   at com.collanos.p2ptl.config.TLConfigurator.configure(Unknown Source)
   at com.collanos.workplace.WorkplaceApplicationAdvisor.preStartup(Unknown Source)
   at org.eclipse.ui.internal.Workbench$27.runWithException(Workbench.java:1359)
   at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
   at org.eclipse.swt.widgets.Synchronizer.syncExec(Synchronizer.java:178)
   at org.eclipse.ui.internal.UISynchronizer.syncExec(UISynchronizer.java:150)
   at org.eclipse.swt.widgets.Display.syncExec(Display.java:4021)
   at org.eclipse.ui.internal.StartupThreading.runWithoutExceptions(StartupThreading.java:94)
   at org.eclipse.ui.internal.Workbench.init(Workbench.java:1356)
   at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2312)
   at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2198)
   at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:493)
   at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:288)
   at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:488)
   at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
   at com.collanos.workplace.WorkplaceApplication.start(Unknown Source)
   at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
   at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
   at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
   at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
   at java.lang.reflect.Method.invoke(Unknown Source)
   at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
   at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
   at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
   at org.eclipse.equinox.launcher.Main.main(Main.java:1212)
Feb 5, 2010 5:04:35 PM net.jxta.peergroup.WorldPeerGroupFactory newWorldPeerGroup
INFO: Making a new World Peer Group instance using : net.jxta.impl.peergroup.Platform
Feb 5, 2010 5:04:35 PM net.jxta.impl.cm.SrdiIndex clearSrdi
INFO: Clearing SRDI for null
Feb 5, 2010 5:04:35 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Always Access Service (net.jxta.impl.access.always.AlwaysAccessService)
Feb 5, 2010 5:04:35 PM net.jxta.impl.endpoint.tcp.IncomingUnicastServer openServerSocket
INFO: Server will accept connections at /0:0:0:0:0:0:0:0:9701
Feb 5, 2010 5:04:35 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the TCP Message Transport (net.jxta.impl.endpoint.tcp.TcpTransport)
Feb 5, 2010 5:04:35 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Rendezvous Service (net.jxta.impl.rendezvous.RendezVousServiceImpl)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Peerinfo Service (net.jxta.impl.peer.PeerInfoServiceImpl)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Endpoint service (net.jxta.impl.endpoint.EndpointServiceImpl)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the HTTP Message Transport (net.jxta.impl.endpoint.servlethttp.ServletHttpTransport)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : None Membership Service (net.jxta.impl.membership.none.NoneMembershipService)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Resolver service (net.jxta.impl.resolver.ResolverServiceImpl)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Discovery service (net.jxta.impl.discovery.DiscoveryServiceImpl)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the IP Multicast Message Transport (net.jxta.impl.endpoint.mcast.McastTransport)
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.tcp.TcpTransport startApp
WARNING: Stalled until there is an endpoint service
Feb 5, 2010 5:04:36 PM net.jxta.impl.rendezvous.RendezVousServiceImpl startApp
WARNING: Stalled until there is an endpoint service
Feb 5, 2010 5:04:36 PM net.jxta.impl.peer.PeerInfoServiceImpl startApp
WARNING: Stalled until there is a resolver service
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.EndpointServiceImpl startApp
INFO: Endpoint Service started.
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.servlethttp.HttpMessageSender start
INFO: HTTP Client Transport started.
Feb 5, 2010 5:04:36 PM net.jxta.impl.discovery.DiscoveryServiceImpl startApp
WARNING: Stalled until there is a rendezvous service
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.mcast.McastTransport startApp
INFO: IP Multicast Message Transport disabled.
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.tcp.TcpTransport$MessengerSelectorThread run
INFO: MessengerSelectorThread polling started
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.tcp.TcpTransport startApp
INFO: TCP Message Transport started.
Feb 5, 2010 5:04:36 PM net.jxta.impl.rendezvous.adhoc.AdhocPeerRdvService <init>
INFO: RendezVous Service is initialized for urn:jxta:jxta-WorldGroup as an ad hoc peer. 
Feb 5, 2010 5:04:36 PM net.jxta.impl.rendezvous.RendezVousServiceImpl startApp
INFO: Rendezvous Serivce started
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.tcp.IncomingUnicastServer run
INFO: Server is ready to accept connections
Feb 5, 2010 5:04:36 PM net.jxta.impl.discovery.DiscoveryServiceImpl beEdge
INFO: Switched to a Edge peer role.
Feb 5, 2010 5:04:36 PM net.jxta.impl.discovery.DiscoveryServiceImpl startApp
INFO: Discovery service started
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup getInterface
INFO: [urn:jxta:jxta-WorldGroup] GROUP REF COUNT INCREMENTED TO: 1 by
   net.jxta.peergroup.NetPeerGroupFactory.<init>(NetPeerGroupFactory.java:206)
Feb 5, 2010 5:04:36 PM net.jxta.peergroup.NetPeerGroupFactory newNetPeerGroup
INFO: Instantiating net peer group : urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202
   Parent : urn:jxta:jxta-WorldGroup "World PeerGroup"[1]
   ID : urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202
   Name : CollanosNetwork
   impl : null
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup getInterface
INFO: [urn:jxta:jxta-WorldGroup] GROUP REF COUNT INCREMENTED TO: 2 by
   net.jxta.impl.peergroup.GenericPeerGroup.loadModule(GenericPeerGroup.java:652)
Feb 5, 2010 5:04:36 PM net.jxta.impl.cm.SrdiIndex clearSrdi
INFO: Clearing SRDI for CollanosNetwork
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the JXME Proxy Service (net.jxta.impl.proxy.ProxyService)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Relay Message Transport (net.jxta.impl.endpoint.relay.RelayTransport)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : PSE Membership Service (net.jxta.impl.membership.pse.PSEMembershipService)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Pipe Service (net.jxta.impl.pipe.PipeServiceImpl)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Router Message Transport (net.jxta.impl.endpoint.router.EndpointRouter)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Always Access Service (net.jxta.impl.access.always.AlwaysAccessService)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Rendezvous Service (net.jxta.impl.rendezvous.RendezVousServiceImpl)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Endpoint service (net.jxta.impl.endpoint.EndpointServiceImpl)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Peerinfo Service (net.jxta.impl.peer.PeerInfoServiceImpl)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Cryptobased-ID Message Transport (net.jxta.impl.endpoint.cbjx.CbJxTransport)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Resolver service (net.jxta.impl.resolver.ResolverServiceImpl)
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.tls.TlsTransport <init>
INFO: Adjusting TLS connection idle timeout to 300000 millis.
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.tls.TlsTransport <init>
INFO: Adjusting TLS min reconnection idle to 60000 millis.
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.tls.TlsTransport <init>
INFO: Adjusting TLS maximum retry queue age to 120000 millis.
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the TLS Message Transport (net.jxta.impl.endpoint.tls.TlsTransport)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Discovery service (net.jxta.impl.discovery.DiscoveryServiceImpl)
Feb 5, 2010 5:04:36 PM net.jxta.impl.proxy.ProxyService startApp
WARNING: Stalled until there is a endpoint service
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.relay.RelayTransport startApp
WARNING: Stalled until there is an endpoint service
Feb 5, 2010 5:04:36 PM net.jxta.impl.membership.pse.PSEMembershipService startApp
INFO: PSE Membmership Service started.
Feb 5, 2010 5:04:36 PM net.jxta.impl.pipe.PipeServiceImpl startApp
WARNING: Stalled until there is an endpoint service
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.router.EndpointRouter startApp
WARNING: Stalled until there is an endpoint service
Feb 5, 2010 5:04:36 PM net.jxta.impl.rendezvous.RendezVousServiceImpl startApp
WARNING: Stalled until there is an endpoint service
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.EndpointServiceImpl startApp
INFO: Endpoint Service started.
Feb 5, 2010 5:04:36 PM net.jxta.impl.peer.PeerInfoServiceImpl startApp
WARNING: Stalled until there is a resolver service
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.cbjx.CbJxTransport startApp
INFO: CbJxTransport started
Feb 5, 2010 5:04:36 PM net.jxta.impl.discovery.DiscoveryServiceImpl startApp
WARNING: Stalled until there is a rendezvous service
Feb 5, 2010 5:04:36 PM net.jxta.impl.proxy.ProxyService startApp
WARNING: Stalled until there is a discovery service
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.relay.RelayTransport startApp
WARNING: Stalled until there is a discovery service
Feb 5, 2010 5:04:36 PM net.jxta.impl.pipe.PipeServiceImpl startApp
WARNING: Stalled until there is a rendezvous service
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.router.EndpointRouter startApp
WARNING: Endpoint Router start stalled until rendezvous service available
Feb 5, 2010 5:04:36 PM net.jxta.impl.rendezvous.edge.EdgePeerRdvService <init>
INFO: RendezVous Service is initialized for urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202 as an Edge peer.
Feb 5, 2010 5:04:36 PM net.jxta.impl.rendezvous.RendezVousServiceImpl startApp
INFO: Rendezvous Serivce started
Feb 5, 2010 5:04:36 PM net.jxta.impl.discovery.DiscoveryServiceImpl beEdge
INFO: Switched to a Edge peer role.
Feb 5, 2010 5:04:36 PM net.jxta.impl.discovery.DiscoveryServiceImpl startApp
INFO: Discovery service started
Feb 5, 2010 5:04:36 PM net.jxta.impl.proxy.ProxyService startApp
WARNING: Stalled until there is a pipe service
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.relay.RelayTransport startApp
WARNING: Stalled until there is a pipe service
Feb 5, 2010 5:04:36 PM net.jxta.impl.rendezvous.edge.EdgePeerRdvService$MonitorTask run
WARNING: Rendezvous connection stalled until router is started!
Feb 5, 2010 5:04:36 PM net.jxta.impl.cm.SrdiIndex <init>
INFO: [urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202 "CollanosNetwork"[0] / urn:jxta:jxta-WorldGroup "World PeerGroup"[2]] : Initialized pipeResolverSrdi
Feb 5, 2010 5:04:36 PM net.jxta.impl.cm.SrdiIndex startGC
INFO: [urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202 "CollanosNetwork"[0] / urn:jxta:jxta-WorldGroup "World PeerGroup"[2]] : Starting SRDI GC Thread for pipeResolverSrdi
Feb 5, 2010 5:04:36 PM net.jxta.impl.cm.SrdiIndex <init>
INFO: [urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202 "CollanosNetwork"[0] / urn:jxta:jxta-WorldGroup "World PeerGroup"[2]] : Initialized routerSrdi
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.router.EndpointRouter startApp
INFO: urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202 "CollanosNetwork"[0] / urn:jxta:jxta-WorldGroup "World PeerGroup"[2] : Router Message Transport started.
Feb 5, 2010 5:04:36 PM net.jxta.impl.proxy.ProxyService startApp
INFO: JXME Proxy Service started.
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.relay.RelayClient startClient
INFO: Started client : relay://uuid-59616261646162614E50472050325033349C0942450E4246B9F5EB39DD2C26E603
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.relay.RelayTransport startApp
INFO: Relay Message Transport started
Feb 5, 2010 5:04:36 PM net.jxta.impl.endpoint.relay.RelayClient run
INFO: Start relay client thread
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded module : Default Network PeerGroup reference implementation (net.jxta.impl.peergroup.ShadowPeerGroup)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup decRefCount
INFO: [urn:jxta:jxta-WorldGroup] GROUP REF COUNT DECCREMENTED TO: 1 by
   net.jxta.peergroup.NetPeerGroupFactory.<init>(NetPeerGroupFactory.java:220)
Feb 5, 2010 5:04:36 PM net.jxta.impl.peergroup.GenericPeerGroup getInterface
INFO: [urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202] GROUP REF COUNT INCREMENTED TO: 1 by
   net.jxta.platform.NetworkManager.startNetwork(NetworkManager.java:412)
Feb 5, 2010 5:04:36 PM net.jxta.platform.NetworkManager startNetwork
INFO: Started JXTA Network!
Feb 5, 2010 5:04:37 PM net.jxta.impl.endpoint.tcp.TcpMessenger <init>
INFO: Creating new TCP Connection to : tcp://91.137.20.253:9701 / 91.137.20.253:9701
Feb 5, 2010 5:04:38 PM net.jxta.impl.endpoint.tcp.TcpMessenger <init>
INFO: Creating new TCP Connection to : tcp://91.137.20.231:9701 / 91.137.20.231:9701
Feb 5, 2010 5:04:38 PM net.jxta.impl.endpoint.tcp.TcpMessenger <init>
INFO: Creating new TCP Connection to : tcp://superedge03.collanos.net:9701 / 91.137.0.78:9701
Feb 5, 2010 5:04:38 PM net.jxta.impl.endpoint.tcp.TcpTransport getMessenger
WARNING: Could not get messenger for tcp://superedge03.collanos.net:9701 : Connection refused
Feb 5, 2010 5:04:38 PM net.jxta.impl.endpoint.servlethttp.HttpClientMessenger <init>
INFO: New messenger : net.jxta.impl.endpoint.servlethttp.HttpClientMessenger@1e758ca {http://91.137.20.252:80} {http://91.137.20.252:80 / jxta://uuid-59616261646162614E50472050325033A1E2BD5D9EBB469FB3A9D6B7D6DBD48803}
Feb 5, 2010 5:04:38 PM net.jxta.impl.endpoint.servlethttp.HttpClientMessenger$MessagePoller run
INFO: Message polling beings for http://91.137.20.252:80/uuid-59616261646162614E50472050325033349C0942450E4246B9F5EB39DD2C26E603?120000,120000,http://91.137.20.252:80
Feb 5, 2010 5:04:41 PM net.jxta.impl.endpoint.tcp.TcpMessenger <init>
INFO: Creating new TCP Connection to : tcp://91.137.20.252:9701 / 91.137.20.252:9701
NetId(TL)=urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202
Feb 5, 2010 5:04:41 PM net.jxta.impl.loader.RefJxtaLoader findModuleImplAdvertisement
WARNING: Failed to find class for urn:jxta:uuid-DEADBEEFDEAFBABAFEEDBABE000000010406
java.lang.ClassNotFoundException: No matching class for : urn:jxta:uuid-DEADBEEFDEAFBABAFEEDBABE000000010406
   at net.jxta.impl.loader.RefJxtaLoader.findClass(RefJxtaLoader.java:240)
   at net.jxta.impl.loader.RefJxtaLoader.findModuleImplAdvertisement(RefJxtaLoader.java:350)
   at net.jxta.impl.peergroup.GenericPeerGroup.loadModule(GenericPeerGroup.java:781)
   at net.jxta.impl.peergroup.GenericPeerGroup.newGroup(GenericPeerGroup.java:1408)
   at net.jxta.impl.peergroup.PeerGroupInterface.newGroup(PeerGroupInterface.java:315)
   at com.collanos.p2ptl.domain.Domain.create(Unknown Source)
   at com.collanos.p2ptl.domain.PrimaryDomain.join(Unknown Source)
   at com.collanos.p2ptl.TransportLayer.create(Unknown Source)
   at com.collanos.workplace.WorkplaceApplicationAdvisor.preStartup(Unknown Source)
   at org.eclipse.ui.internal.Workbench$27.runWithException(Workbench.java:1359)
   at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
   at org.eclipse.swt.widgets.Synchronizer.syncExec(Synchronizer.java:178)
   at org.eclipse.ui.internal.UISynchronizer.syncExec(UISynchronizer.java:150)
   at org.eclipse.swt.widgets.Display.syncExec(Display.java:4021)
   at org.eclipse.ui.internal.StartupThreading.runWithoutExceptions(StartupThreading.java:94)
   at org.eclipse.ui.internal.Workbench.init(Workbench.java:1356)
   at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2312)
   at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2198)
   at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:493)
   at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:288)
   at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:488)
   at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
   at com.collanos.workplace.WorkplaceApplication.start(Unknown Source)
   at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
   at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
   at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
   at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
   at java.lang.reflect.Method.invoke(Unknown Source)
   at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
   at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
   at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
   at org.eclipse.equinox.launcher.Main.main(Main.java:1212)
Feb 5, 2010 5:04:41 PM net.jxta.impl.peergroup.GenericPeerGroup getInterface
INFO: [urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202] GROUP REF COUNT INCREMENTED TO: 2 by
   net.jxta.impl.peergroup.GenericPeerGroup.loadModule(GenericPeerGroup.java:822)
Feb 5, 2010 5:04:41 PM net.jxta.impl.cm.SrdiIndex clearSrdi
INFO: Clearing SRDI for Primary Domain
Feb 5, 2010 5:04:41 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Always Access Service (net.jxta.impl.access.always.AlwaysAccessService)
Feb 5, 2010 5:04:41 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Rendezvous Service (net.jxta.impl.rendezvous.RendezVousServiceImpl)
Feb 5, 2010 5:04:41 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Endpoint service (net.jxta.impl.endpoint.EndpointServiceImpl)
Feb 5, 2010 5:04:41 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Peerinfo Service (net.jxta.impl.peer.PeerInfoServiceImpl)
Feb 5, 2010 5:04:41 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : MIAPMS (net.jxta.impl.membership.PasswdMembershipService)
Feb 5, 2010 5:04:41 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Resolver service (net.jxta.impl.resolver.ResolverServiceImpl)
Feb 5, 2010 5:04:41 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Discovery service (net.jxta.impl.discovery.DiscoveryServiceImpl)
Feb 5, 2010 5:04:41 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded privileged module : Reference Implementation of the Pipe Service (net.jxta.impl.pipe.PipeServiceImpl)
Feb 5, 2010 5:04:41 PM net.jxta.impl.rendezvous.RendezVousServiceImpl startApp
WARNING: Stalled until there is an endpoint service
Feb 5, 2010 5:04:41 PM net.jxta.impl.endpoint.EndpointServiceImpl startApp
INFO: Endpoint Service started.
Feb 5, 2010 5:04:41 PM net.jxta.impl.peer.PeerInfoServiceImpl startApp
WARNING: Stalled until there is a resolver service
Feb 5, 2010 5:04:41 PM net.jxta.impl.discovery.DiscoveryServiceImpl startApp
WARNING: Stalled until there is a rendezvous service
Feb 5, 2010 5:04:41 PM net.jxta.impl.pipe.PipeServiceImpl startApp
WARNING: Stalled until there is a rendezvous service
Feb 5, 2010 5:04:41 PM net.jxta.impl.rendezvous.edge.EdgePeerRdvService <init>
INFO: RendezVous Service is initialized for urn:jxta:uuid-65780D7B8F2F47BB9CC9AD9601D4901575BE74BBCB414A437AF692B40644712202 as an Edge peer.
Feb 5, 2010 5:04:41 PM net.jxta.impl.rendezvous.RendezVousServiceImpl startApp
INFO: Rendezvous Serivce started
Feb 5, 2010 5:04:41 PM net.jxta.impl.discovery.DiscoveryServiceImpl beEdge
INFO: Switched to a Edge peer role.
Feb 5, 2010 5:04:41 PM net.jxta.impl.discovery.DiscoveryServiceImpl startApp
INFO: Discovery service started
Feb 5, 2010 5:04:41 PM net.jxta.impl.pipe.NonBlockingWireOutputPipe <init>
INFO: Constructing for urn:jxta:uuid-75BE74BBCB414A437AF692B4064471225065657256694577B575A9642D36353704
Feb 5, 2010 5:04:41 PM net.jxta.impl.cm.SrdiIndex <init>
INFO: [urn:jxta:uuid-65780D7B8F2F47BB9CC9AD9601D4901575BE74BBCB414A437AF692B40644712202 "Primary Domain"[0] / urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202 "CollanosNetwork"[2] / urn:jxta:jxta-WorldGroup "World PeerGroup"[1]] : Initialized pipeResolverSrdi
Feb 5, 2010 5:04:41 PM net.jxta.impl.cm.SrdiIndex startGC
INFO: [urn:jxta:uuid-65780D7B8F2F47BB9CC9AD9601D4901575BE74BBCB414A437AF692B40644712202 "Primary Domain"[0] / urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202 "CollanosNetwork"[2] / urn:jxta:jxta-WorldGroup "World PeerGroup"[1]] : Starting SRDI GC Thread for pipeResolverSrdi
Feb 5, 2010 5:04:41 PM net.jxta.impl.peergroup.GenericPeerGroup loadModule
INFO: Loaded module : General Purpose Peer Group Implementation (net.jxta.impl.peergroup.StdPeerGroup)
Feb 5, 2010 5:04:41 PM net.jxta.impl.peergroup.GenericPeerGroup getInterface
INFO: [urn:jxta:uuid-65780D7B8F2F47BB9CC9AD9601D4901575BE74BBCB414A437AF692B40644712202] GROUP REF COUNT INCREMENTED TO: 1 by
   net.jxta.impl.peergroup.PeerGroupInterface.newGroup(PeerGroupInterface.java:315)
Feb 5, 2010 5:04:41 PM net.jxta.impl.rendezvous.edge.EdgePeerRdvService addRdv
INFO: New RDV lease from urn:jxta:uuid-59616261646162614E50472050325033A1E2BD5D9EBB469FB3A9D6B7D6DBD48803 C : -1265382281589 / -1265382281588
Feb 5, 2010 5:04:41 PM net.jxta.impl.pipe.NonBlockingWireOutputPipe close
INFO: Closing queue for urn:jxta:uuid-75BE74BBCB414A437AF692B4064471225065657256694577B575A9642D36353704
INSERT INTO UPGRADE_HISTORY ( VERSION, START_TIME) VALUES ('1.2.0.1',CURRENT_TIMESTAMP)
ALTER TABLE RQUEUE ADD COLUMN RP_PIECESIZE INT NOT NULL DEFAULT 0
Execute SQL: SELECT RP_MAKER,RP_CODE,RP_RUID,RP_CRC4,RP_TYPE,RP_SIZE,RP_ZIPE,RP_PRIO,RP_MULTI, RP_PIECENBR, RP_PIECESIZE, RP_DLST FROM RQUEUE WHERE RP_PIECENBR = 0
UPDATE UPGRADE_HISTORY SET END_TIME=CURRENT_TIMESTAMP WHERE VERSION='1.2.0.1' 
INSERT INTO UPGRADE_HISTORY ( VERSION, START_TIME) VALUES ('1.2.0.2',CURRENT_TIMESTAMP)
UPDATE UPGRADE_HISTORY SET END_TIME=CURRENT_TIMESTAMP WHERE VERSION='1.2.0.2' 
INSERT INTO UPGRADE_HISTORY ( VERSION, START_TIME) VALUES ('1.3.0.1',CURRENT_TIMESTAMP)
drop index rp_dlst_rqueue
INSERT INTO UPGRADE_HISTORY ( VERSION, START_TIME) VALUES ('1.3.0.2',CURRENT_TIMESTAMP)
create index rp_status_dlst_rqueue on rqueue(RP_STATE,RP_DLST)
INSERT INTO UPGRADE_HISTORY ( VERSION, START_TIME) VALUES ('1.3.0.2',CURRENT_TIMESTAMP)
create index raddressee_status_idx on RADDRESSEE (STATUS)
UPDATE UPGRADE_HISTORY SET END_TIME=CURRENT_TIMESTAMP WHERE VERSION='1.3.0.2' 
SELECT RP_RUID,RP_CRC4,RP_MAKER,RP_SIZE,RP_ZIPE,RP_PRIO,RP_MULTI,RP_TYPE,RP_TMST,RP_PIECENBR, RP_PIECESIZE, PEER_ID FROM RQUEUE INNER JOIN RPEERADDRESS ON RP_MAKER = PEER_CODE WHERE (RP_MAKER <> ?) AND (RP_DLST = '0') AND (ALIVE = '1') ORDER BY RP_PRIO DESC,RP_TMST
Feb 5, 2010 5:04:43 PM net.jxta.impl.pipe.InputPipeImpl <init>
INFO: Creating InputPipe for urn:jxta:uuid-65780D7B8F2F47BB9CC9AD9601D4901530364246314144448543B4314135393404 of type JxtaPropagate with listener
Feb 5, 2010 5:04:43 PM net.jxta.impl.pipe.WirePipe register
INFO: Registering urn:jxta:uuid-65780D7B8F2F47BB9CC9AD9601D4901530364246314144448543B4314135393404 with pipe resolver.
Feb 5, 2010 5:04:43 PM net.jxta.impl.pipe.NonBlockingWireOutputPipe <init>
INFO: Constructing for urn:jxta:uuid-65780D7B8F2F47BB9CC9AD9601D4901530364246314144448543B4314135393404
Feb 5, 2010 5:04:56 PM net.jxta.impl.rendezvous.edge.EdgePeerRdvService addRdv
INFO: New RDV lease from urn:jxta:uuid-59616261646162614E50472050325033A1E2BD5D9EBB469FB3A9D6B7D6DBD48803 C : -1265382296648 / -1265382296647
Feb 5, 2010 5:06:05 PM net.jxta.impl.endpoint.tcp.TcpMessenger closeImpl
INFO: Normal close (open 86864ms) of socket to : tcp://91.137.20.231:9701 / 91.137.20.231:9701
Feb 5, 2010 5:06:05 PM net.jxta.impl.endpoint.tcp.TcpTransport getMessenger
WARNING: Could not get messenger for tcp://91.137.20.231:9701 : Failed to receive remote welcome message before timeout.
Feb 5, 2010 5:09:52 PM net.jxta.platform.NetworkManager stopNetwork
INFO: Stopping JXTA Network!
Feb 5, 2010 5:09:52 PM net.jxta.impl.peergroup.GenericPeerGroup decRefCount
INFO: [urn:jxta:uuid-75BE74BBCB414A437AF692B40644712202] GROUP REF COUNT DECCREMENTED TO: 1 by
   net.jxta.impl.peergroup.RefCountPeerGroupInterface.stopApp(RefCountPeerGroupInterface.java:140)
Feb 5, 2010 5:09:52 PM net.jxta.platform.NetworkManager stopNetwork
INFO: Stopped JXTA Network!
```

So I tried changing the Java folder into every Java I found on my machine. Then it said that it fails to connect to the IP... But in every case I have the same problem using it. It starts, asks me to fill in my info but I cannot proceed - Next and Finish buttons do not work. The only working thing is Close Button which closes the whole program. Any suggestions?

Using Ubuntu Karmic.

---

