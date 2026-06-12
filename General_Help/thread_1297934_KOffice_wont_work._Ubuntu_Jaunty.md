---
title: "KOffice wont work. Ubuntu Jaunty"
date: 2009-10-22
forum: General Help
---

### Post by D0100 on 2009-10-22
I installed KOffice using apt. All went well, no errors. But when trying to open Krita on menu, nothing happens. I typed Krita in terminal and this was outputted:

```
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 0 CFGSimplification
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 1 IPConstantPropagation
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 2 InstructionCombining
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 3 CFGSimplification
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 4 TailDuplication
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 5 CFGSimplification
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 6 InstructionCombining
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 7 Reassociate
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 8 InstructionCombining
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 9 TailCallElimination
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 10 CFGSimplification
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 11 LICM
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 12 InstructionCombining
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 13 IndVarSimplify
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 14 LoopUnroll
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 15 InstructionCombining
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 16 LoadValueNumbering
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 17 GCSE
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 18 SCCP
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 19 InstructionCombining
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 20 DeadStoreElimination
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 21 AggressiveDCE
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 22 CFGSimplification
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 23 ConstantMerge
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 24 CFGSimplification
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 25 PromoteMemoryToRegister
GTLCore (Debug): in Optimiser_p.cpp at 111 in GTLCore::Optimiser::Private::setLevel: 26 InstructionCombining
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 0
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 1
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 2
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 3
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 4
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 5
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 6
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 7
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 8
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 9
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 10
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 11
GTLCore (Debug): in Type.cpp at 104 in GTLCore::Type::Type: Create type for 14

(<unknown>:21534): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so: wrong ELF class: ELFCLASS32
/home/pedro/.themes/Vista/gtk-2.0/gtkrc:192: Unable to locate image file in pixmap_path: "Toolbar/tool-insensitive.png"
/home/pedro/.themes/Vista/gtk-2.0/gtkrc:195: Background image options specified without filename
/home/pedro/.themes/Vista/gtk-2.0/gtkrc:241: Unable to locate image file in pixmap_path: "Toolbar/tool-insensitive.png"
/home/pedro/.themes/Vista/gtk-2.0/gtkrc:244: Background image options specified without filename
krita(21534) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kritapart.desktop not found"
krita(21534) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: Office/krita.desktop not found"

```Any idea?

---

