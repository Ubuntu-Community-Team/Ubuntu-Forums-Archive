---
title: "Latex in Tomboy Notes"
date: 2011-09-26
forum: General Help
---

### Post by JCM_Pico on 2011-09-26
Hi there,

  I'm trying to write math formulas within a note. To accomplish that I found the [tomboy-latex add-in ]("http://live.gnome.org/Tomboy/PluginList") . I've downloaded the .dll file (pre compiled binary) and placed it in the ~/.config/tomboy/addins/ folder.
But when I try to insert a formula like \[\partial\], and the tomboy crashes, giving me this error....

```
Unhandled Exception: System.ComponentModel.Win32Exception: ApplicationName='dvipng', CommandLine='-pp 1 -T tight -o "/tmp/tbltx_2034832381.png" "/tmp/tbltx_2034832381.dvi"', CurrentDirectory='/tmp/'
  at System.Diagnostics.Process.Start_noshell (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] 
  at System.Diagnostics.Process.Start_common (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] 
  at System.Diagnostics.Process.Start () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Diagnostics.Process:Start ()
  at Tomboy.Latex.LatexImageRequest.CreateImage () [0x00000] 
  at Tomboy.Latex.LatexManager.WorkOnQueue () [0x00000]
``` 


Does anyone had this problem before?
Does anyone knows how to sove this?

---

### Post by JCM_Pico on 2011-09-27
bump...

---

