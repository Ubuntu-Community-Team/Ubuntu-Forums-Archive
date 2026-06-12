---
title: "KWord, no highlighting shown when selecting words (or cursor)"
date: 2011-05-06
forum: General Help
---

### Post by slooksterpsv on 2011-05-06
When I'm using KWord and I try to highlight text or even click to another line, it doesn't show the highlight or the cursor.

I ran the program via Konsole and got the following output:

```

(Soprano::Redland::BackendPlugin) creating model of type "hashes" with options "hash-type='memory',contexts='yes'" 
kword(8807)/koffice (lib komain) KoPluginLoader::load: Loading plugin "Chart Shape" failed,  "Could not find plugin 'Chart Shape' for application 'kword'" 
kword(8807)/kotext TextShapeFactory::newDocumentResourceManager: No KUndoStack found in the document resource manager, creating a new one 
kword(8807)/kdeui (KAction) KActionCollection::setComponentData: this does not work on a KActionCollection containing actions! 
kword(8807)/koffice (filter manager) KoFilterManager::filterAvailable: The library  ""  does not offer a check_ ""  function. 

QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/shawn/.config/ibus/bus
QFile::open: File (/usr/share/kde4/apps/kword/templates/Normal/.source/Letter.kwt) already open
connect failed: No such file or directory
Enchant dict for "en_US" 0x2de8990 
Enchant dict for "en_US" 0x2de8990 
Enchant dict for "en_US" 0x2de8990 
Enchant dict for "en_US" 0x2de8990 
Enchant dict for "en_US" 0x2de8990 
Enchant dict for "en_US" 0x2de8990 
kword(8807)/kdeui (KAction) KActionCollection::setComponentData: this does not work on a KActionCollection containing actions! 
Kross: "Action::setInterpreter: interpreter not found: ruby" 
Kross: "Action::setInterpreter: interpreter not found: ruby" 
kword(8807)/kdeui (KAction) KActionCollection::setComponentData: this does not work on a KActionCollection containing actions! 
kword(8807)/kdeui (kdelibs): Attempt to use QAction "" with KXMLGUIFactory! 
kword(8807)/kotext TextTool::pointToPosition: Clicking in not fully laid-out textframe 
QTextCursor::setPosition: Position '-1' out of range
QTextCursor::setPosition: Position '-1' out of range
kword(8807)/kotext TextTool::pointToPosition: Clicking in not fully laid-out textframe 
QTextCursor::setPosition: Position '-1' out of range
QTextCursor::setPosition: Position '-1' out of range
kword(8807)/kotext TextTool::pointToPosition: Clicking in not fully laid-out textframe 
QTextCursor::setPosition: Position '-1' out of range
QTextCursor::setPosition: Position '-1' out of range
kword(8807)/kotext TextTool::pointToPosition: Clicking in not fully laid-out textframe 
QTextCursor::setPosition: Position '-1' out of range
QTextCursor::setPosition: Position '-1' out of range
kword(8807)/kotext TextTool::pointToPosition: Clicking in not fully laid-out textframe 
QTextCursor::setPosition: Position '-1' out of range
QTextCursor::setPosition: Position '-1' out of range
QTextCursor::setPosition: Position '-1' out of range
QTextCursor::setPosition: Position '-1' out of range
QTextCursor::setPosition: Position '-1' out of range

```

Any ideas? I know I can use LibreOffice, but there's a few features that KWord has that LibreOffice doesn't have.

---

### Post by slooksterpsv on 2011-05-06
Cancel the thread, found lots of related posts on other forums, launchpad bugs, etc. Sorry all, my bad!

---

