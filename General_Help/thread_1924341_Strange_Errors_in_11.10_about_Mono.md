---
title: "Strange Errors in 11.10 about Mono"
date: 2012-02-12
forum: General Help
---

### Post by Redcode on 2012-02-12
Suddenly last night i started getting errors while updating and installing any package..here's the output of dpkg --configure -a

> sudo dpkg --configure -a
Setting up libglade2.0-cil (2.12.10-2ubuntu1) ...

Unhandled Exception: System.MissingMethodException: Method not found: 'System.Reflection.PropertyInfo.op_Equality'.
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.MissingMethodException: Method not found: 'System.Reflection.PropertyInfo.op_Equality'.
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 
W: removing assembly: The assembly mscorlib.dll was not found or could not be loaded. failed!

Unhandled Exception: System.MissingMethodException: Method not found: 'System.Reflection.PropertyInfo.op_Equality'.
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.MissingMethodException: Method not found: 'System.Reflection.PropertyInfo.op_Equality'.
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 
E: installing Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.8.glade-sharp.dll failed
E: Installation of policy.2.8.glade-sharp with /usr/share/cli-common/runtimes.d/mono failed
dpkg: error processing libglade2.0-cil (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libtaglib2.0-cil (2.0.4.0-1~oneiric1) ...
* Installing 2 assemblies from libtaglib2.0-cil into Mono

Unhandled Exception: System.MissingMethodException: Method not found: 'System.Reflection.PropertyInfo.op_Equality'.
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.MissingMethodException: Method not found: 'System.Reflection.PropertyInfo.op_Equality'.
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 
E: installing Assembly /usr/lib/cli/taglib-sharp-2.0/taglib-sharp.dll failed
E: Installation of libtaglib2.0-cil with /usr/share/cli-common/runtimes.d/mono failed
dpkg: error processing libtaglib2.0-cil (--configure):
 subprocess installed post-installation script returned error exit status 29
dpkg: dependency problems prevent configuration of libtaglib-cil-dev:
 libtaglib-cil-dev depends on libtaglib2.0-cil (= 2.0.4.0-1~oneiric1); however:
  Package libtaglib2.0-cil is not configured yet.
dpkg: error processing libtaglib-cil-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libglade2.0-cil
 libtaglib2.0-cil
 libtaglib-cil-dev

tried force,clean,autoremove ..no change at all
someone knows what this is all about?
thnx

---

### Post by directhex on 2012-02-12
Paste the output of "dpkg -l | grep mono"

---

### Post by Redcode on 2012-02-13
i tried installing mono-devel after my last post to see if it helps but same thing
> ii  faenza-icons-mono                                           1.0                                             Faenza Icons Mono
ii  libmono-2.0-1                                               2.10.5-1                                        Mono JIT library
ii  libmono-2.0-dev                                             2.10.5-1                                        Mono JIT library - Development files
ii  libmono-accessibility2.0-cil                                2.10.5-1                                        Mono Accessibility library (for CLI 2.0)
ii  libmono-accessibility4.0-cil                                2.10.5-1                                        Mono Accessibility library (for CLI 4.0)
ii  libmono-addins-cil-dev                                      0.6.1-2ubuntu1                                  addin framework for extensible CLI applications/libraries
ii  libmono-addins-gui0.2-cil                                   0.6.1-2ubuntu1                                  GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                                       0.6.1-2ubuntu1                                  addin framework for extensible CLI applications/libraries
ii  libmono-c5-1.1-cil                                          2.10.5-1                                        Mono C5 library
ii  libmono-cairo2.0-cil                                        2.10.5-1                                        Mono Cairo library (for CLI 2.0)
ii  libmono-cairo4.0-cil                                        2.10.5-1                                        Mono Cairo library (for CLI 4.0)
ii  libmono-cecil-private-cil                                   2.10.5-1                                        Mono.Cecil library
iU  libmono-cil-dev                                             2.10.5-1                                        Mono Base Class Libraries (BCL) - Development files
ii  libmono-codecontracts4.0-cil                                2.10.5-1                                        Mono.CodeContracts library (for CLI 4.0)
ii  libmono-compilerservices-symbolwriter4.0-cil                2.10.5-1                                        Mono.CompilerServices.SymbolWriter library (for CLI 4.0)
ii  libmono-corlib2.0-cil                                       2.10.5-1                                        Mono core library (for CLI 2.0)
ii  libmono-corlib4.0-cil                                       2.10.5-1                                        Mono core library (for CLI 4.0)
ii  libmono-cscompmgd8.0-cil                                    2.10.5-1                                        Mono cscompmgd library (for CLI 2.0)
ii  libmono-csharp4.0-cil                                       2.10.5-1                                        Mono.CSharp library (for CLI 4.0)
ii  libmono-custommarshalers4.0-cil                             2.10.5-1                                        Mono CustomMarshalers library (for CLI 4.0)
ii  libmono-data-tds2.0-cil                                     2.10.5-1                                        Mono Data Library (for CLI 2.0)
ii  libmono-data-tds4.0-cil                                     2.10.5-1                                        Mono Data Library (for CLI 4.0)
ii  libmono-db2-1.0-cil                                         2.10.5-1                                        Mono DB2 library
ii  libmono-debugger-soft2.0-cil                                2.10.5-1                                        Mono Soft Debugger library (for CLI 2.0)
ii  libmono-debugger-soft4.0-cil                                2.10.5-1                                        Mono Soft Debugger library (for CLI 4.0)
ii  libmono-http4.0-cil                                         2.10.5-1                                        Mono.Http library (for CLI 4.0)
ii  libmono-i18n-cjk4.0-cil                                     2.10.5-1                                        Mono I18N.CJK library (for CLI 4.0)
ii  libmono-i18n-mideast4.0-cil                                 2.10.5-1                                        Mono I18N.MidEast library (for CLI 4.0)
ii  libmono-i18n-other4.0-cil                                   2.10.5-1                                        Mono I18N.Other library (for CLI 4.0)
ii  libmono-i18n-rare4.0-cil                                    2.10.5-1                                        Mono I18N.Rare library (for CLI 4.0)
ii  libmono-i18n-west2.0-cil                                    2.10.5-1                                        Mono I18N.West library (for CLI 2.0)
ii  libmono-i18n-west4.0-cil                                    2.10.5-1                                        Mono I18N.West library (for CLI 4.0)
ii  libmono-i18n2.0-cil                                         2.10.5-1                                        Mono I18N libraries (for CLI 2.0)
ii  libmono-i18n4.0-all                                         2.10.5-1                                        Mono I18N libraries (for CLI 4.0)
ii  libmono-i18n4.0-cil                                         2.10.5-1                                        Mono I18N base library (for CLI 4.0)
ii  libmono-ldap2.0-cil                                         2.10.5-1                                        Mono LDAP library (for CLI 2.0)
ii  libmono-ldap4.0-cil                                         2.10.5-1                                        Mono LDAP library (for CLI 4.0)
ii  libmono-management2.0-cil                                   2.10.5-1                                        Mono Management library (for CLI 2.0)
ii  libmono-management4.0-cil                                   2.10.5-1                                        Mono Management library (for CLI 4.0)
ii  libmono-messaging-rabbitmq2.0-cil                           2.10.5-1                                        Mono Messaging RabbitMQ library (for CLI 2.0)
ii  libmono-messaging-rabbitmq4.0-cil                           2.10.5-1                                        Mono Messaging RabbitMQ library (for CLI 4.0)
ii  libmono-messaging2.0-cil                                    2.10.5-1                                        Mono Messaging library (for CLI 2.0)
ii  libmono-messaging4.0-cil                                    2.10.5-1                                        Mono Messaging library (for CLI 4.0)
ii  libmono-microsoft-build-engine4.0-cil                       2.10.5-1                                        Mono Microsoft.Build.Engine library (for CLI 4.0)
ii  libmono-microsoft-build-framework4.0-cil                    2.10.5-1                                        Mono Microsoft.Build.Framework library (for CLI 4.0)
ii  libmono-microsoft-build-tasks-v4.0-4.0-cil                  2.10.5-1                                        Mono Microsoft.Build.Tasks.v4.0 library (for CLI 4.0)
ii  libmono-microsoft-build-utilities-v4.0-4.0-cil              2.10.5-1                                        Mono Microsoft.Build.Utilities.v4.0 library (for CLI 4.0)
ii  libmono-microsoft-build2.0-cil                              2.10.5-1                                        Mono Microsoft.Build libraries (for CLI 2.0)
ii  libmono-microsoft-csharp4.0-cil                             2.10.5-1                                        Mono Microsoft.CSharp library (for CLI 4.0)
ii  libmono-microsoft-visualc10.0-cil                           2.10.5-1                                        Mono Microsoft.VisualC library (for CLI 4.0)
ii  libmono-microsoft-web-infrastructure1.0-cil                 2.10.5-1                                        Mono Microsoft.Web.Infrastructure library (for CLI 4.0)
ii  libmono-microsoft8.0-cil                                    2.10.5-1                                        Mono Microsoft libraries (for CLI 2.0)
ii  libmono-npgsql2.0-cil                                       2.10.5-1                                        Mono Npgsql library (for CLI 2.0)
ii  libmono-npgsql4.0-cil                                       2.10.5-1                                        Mono Npgsql library (for CLI 4.0)
ii  libmono-opensystem-c4.0-cil                                 2.10.5-1                                        Mono OpenSystem.C library (for CLI 4.0)
ii  libmono-oracle2.0-cil                                       2.10.5-1                                        Mono Oracle library (for CLI 2.0)
ii  libmono-oracle4.0-cil                                       2.10.5-1                                        Mono Oracle library (for CLI 4.0)
ii  libmono-peapi2.0-cil                                        2.10.5-1                                        Mono PEAPI library (for CLI 2.0)
ii  libmono-peapi4.0-cil                                        2.10.5-1                                        Mono PEAPI library (for CLI 4.0)
ii  libmono-posix2.0-cil                                        2.10.5-1                                        Mono.Posix library (for CLI 2.0)
ii  libmono-posix4.0-cil                                        2.10.5-1                                        Mono.Posix library (for CLI 4.0)
ii  libmono-rabbitmq2.0-cil                                     2.10.5-1                                        Mono RabbitMQ.Client library (for CLI 2.0)
ii  libmono-rabbitmq4.0-cil                                     2.10.5-1                                        Mono RabbitMQ.Client library (for CLI 4.0)
ii  libmono-relaxng2.0-cil                                      2.10.5-1                                        Mono Relaxng library (for CLI 2.0)
ii  libmono-relaxng4.0-cil                                      2.10.5-1                                        Mono Relaxng library (for CLI 4.0)
ii  libmono-security2.0-cil                                     2.10.5-1                                        Mono Security library (for CLI 2.0)
ii  libmono-security4.0-cil                                     2.10.5-1                                        Mono Security library (for CLI 4.0)
ii  libmono-sharpzip2.6-cil                                     2.10.5-1                                        Mono SharpZipLib library (for CLI 2.0)
ii  libmono-sharpzip2.84-cil                                    2.10.5-1                                        Mono SharpZipLib library (for CLI 2.0)
ii  libmono-sharpzip4.84-cil                                    2.10.5-1                                        Mono SharpZipLib library (for CLI 4.0)
ii  libmono-simd2.0-cil                                         2.10.5-1                                        Mono SIMD (for CLI 2.0)
ii  libmono-simd4.0-cil                                         2.10.5-1                                        Mono SIMD (for CLI 4.0)
ii  libmono-sqlite2.0-cil                                       2.10.5-1                                        Mono Sqlite library (for CLI 2.0)
ii  libmono-sqlite4.0-cil                                       2.10.5-1                                        Mono Sqlite library (for CLI 4.0)
ii  libmono-system-componentmodel-composition4.0-cil            2.10.5-1                                        Mono System.ComponentModel.Composition library (for CLI 4.0)
ii  libmono-system-componentmodel-dataannotations4.0-cil        2.10.5-1                                        Mono System.ComponentModel.DataAnnotations library (for CLI 4.0)
ii  libmono-system-configuration-install4.0-cil                 2.10.5-1                                        Mono System.Configuration.Install library (for CLI 4.0)
ii  libmono-system-configuration4.0-cil                         2.10.5-1                                        Mono System.Configuration library (for CLI 4.0)
ii  libmono-system-core4.0-cil                                  2.10.5-1                                        Mono System.Core library (for CLI 4.0)
ii  libmono-system-data-datasetextensions4.0-cil                2.10.5-1                                        Mono System.Data.DataSetExtensions library (for CLI 4.0)
ii  libmono-system-data-linq2.0-cil                             2.10.5-1                                        Mono System.Data.Linq Library (for CLI 2.0)
ii  libmono-system-data-linq4.0-cil                             2.10.5-1                                        Mono System.Data.Linq Library (for CLI 4.0)
ii  libmono-system-data-services-client4.0-cil                  2.10.5-1                                        Mono System.Data.Services.Client library (for CLI 4.0)
ii  libmono-system-data-services4.0-cil                         2.10.5-1                                        Mono System.Data.Services library (for CLI 4.0)
ii  libmono-system-data2.0-cil                                  2.10.5-1                                        Mono System.Data Library (for CLI 2.0)
ii  libmono-system-data4.0-cil                                  2.10.5-1                                        Mono System.Data library (for CLI 4.0)
ii  libmono-system-design4.0-cil                                2.10.5-1                                        Mono System.Design Library (for CLI 4.0)
ii  libmono-system-drawing-design4.0-cil                        2.10.5-1                                        Mono System.Drawing.Design (for CLI 4.0)
ii  libmono-system-drawing4.0-cil                               2.10.5-1                                        Mono System.Drawing library (for CLI 4.0)
ii  libmono-system-dynamic4.0-cil                               2.10.5-1                                        Mono System.Dynamic library (for CLI 4.0)
ii  libmono-system-enterpriseservices4.0-cil                    2.10.5-1                                        Mono System.EnterpriseServices library (for CLI 4.0)
ii  libmono-system-identitymodel-selectors4.0-cil               2.10.5-1                                        Mono System.IdentityModel.Selectors Library (for CLI 4.0)
ii  libmono-system-identitymodel4.0-cil                         2.10.5-1                                        Mono System.IdentityModel Library (for CLI 4.0)
ii  libmono-system-ldap2.0-cil                                  2.10.5-1                                        Mono System.DirectoryServices library (for CLI 2.0)
ii  libmono-system-ldap4.0-cil                                  2.10.5-1                                        Mono System.DirectoryServices library (for CLI 4.0)
ii  libmono-system-management4.0-cil                            2.10.5-1                                        Mono System.Management library (for CLI 4.0)
ii  libmono-system-messaging2.0-cil                             2.10.5-1                                        Mono System.Messaging Library (for CLI 2.0)
ii  libmono-system-messaging4.0-cil                             2.10.5-1                                        Mono System.Messaging library (for CLI 4.0)
ii  libmono-system-net4.0-cil                                   2.10.5-1                                        Mono System.Net library (for CLI 4.0)
ii  libmono-system-numerics4.0-cil                              2.10.5-1                                        Mono System.Numerics library (for CLI 4.0)
ii  libmono-system-runtime-caching4.0-cil                       2.10.5-1                                        Mono System.Runtime.Caching Library (for CLI 4.0)
ii  libmono-system-runtime-durableinstancing4.0-cil             2.10.5-1                                        Mono System.Runtime.DurableInstancing Library (for CLI 4.0)
ii  libmono-system-runtime-serialization-formatters-soap4.0-cil 2.10.5-1                                        Mono System.Runtime.Serialization.Formatters.Soap Library (for CLI 4.0)
ii  libmono-system-runtime-serialization4.0-cil                 2.10.5-1                                        Mono System.Runtime.Serialization Library (for CLI 4.0)
ii  libmono-system-runtime2.0-cil                               2.10.5-1                                        Mono System.Runtime Library (for CLI 2.0)
ii  libmono-system-runtime4.0-cil                               2.10.5-1                                        Mono System.Runtime library (for CLI 4.0)
ii  libmono-system-security4.0-cil                              2.10.5-1                                        Mono System.Security library (for CLI 4.0)
ii  libmono-system-servicemodel-discovery4.0-cil                2.10.5-1                                        Mono System.ServiceModel.Discovery Library (for CLI 4.0)
ii  libmono-system-servicemodel-routing4.0-cil                  2.10.5-1                                        Mono System.ServiceModel.Routing Library (for CLI 4.0)
ii  libmono-system-servicemodel-web4.0-cil                      2.10.5-1                                        Mono System.ServiceModel.Web Library (for CLI 4.0)
ii  libmono-system-servicemodel4.0-cil                          2.10.5-1                                        Mono System.ServiceModel Library (for CLI 4.0)
ii  libmono-system-serviceprocess4.0-cil                        2.10.5-1                                        Mono System.ServiceProcess library (for CLI 4.0)
ii  libmono-system-transactions4.0-cil                          2.10.5-1                                        Mono System.Transactions library (for CLI 4.0)
ii  libmono-system-web-abstractions4.0-cil                      2.10.5-1                                        Mono System.Web.Abstractions library (for CLI 4.0)
ii  libmono-system-web-applicationservices4.0-cil               2.10.5-1                                        Mono System.Web.ApplicationServices library (for CLI 4.0)
ii  libmono-system-web-dynamicdata4.0-cil                       2.10.5-1                                        Mono System.Web.DynamicData library (for CLI 4.0)
ii  libmono-system-web-extensions-design4.0-cil                 2.10.5-1                                        Mono System.Web.Extensions.Design library (for CLI 4.0)
ii  libmono-system-web-extensions4.0-cil                        2.10.5-1                                        Mono System.Web.Extensions library (for CLI 4.0)
ii  libmono-system-web-mvc1.0-cil                               2.10.5-1                                        Mono ASP.NET MVC Library (for CLI 2.0)
ii  libmono-system-web-mvc2.0-cil                               2.10.5-1                                        Mono ASP.NET MVC Library (for CLI 2.0)
ii  libmono-system-web-routing4.0-cil                           2.10.5-1                                        Mono System.Web.Routing (for CLI 4.0)
ii  libmono-system-web-services4.0-cil                          2.10.5-1                                        Mono System.Web.Services (for CLI 4.0)
ii  libmono-system-web2.0-cil                                   2.10.5-1                                        Mono System.Web Library (for CLI 2.0)
ii  libmono-system-web4.0-cil                                   2.10.5-1                                        Mono System.Web library (for CLI 4.0)
ii  libmono-system-windows-forms-datavisualization4.0-cil       2.10.5-1                                        Mono System.Windows.Forms.DataVisualization Library (for CLI 4.0)
ii  libmono-system-windows-forms4.0-cil                         2.10.5-1                                        Mono System.Windows.Forms Library (for CLI 4.0)
ii  libmono-system-xaml4.0-cil                                  2.10.5-1                                        Mono System.Xaml Library (for CLI 4.0)
ii  libmono-system-xml-linq4.0-cil                              2.10.5-1                                        Mono System.Xml.Linq library (for CLI 4.0)
ii  libmono-system-xml4.0-cil                                   2.10.5-1                                        Mono System.Xml library (for CLI 4.0)
ii  libmono-system2.0-cil                                       2.10.5-1                                        Mono System libraries (for CLI 2.0)
ii  libmono-system4.0-cil                                       2.10.5-1                                        Mono System libraries (for CLI 4.0)
ii  libmono-tasklets2.0-cil                                     2.10.5-1                                        Mono Tasklets library (for CLI 2.0)
ii  libmono-tasklets4.0-cil                                     2.10.5-1                                        Mono Tasklets library (for CLI 4.0)
ii  libmono-wcf3.0-cil                                          2.10.5-1                                        Mono WCF libraries (for CLI 2.0)
ii  libmono-web4.0-cil                                          2.10.5-1                                        Mono.Web library (for CLI 4.0)
ii  libmono-webbrowser2.0-cil                                   2.10.5-1                                        Mono Web Browser library (for CLI 2.0)
ii  libmono-webbrowser4.0-cil                                   2.10.5-1                                        Mono Web Browser library (for CLI 4.0)
ii  libmono-webmatrix-data4.0-cil                               2.10.5-1                                        Mono WebMatrix.Data Library (for CLI 2.0)
ii  libmono-windowsbase3.0-cil                                  2.10.5-1                                        Mono WindowsBase library (for CLI 2.0)
ii  libmono-windowsbase4.0-cil                                  2.10.5-1                                        Mono WindowsBase library (for CLI 4.0)
ii  libmono-winforms2.0-cil                                     2.10.5-1                                        Mono System.Windows.Forms library (for CLI 2.0)
ii  libmono-zeroconf1.0-cil                                     0.9.0-3~ubuntu0.1                               CLI library for multicast DNS service discovery
ii  libmono2.0-cil                                              2.10.5-1                                        Mono libraries (for CLI 2.0)
ii  mono-4.0-gac                                                2.10.5-1                                        Mono GAC tool (for CLI 4.0)
ii  mono-csharp-shell                                           2.10.5-1                                        interactive C# shell
iU  mono-devel                                                  2.10.5-1                                        Mono development tools
ii  mono-dmcs                                                   2.10.5-1                                        Mono C# 4.0 compiler for CLI 4.0
ii  mono-gac                                                    2.10.5-1                                        Mono GAC tool
ii  mono-runtime                                                2.10.5-1                                        Mono runtime
ii  mono-xbuild                                                 2.10.5-1                                        MSBuild-compatible build system for Mono
ii  ubuntu-mono                                                 0.0.37                                          Ubuntu Mono Icon theme


---

### Post by directhex on 2012-02-13
Looks to me like your libmono-corlib4.0-cil package is corrupted.

Download [http://se.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib4.0-cil_2.10.5-1_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib4.0-cil_2.10.5-1_all.deb) and install it with "dpkg -i" in a terminal. Ought to fix things.

---

### Post by Redcode on 2012-02-13
> **directhex said:**
> Looks to me like your libmono-corlib4.0-cil package is corrupted.

Download [http://se.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib4.0-cil_2.10.5-1_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib4.0-cil_2.10.5-1_all.deb) and install it with "dpkg -i" in a terminal. Ought to fix things.

you were right sir,it was corlib4.0-cil_..reinstalling the pkg took care of the problem
thanks so much for your help :D

---

