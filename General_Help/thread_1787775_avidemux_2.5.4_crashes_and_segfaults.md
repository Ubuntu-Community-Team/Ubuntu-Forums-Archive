---
title: "avidemux 2.5.4 crashes and segfaults"
date: 2011-06-21
forum: General Help
---

### Post by Rosscopico on 2011-06-21
Hi all,
I am trying to create a time lapse video. I have learned how to shot the time lapse frames using VLC. Ive also learned how to batch rename the files in sequential order using GPRename. Now Im trying to stitch the frames back together.
I made a short video of 176 frames & it plays, but when I try to save it I get the following crash message:-
```
Assert failed :0
 at line 386, file /build/buildd/avidemux-2.5.4/avidemux/ADM_encoder/adm_encConfig.cppADM_backTrack
videoCodecGetMode()
ADM_Composer::saveAsScript(char const*, char const*)
saveCrashProject()
ADM_backTrack
videoCodecGetMode()
ADM_Composer::saveAsScript(char const*, char const*)
A_saveWorkbench(char const*)
FileSel_ReadWrite(void (*)(char const*), int, char const*, char const*)
avidemux2_gtk() [0x816a279]
GUI_FileSelWrite(char const*, void (*)(char const*))
HandleAction(Action)
guiCallback(_GtkMenuItem*, void*)
g_cclosure_marshal_VOID__VOID
g_closure_invoke

g_signal_emit_valist
g_signal_emit
gtk_menu_item_activate
```

Can anyone pls tell me what it is & how to fix it?
PS, I am using Natty.

---

### Post by Rosscopico on 2011-06-21
I have also found when I try to stitch a larger number of frames (about 3700 frames) together, I get a different message, as the crash happens when I try to open the files in avidemux. The message is:-
```
Segfault
 at line 0, file ??ADM_backTrack
sig_segfault_handler(int)
[0xc97400]
fseek
picHeader::open(char const*)
ADM_Composer::addFile(char const*, unsigned char, fileType)
avidemux2_gtk() [0x808d6f2]
FileSel_ReadWrite(void (*)(char const*), int, char const*, char const*)
avidemux2_gtk() [0x816a279]
GUI_FileSelRead(char const*, void (*)(char const*))
HandleAction(Action)
guiCallback(_GtkMenuItem*, void*)
g_cclosure_marshal_VOID__VOID
g_closure_invoke

g_signal_emit_valist
g_signal_emit_by_name

g_cclosure_marshal_VOID__VOID
g_closure_invoke

```
Anyone have any suggestions?

---

