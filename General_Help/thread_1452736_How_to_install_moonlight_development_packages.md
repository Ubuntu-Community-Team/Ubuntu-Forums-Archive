---
title: "How to install moonlight development packages?"
date: 2010-04-12
forum: General Help
---

### Post by alex_sv on 2010-04-12
Hi all,

I'd like to install Moonlight dev packages on my Ubuntu.
I've installed all the related Moonlight packages on my Ubuntu 9.10, but still can't see Moonlight project template in MonoDevelop.

Am I missing something?

Does anyone tried to develop moonlight apps on ubuntu?
Is it possible to install and setup dev environment without having to compiling and configuring all the mono-related stuff?

I tried to ask this question on the Moonlight mailing list 4 days ago but still got no answer.

Thanks in advance!

At the moment I have the following packages installed:

> 
~$ dpkg -l | grep moon
ii  libmoon                                   1.0.1-3ubuntu0.xul191build1                            Free Software clone of Silverlight 1.0 - unstable runti
ii  moonlight-plugin-core                     1.0.1-3ubuntu0.xul191build1                            Free Software clone of Silverlight 1.0 - plugin core co
ii  moonlight-plugin-mozilla                  1.0.1-3ubuntu0.xul191build1                            Free Software clone of Silverlight 1.0 - Xulrunner 1.9 


> 
ii  libmono-accessibility2.0-cil              2.4.2.3+dfsg-2                                         Mono Accessibility library (for CLI 2.0)
ii  libmono-addins-gui0.2-cil                 0.4-5                                                  GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                     0.4-5                                                  addin framework for extensible CLI applications/librari
ii  libmono-cairo2.0-cil                      2.4.2.3+dfsg-2                                         Mono Cairo library (for CLI 2.0)
ii  libmono-cecil-private-cil                 2.4.2.3+dfsg-2                                         Mono.Cecil library
ii  libmono-corlib1.0-cil                     2.4.2.3+dfsg-2                                         Mono core library (for CLI 1.0)
ii  libmono-corlib2.0-cil                     2.4.2.3+dfsg-2                                         Mono core library (for CLI 2.0)
ii  libmono-data-tds1.0-cil                   2.4.2.3+dfsg-2                                         Mono Data library (for CLI 1.0)
ii  libmono-data-tds2.0-cil                   2.4.2.3+dfsg-2                                         Mono Data Library (for CLI 2.0)
ii  libmono-dev                               2.4.2.3+dfsg-2                                         Mono JIT library - Development files
ii  libmono-getoptions2.0-cil                 2.4.2.3+dfsg-2                                         Mono.GetOptions library (for CLI 2.0)
ii  libmono-i18n-west1.0-cil                  2.4.2.3+dfsg-2                                         Mono I18N.West library (for CLI 1.0)
ii  libmono-i18n-west2.0-cil                  2.4.2.3+dfsg-2                                         Mono I18N.West library (for CLI 2.0)
ii  libmono-management2.0-cil                 2.4.2.3+dfsg-2                                         Mono Management library (for CLI 2.0)
ii  libmono-messaging2.0-cil                  2.4.2.3+dfsg-2                                         Mono Messaging library (for CLI 2.0)
ii  libmono-peapi2.0-cil                      2.4.2.3+dfsg-2                                         Mono PEAPI library (for CLI 2.0)
ii  libmono-posix2.0-cil                      2.4.2.3+dfsg-2                                         Mono.Posix library (for CLI 2.0)
ii  libmono-relaxng1.0-cil                    2.4.2.3+dfsg-2                                         Mono Relaxng library (for CLI 1.0)
ii  libmono-security1.0-cil                   2.4.2.3+dfsg-2                                         Mono Security library (for CLI 1.0)
ii  libmono-security2.0-cil                   2.4.2.3+dfsg-2                                         Mono Security library (for CLI 2.0)
ii  libmono-sharpzip0.84-cil                  2.4.2.3+dfsg-2                                         Mono SharpZipLib library (for CLI 1.0)
ii  libmono-sharpzip2.84-cil                  2.4.2.3+dfsg-2                                         Mono SharpZipLib library (for CLI 2.0)
ii  libmono-sqlite2.0-cil                     2.4.2.3+dfsg-2                                         Mono Sqlite library (for CLI 2.0)
ii  libmono-system-data1.0-cil                2.4.2.3+dfsg-2                                         Mono System.Data library (for CLI 1.0)
ii  libmono-system-data2.0-cil                2.4.2.3+dfsg-2                                         Mono System.Data Library (for CLI 2.0)
ii  libmono-system-messaging2.0-cil           2.4.2.3+dfsg-2                                         Mono System.Messaging Library (for CLI 2.0)
ii  libmono-system-runtime1.0-cil             2.4.2.3+dfsg-2                                         Mono System.Runtime library (for CLI 1.0)
ii  libmono-system-runtime2.0-cil             2.4.2.3+dfsg-2                                         Mono System.Runtime Library (for CLI 2.0)
ii  libmono-system-web1.0-cil                 2.4.2.3+dfsg-2                                         Mono System.Web library (for CLI 1.0)
ii  libmono-system-web2.0-cil                 2.4.2.3+dfsg-2                                         Mono System.Web Library (for CLI 2.0)
ii  libmono-system1.0-cil                     2.4.2.3+dfsg-2                                         Mono System libraries (for CLI 1.0)
ii  libmono-system2.0-cil                     2.4.2.3+dfsg-2                                         Mono System libraries (for CLI 2.0)
ii  libmono-wcf3.0-cil                        2.4.2.3+dfsg-2                                         Mono WCF libraries (for CLI 2.0)
ii  libmono-webbrowser0.5-cil                 2.4.2.3+dfsg-2                                         Mono Web Browser library
ii  libmono-winforms2.0-cil                   2.4.2.3+dfsg-2                                         Mono System.Windows.Forms library (for CLI 2.0)
ii  libmono0                                  2.4.2.3+dfsg-2                                         Mono JIT library
ii  libmono2.0-cil                            2.4.2.3+dfsg-2                                         Mono libraries (for CLI 2.0)
ii  mono-2.0-devel                            2.4.2.3+dfsg-2                                         Mono development tools for CLI 2.0
ii  mono-2.0-gac                              2.4.2.3+dfsg-2                                         Mono GAC tool (for CLI 2.0)
rc  mono-common                               2.0.1-4ubuntu0.1                                       common files for Mono
ii  mono-csharp-shell                         2.4.2.3+dfsg-2                                         interactive C# shell
ii  mono-devel                                2.4.2.3+dfsg-2                                         Mono development tools
ii  mono-gac                                  2.4.2.3+dfsg-2                                         Mono GAC tool
ii  mono-gmcs                                 2.4.2.3+dfsg-2                                         Mono C# 2.0 and C# 3.0 compiler for CLI 2.0
ii  mono-runtime                              2.4.2.3+dfsg-2                                         Mono runtime
ii  monodevelop                               2.0+dfsg-2ubuntu3                                      Development Environment for GNOME
ii  monodevelop-nunit                         2.0+dfsg-2ubuntu3                                      NUnit plugin for MonoDevelop
ii  monodevelop-versioncontrol                2.0+dfsg-2ubuntu3                                      VersionControl plugin for MonoDevelop
ii  monodoc-base                              2.4.2.3+dfsg-2                                         shared MonoDoc binaries
ii  monodoc-manual                            2.4.2.3+dfsg-2                                         compiled XML documentation from the Mono project


---

