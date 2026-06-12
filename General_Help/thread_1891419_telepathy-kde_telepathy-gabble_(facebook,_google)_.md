---
title: "telepathy-kde telepathy-gabble (facebook, google) issues"
date: 2011-12-05
forum: General Help
---

### Post by buzzmandt on 2011-12-05
im having issues with the most current version
gabble won't connect to facebook and google talk and telepathy-kde guys send me to telepathy-gabble guys, and they send me to telepathy, who in turn sends me back....bla bla.....
help....


```
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ GABBLE_PERSIST=true GABBLE_DEBUG=all /usr/lib/telepathy/telepathy-gabble
(process:4461): tp-glib/proxy-DEBUG: tp_proxy_dispose: 0x10de000
(process:4461): tp-glib/proxy-DEBUG: tp_proxy_invalidate: 0x10de000: Proxy unreferenced
(process:4461): tp-glib/proxy-DEBUG: tp_proxy_finalize: 0x10de000
(process:4461): gabble-DEBUG: gabble_plugin_loader_probe (plugin-loader.c:130): probing /usr/lib/telepathy/gabble-0
** (process:4461): DEBUG: gabble_plugin_create: loaded
(process:4461): gabble-DEBUG: plugin_loader_try_to_load (plugin-loader.c:99): loaded 'Gateway registration plugin' version 0.15.0 (/usr/lib/telepathy/gabble-0/gateways.so), implementing these sidecars: org.freedesktop.Telepathy.Gabble.Plugin.Gateways
(telepathy-gabble:4461): tp-glib-DEBUG: started version 0.15.0 (telepathy-glib version 0.17.3)
(telepathy-gabble:4461): tp-glib/params-DEBUG: tp_base_protocol_sanitize_parameters: using specified value for account: "buzzmandt@chat.facebook.com"
(telepathy-gabble:4461): tp-glib/params-DEBUG: tp_base_protocol_sanitize_parameters: using specified value for server: "chat.facebook.com"
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_class_init (connection.c:920): Initializing (GabbleConnectionClass *)0x1100620
(telepathy-gabble:4461): tp-glib/presence-DEBUG: tp_presence_mixin_class_init: called.
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_init (connection.c:519): Initializing (GabbleConnection *)0x110a160
(telepathy-gabble:4461): gabble-DEBUG: gabble_capabilities_init (capabilities.c:234): 0x110a160
(telepathy-gabble:4461): gabble-DEBUG: gabble_roomlist_manager_constructed (roomlist-manager.c:210): 0x10d62c0
(telepathy-gabble:4461): gabble-DEBUG: gabble_signal_connect_weak (util.c:966): connecting to 0x110a160:status-changed with context 0x10ff420
(telepathy-gabble:4461): gabble-DEBUG: gabble_signal_connect_weak (util.c:966): connecting to 0x110a160:status-changed with context 0x10ff280
(telepathy-gabble:4461): gabble-DEBUG: gabble_server_tls_manager_constructed (server-tls-manager.c:418): Server TLS Manager constructed
(telepathy-gabble:4461): gabble-DEBUG: gabble_signal_connect_weak (util.c:966): connecting to 0x110a160:status-changed with context 0x10ff340
(telepathy-gabble:4461): gabble-DEBUG: gabble_signal_connect_weak (util.c:966): connecting to 0x110a160:status-changed with context 0x10ff660
(telepathy-gabble:4461): gabble-DEBUG: gabble_signal_connect_weak (util.c:966): connecting to 0x110a160:porter-available with context 0x10ff160
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_constructor (connection.c:390): Post-construction: (GabbleConnection *)0x110a160
(telepathy-gabble:4461): tp-glib/presence-DEBUG: tp_presence_mixin_init: called.
(telepathy-gabble:4461): gabble-DEBUG: gabble_signal_connect_weak (util.c:966): connecting to 0x10d6340:item-found with context 0x111d360
(telepathy-gabble:4461): gabble-DEBUG: gabble_signal_connect_weak (util.c:966): connecting to 0x110a160:status-changed with context 0x111d2e0
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_constructed (connection.c:502): defaulted resource to 1b01d469
(telepathy-gabble:4461): tp-glib/connection-DEBUG: tp_base_connection_register: 0x110a160: bus name org.freedesktop.Telepathy.Connection.gabble.jabber.buzzmandt_40chat_2efacebook_2ecom_2f1b01d469; object path /org/freedesktop/Telepathy/Connection/gabble/jabber/buzzmandt_40chat_2efacebook_2ecom_2f1b01d469
(telepathy-gabble:4461): tp-glib/connection-DEBUG: tp_presence_mixin_get_contacts_dbus_property: called.
(telepathy-gabble:4461): tp-glib/presence-DEBUG: tp_presence_mixin_get_simple_presence_dbus_property: called.
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3399): enter
(telepathy-gabble:4461): gabble-DEBUG: gabble_media_factory_add_caps (media-factory.c:1016): Client org.freedesktop.Telepathy.Client.KDE.TextUi media capabilities:
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3469): client org.freedesktop.Telepathy.Client.KDE.TextUi has no interesting capabilities
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3491): client org.freedesktop.Telepathy.Client.KDE.TextUi has no interesting data forms
(telepathy-gabble:4461): gabble-DEBUG: gabble_media_factory_add_caps (media-factory.c:1016): Client org.freedesktop.Telepathy.Client.KDE.SASLHandler media capabilities:                       
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3469): client org.freedesktop.Telepathy.Client.KDE.SASLHandler has no interesting capabilities      
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3491): client org.freedesktop.Telepathy.Client.KDE.SASLHandler has no interesting data forms        
(telepathy-gabble:4461): gabble-DEBUG: gabble_media_factory_add_caps (media-factory.c:1016): Client org.freedesktop.Telepathy.Client.KDE.FileTransferHandler media capabilities:               
(telepathy-gabble:4461): gabble-DEBUG: gabble_ft_manager_represent_client (ft-manager.c:1040): client org.freedesktop.Telepathy.Client.KDE.FileTransferHandler supports file transfer          
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3460): client org.freedesktop.Telepathy.Client.KDE.FileTransferHandler contributes:                 
  --begin--                                                                                                                                                                                    
  Feature: [http://jabber.org/protocol/si/profile/file-transfer](http://jabber.org/protocol/si/profile/file-transfer)
  Feature: [http://telepathy.freedesktop.org/xmpp/file-transfer-metadata](http://telepathy.freedesktop.org/xmpp/file-transfer-metadata)
  Feature: [http://google.com/xmpp/protocol/share/v1](http://google.com/xmpp/protocol/share/v1)
  --end--

(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3491): client org.freedesktop.Telepathy.Client.KDE.FileTransferHandler has no interesting data forms
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_refresh_capabilities (connection.c:2446): incorporating caps for org.freedesktop.Telepathy.Client.KDE.FileTransferHandler:
  --begin--
  Feature: [http://jabber.org/protocol/si/profile/file-transfer](http://jabber.org/protocol/si/profile/file-transfer)
  Feature: [http://telepathy.freedesktop.org/xmpp/file-transfer-metadata](http://telepathy.freedesktop.org/xmpp/file-transfer-metadata)
  Feature: [http://google.com/xmpp/protocol/share/v1](http://google.com/xmpp/protocol/share/v1)
  --end--

(telepathy-gabble:4461): gabble-DEBUG: gabble_presence_set_capabilities (presence.c:336): about to add caps to resource 1b01d469 with serial 1
(telepathy-gabble:4461): gabble-DEBUG: gabble_presence_set_capabilities (presence.c:347): found resource 1b01d469
(telepathy-gabble:4461): gabble-DEBUG: gabble_presence_set_capabilities (presence.c:352): new serial 1, old 0, clearing caps
(telepathy-gabble:4461): gabble-DEBUG: gabble_presence_set_capabilities (presence.c:360): updating caps for resource 1b01d469
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_refresh_capabilities (connection.c:2478): not emitting self-presence stanza: not connected yet
(telepathy-gabble:4461): tp-glib/presence-DEBUG: tp_presence_mixin_simple_presence_set_presence: called.
(telepathy-gabble:4461): tp-glib/presence-DEBUG: check_for_status: Found status "available", checking if it's available...
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3399): enter
(telepathy-gabble:4461): gabble-DEBUG: gabble_media_factory_add_caps (media-factory.c:1016): Client org.freedesktop.Telepathy.Client.KDE.TextUi media capabilities:
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3469): client org.freedesktop.Telepathy.Client.KDE.TextUi has no interesting capabilities
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3491): client org.freedesktop.Telepathy.Client.KDE.TextUi has no interesting data forms
(telepathy-gabble:4461): gabble-DEBUG: gabble_media_factory_add_caps (media-factory.c:1016): Client org.freedesktop.Telepathy.Client.KDE.SASLHandler media capabilities:
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3469): client org.freedesktop.Telepathy.Client.KDE.SASLHandler has no interesting capabilities
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3491): client org.freedesktop.Telepathy.Client.KDE.SASLHandler has no interesting data forms
(telepathy-gabble:4461): gabble-DEBUG: gabble_media_factory_add_caps (media-factory.c:1016): Client org.freedesktop.Telepathy.Client.KDE.FileTransferHandler media capabilities:
(telepathy-gabble:4461): gabble-DEBUG: gabble_ft_manager_represent_client (ft-manager.c:1040): client org.freedesktop.Telepathy.Client.KDE.FileTransferHandler supports file transfer
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3460): client org.freedesktop.Telepathy.Client.KDE.FileTransferHandler contributes:
  --begin--
  Feature: [http://jabber.org/protocol/si/profile/file-transfer](http://jabber.org/protocol/si/profile/file-transfer)
  Feature: [http://telepathy.freedesktop.org/xmpp/file-transfer-metadata](http://telepathy.freedesktop.org/xmpp/file-transfer-metadata)
  Feature: [http://google.com/xmpp/protocol/share/v1](http://google.com/xmpp/protocol/share/v1)
  --end--

(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_update_capabilities (connection.c:3491): client org.freedesktop.Telepathy.Client.KDE.FileTransferHandler has no interesting data forms
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_refresh_capabilities (connection.c:2446): incorporating caps for org.freedesktop.Telepathy.Client.KDE.FileTransferHandler:
  --begin--
  Feature: [http://jabber.org/protocol/si/profile/file-transfer](http://jabber.org/protocol/si/profile/file-transfer)
  Feature: [http://telepathy.freedesktop.org/xmpp/file-transfer-metadata](http://telepathy.freedesktop.org/xmpp/file-transfer-metadata)
  Feature: [http://google.com/xmpp/protocol/share/v1](http://google.com/xmpp/protocol/share/v1)
  --end--

(telepathy-gabble:4461): gabble-DEBUG: gabble_presence_set_capabilities (presence.c:336): about to add caps to resource 1b01d469 with serial 2
(telepathy-gabble:4461): gabble-DEBUG: gabble_presence_set_capabilities (presence.c:347): found resource 1b01d469
(telepathy-gabble:4461): gabble-DEBUG: gabble_presence_set_capabilities (presence.c:352): new serial 2, old 1, clearing caps
(telepathy-gabble:4461): gabble-DEBUG: gabble_presence_set_capabilities (presence.c:360): updating caps for resource 1b01d469
(telepathy-gabble:4461): gabble-DEBUG: gabble_connection_refresh_capabilities (connection.c:2469): nothing to do
(telepathy-gabble:4461): gabble-DEBUG: _gabble_connection_connect (connection.c:2141): disabling SRV because "server" or "old-ssl" was specified or port was not 5222, will connect to chat.facebook.com
(telepathy-gabble:4461): gabble-DEBUG: _gabble_connection_connect (connection.c:2200): Start connecting


** CRITICAL **: unable to create '/home/buzzmandt/.cache/dconf'; dconf will not work properly.
Trace/breakpoint trap (core dumped)
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ 
```


I'm sure it's about the "** CRITICAL **: unable to create '/home/buzzmandt/.cache/dconf'; dconf will not work properly.
Trace/breakpoint trap (core dumped)"

I do have full permissions as far as i can tell in the .cache folder, not sure why it can't create there.  can anyone help here?

---

### Post by buzzmandt on 2011-12-09
Well. I really hate bumps but........

*bump*

Anybody?

---

### Post by buzzmandt on 2011-12-14
Already then.... nobody lol.

anyway, i went ahead and put a bug report in:
[https://bugs.launchpad.net/ubuntu/+source/libproxy/+bug/904042](https://bugs.launchpad.net/ubuntu/+source/libproxy/+bug/904042)

Which was subsequently marked a duplicate of:
[https://bugs.launchpad.net/ubuntu/+source/libproxy/+bug/893031](https://bugs.launchpad.net/ubuntu/+source/libproxy/+bug/893031)

which is odd to me since i'm not using empathy, but, I will await the fix of libproxy and see what happens.

this posted just in case someone needs to run across it.

---

### Post by mfraser on 2011-12-17
Was getting this myself, but I fixed it by creating a directory in .cache called dconf.

---

### Post by Orion2000za on 2012-01-06
am not sure it is the same problem but I suddenly had fbook/jabber connecting/disconnecting repeatedly. 

via IRC got the tip to stop mission-control5 (or similar) process and then remove /home/.mission-control/accounts directory, then you have to recreate any accounts.

Worked for me, things now back to 0.2 version expected status

---

