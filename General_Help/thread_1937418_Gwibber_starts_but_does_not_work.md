---
title: "Gwibber starts but does not work"
date: 2012-03-07
forum: General Help
---

### Post by grizzlyaka on 2012-03-07
I can get Gwibber to Start but it does not work properly. I cannot add broadcast accounts. I am running 11.10. Any help would be appreciated. Here is the output from the terminal window when starting Gwibber:

grizzlyaka@grizzlyaka-MS-7021:~$ gwibber


** (gwibber:2602): CRITICAL **: file /build/buildd/gwibber-3.3.1+1234~oneiric1/libgwibber/messages.vala: line 60: unexpected error: Error calling StartServiceByName for com.Gwibber.Messages: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/gwibber-service exited with status 1 (g-dbus-error-quark, 25)

** (gwibber:2602): CRITICAL **: file /build/buildd/gwibber-3.3.1+1234~oneiric1/libgwibber/connection.vala: line 83: unexpected error: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus) (g-dbus-error-quark, 4)

** (gwibber:2602): CRITICAL **: file /build/buildd/gwibber-3.3.1+1234~oneiric1/libgwibber/accounts.vala: line 110: unexpected error: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus) (g-dbus-error-quark, 4)


** (gwibber:2602): CRITICAL **: file /build/buildd/gwibber-3.3.1+1234~oneiric1/libgwibber/streams.vala: line 103: unexpected error: Error calling StartServiceByName for com.Gwibber.Streams: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/gwibber-service exited with status 1 (g-dbus-error-quark, 25)

** (gwibber:2602): CRITICAL **: gwibber_streams_get_stream_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_stream_filter_model: assertion `self != NULL' failed

(gwibber:2602): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2602): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2602): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2602): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2602): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2602): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2602): dee-CRITICAL **: dee_model_get_last_iter: assertion `DEE_IS_MODEL (self)' failed

(gwibber:2602): dee-CRITICAL **: dee_model_register_tag: assertion `DEE_IS_MODEL (self)' failed

(gwibber:2602): dee-CRITICAL **: dee_model_get_first_iter: assertion `DEE_IS_MODEL (self)' failed

(gwibber:2602): dee-CRITICAL **: dee_model_get_last_iter: assertion `DEE_IS_MODEL (self)' failed

(gwibber:2602): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2602): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2602): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2602): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2602): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2602): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2602): dee-CRITICAL **: You must set the 'back-end' property of the DeeProxyModel upon creation.

** (gwibber:2602): CRITICAL **: gwibber_streams_get_stream_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_stream_filter_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_get_stream_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_stream_filter_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_get_stream_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_stream_filter_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_get_stream_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_stream_filter_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_get_stream_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_stream_filter_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_get_stream_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_stream_filter_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_get_stream_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: gwibber_streams_stream_filter_model: assertion `self != NULL' failed

** (gwibber:2602): CRITICAL **: file /build/buildd/gwibber-3.3.1+1234~oneiric1/libgwibber/messages.vala: line 60: unexpected error: Error calling StartServiceByName for com.Gwibber.Messages: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/gwibber-service exited with status 1 (g-dbus-error-quark, 25)

(gwibber:2602): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2602): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2602): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2602): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2602): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2602): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2602): dee-CRITICAL **: dee_model_get_last_iter: assertion `DEE_IS_MODEL (self)' failed

(gwibber:2602): dee-CRITICAL **: dee_model_register_tag: assertion `DEE_IS_MODEL (self)' failed

(gwibber:2602): dee-CRITICAL **: dee_model_get_first_iter: assertion `DEE_IS_MODEL (self)' failed

(gwibber:2602): dee-CRITICAL **: dee_model_get_last_iter: assertion `DEE_IS_MODEL (self)' failed

(gwibber:2602): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2602): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2602): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2602): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2602): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gwibber:2602): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gwibber:2602): dee-CRITICAL **: You must set the 'back-end' property of the DeeProxyModel upon creation.



** (gwibber:2602): CRITICAL **: file /build/buildd/gwibber-3.3.1+1234~oneiric1/libgwibber/service.vala: line 470: unexpected error: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus) (g-dbus-error-quark, 4)

** (gwibber:2602): CRITICAL **: file /build/buildd/gwibber-3.3.1+1234~oneiric1/libgwibber/accounts.vala: line 110: unexpected error: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus) (g-dbus-error-quark, 4)

(gwibber:2602): dee-CRITICAL **: dee_model_get_last_iter: assertion `DEE_IS_MODEL (self)' failed
Loading plugin for friendfeed
Loading plugin for pingfm
Loading plugin for sohu
Loading plugin for buzz
Loading plugin for twitter
Loading plugin for foursquare

(gwibber:2602): dee-CRITICAL **: dee_model_get_last_iter: assertion `DEE_IS_MODEL (self)' failed
Loading plugin for sina
Loading plugin for qaiku
Loading plugin for statusnet
Loading plugin for flickr
Loading plugin for facebook
Loading plugin for identica
Loading plugin for digg
grizzlyaka@grizzlyaka-MS-7021:~$ ERROR:dbus.proxies:Introspect error on com.Gwibber.Service:/com/gwibber/Service: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Traceback (most recent call last):
  File "/usr/bin/gwibber-accounts", line 108, in <module>
    accounts.GwibberAccountManager(selected_account=selected_account, condition=condition, message=message)
  File "/usr/lib/pymodules/python2.7/gwibber/accounts.py", line 55, in __init__
    self.services = json.loads(self.gwibber.GetServices())
  File "/usr/lib/pymodules/python2.7/gwibber/lib/__init__.py", line 39, in GetServices
    return self.service.GetServices()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 143, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

---

