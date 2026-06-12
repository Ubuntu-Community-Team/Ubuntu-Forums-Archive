---
title: "Problem Installing ADT with Eclipse"
date: 2010-01-16
forum: General Help
---

### Post by npattillo on 2010-01-16
I am just getting into development using Eclipse and I am trying to install the android development tool using it but I am getting this message;

Cannot complete the install because one or more required items could not be found.
  Software being installed: Android Development Tools 0.9.5.v200911191123-20404 (com.android.ide.eclipse.adt.feature.group 0.9.5.v200911191123-20404)
  Missing requirement: Android Development Tools 0.9.5.v200911191123-20404 (com.android.ide.eclipse.adt.feature.group 0.9.5.v200911191123-20404) requires 'org.eclipse.wst.xml.ui 0.0.0' but it could not be found

Any suggestions on what I need to do in terminal or otherwise to get this resolved? Thanks for your help.;)

---

### Post by MeanEYE on 2010-02-04
> **npattillo said:**
> I am just getting into development using Eclipse and I am trying to install the android development tool using it but I am getting this message;

Cannot complete the install because one or more required items could not be found.
  Software being installed: Android Development Tools 0.9.5.v200911191123-20404 (com.android.ide.eclipse.adt.feature.group 0.9.5.v200911191123-20404)
  Missing requirement: Android Development Tools 0.9.5.v200911191123-20404 (com.android.ide.eclipse.adt.feature.group 0.9.5.v200911191123-20404) requires 'org.eclipse.wst.xml.ui 0.0.0' but it could not be found

Any suggestions on what I need to do in terminal or otherwise to get this resolved? Thanks for your help.;)

I have the same problem. The thing is, if you manually download Eclipse form official site and then try to install ADT everything works like it should :/.

Am gonna try and find a solution, but... :) we'll see...

---

### Post by MeanEYE on 2010-02-04
Got it...

The thing is, default source for Eclipse is missing. The solution, go to "Install new software" from Help menu... then click on Add new software source with address "http://download.eclipse.org/releases/galileo/". Restart Eclipse and try installing ADT now. 

Please note that calculating dependencies took some time. :) 

Have fun!

---

### Post by reeceh on 2010-12-06
> **MeanEYE said:**
> Got it...

The thing is, default source for Eclipse is missing. The solution, go to "Install new software" from Help menu... then click on Add new software source with address "http://download.eclipse.org/releases/galileo/". Restart Eclipse and try installing ADT now. 

Please note that calculating dependencies took some time. :) 

Have fun!

You sir are my hero. 

Fixed my problem completely!

---

