---
title: "Oops!"
date: 2010-02-19
forum: General Help
---

### Post by clicker4721 on 2010-02-19
I accidentally deleted the Cover Art Rhythmbox plugin, would someone please post the tarball of it for me?  It would be much appreciated.

---

### Post by n0dix on 2010-02-19
if you reinstall the program don't get the plugin back.

---

### Post by darolu on 2010-02-19
Did you **delete** the plug in? or did you only disable it?

I have no idea how to actually delete a plug in, so I tend to believe you only disabled it; to re-enable it simply click on Edit - Plug ins (complements) and browse the list until you find the cover art one and enable it.

Anyways, you can find plug ins here:

[http://live.gnome.org/Rhythmbox/RelatedTools](http://live.gnome.org/Rhythmbox/RelatedTools)

[http://live.gnome.org/RhythmboxPlugins/ThirdParty](http://live.gnome.org/RhythmboxPlugins/ThirdParty)

---

### Post by sandyd on 2010-02-19
Dont see that exact plugin, but

---

### Post by clicker4721 on 2010-02-20
> **carlee said:**
> Dont see that exact plugin, but
Yes, that's pretty much what I needed.  No, people, I actually deleted the folder containing the plugin when installing the others, and since I was in sudo mode, it was unrecoverable.  Thanks, Carlee.

---

### Post by clicker4721 on 2010-02-21
> **n0dix said:**
> if you reinstall the program don't get the plugin back.
Ahh! That worked even better!

---

### Post by clicker4721 on 2010-02-22
Well, strangely (and, yes, I have the check box for it enabled), the cover art plugin isn't doing anything anyway...any tips?

---

### Post by n0dix on 2010-02-22
Try to drag and drop the cover image in the box.

---

### Post by clicker4721 on 2010-02-23
> **n0dix said:**
> Try to drag and drop the cover image in the box.
But, uh...there's no box.

---

### Post by n0dix on 2010-02-23
> **clicker4721 said:**
> But, uh...there's no box.

I mean in the image of the CD. Drag and drop the cover in the image.

---

### Post by clicker4721 on 2010-02-23
> **n0dix said:**
> I mean in the image of the CD. Drag and drop the cover in the image.

No; I know what you meant:  the image of the CD in the bottom left of Rhythmbox--it's not there. :confused:

---

### Post by n0dix on 2010-02-23
I don't have idea, if you reinstall and still have problems :( . 

Try with another program, Exaile, Banshee, and Amarok (qt library).

---

### Post by clicker4721 on 2010-02-23
> **n0dix said:**
> I don't have idea, if you reinstall and still have problems :( . 

Try with another program, Exaile, Banshee, and Amarok (qt library).

I reinstalled just so I could get it back; I don't think...yeah, I don't know what to do, either.

---

### Post by raktarok on 2010-02-23
I don't know what is wrong, but try these..

If you used the tar ball posted, check the permissions of the cover art plugin folder. It should have all write, read, and execute permissions for the current user.

Remove the whole rhythmbox config directory, remove rhythmbox, and start fresh. Or you could just do this..
```
sudo apt-get purge rhythmbox && sudo apt-get install rhythmbox
```


Hope this helped!

---

### Post by clicker4721 on 2010-02-23
> **raktarok said:**
> I don't know what is wrong, but try these..

If you used the tar ball posted, check the permissions of the cover art plugin folder. It should have all write, read, and execute permissions for the current user.

Remove the whole rhythmbox config directory, remove rhythmbox, and start fresh. Or you could just do this..
```
sudo apt-get purge rhythmbox && sudo apt-get install rhythmbox
```


Hope this helped!
```
clicker4721@clicker4721d:~$ sudo apt-get purge rhythmbox && sudo apt-get install rhythmbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  rhythmbox*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 14.8MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 165461 files and directories currently installed.)
Removing rhythmbox ...
Purging configuration files for rhythmbox ...
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/daap' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/ipod' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/rb' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/jamendo' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/magnatune' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/lyrics' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/artdisplay' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/visualizer' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/iradio' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/audioscrobbler' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/audiocd' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox' not empty so not removed.
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  python-coherence
The following NEW packages will be installed:
  rhythmbox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3514kB of archives.
After this operation, 14.8MB of additional disk space will be used.
Selecting previously deselected package rhythmbox.
(Reading database ... 164934 files and directories currently installed.)
Unpacking rhythmbox (from .../rhythmbox_0.12.0-0ubuntu4_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up rhythmbox (0.12.0-0ubuntu4) ...

Processing triggers for menu ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
clicker4721@clicker4721d:~$ 

```
I can't say for sure, but it doesn't seem to have done anything.

---

### Post by sandyd on 2010-02-23
> **clicker4721 said:**
> ```
clicker4721@clicker4721d:~$ sudo apt-get purge rhythmbox && sudo apt-get install rhythmbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  rhythmbox*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 14.8MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 165461 files and directories currently installed.)
Removing rhythmbox ...
Purging configuration files for rhythmbox ...
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/daap' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/ipod' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/rb' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/jamendo' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/magnatune' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/lyrics' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/artdisplay' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/visualizer' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/iradio' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/audioscrobbler' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins/audiocd' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox/plugins' not empty so not removed.
dpkg - warning: while removing rhythmbox, directory `/usr/lib/rhythmbox' not empty so not removed.
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  python-coherence
The following NEW packages will be installed:
  rhythmbox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3514kB of archives.
After this operation, 14.8MB of additional disk space will be used.
Selecting previously deselected package rhythmbox.
(Reading database ... 164934 files and directories currently installed.)
Unpacking rhythmbox (from .../rhythmbox_0.12.0-0ubuntu4_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up rhythmbox (0.12.0-0ubuntu4) ...

Processing triggers for menu ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
clicker4721@clicker4721d:~$ 

```I can't say for sure, but it doesn't seem to have done anything.
do this instead.
```

sudo rm -rf /usr/lib/rhythmbox/
sudo apt-get purge rhythmbox && sudo apt-get install rhythmbox

```

---

### Post by clicker4721 on 2010-02-25
> **carlee said:**
> do this instead.
```

sudo rm -rf /usr/lib/rhythmbox/
sudo apt-get purge rhythmbox && sudo apt-get install rhythmbox

```
Okay...and then all the plugins disappeared. So, I reinstalled the Rhythmbox package in Synaptic, and everything works **exactly** like it did before. :-|

---

### Post by raktarok on 2010-02-25
Glad to hear that its working now!

---

### Post by clicker4721 on 2010-02-25
> **raktarok said:**
> Glad to hear that its working now!
No, I mean like it was before--as in, the plugin still does nothing. It never functioned correctly. Still doesn't. :(

---

### Post by n0dix on 2010-02-25
> **raktarok said:**
> Glad to hear that its working now!

ahh,??? ;)

Btw, the world doesn't end with RhythmBox, you can install other programs like Exaile, Banshee, Amarok, Songbird, etc.

---

### Post by raktarok on 2010-02-25
Oops! sorry about that misunderstanding :)

no idea why its not working. Does this happen even when you login as some other user? and do all other plugins work all right?

---

### Post by raktarok on 2010-02-25
Also try starting rhytmbox like this from the terminal:
```

rhythmbox -d 

```
It starts the player in debug mode, and now, see if you get any error output etc. when you fiddle with the plugin.

---

### Post by clicker4721 on 2010-02-25
> **n0dix said:**
> ahh,??? ;)

Btw, the world doesn't end with RhythmBox, you can install other programs like Exaile, Banshee, Amarok, Songbird, etc.

I don't know what the >  ahh,??? ;)  means, but...yeah, I know Rhythmbox isn't the end, it's just that I'm not particularly a fan of installing multiple programs that do the exact same thing, and for me, pretty much all media library programs are alike. Exaile and Banshee I'm considering because I've heard the integrate well with AWN. Songbird I've tried, but the skin I wanted (and basically the only reason I tried it) didn't work. And Amarok? Eh, I'll stick with just GNOME libs until I start trying to install KDE 3.5 for Baghira alongside. If worst comes to worst, though, I would consider others, though if I can't get this working. And it's not that the program doesn't work; it indexes and plays my music wonderfully, it's that one stubborn plugin! Well, I'll come up with something....

---

### Post by clicker4721 on 2010-02-25
> **raktarok said:**
> Also try starting rhytmbox like this from the terminal:
```

rhythmbox -d 

```It starts the player in debug mode, and now, see if you get any error output etc. when you fiddle with the plugin.
Here's the scoop:
```

(19:42:14) [0x2193500] [rb_python_module_init] rb-python-module.c:395: Init of python module
(19:42:14) [0x2193500] [rb_python_object_get_type] rb-python-plugin.c:269: Registering python plugin instance: ArtDisplayPlugin+RBPythonPlugin

(rhythmbox:18549): GLib-GObject-WARNING **: Two different plugins tried to register 'ArtDisplayPlugin+RBPythonPlugin'.

(rhythmbox:18549): Rhythmbox-CRITICAL **: rb_plugin_activate: assertion `RB_IS_PLUGIN (plugin)' failed
(19:42:27) [0x2193500] [rb_shell_window_configure_cb] rb-shell.c:1635: storing window size of 1001:677
(19:42:27) [0x2193500] [rb_shell_window_configure_cb] rb-shell.c:1647: storing window position of 715:110

(rhythmbox:18549): Rhythmbox-CRITICAL **: rb_plugin_deactivate: assertion `RB_IS_PLUGIN (plugin)' failed

```Other than where it says failed, I don't know what it means... A little more help, Doc?

EDIT: By the way, this is the part where I click activate the plugin and deactivate it. Yes, I have had it activated before and it still didn't work--I'm not that stupid. Anyway, like I said, this is just the part where I select the check box, then deselect it.

---

### Post by raktarok on 2010-02-25
> **clicker4721 said:**
> 

(rhythmbox:18549): GLib-GObject-WARNING **: Two different plugins tried to register 'ArtDisplayPlugin+RBPythonPlugin'.

This may be the problem. Maybe you have a copy of the plugin in the rhythmbox config directory? Please check the directory **.gnome2/rhythmbox **in your home folder, and see if there are any plugins inside it. Delete them if there are.

If this does not help, try disabling all other plugins, and see if it works when it is the only one enabled. You can also try deleting all other plugin folders from /usr/lib/rhythmbox/plugins directory, and see if it works now..

Also try deleting the whole rhythmbox directory in .gnome2...

---

### Post by clicker4721 on 2010-02-26
> **raktarok said:**
> This may be the problem. Maybe you have a copy of the plugin in the rhythmbox config directory? Please check the directory **.gnome2/rhythmbox **in your home folder, and see if there are any plugins inside it. Delete them if there are.

If this does not help, try disabling all other plugins, and see if it works when it is the only one enabled. You can also try deleting all other plugin folders from /usr/lib/rhythmbox/plugins directory, and see if it works now..

Also try deleting the whole rhythmbox directory in .gnome2...
Alright! The plugin itself works, and it will display cover art. Unfortunately, it will not fetch it; which, I know, can be overcome with a simple drag-and-drop but getting the cover is an inconvenience.  Regardless, it works fine--apparently, whenever I extracted Carlee's tarball, I hit merge, and the Linux file system allows duplicates, so I had two of almost every script in the lib directory. In contrast, I use AWN, and am trying to implement the AWN Rhythmbox Cover Art plugin alongside the Cover Art Display plugin. The same error occurs whenever I try to use it with the Cover Art Display plugin...Remediable?

EDIT: With some more piddling, got Cover Art plugin working correctly, i.e. fetching works.

---

### Post by clicker4721 on 2010-02-26
I think the key to my problem is in this error readout:
```

(19:38:36) [0x18e8500] [rb_python_module_init] rb-python-module.c:395: Init of python module
(19:38:36) [0x18e8500] [rb_python_object_get_type] rb-python-plugin.c:269: Registering python plugin instance: ArtDisplayPlugin+RBPythonPlugin

(rhythmbox:12684): GLib-GObject-WARNING **: Two different plugins tried to register 'ArtDisplayPlugin+RBPythonPlugin'.

(rhythmbox:12684): Rhythmbox-CRITICAL **: rb_plugin_activate: assertion `RB_IS_PLUGIN (plugin)' failed

(rhythmbox:12684): Rhythmbox-CRITICAL **: rb_plugin_deactivate: assertion `RB_IS_PLUGIN (plugin)' failed

```
This has to be more specific than I'm giving it credit for. Apparently, both cover art viewers are registering the same something...I've tried deleting scripts from one directory and seeing if the other plugin still works--no good. Please help, I'm almost through. :D

---

### Post by raktarok on 2010-02-26
Did you use the plugin from this page?
[http://wiki.awn-project.org/Plugins:Rhythmbox](http://wiki.awn-project.org/Plugins:Rhythmbox)

The screenshots there show the plugin working with the latest design of awn. Which version of awn are you using? are you using the one found in the repos, or in ppa? Try updating awn by adding this line to your sources, if you have not done so.

```
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu karmic main
```

You are using karmic, right? and now install the latest awn:

```
sudo apt-get install avant-window-navigator-trunk 
```

I am using the old, stable awn and I tried using the awn rhythmbox plugin from the above webpage. I am also getting the same error as you. I tried fiddling with the plugin files, but I have had no luck so far.

And I also noticed that the cover art plugin is not fetching covers for me, how did you solve that? I would like to learn that too..  

Hope we solve this soon!

---

### Post by clicker4721 on 2010-02-27
> **raktarok said:**
> Did you use the plugin from this page?
[http://wiki.awn-project.org/Plugins:Rhythmbox](http://wiki.awn-project.org/Plugins:Rhythmbox)

The screenshots there show the plugin working with the latest design of awn. Which version of awn are you using? are you using the one found in the repos, or in ppa? Try updating awn by adding this line to your sources, if you have not done so.

```
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu karmic main
```You are using karmic, right? and now install the latest awn:

```
sudo apt-get install avant-window-navigator-trunk 
```I am using the old, stable awn and I tried using the awn rhythmbox plugin from the above webpage. I am also getting the same error as you. I tried fiddling with the plugin files, but I have had no luck so far.

And I also noticed that the cover art plugin is not fetching covers for me, how did you solve that? I would like to learn that too..  

Hope we solve this soon!

1.     Yes, that's where I download my plugin.
2.     No, I'm using Jaunty because it is so much more customizable then Karmic; for me, personal is the name of the game.
3.     I too, tried tweaking them, and only did so well.
4.    The cover art problem is strange; I'm not real sure what I did.  I did a bunch of screw-up, and then a reinstall fixed it. Go figure.

---

### Post by clicker4721 on 2010-03-02
Uhh...hello?

---

### Post by raktarok on 2010-03-02
Oh, I gave up on this, could not make it work. I started on programming stuff only recently, and I have not used python at all, so I can't figure what's wrong with the plugin. Why don't you file a bug for this problem, maybe the developers will hear you? .

Most probably, this is not a problem with awn, but did you try using other versions of awn?

and I am afraid you will have to do without the awn plugin for the time being. Maybe other people in the forum can help you here....if I find something new, I will post here again.   

Good luck!

---

### Post by clicker4721 on 2010-03-03
> **raktarok said:**
> Oh, I gave up on this, could not make it work. I started on programming stuff only recently, and I have not used python at all, so I can't figure what's wrong with the plugin. Why don't you file a bug for this problem, maybe the developers will hear you? .

Most probably, this is not a problem with awn, but did you try using other versions of awn?

and I am afraid you will have to do without the awn plugin for the time being. Maybe other people in the forum can help you here....if I find something new, I will post here again.   

Good luck!

Alright, to deeper delving I continue!

---

