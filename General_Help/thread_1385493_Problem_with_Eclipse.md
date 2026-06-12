---
title: "Problem with Eclipse"
date: 2010-01-19
forum: General Help
---

### Post by kernco on 2010-01-19
I'm trying to setup the GWT (Google Web Toolkit) plugin for Eclipse.  I installed Eclipse 3.5 from the repositories and went through the normal process to install plugins.  I encountered these errors:
```
Cannot complete the install because one or more required items could not be found.
  Software being installed: Google Plugin for Eclipse 3.5 1.2.0.v200912062003 (com.google.gdt.eclipse.suite.e35.feature.feature.group 1.2.0.v200912062003)
  Missing requirement: Google Web Toolkit Plugin 1.2.0.v200912062003 (com.google.gwt.eclipse.core 1.2.0.v200912062003) requires 'bundle org.eclipse.wst.xml.ui 0.0.0' but it could not be found
  Cannot satisfy dependency:
    From: Google Plugin for Eclipse 3.5 1.2.0.v200912062003 (com.google.gdt.eclipse.suite.e35.feature.feature.group 1.2.0.v200912062003)
    To: com.google.gwt.eclipse.core [1.2.0.v200912062003]
```
After some Googling, it looked like a solution might be to remove the Eclipse packages and download and install it myself from the Eclipse website.  I tried this, unpacking it into my home directory, and encountered different problems.  Now when I go into the dialog to install new plugins, the box where it normally displays the choices is white.  If I mouse over the area, I see the tree view arrows appear, and if I click then the "next" button of the dialog activates, so it's registering that I'm checking the plugins to install, even if I can't see them.  The "Next" button doesn't do anything when I click on it, though.  It doesn't advance the dialog.

I'm using Sun's Java, not gcj or OpenJDK.  Does anyone know how I'd try fixing these errors?  I'd like a working Eclipse, whether it's from the packages or from installing it myself.  I searched my system for the missing org.eclipse.wst.xml.ui and it does appear in the Eclipse directory I unpacked myself, but not anywhere outside my home directory, so it's apparently not in what the Ubuntu packages installed.

---

### Post by devreez on 2010-02-03
I had this problem as well. I ended up finding the answer on the Google Group for the plugin itself.

Found here: [http://code.google.com/p/google-web-toolkit/issues/detail?id=4240](http://code.google.com/p/google-web-toolkit/issues/detail?id=4240)

[INDENT]I add update site [http://download.eclipse.org/releases/galileo](http://download.eclipse.org/releases/galileo) to list of update 
sites. Set this site as active. Update you eclipse. After this install plugins.[/INDENT]

---

