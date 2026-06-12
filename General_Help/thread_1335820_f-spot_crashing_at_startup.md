---
title: "f-spot crashing at startup"
date: 2009-11-23
forum: General Help
---

### Post by linuxgrrl on 2009-11-23
hi, 
fresh install of 9.10 amd64, trying to use f-spot with a photos.db from my prior ubuntu install (I've copied the photos over).  F-spot crashes on startup with a "fatal error." I'm not using the "new wave" theme which (for many other people) seems to cause a crash. Tried reporting a bug, but I'm a little despairing since there are so darn many already reported with f-spot.  Any suggestions welcome.
Terminal output below.

REALLY sick of having photos.db screw up every single time I upgrade f-spot.  This is about the 3rd upgrade in a row where there has been some monstrous fault.  It's as if they don't even test the software.  Why is it so hard to keep the database format consistent from one release to the next, or at least manage the changes without fscking up the whole thing.

```
mary@mythbox:~/.config/f-spot$ f-spot
[Info  21:12:24.983] Initializing DBus
[Info  21:12:25.079] Initializing Mono.Addins
[Info  21:12:25.230] Starting new FSpot server (f-spot 0.6.1.5)
[Info  21:12:25.330] Updating F-Spot Database
[Info  21:12:26.299] Database updates completed successfully (in 0.968055s).

** (f-spot:5105): CRITICAL **: atk_object_set_name: assertion `name !=
NULL' failed

** (f-spot:5105): CRITICAL **: atk_object_set_name: assertion `name !=
NULL' failed

** (f-spot:5105): CRITICAL **: atk_object_set_name: assertion `name !=
NULL' failed

** (f-spot:5105): CRITICAL **: atk_object_set_name: assertion `name !=
NULL' failed

** (f-spot:5105): CRITICAL **: atk_object_set_name: assertion `name !=
NULL' failed
[Warn  21:12:26.713] Caught an exception - URI scheme must start with
a letter and must consist of one of alphabet, digits, '+', '-' or '.'
character. (in `System')
 at System.Uri.Parse (UriKind kind, System.String uriString) [0x00000]
 at System.Uri.ParseUri (UriKind kind) [0x00000]
 at System.Uri..ctor (System.Uri baseUri, System.String relativeUri,
Boolean dontEscape) [0x00000]
 at System.Uri..ctor (System.Uri baseUri, System.String relativeUri) [0x00000]
 at FSpot.Widgets.FolderTreeModel.UpdateFolderTree () [0x00000]
 at FSpot.Widgets.FolderTreeModel..ctor () [0x00000]
 at FSpot.Widgets.FolderTreeView..ctor () [0x00000]
 at FSpot.Widgets.FolderTreePage..ctor () [0x00000]
 at (wrapper managed-to-native)
System.Reflection.MonoCMethod:InternalInvoke
(object,object[],System.Exception&)
 at System.Reflection.MonoCMethod.Invoke (System.Object obj,
BindingFlags invokeAttr, System.Reflection.Binder binder,
System.Object[] parameters, System.Globalization.CultureInfo culture)
[0x00000]
Exception has been thrown by the target of an invocation. (in `mscorlib')
 at System.Reflection.MonoCMethod.Invoke (System.Object obj,
BindingFlags invokeAttr, System.Reflection.Binder binder,
System.Object[] parameters, System.Globalization.CultureInfo culture)
[0x00000]
 at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr,
System.Reflection.Binder binder, System.Object[] parameters,
System.Globalization.CultureInfo culture) [0x00000]
 at System.Reflection.ConstructorInfo.Invoke (System.Object[]
parameters) [0x00000]
 at System.Activator.CreateInstance (System.Type type, Boolean
nonPublic) [0x00000]
 at Mono.Addins.RuntimeAddin.CreateInstance (System.String typeName,
Boolean throwIfNotFound) [0x00000]
 at Mono.Addins.RuntimeAddin.CreateInstance (System.String typeName) [0x00000]
 at FSpot.Widgets.SidebarPageNode.GetSidebarPage () [0x00000]
 at MainWindow.OnSidebarExtensionChanged (System.Object s,
Mono.Addins.ExtensionNodeEventArgs args) [0x00000]
 at Mono.Addins.ExtensionNode.OnChildNodeAdded
(Mono.Addins.ExtensionNode node) [0x00000]
 at Mono.Addins.ExtensionNode.NotifyChildChanged () [0x00000]
 at Mono.Addins.TreeNode.NotifyChildrenChanged () [0x00000]
 at Mono.Addins.ExtensionContext.NotifyConditionChanged
(Mono.Addins.ConditionType cond) [0x00000]
 at Mono.Addins.ExtensionContext.OnConditionChanged (System.Object s,
System.EventArgs a) [0x00000]
 at Mono.Addins.ConditionType.NotifyChanged () [0x00000]
 at FSpot.Extensions.ViewModeCondition.<ViewModeCondition>m__5 () [0x00000]
 at FSpot.Extensions.ViewModeCondition.set_Mode (ViewMode value) [0x00000]
 at FSpot.Widgets.Sidebar.HandleContextChanged (System.Object sender,
System.EventArgs args) [0x00000]
```

---

### Post by directhex on 2009-11-24
Assuming it doesn't contain any information you'd consider sensitive, can you post your photos.db file somewhere so it can be analysed for issues?

The problem developers have is that they don't necessarily experience bugs themselves - and that means they need test cases to check against

---

### Post by linuxgrrl on 2009-11-24
Thank you for replying ... here it is, attached.
It worked fine under Intrepid.  
PS This is is the file as it existed *before* attempting to open in Karmic (i.e., before it was "updated").

---

### Post by r1chard on 2009-12-16
Same issue. :( 

Seems like there is a bug reported, but at time of writing, Launchpad seems broken :(

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/469334](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/469334)

---

### Post by tsh on 2009-12-16
Yep, same problem here. Really, the problem seems that noone really works on f-spot. The website has virtually no useful user documentation. Any goos alternatives? Seems laughable that there is no support for moving a database from one machine to another.

---

### Post by yester64 on 2009-12-16
Personally. i tossed F-Spot since it takes forever to import photos. Everything over 10T photos takes up to 6 hours or more.
Try digiKam instead. It is KDE ware but very good.
Never had any startup problems, but i think it can be the database since it gave me problems with reinstalling.

---

### Post by linuxgrrl on 2009-12-18
> **r1chard said:**
> Same issue. :( 

Seems like there is a bug reported, but at time of writing, Launchpad seems broken :(

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/469334](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/469334)

hi everybody,
I eventually got my database to open. The problem was indeed a bug, the new version of f-spot chokes if any filepaths in your database contain a ":" (there may be other characters too, but : was the problem in my case.)  Years ago I had used Gthumb to import some photos and it put a timestamp in one file path like "21:58." This was a little time bomb waiting to go off.

A kind soul on the f-spot mailing list, <f-spot-list@gnome.org>, actually repaired my db and emailed it back to me without the ":" a couple weeks ago. So I now feel pretty bad about having ranted about the devs :)

So I guess it's not fair to say that nobody works on f-spot.  I'm just not sure why Ubuntu would ship a version that chokes for so many users.  I'm so happy with f-spot's featureset and UI, it's still worth it to me to deal with these hiccups but I can only imagine how annoying a new-ish user or someone with less patience.

---

### Post by kkinder on 2010-04-15
This is a problem for me too. I don't want to rename my files either, as those are what the files are named and changing them would make my files (directories, actually) less precisely named. I have directories like "2008-10: Vacation in California" or such.

Not sure what to do.

---

