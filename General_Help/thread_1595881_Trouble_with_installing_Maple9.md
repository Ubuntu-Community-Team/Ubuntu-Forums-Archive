---
title: "Trouble with installing Maple9"
date: 2010-10-13
forum: General Help
---

### Post by yellowzelo on 2010-10-13
Hi, this is what I get:

```
martin@compal:/data/MAPLE_9$ sh ./installMapleLinuxSU 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: cmd. line:6: warning: escape sequence `\.' treated as plain `.'

Launching installer...

**current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using defaultWarning: translation table syntax error: Unknown keysym name:  osfActivate**
Warning: ... found while parsing ':<Key>osfActivate:            ManagerParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfBeginLine
Warning: ... found while parsing ':<Key>osfBeginLine:           ManagerGadgetTraverseHome()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfHelp
Warning: ... found while parsing ':<Key>osfHelp:                        ManagerGadgetHelp()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:    DrawingAreaInput() ManagerParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfUp
Warning: ... found while parsing ':<Key>osfUp:          DrawingAreaInput() ManagerGadgetTraverseUp()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:    PrimitiveParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfHelp
Warning: ... found while parsing ':<Key>osfHelp:                Help()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:    PrimitiveParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfCancel
Warning: ... found while parsing ':<Key>osfCancel:      MenuEscape()'
Warning: String to TranslationTable conversion encountered errors                                                                                                     
Warning: translation table syntax error: Unknown keysym name:  osfSelect                                                                                              
Warning: ... found while parsing ':<Key>osfSelect:      ArmAndActivate()'                                                                                             
Warning: String to TranslationTable conversion encountered errors                                                                                                     
Warning: translation table syntax error: Unknown keysym name:  osfActivate                                                                                            
Warning: ... found while parsing ':<Key>osfActivate:            PrimitiveParentActivate()'                                                                            
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfCancel
Warning: ... found while parsing '<Key>osfCancel:                       MenuEscape()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfSelect
Warning: ... found while parsing ':<Key>osfSelect:      ManagerGadgetSelect()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfSelect
Warning: ... found while parsing ':<Key>osfSelect:      MenuBarGadgetSelect()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:    ManagerParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfHelp
Warning: ... found while parsing ':<Key>osfHelp:                MenuHelp()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfPrimaryPaste
Warning: ... found while parsing ':m <Key>osfPrimaryPaste:cut-primary()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:            PrimitiveParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.InternalError: Current locale is not supported
        at sun.awt.motif.MWindowPeer.pSetTitle(Native Method)
        at sun.awt.motif.MWindowPeer.init(Unknown Source)
        at sun.awt.motif.MFramePeer.<init>(Unknown Source)
        at sun.awt.motif.MToolkit.createFrame(Unknown Source)
        at java.awt.Frame.addNotify(Unknown Source)
        at com.zerog.ia.installer.Main.d(DashoA8113)
        at com.zerog.ia.installer.Main.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

```Could you help me, please?
Thank you.

---

