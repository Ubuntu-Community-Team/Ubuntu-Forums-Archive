---
title: "DBus.Error.NoReply when starting Kontact"
date: 2009-07-16
forum: General Help
---

### Post by Firestem4 on 2009-07-16
I'm having an issue when I try to start Kontact in Kubuntu 9.04. 

```
icarus@icarus-linux:~$ kontact
Calling appendChild() on a null node does nothing.   
Calling appendChild() on a null node does nothing.   
Calling appendChild() on a null node does nothing.   
Calling appendChild() on a null node does nothing.   
Calling appendChild() on a null node does nothing.   
Calling appendChild() on a null node does nothing.   
Calling appendChild() on a null node does nothing.   
Calling appendChild() on a null node does nothing.   
Calling appendChild() on a null node does nothing.   
Calling appendChild() on a null node does nothing.   
Calling appendChild() on a null node does nothing.   
kontact(8918)/kmail (storage internals) KMFolderIndex::openInternal: KDE_fopen(indexLocation()= "/home/icarus/.kde/share/apps/kmail/mail/.outbox.index" , "r+") == mIndexStream ==  0x8e194a8
kontact(8918)/kmail (storage internals) KMFolderIndex::openInternal: KDE_fopen(indexLocation()= "/home/icarus/.kde/share/apps/kmail/mail/.drafts.index" , "r+") == mIndexStream ==  0x8de4058
kontact(8918)/kmail (storage internals) KMFolderIndex::openInternal: KDE_fopen(indexLocation()= "/home/icarus/.kde/share/apps/kmail/mail/.templates.index" , "r+") == mIndexStream ==  0x8e2f7a0
kontact(8918)/kmail (storage internals) KMFolderIndex::openInternal: KDE_fopen(indexLocation()= "/home/icarus/.kde/share/apps/kmail/mail/.inbox.index" , "r+") == mIndexStream ==  0x96bd000
kontact(8918)/kmail (storage internals) KMFolderMaildir::reallyDoClose: fclose(mIndexStream =  0x96bd000 )
kontact(8918)/kmail (storage internals) KMFolderIndex::openInternal: KDE_fopen(indexLocation()= "/home/icarus/.kde/share/apps/kmail/mail/.inbox.index" , "r+") == mIndexStream ==  0x96c3ae8
kontact(8918)/kmail (storage internals) KMFolderMaildir::reallyDoClose: fclose(mIndexStream =  0x96c3ae8 )
Object::connect: No such signal Akregator::SubscriptionListView::signalDropped (KUrl::List &, Akregator::TreeNode*, Akregator::Folder*) in /build/buildd/kdepim-4.2.4/akregator/src/mainwidget.cpp:142
Object::connect:  (sender name:   'feedtree')
Object::connect:  (receiver name: 'akregator_view')
Object::connect: No such signal Akregator::ArticleListView::UserActionTakingPlace() in /build/buildd/kdepim-4.2.4/akregator/src/mainwidget.cpp:192
Object::connect:  (receiver name: 'akregator_view')
Object::connect: No such signal Akregator::TrayIcon::toggleShowPart() in /build/buildd/kdepim-4.2.4/akregator/src/akregator_part.cpp:161
Object::connect: No such signal Akregator::Part::showPart() in /build/buildd/kdepim-4.2.4/kontact/plugins/akregator/akregator_plugin.cpp:102
Object::connect:  (receiver name: 'akregator')
<unknown program name>(8917)/: Communication problem with  "kontact" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." "


```

I'm made sure that dbus was running (obvious fact it is anyways because the rest of the computer is working just dandy.)

When i start Kontact the computer takes an unusually high amount of resources and the computer becomes unresponsive for a minute or two. Kontact eventually resumes even after the terminal output quits. (Akregator loads in the tray and starts Kontact up eventually.)

After it is running kontact runs generally like normal. However I can not deal with the starting-problem

I haven't done anything and there was no recent upgrade that changed dbus or kontact/kde. 

Any idea's anyone?

Thanks in advance!

---

