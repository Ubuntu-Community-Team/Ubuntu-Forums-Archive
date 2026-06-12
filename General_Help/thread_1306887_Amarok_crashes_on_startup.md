---
title: "Amarok crashes on startup"
date: 2009-10-30
forum: General Help
---

### Post by geo909 on 2009-10-30
Hello all,

first of all, this is a problem I have with a laptop running debian. Since everything is so similar and I spend a lot of time in these forums I thought I'd ask here, I didn't have any luck in the Debian forums. 

Ok, so here is my problem, any help would be greatly appreciated:

I am running debian squeeze, and recently I upgraded to amarok 2.2.0.
Everything ran smoothly for a couple of days and then one day amarok did 
not wake up again. In fact, every time I try to launch it, it shows the splash screen for a whle and then it crashes before it actually starts.

Here's what I get when I try to do that from the console:

```
jorge@flamingo:~$ amarok
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
<unknown program name>(13851)/: Communication problem with  "amarok" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 

kbuildsycoca4 running...
jorge@flamingo:~$ kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Object::connect: No such signal BrowserCategoryList::leavingTree()
Object::connect:  (sender name:   'internet')
QDBusObjectPath: invalid path ""
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kglobalaccel.so
Object::connect: No such signal BrowserCategoryList::leavingTree()
Object::connect:  (sender name:   'root list')
Object::connect: No such slot BrowserWidget::categoryChanged()
Object::connect:  (sender name:   'root list')
QLayout: Attempting to add QLayout "" to Playlist::SortWidget "", which already has a layout
QWidget::insertAction: Attempt to insert null action
findServiceByDesktopPath:  not found
Object::connect: No such signal BrowserWidget::widgetActivated( int )
Object::connect:  (receiver name: 'MainWindow')
Object::connect: No such signal CollectionWidget::home()
Object::connect:  (sender name:   'collections')
Object::connect:  (receiver name: 'root list')
Object::connect: No such signal ServiceBrowser::home()
Object::connect:  (sender name:   'internet')
Object::connect:  (receiver name: 'root list')
Object::connect: No such signal BrowserCategoryList::leavingTree()
Object::connect:  (sender name:   'playlists')
Object::connect: No such signal PlaylistBrowserNS::DynamicCategory::home()
Object::connect:  (receiver name: 'playlists')
"building tree with 7 leafs." 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
QIcon :  QVariant(QIcon, ) 
QString :  QVariant(QString, "") 
QString :  QVariant(QString, "") 
m_groupHash:  
(0, 1, 2, 3, 4, 5, 6) 
Object::connect: No such signal PlaylistBrowserNS::PlaylistCategory::home()
Object::connect:  (receiver name: 'playlists')
Object::connect: No such signal PlaylistBrowserNS::PodcastCategory::home()
Object::connect:  (receiver name: 'playlists')
Object::connect: No such signal PlaylistBrowserNS::PlaylistBrowser::home()
Object::connect:  (sender name:   'playlists')
Object::connect:  (receiver name: 'root list')
Object::connect: No such signal FileBrowser::Widget::home()
Object::connect:  (sender name:   'files')
Object::connect:  (receiver name: 'root list')
HTTP GET  QUrl( "http://post.audioscrobbler.com:80/?hs=true&p=1.2.1&c=ark&v=2.2.0&u=giorgos909&t=1256941207&a=90925472d70a84c244191dc1589626a7&api_key=402d3ca8e9bc9d3cf9b85e1202944ca5&sk=cf4234d75cf032a9f3afb4358f2503c1" )  
jorge@flamingo:~$ kdeinit4: preparing to launch /usr/bin/knotify4
KCrash: Application 'amarok' crashing...
sock_file=/home/jorge/.kde/socket-flamingo/kdeinit4__0
kdeinit4: preparing to launch /usr/lib/kde4/libexec/drkonqi
jorge@flamingo:~$ Unable to start Dr. Konqi


```

So I get the above and then amarok crashes.

Any ideas, please? Tell me if you need more info.

Thanks a lot in advance

EDIT: forgot to mention that I have a minimal install with the dwm window manager (so, no desktops). Though everything else runs smoothly, including the previous version of amarok (2.1x).

---

### Post by geo909 on 2009-10-30
Fixed: for some reason, amarok could start when I disabled the mysql daemon.
It nust have to do with some invalid entry in the database menu (eg wrong password etc).

Thanks

---

