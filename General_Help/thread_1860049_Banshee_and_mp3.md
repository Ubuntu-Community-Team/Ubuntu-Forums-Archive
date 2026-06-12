---
title: "Banshee and mp3"
date: 2011-10-14
forum: General Help
---

### Post by xingular on 2011-10-14
I fresh installed Ubuntu and when I open Banshee all I obtain is a white screen "named" Banshee. I can not play any mp3 file and in desktops they appear with a clock in the icon rather than a "music note".

Restricted extras are "ON" and during the installation I check the "Install restricted extras" option.

How can I start to solve this problem? I have complety no idea...

---

### Post by thatguruguy on 2011-10-14
Open a terminal and type "banshee" (without the quotes, of course).  Post the results here.

Have you run an update yet?  Some updates to banshee came through right after the launch of 11.10.

---

### Post by sgage on 2011-10-14
> **xingular said:**
> I fresh installed Ubuntu and when I open Banshee all I obtain is a white screen "named" Banshee. I can not play any mp3 file and in desktops they appear with a clock in the icon rather than a "music note".

Restricted extras are "ON" and during the installation I check the "Install restricted extras" option.

How can I start to solve this problem? I have complety no idea...

The first time I started Banshee after installing I got a blank window as well. I quit it (from the 'Media' menu), restarted, and it worked fine after that. Well, it worked as well as it ever has ;)

---

### Post by xingular on 2011-10-14
I tried with a fresh installation with updates and a new installation without updates.

In the installation with updates (updates during the installation) the message obtained in terminal was (I believe that at this moment folder "music" had a lot of mp3, this important, see below on the second part of this post) 

[php]
banshee
[Info  01:55:24.706] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, x86_64) @ 2011-09-23 04:47:58 UTC]

(Banshee:1538): Gtk-WARNING **: Imposible> [QUOTE][/QUOTE] encontrar el motor de temas en la ruta al _modulo: «pixmap»,


(Banshee:1538): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «pixmap»,

(Banshee:1538): 
Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «pixmap»,

(Banshee:1538): 
Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «pixmap»,
[/php]

The installation is in Spanish, so the traduction is: Unable to find the theme (I think theme is the correct word for "temas") engines in the route to the <<pixmap>> module


But now, the interesting part. In the actual installation (without updates) I can open Banshee and I can see the entirely program without problems. But! when I copy a lot of mp3 files to the folder "Music", I can not start banshee! The only I have is the famous white window!

So, I tried to copy only one file. But this file can not be opened (program gets "freeze" when I push the play button). I think this happens because restricted extras are not installed. I don't have more time for today, so finally I typed "banshee" in the terminal and this is what I have now (another time the sentence in spanish and this time a lot of more things).

[PHP]banshee
[Info  01:55:24.706] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, x86_64) @ 2011-09-23 04:47:58 UTC]

(Banshee:1538): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «pixmap»,


(Banshee:1538): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «pixmap»,

(Banshee:1538): 
Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «pixmap»,

(Banshee:1538): 
Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «pixmap»,


[Info  01:55:29.466] Updating web proxy from GConf
[Info  01:55:29.596] All services are started 4,002873
** (Banshee:1538): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged

(Banshee:1538): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

[Info  01:55:35.014] AmazonMP3 store redirect URL: [https://one.ubuntu.com/music/store/amz/](https://one.ubuntu.com/music/store/amz/)

[Info  01:55:36.405] nereid Client Started
[Info  01:55:36.894] GStreamer version 0.10.35.0, gapless: True, replaygain: False
** (Banshee:1538): DEBUG: MP3 playback is missing.

[Warn  01:55:48.658] Caught an exception - System.Net.WebException: The request timed out (in `System')
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.GetHttpStream (System.Uri uri, System.String[] ignoreMimeTypes) [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.GetHttpStream (System.Uri uri) [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.Rhapsody.RhapsodyQueryJob.Run () [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.Run () [0x00000] in <filename unknown>:0 

** 

(Banshee:1538): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 1041, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 640, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 778, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/rosalinda/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:1538): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:1538): WARNING **: Error rescanning Purchased Music: No existe el archivo o el directorio
** (Banshee:1538): DEBUG: Got notification of SyncDaemon startup in NameOwnerChanged
** (Banshee:1538): DEBUG: Loading the real store page

** (Banshee:1538): WARNING **: Got less number of items in credentials hash table than expected![/PHP]

The sentence: No existe el archivo o el directorio means= The file or folder does not exists

Note: I "deleted" Ubuntu One from the list of applications at the start of the system.

---

