---
title: "Eclipse Ganymede USED to work"
date: 2009-09-23
forum: General Help
---

### Post by Rob_H on 2009-09-23
I've been running Eclipse 3.4 (Ganymede) quite happily on my Jaunty box for months. Suddenly, though, it has started crashing regularly with this error:

```
java.version=1.5.0_19
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2009-09-23 10:18:45.570
!MESSAGE Application error
!STACK 1
org.eclipse.swt.SWTError: XPCOM error -2147467262
        at org.eclipse.swt.browser.Mozilla.error(Mozilla.java:1638)
        at org.eclipse.swt.browser.Mozilla.setText(Mozilla.java:1861)
        at org.eclipse.swt.browser.Browser.setText(Browser.java:737)
        at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.generateContentForPage(BrowserIntroPartImplementation.java:252)
        at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.dynamicStandbyStateChanged(BrowserIntroPartImplementation.java:451)
        at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.doStandbyStateChanged(BrowserIntroPartImplementation.java:658)
        at org.eclipse.ui.internal.intro.impl.model.AbstractIntroPartImplementation.standbyStateChanged(AbstractIntroPartImplementation.java:249)
        at org.eclipse.ui.internal.intro.impl.model.IntroPartPresentation.standbyStateChanged(IntroPartPresentation.java:443)
        at org.eclipse.ui.intro.config.CustomizableIntroPart.standbyStateChanged(CustomizableIntroPart.java:266)
        at org.eclipse.ui.internal.ViewIntroAdapterPart$2.run(ViewIntroAdapterPart.java:74)
        at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
...

```

It seems to crash any time the internal web browser is invoked. I haven't changed my plugin configuration lately, so I can only assume that a regular software update caused this. Anyone else seeing it? For what it's worth, Eclipse 3.5 (Galileo) does not have the problem. Unfortunately, I can't give up 3.4 entirely because I need the Maven plugin, which is not compatible with 3.5. Any help appreciated.

---

### Post by justinwalsh on 2009-11-14
[FONT=Arial]Add
[/FONT][FONT=Arial][FONT=Courier New]-Dorg.eclipse.swt.browser.XULRunnerPath=/dev/null[/FONT]

to your eclipse.ini file
[/FONT][FONT=Arial]
[/FONT]

---

