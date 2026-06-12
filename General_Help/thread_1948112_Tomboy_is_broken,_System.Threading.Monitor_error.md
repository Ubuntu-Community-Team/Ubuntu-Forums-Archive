---
title: "Tomboy is broken, System.Threading.Monitor error"
date: 2012-03-27
forum: General Help
---

### Post by MadHatter93 on 2012-03-27
So i was trying to upgrade Tomboy notes to the dev version 1.9.10, and had to compile from source. After many dependencies were satisfied, I configured, made, and installed Tomboy 1.9.10... only to be promptly greeted by this bit of code:

```
Missing method System.Threading.Monitor::Enter(object,bool&) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/dbus-sharp/1.0.0.0__5675b0c3093115b5/dbus-sharp.dll

Unhandled Exception: System.Exception: Unable to open the system message bus. ---> System.MissingMethodException: Method not found: 'System.Threading.Monitor.Enter'.
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject[IBus] (System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Bus..ctor (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Tomboy.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Application.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.Exception: Unable to open the system message bus. ---> System.MissingMethodException: Method not found: 'System.Threading.Monitor.Enter'.
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject[IBus] (System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Bus..ctor (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Tomboy.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Application.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] in <filename unknown>:0 
```

So, I promptly purged Tomboy and reinstalled using the latest stable version through apt, which has been working previously. It gave me the same message. Restarted, same message. Purged again, reinstalled again, same message. I think that one of the dependencies I manually installed may have broken it, but I'm not sure which one. Any help? Thanks in advance, guys.

---

### Post by MadHatter93 on 2012-03-28
Side note: Forgot to include my system stats:
Ubuntu 11.10x86_64, Kernel 3.0.0-17
Lenovo G770 Laptop
i5 Dual core with threading
Desktop environment: Gnome 3.2 

I'm not that inexperienced with ubuntu, however this is beyond anything I've dealt wih yet

---

### Post by directhex on 2012-03-29
> **MadHatter93 said:**
> So i was trying to upgrade Tomboy notes to the dev version 1.9.10, and had to compile from source. After many dependencies were satisfied, I configured, made, and installed Tomboy 1.9.10... only to be promptly greeted by this bit of code:

```
Missing method System.Threading.Monitor::Enter(object,bool&) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/dbus-sharp/1.0.0.0__5675b0c3093115b5/dbus-sharp.dll

Unhandled Exception: System.Exception: Unable to open the system message bus. ---> System.MissingMethodException: Method not found: 'System.Threading.Monitor.Enter'.
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject[IBus] (System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Bus..ctor (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Tomboy.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Application.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.Exception: Unable to open the system message bus. ---> System.MissingMethodException: Method not found: 'System.Threading.Monitor.Enter'.
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject[IBus] (System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Bus..ctor (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Tomboy.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Application.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] in <filename unknown>:0 
```

So, I promptly purged Tomboy and reinstalled using the latest stable version through apt, which has been working previously. It gave me the same message. Restarted, same message. Purged again, reinstalled again, same message. I think that one of the dependencies I manually installed may have broken it, but I'm not sure which one. Any help? Thanks in advance, guys.

11.10? Are you sure? The error message doesn't seem possible on 11.10. More specifically, /usr/lib/mono/gac/dbus-sharp/1.0.0.0__5675b0c3093115b5/dbus-sharp.dll does not reference /usr/lib/mono/2.0/mscorlib.dll on 11.10.

Paste the output of "dpkg -l \*-cil \*mono\* tomboy | grep ^ii" and "which mono"

---

### Post by MadHatter93 on 2012-03-29
Yes, I'm sure it's 11.10, I installed it myself.

Output of "dpkg -l \*-cil \*mono\* tomboy | grep ^ii":
```
ii  libappindicator0.1-cil                                      0.4.1-0ubuntu2                          CLI bindings for libappindicator
ii  libboo2.0.9-cil                                             0.9.5~git20110729.r1.202a430-1          python-like language and compiler for the CLI - library files
ii  libdbus-glib1.0-cil                                         0.5.0-3build1                           CLI implementation of D-Bus (GLib mainloop integration)
ii  libdbus1.0-cil                                              0.7.0-4                                 CLI implementation of D-Bus
ii  libgconf2.0-cil                                             2.24.2-1                                CLI binding for GConf 2.24
ii  libgdata1.7-cil                                             1.7.0.1-1build1                         Google GData CLI client library
ii  libgkeyfile1.0-cil                                          0.1-2ubuntu2                            GObject-based wrapper library for GKeyFile -- CLI bindings
ii  libglade2.0-cil                                             2.12.10-2ubuntu1                        CLI binding for the Glade libraries 2.6
ii  libglib2.0-cil                                              2.12.10-2ubuntu1                        CLI binding for the GLib utility library 2.12
ii  libgmime2.4-cil                                             2.4.26-0ubuntu2                         CLI binding for the GMime library
ii  libgtk-sharp-beans-cil                                      2.14.1-2build2                          Supplementary CLI bindings for GTK 2.14+
ii  libgtk2.0-cil                                               2.12.10-2ubuntu1                        CLI binding for the GTK+ toolkit 2.12
ii  libgudev1.0-cil                                             0.1-2build1                             GObject-based wrapper library for libudev -- CLI bindings
ii  liblaunchpad-integration1.0-cil                             0.1.54                                  CLI bindings for liblaunchpad-integration
ii  libmono-2.0-1                                               2.10.5-1                                Mono JIT library
ii  libmono-2.0-dev                                             2.10.5-1                                Mono JIT library - Development files
ii  libmono-accessibility2.0-cil                                2.10.5-1                                Mono Accessibility library (for CLI 2.0)
ii  libmono-accessibility4.0-cil                                2.10.5-1                                Mono Accessibility library (for CLI 4.0)
ii  libmono-addins-cil-dev                                      0.6.2-1ubuntu1~hyper1+oneiric           addin framework for extensible CLI applications/libraries
ii  libmono-addins-gui-cil-dev                                  0.6.2-1ubuntu1~hyper1+oneiric           GTK# frontend library for Mono.Addins
ii  libmono-addins-gui0.2-cil                                   0.6.2-1ubuntu1~hyper1+oneiric           GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                                       0.6.2-1ubuntu1~hyper1+oneiric           addin framework for extensible CLI applications/libraries
ii  libmono-c5-1.1-cil                                          2.10.5-1                                Mono C5 library
ii  libmono-cairo2.0-cil                                        2.10.5-1                                Mono Cairo library (for CLI 2.0)
ii  libmono-cairo4.0-cil                                        2.10.5-1                                Mono Cairo library (for CLI 4.0)
ii  libmono-cecil-private-cil                                   2.10.5-1                                Mono.Cecil library
ii  libmono-cil-dev                                             2.10.5-1                                Mono Base Class Libraries (BCL) - Development files
ii  libmono-codecontracts4.0-cil                                2.10.5-1                                Mono.CodeContracts library (for CLI 4.0)
ii  libmono-compilerservices-symbolwriter4.0-cil                2.10.5-1                                Mono.CompilerServices.SymbolWriter library (for CLI 4.0)
ii  libmono-corlib2.0-cil                                       2.10.5-1                                Mono core library (for CLI 2.0)
ii  libmono-corlib4.0-cil                                       2.10.5-1                                Mono core library (for CLI 4.0)
ii  libmono-cscompmgd8.0-cil                                    2.10.5-1                                Mono cscompmgd library (for CLI 2.0)
ii  libmono-csharp4.0-cil                                       2.10.5-1                                Mono.CSharp library (for CLI 4.0)
ii  libmono-custommarshalers4.0-cil                             2.10.5-1                                Mono CustomMarshalers library (for CLI 4.0)
ii  libmono-data-tds2.0-cil                                     2.10.5-1                                Mono Data Library (for CLI 2.0)
ii  libmono-data-tds4.0-cil                                     2.10.5-1                                Mono Data Library (for CLI 4.0)
ii  libmono-db2-1.0-cil                                         2.10.5-1                                Mono DB2 library
ii  libmono-debugger-soft2.0-cil                                2.10.5-1                                Mono Soft Debugger library (for CLI 2.0)
ii  libmono-debugger-soft4.0-cil                                2.10.5-1                                Mono Soft Debugger library (for CLI 4.0)
ii  libmono-http4.0-cil                                         2.10.5-1                                Mono.Http library (for CLI 4.0)
ii  libmono-i18n-cjk4.0-cil                                     2.10.5-1                                Mono I18N.CJK library (for CLI 4.0)
ii  libmono-i18n-mideast4.0-cil                                 2.10.5-1                                Mono I18N.MidEast library (for CLI 4.0)
ii  libmono-i18n-other4.0-cil                                   2.10.5-1                                Mono I18N.Other library (for CLI 4.0)
ii  libmono-i18n-rare4.0-cil                                    2.10.5-1                                Mono I18N.Rare library (for CLI 4.0)
ii  libmono-i18n-west2.0-cil                                    2.10.5-1                                Mono I18N.West library (for CLI 2.0)
ii  libmono-i18n-west4.0-cil                                    2.10.5-1                                Mono I18N.West library (for CLI 4.0)
ii  libmono-i18n2.0-cil                                         2.10.5-1                                Mono I18N libraries (for CLI 2.0)
ii  libmono-i18n4.0-all                                         2.10.5-1                                Mono I18N libraries (for CLI 4.0)
ii  libmono-i18n4.0-cil                                         2.10.5-1                                Mono I18N base library (for CLI 4.0)
ii  libmono-ldap2.0-cil                                         2.10.5-1                                Mono LDAP library (for CLI 2.0)
ii  libmono-ldap4.0-cil                                         2.10.5-1                                Mono LDAP library (for CLI 4.0)
ii  libmono-management2.0-cil                                   2.10.5-1                                Mono Management library (for CLI 2.0)
ii  libmono-management4.0-cil                                   2.10.5-1                                Mono Management library (for CLI 4.0)
ii  libmono-messaging-rabbitmq2.0-cil                           2.10.5-1                                Mono Messaging RabbitMQ library (for CLI 2.0)
ii  libmono-messaging-rabbitmq4.0-cil                           2.10.5-1                                Mono Messaging RabbitMQ library (for CLI 4.0)
ii  libmono-messaging2.0-cil                                    2.10.5-1                                Mono Messaging library (for CLI 2.0)
ii  libmono-messaging4.0-cil                                    2.10.5-1                                Mono Messaging library (for CLI 4.0)
ii  libmono-microsoft-build-engine4.0-cil                       2.10.5-1                                Mono Microsoft.Build.Engine library (for CLI 4.0)
ii  libmono-microsoft-build-framework4.0-cil                    2.10.5-1                                Mono Microsoft.Build.Framework library (for CLI 4.0)
ii  libmono-microsoft-build-tasks-v4.0-4.0-cil                  2.10.5-1                                Mono Microsoft.Build.Tasks.v4.0 library (for CLI 4.0)
ii  libmono-microsoft-build-utilities-v4.0-4.0-cil              2.10.5-1                                Mono Microsoft.Build.Utilities.v4.0 library (for CLI 4.0)
ii  libmono-microsoft-build2.0-cil                              2.10.5-1                                Mono Microsoft.Build libraries (for CLI 2.0)
ii  libmono-microsoft-csharp4.0-cil                             2.10.5-1                                Mono Microsoft.CSharp library (for CLI 4.0)
ii  libmono-microsoft-visualc10.0-cil                           2.10.5-1                                Mono Microsoft.VisualC library (for CLI 4.0)
ii  libmono-microsoft-web-infrastructure1.0-cil                 2.10.5-1                                Mono Microsoft.Web.Infrastructure library (for CLI 4.0)
ii  libmono-microsoft8.0-cil                                    2.10.5-1                                Mono Microsoft libraries (for CLI 2.0)
ii  libmono-npgsql2.0-cil                                       2.10.5-1                                Mono Npgsql library (for CLI 2.0)
ii  libmono-npgsql4.0-cil                                       2.10.5-1                                Mono Npgsql library (for CLI 4.0)
ii  libmono-opensystem-c4.0-cil                                 2.10.5-1                                Mono OpenSystem.C library (for CLI 4.0)
ii  libmono-oracle2.0-cil                                       2.10.5-1                                Mono Oracle library (for CLI 2.0)
ii  libmono-oracle4.0-cil                                       2.10.5-1                                Mono Oracle library (for CLI 4.0)
ii  libmono-peapi2.0-cil                                        2.10.5-1                                Mono PEAPI library (for CLI 2.0)
ii  libmono-peapi4.0-cil                                        2.10.5-1                                Mono PEAPI library (for CLI 4.0)
ii  libmono-posix2.0-cil                                        2.10.5-1                                Mono.Posix library (for CLI 2.0)
ii  libmono-posix4.0-cil                                        2.10.5-1                                Mono.Posix library (for CLI 4.0)
ii  libmono-profiler                                            2.10.5-1                                Mono profiler libraries
ii  libmono-rabbitmq2.0-cil                                     2.10.5-1                                Mono RabbitMQ.Client library (for CLI 2.0)
ii  libmono-rabbitmq4.0-cil                                     2.10.5-1                                Mono RabbitMQ.Client library (for CLI 4.0)
ii  libmono-relaxng2.0-cil                                      2.10.5-1                                Mono Relaxng library (for CLI 2.0)
ii  libmono-relaxng4.0-cil                                      2.10.5-1                                Mono Relaxng library (for CLI 4.0)
ii  libmono-security2.0-cil                                     2.10.5-1                                Mono Security library (for CLI 2.0)
ii  libmono-security4.0-cil                                     2.10.5-1                                Mono Security library (for CLI 4.0)
ii  libmono-sharpzip2.6-cil                                     2.10.5-1                                Mono SharpZipLib library (for CLI 2.0)
ii  libmono-sharpzip2.84-cil                                    2.10.5-1                                Mono SharpZipLib library (for CLI 2.0)
ii  libmono-sharpzip4.84-cil                                    2.10.5-1                                Mono SharpZipLib library (for CLI 4.0)
ii  libmono-simd2.0-cil                                         2.10.5-1                                Mono SIMD (for CLI 2.0)
ii  libmono-simd4.0-cil                                         2.10.5-1                                Mono SIMD (for CLI 4.0)
ii  libmono-sqlite2.0-cil                                       2.10.5-1                                Mono Sqlite library (for CLI 2.0)
ii  libmono-sqlite4.0-cil                                       2.10.5-1                                Mono Sqlite library (for CLI 4.0)
ii  libmono-system-componentmodel-composition4.0-cil            2.10.5-1                                Mono System.ComponentModel.Composition library (for CLI 4.0)
ii  libmono-system-componentmodel-dataannotations4.0-cil        2.10.5-1                                Mono System.ComponentModel.DataAnnotations library (for CLI 4.0)
ii  libmono-system-configuration-install4.0-cil                 2.10.5-1                                Mono System.Configuration.Install library (for CLI 4.0)
ii  libmono-system-configuration4.0-cil                         2.10.5-1                                Mono System.Configuration library (for CLI 4.0)
ii  libmono-system-core4.0-cil                                  2.10.5-1                                Mono System.Core library (for CLI 4.0)
ii  libmono-system-data-datasetextensions4.0-cil                2.10.5-1                                Mono System.Data.DataSetExtensions library (for CLI 4.0)
ii  libmono-system-data-linq2.0-cil                             2.10.5-1                                Mono System.Data.Linq Library (for CLI 2.0)
ii  libmono-system-data-linq4.0-cil                             2.10.5-1                                Mono System.Data.Linq Library (for CLI 4.0)
ii  libmono-system-data-services-client4.0-cil                  2.10.5-1                                Mono System.Data.Services.Client library (for CLI 4.0)
ii  libmono-system-data-services4.0-cil                         2.10.5-1                                Mono System.Data.Services library (for CLI 4.0)
ii  libmono-system-data2.0-cil                                  2.10.5-1                                Mono System.Data Library (for CLI 2.0)
ii  libmono-system-data4.0-cil                                  2.10.5-1                                Mono System.Data library (for CLI 4.0)
ii  libmono-system-design4.0-cil                                2.10.5-1                                Mono System.Design Library (for CLI 4.0)
ii  libmono-system-drawing-design4.0-cil                        2.10.5-1                                Mono System.Drawing.Design (for CLI 4.0)
ii  libmono-system-drawing4.0-cil                               2.10.5-1                                Mono System.Drawing library (for CLI 4.0)
ii  libmono-system-dynamic4.0-cil                               2.10.5-1                                Mono System.Dynamic library (for CLI 4.0)
ii  libmono-system-enterpriseservices4.0-cil                    2.10.5-1                                Mono System.EnterpriseServices library (for CLI 4.0)
ii  libmono-system-identitymodel-selectors4.0-cil               2.10.5-1                                Mono System.IdentityModel.Selectors Library (for CLI 4.0)
ii  libmono-system-identitymodel4.0-cil                         2.10.5-1                                Mono System.IdentityModel Library (for CLI 4.0)
ii  libmono-system-ldap2.0-cil                                  2.10.5-1                                Mono System.DirectoryServices library (for CLI 2.0)
ii  libmono-system-ldap4.0-cil                                  2.10.5-1                                Mono System.DirectoryServices library (for CLI 4.0)
ii  libmono-system-management4.0-cil                            2.10.5-1                                Mono System.Management library (for CLI 4.0)
ii  libmono-system-messaging2.0-cil                             2.10.5-1                                Mono System.Messaging Library (for CLI 2.0)
ii  libmono-system-messaging4.0-cil                             2.10.5-1                                Mono System.Messaging library (for CLI 4.0)
ii  libmono-system-net4.0-cil                                   2.10.5-1                                Mono System.Net library (for CLI 4.0)
ii  libmono-system-numerics4.0-cil                              2.10.5-1                                Mono System.Numerics library (for CLI 4.0)
ii  libmono-system-runtime-caching4.0-cil                       2.10.5-1                                Mono System.Runtime.Caching Library (for CLI 4.0)
ii  libmono-system-runtime-durableinstancing4.0-cil             2.10.5-1                                Mono System.Runtime.DurableInstancing Library (for CLI 4.0)
ii  libmono-system-runtime-serialization-formatters-soap4.0-cil 2.10.5-1                                Mono System.Runtime.Serialization.Formatters.Soap Library (for CLI 4.0)
ii  libmono-system-runtime-serialization4.0-cil                 2.10.5-1                                Mono System.Runtime.Serialization Library (for CLI 4.0)
ii  libmono-system-runtime2.0-cil                               2.10.5-1                                Mono System.Runtime Library (for CLI 2.0)
ii  libmono-system-runtime4.0-cil                               2.10.5-1                                Mono System.Runtime library (for CLI 4.0)
ii  libmono-system-security4.0-cil                              2.10.5-1                                Mono System.Security library (for CLI 4.0)
ii  libmono-system-servicemodel-discovery4.0-cil                2.10.5-1                                Mono System.ServiceModel.Discovery Library (for CLI 4.0)
ii  libmono-system-servicemodel-routing4.0-cil                  2.10.5-1                                Mono System.ServiceModel.Routing Library (for CLI 4.0)
ii  libmono-system-servicemodel-web4.0-cil                      2.10.5-1                                Mono System.ServiceModel.Web Library (for CLI 4.0)
ii  libmono-system-servicemodel4.0-cil                          2.10.5-1                                Mono System.ServiceModel Library (for CLI 4.0)
ii  libmono-system-serviceprocess4.0-cil                        2.10.5-1                                Mono System.ServiceProcess library (for CLI 4.0)
ii  libmono-system-transactions4.0-cil                          2.10.5-1                                Mono System.Transactions library (for CLI 4.0)
ii  libmono-system-web-abstractions4.0-cil                      2.10.5-1                                Mono System.Web.Abstractions library (for CLI 4.0)
ii  libmono-system-web-applicationservices4.0-cil               2.10.5-1                                Mono System.Web.ApplicationServices library (for CLI 4.0)
ii  libmono-system-web-dynamicdata4.0-cil                       2.10.5-1                                Mono System.Web.DynamicData library (for CLI 4.0)
ii  libmono-system-web-extensions-design4.0-cil                 2.10.5-1                                Mono System.Web.Extensions.Design library (for CLI 4.0)
ii  libmono-system-web-extensions4.0-cil                        2.10.5-1                                Mono System.Web.Extensions library (for CLI 4.0)
ii  libmono-system-web-mvc1.0-cil                               2.10.5-1                                Mono ASP.NET MVC Library (for CLI 2.0)
ii  libmono-system-web-mvc2.0-cil                               2.10.5-1                                Mono ASP.NET MVC Library (for CLI 2.0)
ii  libmono-system-web-routing4.0-cil                           2.10.5-1                                Mono System.Web.Routing (for CLI 4.0)
ii  libmono-system-web-services4.0-cil                          2.10.5-1                                Mono System.Web.Services (for CLI 4.0)
ii  libmono-system-web2.0-cil                                   2.10.5-1                                Mono System.Web Library (for CLI 2.0)
ii  libmono-system-web4.0-cil                                   2.10.5-1                                Mono System.Web library (for CLI 4.0)
ii  libmono-system-windows-forms-datavisualization4.0-cil       2.10.5-1                                Mono System.Windows.Forms.DataVisualization Library (for CLI 4.0)
ii  libmono-system-windows-forms4.0-cil                         2.10.5-1                                Mono System.Windows.Forms Library (for CLI 4.0)
ii  libmono-system-xaml4.0-cil                                  2.10.5-1                                Mono System.Xaml Library (for CLI 4.0)
ii  libmono-system-xml-linq4.0-cil                              2.10.5-1                                Mono System.Xml.Linq library (for CLI 4.0)
ii  libmono-system-xml4.0-cil                                   2.10.5-1                                Mono System.Xml library (for CLI 4.0)
ii  libmono-system2.0-cil                                       2.10.5-1                                Mono System libraries (for CLI 2.0)
ii  libmono-system4.0-cil                                       2.10.5-1                                Mono System libraries (for CLI 4.0)
ii  libmono-tasklets2.0-cil                                     2.10.5-1                                Mono Tasklets library (for CLI 2.0)
ii  libmono-tasklets4.0-cil                                     2.10.5-1                                Mono Tasklets library (for CLI 4.0)
ii  libmono-wcf3.0-cil                                          2.10.5-1                                Mono WCF libraries (for CLI 2.0)
ii  libmono-web4.0-cil                                          2.10.5-1                                Mono.Web library (for CLI 4.0)
ii  libmono-webbrowser2.0-cil                                   2.10.5-1                                Mono Web Browser library (for CLI 2.0)
ii  libmono-webbrowser4.0-cil                                   2.10.5-1                                Mono Web Browser library (for CLI 4.0)
ii  libmono-webmatrix-data4.0-cil                               2.10.5-1                                Mono WebMatrix.Data Library (for CLI 2.0)
ii  libmono-windowsbase3.0-cil                                  2.10.5-1                                Mono WindowsBase library (for CLI 2.0)
ii  libmono-windowsbase4.0-cil                                  2.10.5-1                                Mono WindowsBase library (for CLI 4.0)
ii  libmono-winforms2.0-cil                                     2.10.5-1                                Mono System.Windows.Forms library (for CLI 2.0)
ii  libmono-zeroconf1.0-cil                                     0.9.0-3~ubuntu0.1                       CLI library for multicast DNS service discovery
ii  libmono2.0-cil                                              2.10.5-1                                Mono libraries (for CLI 2.0)
ii  libnotify0.4-cil                                            0.4.0~r3032-4~ubuntu0.1                 CLI library for desktop notifications
ii  libnunit2.5-cil                                             2.5.10.11092+dfsg-1                     Unit test framework for CLI
ii  libtaglib2.0-cil                                            2.0.3.7+dfsg-1build1                    CLI library for accessing audio and video files metadata
ii  libubuntuone1.0-cil                                         0.11.0-0ubuntu3                         CLI bindings for Ubuntu One widget library
ii  libwebkit1.1-cil                                            0.3-3ubuntu3                            CLI binding for the WebKit library
ii  mono-2.0-gac                                                2.10.5-1                                Mono GAC tool (for CLI 2.0)
ii  mono-2.0-service                                            2.10.5-1                                Mono service manager for CLI 2.0
ii  mono-4.0-gac                                                2.10.5-1                                Mono GAC tool (for CLI 4.0)
ii  mono-4.0-service                                            2.10.5-1                                Mono service manager for CLI 4.0
ii  mono-addins-utils                                           0.6.2-1ubuntu1~hyper1+oneiric           Command-line utility for Mono.Addins management
ii  mono-complete                                               2.10.5-1                                complete Mono runtime, development tools and all libraries
ii  mono-csharp-shell                                           2.10.5-1                                interactive C# shell
ii  mono-devel                                                  2.10.5-1                                Mono development tools
ii  mono-dmcs                                                   2.10.5-1                                Mono C# 4.0 compiler for CLI 4.0
ii  mono-gac                                                    2.10.5-1                                Mono GAC tool
ii  mono-gmcs                                                   2.10.5-1                                Mono C# 2.0 and C# 3.0 compiler for CLI 2.0
ii  mono-jay                                                    2.10.5-1                                LALR(1) parser generator oriented to Java/CLI
ii  mono-mcs                                                    2.10.5-1                                Mono C# 2.0 / 3.0 / 4.0  compiler for CLI 2.0 / 4.0
ii  mono-runtime                                                2.10.5-1                                Mono runtime
ii  mono-runtime-sgen                                           2.10.5-1                                Mono runtime - SGen (experimental)
ii  mono-utils                                                  2.10.5-1                                Mono utilities
ii  mono-xbuild                                                 2.10.5-1                                MSBuild-compatible build system for Mono
ii  monodoc-base                                                2.10.5-1                                shared MonoDoc binaries
ii  monodoc-browser                                             2.10-1                                  MonoDoc GTK+ based viewer
ii  monodoc-gtk2.0-manual                                       2.12.10-2ubuntu1                        compiled XML documentation for GTK# 2.10
ii  monodoc-manual                                              2.10.5-1                                compiled XML documentation from the Mono project
ii  tomboy                                                      1.8.0-1ubuntu1.1.1                      desktop note taking program using Wiki style links
ii  ubuntu-mono                                                 0.0.37                                  Ubuntu Mono Icon theme

```

Output of "which mono":
```
/usr/bin/mono
```

---

### Post by directhex on 2012-03-30
> **MadHatter93 said:**
> Yes, I'm sure it's 11.10, I installed it myself.

Output of "dpkg -l \*-cil \*mono\* tomboy | grep ^ii":
```
ii  libappindicator0.1-cil                                      0.4.1-0ubuntu2                          CLI bindings for libappindicator
ii  libboo2.0.9-cil                                             0.9.5~git20110729.r1.202a430-1          python-like language and compiler for the CLI - library files
ii  libdbus-glib1.0-cil                                         0.5.0-3build1                           CLI implementation of D-Bus (GLib mainloop integration)
ii  libdbus1.0-cil                                              0.7.0-4                                 CLI implementation of D-Bus
ii  libgconf2.0-cil                                             2.24.2-1                                CLI binding for GConf 2.24
ii  libgdata1.7-cil                                             1.7.0.1-1build1                         Google GData CLI client library
ii  libgkeyfile1.0-cil                                          0.1-2ubuntu2                            GObject-based wrapper library for GKeyFile -- CLI bindings
ii  libglade2.0-cil                                             2.12.10-2ubuntu1                        CLI binding for the Glade libraries 2.6
ii  libglib2.0-cil                                              2.12.10-2ubuntu1                        CLI binding for the GLib utility library 2.12
ii  libgmime2.4-cil                                             2.4.26-0ubuntu2                         CLI binding for the GMime library
ii  libgtk-sharp-beans-cil                                      2.14.1-2build2                          Supplementary CLI bindings for GTK 2.14+
ii  libgtk2.0-cil                                               2.12.10-2ubuntu1                        CLI binding for the GTK+ toolkit 2.12
ii  libgudev1.0-cil                                             0.1-2build1                             GObject-based wrapper library for libudev -- CLI bindings
ii  liblaunchpad-integration1.0-cil                             0.1.54                                  CLI bindings for liblaunchpad-integration
ii  libmono-2.0-1                                               2.10.5-1                                Mono JIT library
ii  libmono-2.0-dev                                             2.10.5-1                                Mono JIT library - Development files
ii  libmono-accessibility2.0-cil                                2.10.5-1                                Mono Accessibility library (for CLI 2.0)
ii  libmono-accessibility4.0-cil                                2.10.5-1                                Mono Accessibility library (for CLI 4.0)
ii  libmono-addins-cil-dev                                      0.6.2-1ubuntu1~hyper1+oneiric           addin framework for extensible CLI applications/libraries
ii  libmono-addins-gui-cil-dev                                  0.6.2-1ubuntu1~hyper1+oneiric           GTK# frontend library for Mono.Addins
ii  libmono-addins-gui0.2-cil                                   0.6.2-1ubuntu1~hyper1+oneiric           GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                                       0.6.2-1ubuntu1~hyper1+oneiric           addin framework for extensible CLI applications/libraries
ii  libmono-c5-1.1-cil                                          2.10.5-1                                Mono C5 library
ii  libmono-cairo2.0-cil                                        2.10.5-1                                Mono Cairo library (for CLI 2.0)
ii  libmono-cairo4.0-cil                                        2.10.5-1                                Mono Cairo library (for CLI 4.0)
ii  libmono-cecil-private-cil                                   2.10.5-1                                Mono.Cecil library
ii  libmono-cil-dev                                             2.10.5-1                                Mono Base Class Libraries (BCL) - Development files
ii  libmono-codecontracts4.0-cil                                2.10.5-1                                Mono.CodeContracts library (for CLI 4.0)
ii  libmono-compilerservices-symbolwriter4.0-cil                2.10.5-1                                Mono.CompilerServices.SymbolWriter library (for CLI 4.0)
ii  libmono-corlib2.0-cil                                       2.10.5-1                                Mono core library (for CLI 2.0)
ii  libmono-corlib4.0-cil                                       2.10.5-1                                Mono core library (for CLI 4.0)
ii  libmono-cscompmgd8.0-cil                                    2.10.5-1                                Mono cscompmgd library (for CLI 2.0)
ii  libmono-csharp4.0-cil                                       2.10.5-1                                Mono.CSharp library (for CLI 4.0)
ii  libmono-custommarshalers4.0-cil                             2.10.5-1                                Mono CustomMarshalers library (for CLI 4.0)
ii  libmono-data-tds2.0-cil                                     2.10.5-1                                Mono Data Library (for CLI 2.0)
ii  libmono-data-tds4.0-cil                                     2.10.5-1                                Mono Data Library (for CLI 4.0)
ii  libmono-db2-1.0-cil                                         2.10.5-1                                Mono DB2 library
ii  libmono-debugger-soft2.0-cil                                2.10.5-1                                Mono Soft Debugger library (for CLI 2.0)
ii  libmono-debugger-soft4.0-cil                                2.10.5-1                                Mono Soft Debugger library (for CLI 4.0)
ii  libmono-http4.0-cil                                         2.10.5-1                                Mono.Http library (for CLI 4.0)
ii  libmono-i18n-cjk4.0-cil                                     2.10.5-1                                Mono I18N.CJK library (for CLI 4.0)
ii  libmono-i18n-mideast4.0-cil                                 2.10.5-1                                Mono I18N.MidEast library (for CLI 4.0)
ii  libmono-i18n-other4.0-cil                                   2.10.5-1                                Mono I18N.Other library (for CLI 4.0)
ii  libmono-i18n-rare4.0-cil                                    2.10.5-1                                Mono I18N.Rare library (for CLI 4.0)
ii  libmono-i18n-west2.0-cil                                    2.10.5-1                                Mono I18N.West library (for CLI 2.0)
ii  libmono-i18n-west4.0-cil                                    2.10.5-1                                Mono I18N.West library (for CLI 4.0)
ii  libmono-i18n2.0-cil                                         2.10.5-1                                Mono I18N libraries (for CLI 2.0)
ii  libmono-i18n4.0-all                                         2.10.5-1                                Mono I18N libraries (for CLI 4.0)
ii  libmono-i18n4.0-cil                                         2.10.5-1                                Mono I18N base library (for CLI 4.0)
ii  libmono-ldap2.0-cil                                         2.10.5-1                                Mono LDAP library (for CLI 2.0)
ii  libmono-ldap4.0-cil                                         2.10.5-1                                Mono LDAP library (for CLI 4.0)
ii  libmono-management2.0-cil                                   2.10.5-1                                Mono Management library (for CLI 2.0)
ii  libmono-management4.0-cil                                   2.10.5-1                                Mono Management library (for CLI 4.0)
ii  libmono-messaging-rabbitmq2.0-cil                           2.10.5-1                                Mono Messaging RabbitMQ library (for CLI 2.0)
ii  libmono-messaging-rabbitmq4.0-cil                           2.10.5-1                                Mono Messaging RabbitMQ library (for CLI 4.0)
ii  libmono-messaging2.0-cil                                    2.10.5-1                                Mono Messaging library (for CLI 2.0)
ii  libmono-messaging4.0-cil                                    2.10.5-1                                Mono Messaging library (for CLI 4.0)
ii  libmono-microsoft-build-engine4.0-cil                       2.10.5-1                                Mono Microsoft.Build.Engine library (for CLI 4.0)
ii  libmono-microsoft-build-framework4.0-cil                    2.10.5-1                                Mono Microsoft.Build.Framework library (for CLI 4.0)
ii  libmono-microsoft-build-tasks-v4.0-4.0-cil                  2.10.5-1                                Mono Microsoft.Build.Tasks.v4.0 library (for CLI 4.0)
ii  libmono-microsoft-build-utilities-v4.0-4.0-cil              2.10.5-1                                Mono Microsoft.Build.Utilities.v4.0 library (for CLI 4.0)
ii  libmono-microsoft-build2.0-cil                              2.10.5-1                                Mono Microsoft.Build libraries (for CLI 2.0)
ii  libmono-microsoft-csharp4.0-cil                             2.10.5-1                                Mono Microsoft.CSharp library (for CLI 4.0)
ii  libmono-microsoft-visualc10.0-cil                           2.10.5-1                                Mono Microsoft.VisualC library (for CLI 4.0)
ii  libmono-microsoft-web-infrastructure1.0-cil                 2.10.5-1                                Mono Microsoft.Web.Infrastructure library (for CLI 4.0)
ii  libmono-microsoft8.0-cil                                    2.10.5-1                                Mono Microsoft libraries (for CLI 2.0)
ii  libmono-npgsql2.0-cil                                       2.10.5-1                                Mono Npgsql library (for CLI 2.0)
ii  libmono-npgsql4.0-cil                                       2.10.5-1                                Mono Npgsql library (for CLI 4.0)
ii  libmono-opensystem-c4.0-cil                                 2.10.5-1                                Mono OpenSystem.C library (for CLI 4.0)
ii  libmono-oracle2.0-cil                                       2.10.5-1                                Mono Oracle library (for CLI 2.0)
ii  libmono-oracle4.0-cil                                       2.10.5-1                                Mono Oracle library (for CLI 4.0)
ii  libmono-peapi2.0-cil                                        2.10.5-1                                Mono PEAPI library (for CLI 2.0)
ii  libmono-peapi4.0-cil                                        2.10.5-1                                Mono PEAPI library (for CLI 4.0)
ii  libmono-posix2.0-cil                                        2.10.5-1                                Mono.Posix library (for CLI 2.0)
ii  libmono-posix4.0-cil                                        2.10.5-1                                Mono.Posix library (for CLI 4.0)
ii  libmono-profiler                                            2.10.5-1                                Mono profiler libraries
ii  libmono-rabbitmq2.0-cil                                     2.10.5-1                                Mono RabbitMQ.Client library (for CLI 2.0)
ii  libmono-rabbitmq4.0-cil                                     2.10.5-1                                Mono RabbitMQ.Client library (for CLI 4.0)
ii  libmono-relaxng2.0-cil                                      2.10.5-1                                Mono Relaxng library (for CLI 2.0)
ii  libmono-relaxng4.0-cil                                      2.10.5-1                                Mono Relaxng library (for CLI 4.0)
ii  libmono-security2.0-cil                                     2.10.5-1                                Mono Security library (for CLI 2.0)
ii  libmono-security4.0-cil                                     2.10.5-1                                Mono Security library (for CLI 4.0)
ii  libmono-sharpzip2.6-cil                                     2.10.5-1                                Mono SharpZipLib library (for CLI 2.0)
ii  libmono-sharpzip2.84-cil                                    2.10.5-1                                Mono SharpZipLib library (for CLI 2.0)
ii  libmono-sharpzip4.84-cil                                    2.10.5-1                                Mono SharpZipLib library (for CLI 4.0)
ii  libmono-simd2.0-cil                                         2.10.5-1                                Mono SIMD (for CLI 2.0)
ii  libmono-simd4.0-cil                                         2.10.5-1                                Mono SIMD (for CLI 4.0)
ii  libmono-sqlite2.0-cil                                       2.10.5-1                                Mono Sqlite library (for CLI 2.0)
ii  libmono-sqlite4.0-cil                                       2.10.5-1                                Mono Sqlite library (for CLI 4.0)
ii  libmono-system-componentmodel-composition4.0-cil            2.10.5-1                                Mono System.ComponentModel.Composition library (for CLI 4.0)
ii  libmono-system-componentmodel-dataannotations4.0-cil        2.10.5-1                                Mono System.ComponentModel.DataAnnotations library (for CLI 4.0)
ii  libmono-system-configuration-install4.0-cil                 2.10.5-1                                Mono System.Configuration.Install library (for CLI 4.0)
ii  libmono-system-configuration4.0-cil                         2.10.5-1                                Mono System.Configuration library (for CLI 4.0)
ii  libmono-system-core4.0-cil                                  2.10.5-1                                Mono System.Core library (for CLI 4.0)
ii  libmono-system-data-datasetextensions4.0-cil                2.10.5-1                                Mono System.Data.DataSetExtensions library (for CLI 4.0)
ii  libmono-system-data-linq2.0-cil                             2.10.5-1                                Mono System.Data.Linq Library (for CLI 2.0)
ii  libmono-system-data-linq4.0-cil                             2.10.5-1                                Mono System.Data.Linq Library (for CLI 4.0)
ii  libmono-system-data-services-client4.0-cil                  2.10.5-1                                Mono System.Data.Services.Client library (for CLI 4.0)
ii  libmono-system-data-services4.0-cil                         2.10.5-1                                Mono System.Data.Services library (for CLI 4.0)
ii  libmono-system-data2.0-cil                                  2.10.5-1                                Mono System.Data Library (for CLI 2.0)
ii  libmono-system-data4.0-cil                                  2.10.5-1                                Mono System.Data library (for CLI 4.0)
ii  libmono-system-design4.0-cil                                2.10.5-1                                Mono System.Design Library (for CLI 4.0)
ii  libmono-system-drawing-design4.0-cil                        2.10.5-1                                Mono System.Drawing.Design (for CLI 4.0)
ii  libmono-system-drawing4.0-cil                               2.10.5-1                                Mono System.Drawing library (for CLI 4.0)
ii  libmono-system-dynamic4.0-cil                               2.10.5-1                                Mono System.Dynamic library (for CLI 4.0)
ii  libmono-system-enterpriseservices4.0-cil                    2.10.5-1                                Mono System.EnterpriseServices library (for CLI 4.0)
ii  libmono-system-identitymodel-selectors4.0-cil               2.10.5-1                                Mono System.IdentityModel.Selectors Library (for CLI 4.0)
ii  libmono-system-identitymodel4.0-cil                         2.10.5-1                                Mono System.IdentityModel Library (for CLI 4.0)
ii  libmono-system-ldap2.0-cil                                  2.10.5-1                                Mono System.DirectoryServices library (for CLI 2.0)
ii  libmono-system-ldap4.0-cil                                  2.10.5-1                                Mono System.DirectoryServices library (for CLI 4.0)
ii  libmono-system-management4.0-cil                            2.10.5-1                                Mono System.Management library (for CLI 4.0)
ii  libmono-system-messaging2.0-cil                             2.10.5-1                                Mono System.Messaging Library (for CLI 2.0)
ii  libmono-system-messaging4.0-cil                             2.10.5-1                                Mono System.Messaging library (for CLI 4.0)
ii  libmono-system-net4.0-cil                                   2.10.5-1                                Mono System.Net library (for CLI 4.0)
ii  libmono-system-numerics4.0-cil                              2.10.5-1                                Mono System.Numerics library (for CLI 4.0)
ii  libmono-system-runtime-caching4.0-cil                       2.10.5-1                                Mono System.Runtime.Caching Library (for CLI 4.0)
ii  libmono-system-runtime-durableinstancing4.0-cil             2.10.5-1                                Mono System.Runtime.DurableInstancing Library (for CLI 4.0)
ii  libmono-system-runtime-serialization-formatters-soap4.0-cil 2.10.5-1                                Mono System.Runtime.Serialization.Formatters.Soap Library (for CLI 4.0)
ii  libmono-system-runtime-serialization4.0-cil                 2.10.5-1                                Mono System.Runtime.Serialization Library (for CLI 4.0)
ii  libmono-system-runtime2.0-cil                               2.10.5-1                                Mono System.Runtime Library (for CLI 2.0)
ii  libmono-system-runtime4.0-cil                               2.10.5-1                                Mono System.Runtime library (for CLI 4.0)
ii  libmono-system-security4.0-cil                              2.10.5-1                                Mono System.Security library (for CLI 4.0)
ii  libmono-system-servicemodel-discovery4.0-cil                2.10.5-1                                Mono System.ServiceModel.Discovery Library (for CLI 4.0)
ii  libmono-system-servicemodel-routing4.0-cil                  2.10.5-1                                Mono System.ServiceModel.Routing Library (for CLI 4.0)
ii  libmono-system-servicemodel-web4.0-cil                      2.10.5-1                                Mono System.ServiceModel.Web Library (for CLI 4.0)
ii  libmono-system-servicemodel4.0-cil                          2.10.5-1                                Mono System.ServiceModel Library (for CLI 4.0)
ii  libmono-system-serviceprocess4.0-cil                        2.10.5-1                                Mono System.ServiceProcess library (for CLI 4.0)
ii  libmono-system-transactions4.0-cil                          2.10.5-1                                Mono System.Transactions library (for CLI 4.0)
ii  libmono-system-web-abstractions4.0-cil                      2.10.5-1                                Mono System.Web.Abstractions library (for CLI 4.0)
ii  libmono-system-web-applicationservices4.0-cil               2.10.5-1                                Mono System.Web.ApplicationServices library (for CLI 4.0)
ii  libmono-system-web-dynamicdata4.0-cil                       2.10.5-1                                Mono System.Web.DynamicData library (for CLI 4.0)
ii  libmono-system-web-extensions-design4.0-cil                 2.10.5-1                                Mono System.Web.Extensions.Design library (for CLI 4.0)
ii  libmono-system-web-extensions4.0-cil                        2.10.5-1                                Mono System.Web.Extensions library (for CLI 4.0)
ii  libmono-system-web-mvc1.0-cil                               2.10.5-1                                Mono ASP.NET MVC Library (for CLI 2.0)
ii  libmono-system-web-mvc2.0-cil                               2.10.5-1                                Mono ASP.NET MVC Library (for CLI 2.0)
ii  libmono-system-web-routing4.0-cil                           2.10.5-1                                Mono System.Web.Routing (for CLI 4.0)
ii  libmono-system-web-services4.0-cil                          2.10.5-1                                Mono System.Web.Services (for CLI 4.0)
ii  libmono-system-web2.0-cil                                   2.10.5-1                                Mono System.Web Library (for CLI 2.0)
ii  libmono-system-web4.0-cil                                   2.10.5-1                                Mono System.Web library (for CLI 4.0)
ii  libmono-system-windows-forms-datavisualization4.0-cil       2.10.5-1                                Mono System.Windows.Forms.DataVisualization Library (for CLI 4.0)
ii  libmono-system-windows-forms4.0-cil                         2.10.5-1                                Mono System.Windows.Forms Library (for CLI 4.0)
ii  libmono-system-xaml4.0-cil                                  2.10.5-1                                Mono System.Xaml Library (for CLI 4.0)
ii  libmono-system-xml-linq4.0-cil                              2.10.5-1                                Mono System.Xml.Linq library (for CLI 4.0)
ii  libmono-system-xml4.0-cil                                   2.10.5-1                                Mono System.Xml library (for CLI 4.0)
ii  libmono-system2.0-cil                                       2.10.5-1                                Mono System libraries (for CLI 2.0)
ii  libmono-system4.0-cil                                       2.10.5-1                                Mono System libraries (for CLI 4.0)
ii  libmono-tasklets2.0-cil                                     2.10.5-1                                Mono Tasklets library (for CLI 2.0)
ii  libmono-tasklets4.0-cil                                     2.10.5-1                                Mono Tasklets library (for CLI 4.0)
ii  libmono-wcf3.0-cil                                          2.10.5-1                                Mono WCF libraries (for CLI 2.0)
ii  libmono-web4.0-cil                                          2.10.5-1                                Mono.Web library (for CLI 4.0)
ii  libmono-webbrowser2.0-cil                                   2.10.5-1                                Mono Web Browser library (for CLI 2.0)
ii  libmono-webbrowser4.0-cil                                   2.10.5-1                                Mono Web Browser library (for CLI 4.0)
ii  libmono-webmatrix-data4.0-cil                               2.10.5-1                                Mono WebMatrix.Data Library (for CLI 2.0)
ii  libmono-windowsbase3.0-cil                                  2.10.5-1                                Mono WindowsBase library (for CLI 2.0)
ii  libmono-windowsbase4.0-cil                                  2.10.5-1                                Mono WindowsBase library (for CLI 4.0)
ii  libmono-winforms2.0-cil                                     2.10.5-1                                Mono System.Windows.Forms library (for CLI 2.0)
ii  libmono-zeroconf1.0-cil                                     0.9.0-3~ubuntu0.1                       CLI library for multicast DNS service discovery
ii  libmono2.0-cil                                              2.10.5-1                                Mono libraries (for CLI 2.0)
ii  libnotify0.4-cil                                            0.4.0~r3032-4~ubuntu0.1                 CLI library for desktop notifications
ii  libnunit2.5-cil                                             2.5.10.11092+dfsg-1                     Unit test framework for CLI
ii  libtaglib2.0-cil                                            2.0.3.7+dfsg-1build1                    CLI library for accessing audio and video files metadata
ii  libubuntuone1.0-cil                                         0.11.0-0ubuntu3                         CLI bindings for Ubuntu One widget library
ii  libwebkit1.1-cil                                            0.3-3ubuntu3                            CLI binding for the WebKit library
ii  mono-2.0-gac                                                2.10.5-1                                Mono GAC tool (for CLI 2.0)
ii  mono-2.0-service                                            2.10.5-1                                Mono service manager for CLI 2.0
ii  mono-4.0-gac                                                2.10.5-1                                Mono GAC tool (for CLI 4.0)
ii  mono-4.0-service                                            2.10.5-1                                Mono service manager for CLI 4.0
ii  mono-addins-utils                                           0.6.2-1ubuntu1~hyper1+oneiric           Command-line utility for Mono.Addins management
ii  mono-complete                                               2.10.5-1                                complete Mono runtime, development tools and all libraries
ii  mono-csharp-shell                                           2.10.5-1                                interactive C# shell
ii  mono-devel                                                  2.10.5-1                                Mono development tools
ii  mono-dmcs                                                   2.10.5-1                                Mono C# 4.0 compiler for CLI 4.0
ii  mono-gac                                                    2.10.5-1                                Mono GAC tool
ii  mono-gmcs                                                   2.10.5-1                                Mono C# 2.0 and C# 3.0 compiler for CLI 2.0
ii  mono-jay                                                    2.10.5-1                                LALR(1) parser generator oriented to Java/CLI
ii  mono-mcs                                                    2.10.5-1                                Mono C# 2.0 / 3.0 / 4.0  compiler for CLI 2.0 / 4.0
ii  mono-runtime                                                2.10.5-1                                Mono runtime
ii  mono-runtime-sgen                                           2.10.5-1                                Mono runtime - SGen (experimental)
ii  mono-utils                                                  2.10.5-1                                Mono utilities
ii  mono-xbuild                                                 2.10.5-1                                MSBuild-compatible build system for Mono
ii  monodoc-base                                                2.10.5-1                                shared MonoDoc binaries
ii  monodoc-browser                                             2.10-1                                  MonoDoc GTK+ based viewer
ii  monodoc-gtk2.0-manual                                       2.12.10-2ubuntu1                        compiled XML documentation for GTK# 2.10
ii  monodoc-manual                                              2.10.5-1                                compiled XML documentation from the Mono project
ii  tomboy                                                      1.8.0-1ubuntu1.1.1                      desktop note taking program using Wiki style links
ii  ubuntu-mono                                                 0.0.37                                  Ubuntu Mono Icon theme

```

Output of "which mono":
```
/usr/bin/mono
```

Hm.

Install mono-utils and run "monodis --assemblyref /usr/lib/mono/gac/dbus-sharp/1.0.0.0__5675b0c3093115b5/dbus-sharp.dll"

The output should be:
```
AssemblyRef Table
1: Version=4.0.0.0
	Name=mscorlib
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
2: Version=4.0.0.0
	Name=System
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
3: Version=4.0.0.0
	Name=System.Xml
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
4: Version=4.0.0.0
	Name=System.Core
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
```

---

### Post by MadHatter93 on 2012-03-30
Output:
```
bill@Ubuntu11:~$ monodis --assemblyref /usr/lib/mono/gac/dbus-sharp/1.0.0.0__5675b0c3093115b5/dbus-sharp.dll
AssemblyRef Table
1: Version=4.0.0.0
	Name=mscorlib
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
2: Version=4.0.0.0
	Name=System
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
3: Version=4.0.0.0
	Name=System.Xml
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
4: Version=4.0.0.0
	Name=System.Core
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 

bill@Ubuntu11:~$ 
```

---

### Post by directhex on 2012-03-30
... huh.

Can you install "debsums" and run "debsums -s -a" - this will produce a list of corrupted packages which you should reinstall.

---

### Post by MadHatter93 on 2012-03-30
Output: 
```
bill@Ubuntu11:~$ debsums tomboy -s -a
debsums: changed file /usr/share/gnome/help/tomboy/es/figures/notebook-icon.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/es/figures/tomboy-pindown.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/es/figures/tomboy-pinup.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/es/figures/tomboy-tools.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/eu/figures/notebook-icon.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/eu/figures/tomboy-pindown.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/eu/figures/tomboy-pinup.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/eu/figures/tomboy-tools.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/it/figures/notebook-icon.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/it/figures/tomboy-pindown.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/it/figures/tomboy-pinup.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/it/figures/tomboy-tools.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/pl/figures/notebook-icon.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/pl/figures/tomboy-pindown.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/pl/figures/tomboy-pinup.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/sv/figures/notebook-icon.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/sv/figures/tomboy-pindown.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/sv/figures/tomboy-pinup.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/sv/figures/tomboy-tools.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/uk/figures/tomboy-pindown.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/uk/figures/tomboy-pinup.png (from tomboy package)
debsums: changed file /usr/share/gnome/help/tomboy/uk/figures/tomboy-tools.png (from tomboy package)
bill@Ubuntu11:~$ 
```

I'm not entirely sure how to fix anything, because that's only help files, and they're only images

---

### Post by MadHatter93 on 2012-04-21
So, with a lot of internet research I've figured out part of the problem. Tomboy is set to compile using gmcs, the Mono 2.0 compiler, while Ubuntu has upgraded to Mono 4.0, and uses the csc compiler. Unfortunately, I do not know how to make Tomboy compile using csc instead of gmcs, because while I know how to compile from source, I don't do it very often and don't know much about options and switches. Could anyone help me here? I just need to tell Tomboy to point to Mono 4.0 instead of Mono 2.0 when compiling.

---

### Post by directhex on 2012-04-23
> **MadHatter93 said:**
> So, with a lot of internet research I've figured out part of the problem. Tomboy is set to compile using gmcs, the Mono 2.0 compiler, while Ubuntu has upgraded to Mono 4.0, and uses the csc compiler. Unfortunately, I do not know how to make Tomboy compile using csc instead of gmcs, because while I know how to compile from source, I don't do it very often and don't know much about options and switches. Could anyone help me here? I just need to tell Tomboy to point to Mono 4.0 instead of Mono 2.0 when compiling.

Huh? Where did your Tomboy come from then? All Mono packages in 11.10 are built for 4.0

---

