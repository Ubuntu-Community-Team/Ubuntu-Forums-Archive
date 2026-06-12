---
title: "Problem in Java program (NMRViewJ) exporting Vector Graphics files using freeHEP"
date: 2012-08-22
forum: General Help
---

### Post by iggi916 on 2012-08-22
Hello all.

I'm relatively new to Ubuntu but I've been having a problem recently. I'm using a program called NMRViewJ to visualize NMR spectra. It has the ability to export these spectra as either bitmaps (png, jpeg etc) or vector graphics files (ps, svg etc). The bitmap export works. However, when trying to export as a vector graphics file, the export dialog doesn't show up and instead I get an error message such as below. The program comes with various freehep-*.jar files, one of which I assume it uses for the export and is causing this problem.

The export process worked for me briefly while I was using Natty and an older version of NMRViewJ, but I have been unable to recreate that. If anyone can help in any way, that would be greatly appreciated. Thanks!

```
Exception in thread "main" java.lang.ExceptionInInitializerError
	at org.freehep.graphicsio.gif.GIFImageWriteParam.<init>(GIFImageWriteParam.java:28)
	at org.freehep.graphicsio.gif.GIFImageWriter.getDefaultWriteParam(GIFImageWriter.java:73)
	at org.freehep.graphicsio.exportchooser.ImageExportFileType.<init>(ImageExportFileType.java:71)
	at org.freehep.graphicsio.gif.GIFExportFileType.<init>(GIFExportFileType.java:42)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
	at java.lang.reflect.Constructor.newInstance(Unknown Source)
	at java.lang.Class.newInstance0(Unknown Source)
	at java.lang.Class.newInstance(Unknown Source)
	at org.freehep.util.Service.providers(Service.java:71)
	at org.freehep.util.export.ExportFileTypeRegistry.addApplicationClasspathExportFileTypes(ExportFileTypeRegistry.java:118)
	at org.freehep.util.export.ExportFileTypeRegistry.getDefaultInstance(ExportFileTypeRegistry.java:50)
	at org.freehep.util.export.ExportFileType.getExportFileTypes(ExportFileType.java:181)
	at org.freehep.util.export.ExportFileType.getExportFileTypes(ExportFileType.java:173)
	at org.freehep.util.export.ExportDialog.addAllExportFileTypes(ExportDialog.java:64)
	at org.freehep.util.export.ExportDialog.<init>(ExportDialog.java:130)
	at org.freehep.util.export.ExportDialog.<init>(ExportDialog.java:90)
	at org.freehep.util.export.ExportDialog.<init>(ExportDialog.java:82)
	at com.onemoonsci.datachord.plot.ExportCmd.cmdProc2(ExportCmd.java:68)
	at com.onemoonsci.datachord.plot.ExportCmd.cmdProc(ExportCmd.java:32)
	at tcl.lang.Parser.evalObjv(Parser.java:811)
	at tcl.lang.Parser.eval2(Parser.java:1201)
	at tcl.lang.Procedure.cmdProc(Procedure.java:162)
	at tcl.lang.Parser.evalObjv(Parser.java:811)
	at tcl.lang.Parser.eval2(Parser.java:1201)
	at tcl.lang.Interp.eval(Interp.java:2277)
	at tcl.lang.Interp.eval(Interp.java:2254)
	at com.onemoonscientific.swank.SwkCommandListener.processEvent(SwkCommandListener.java:76)
	at com.onemoonscientific.swank.BindEvent.processEvent(BindEvent.java:86)
	at tcl.lang.Notifier.serviceEvent(Notifier.java:394)
	at tcl.lang.Notifier.doOneEvent(Notifier.java:538)
	at tcl.lang.cmd.VwaitCmd.cmdProc(VwaitCmd.java:65)
	at tcl.lang.AutoloadStub.cmdProc(Extension.java:128)
	at tcl.lang.Parser.evalObjv(Parser.java:811)
	at tcl.lang.Parser.eval2(Parser.java:1201)
	at tcl.lang.Interp.eval(Interp.java:2277)
	at tcl.lang.Interp.evalResource(Interp.java:2852)
	at tcl.lang.NvShell.main(NvShell.java:145)
Caused by: java.lang.NullPointerException
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.freehep.graphics2d.PixelGraphics2D.<clinit>(PixelGraphics2D.java:101)
	... 39 more
```

---

