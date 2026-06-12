---
title: "Deluge -- Can't add torrents!  Help!"
date: 2009-11-20
forum: General Help
---

### Post by greylander on 2009-11-20
Hi, I suddenly cannot add new torrents to Deluge unless I manually add the torrent file in the user interface.

Specifically, when firefox invokes Deluge on downloaded torrent files, deluge will start up, but the new torrent file is not added.

Additionally, if deluge is already running, then a new copy of deluge starts (to "drop" icons in the taskbar instead of one).

This problem started at some point while I was trying to get magnet links to work, and at first I thought that it was specifically a problem with magnet links, but then I tried a regular torrent file and same problem.

In my attempt to get magnet links to work, I tried the instructions in the first two posts of this thread (modified for deluge instead of asureus):  [http://ubuntuforums.org/showthread.php?t=1273985](http://ubuntuforums.org/showthread.php?t=1273985)

specifically, in firefox about:config, I did this...

```
Type about:config into the address bar and press Enter.
* Right-click -> New -> Boolean -> Name: network.protocol-handler.external.magnet -> Value -> true
* Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /usr/bin/deluge
* Ensure network.protocol-handler.expose-all is set to true. 
```

...which had no effect (Firefox did not call deluge on magnet links and still said that no protocol was specified for magnet links).

Then I used these gconftool-2 commands:

```
gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/deluge %s"
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true
```

Which had part of the desired effect.  Firefox now knows to call deluge for magnet links.  But now the problem I first described occurs.  New torrents (whether magnet links or torrent files) are not added to deluge and if an instance of deluge is already running, a new instance is started (the new torrent is not added in either instance).

I was using Deluge 1.6 when this happened.  I have tried upgrading to 1.2.0-rc3 with no change.  I then fully uninstalled and reinstalled it (I also manually deleted my ~/.config/deluge folder before re-installing).  Still no change.

Because the above steps are magnet-link specific, I dont' see how this should affect the behavior on regular torrent files.  

I would like to post this question to the deluge forums at the deluge website ( [http://dev.deluge-torrent.info/](http://dev.deluge-torrent.info/) ), but I'm unable to register, and there is no other contact-link other than to use their community forum.  The registration fails to send an activation email (yes, I have checked my spam folder, and retried several times, double-checking my email address).  If someone knows how to contact the deluge-developers or someone in charge of their website, that'd be a big help.

---

### Post by P4man on 2009-11-20
do you know if the problem is firefox or deluge? I guess you could find out by using another torrent client or another browser. Alternatively, save a torrent file and double click it (or right click and open it with deluge). Does that work properly?

---

### Post by greylander on 2009-11-20
Good question.  I should have thought to test that.

Double clicking a torrent file form the file browser has exactly the same effect as opening a torrent from firefox.  Deluge starts but does not add the torrent, and if already running a new copy of deluge starts.

I have tried calling deluge directly from the command line, but I do not know if I have the right the syntax.  I would expect "deluge torrentfilename" to work, but I don't really know if that is the correct way to invoke it.  But when I try to start deluge that way, again it is the same problem, including that it will invoke a 2nd copy of deluge if already running.

"deluge -h" gives syntax of "deluge [options] [actions]" and lists the available options, but no indication of what "[actions]" should look like.  For example, maybe to add a torrent I need to type something like "deluge -add filname" or "deluge --Add=filename" or something like that?

---

### Post by P4man on 2009-11-20
just ```
deluge /path/to/torrent.torrent
```

But really, I would just reinstall deluge.
First delete ~/.config/deluge
(that will delete all settings and states)
then reinstall
```
sudo apt-get install --reinstall deluge
```

---

### Post by greylander on 2009-11-20
I already did the re-install, complete with deleting ~/.config/deluge.  I used the "completely remove" option in synaptic for the uninstall.  No change.

---

### Post by P4man on 2009-11-20
So its not in deluge but elsewhere. perhaps try to undo your changes in gconf
```

gconftool-2 --recursive-unset /desktop/gnome/url-handlers/magnet
```

though it would surprise me if that helps.
have you tried with another user?

---

### Post by greylander on 2009-11-20
Unset the gconf setting as suggested.  Still no change (tested by double-clicking torrent files).

---

### Post by carniola on 2009-11-20
What version are you using? I had the exact same problem after upgrading to 1.2.0_rc3 

I fixed it by uninstalling and then installing the deb package (v. 1.1.9-1) over at [_getdeb_]("http://www.getdeb.net/updates/?q=deluge"). It was back to normal then.

---

### Post by P4man on 2009-11-20
> **carniola said:**
> What version are you using? I had the exact same problem after upgrading to 1.2.0_rc3 

I fixed it by uninstalling and then installing the deb package (v. 1.1.9-1) over at [_getdeb_]("http://www.getdeb.net/updates/?q=deluge"). It was back to normal then.

aaaah. That could be it. greylander did you add a PPA to your software sources that has this beta version? If so reinstalling wont help as it will reinstall that version again each time. Remove it from your software sources (system > administration > software sources). Then remove deluge and reinstall it from the official repositories. There is a reason software is tested before they put it in the official repo's ;)

---

### Post by greylander on 2009-11-20
If it helps, here is the first few dozen lines of debug log from deluge.  The only two lines referencing the torent file name are the ones you see here echoing the parameter and indicating that it is passed to the GUI.  There is not later entry indicating any attempt to open or read the torrent file.

Another oddity is the "[WARNING ] 12:36:14 config:402 Unable to open config file: /home/greylander/.config/deluge/ui.conf" line.  I checked permissions on this file, and it is read/writeable -- I even verified by opening/changing/saving the file with a a text editor.  Yet this warning occurs every time, along with the subsequent steps of backing it up and creating a new one.  I have no idea why this is happening or if it is at all related to the problem at hand.



```
[INFO    ] 12:21:45 main:114 Deluge ui 1.2.0-rc3
[DEBUG   ] 12:21:45 main:115 options: {'loglevel': 'debug', 'default_ui': None, 'args': None, 'quiet': False, 'ui': None, 'logfile': 'deluge.dbg', 'conf
ig': None}
[DEBUG   ] 12:21:45 main:116 args: ['/home/greylander/Downloads/Torrents/Jethro_Tull_Discography.4041527.TPB-1.torrent']
[DEBUG   ] 12:21:45 main:117 ui_args: ['/home/greylander/Downloads/Torrents/Jethro_Tull_Discography.4041527.TPB-1.torrent']
[INFO    ] 12:21:45 main:120 Starting ui..
[DEBUG   ] 12:21:45 ui:109 UI init..
[DEBUG   ] 12:21:45 configmanager:111 Getting config 'ui.conf'
[DEBUG   ] 12:21:45 config:374 Config /home/greylander/.config/deluge/ui.conf version: 1.1 loaded: {'default_ui': u'gtk'}
[WARNING ] 12:21:45 config:402 Unable to open config file: /home/greylander/.config/deluge/ui.conf
[DEBUG   ] 12:21:45 config:408 Saving new config file /home/greylander/.config/deluge/ui.conf.new
[DEBUG   ] 12:21:45 config:421 Backing up old config file to /home/greylander/.config/deluge/ui.conf~
[DEBUG   ] 12:21:45 config:429 Moving new config file /home/greylander/.config/deluge/ui.conf.new to /home/greylander/.config/deluge/ui.conf..
[INFO    ] 12:21:45 ui:126 Starting GtkUI..
[DEBUG   ] 12:21:45 gtkui:168 GNOME session 'die' handler registered!
[DEBUG   ] 12:21:45 configmanager:111 Getting config 'gtkui.conf'
[DEBUG   ] 12:21:45 config:374 Config /home/greylander/.config/deluge/gtkui.conf version: 1.1 loaded: {'close_to_tray': True, 'ntf_sound_path': u'/home/
greylander', 'window_width': 872, 'default_load_path': u'/home/greylander/Downloads/Torrents', 'window_y_pos': 53, 'ntf_email': False, 'tray_upload_spee
d_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'show_statusbar': True, 'ntf_popup': False, 'ntf_pass': u'', 'show_sidebar': True, 'window_maximized': False, '
enable_system_tray': True, 'tray_download_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'show_connection_manager_on_start': True, 'lock_tray': False, 'nt
f_sound': False, 'tray_password': u'', 'focus_add_dialog': True, 'ntf_server': u'', 'start_in_tray': False, 'ntf_tray_blink': True, 'check_new_releases'
: False, 'autoadd_queued': False, 'autoconnect_host_id': None, 'classic_mode': True, 'window_pane_position': 502, 'enabled_plugins': [], 'show_rate_in_t
itle': False, 'autoadd_enable': False, 'ntf_username': u'', 'interactive_add': True, 'sidebar_show_zero': False, 'window_x_pos': 424, 'window_height': 8
27, 'ntf_security': None, 'connection_limit_list': [50, 100, 200, 300, 500], 'sidebar_position': 170, 'show_new_releases': False, 'autoconnect': False, 
'choose_directory_dialog_path': u'/home/greylander', 'sidebar_show_trackers': True, 'autostart_localhost': False, 'show_toolbar': True, 'autoadd_locatio
n': u'', 'ntf_email_add': u'', 'signal_port': 40000}
[DEBUG   ] 12:21:45 component:99 Registered QueuedTorrents with ComponentRegistry..
[DEBUG   ] 12:21:45 configmanager:111 Getting config 'gtkui.conf'
[DEBUG   ] 12:21:45 component:99 Registered IPCInterface with ComponentRegistry..
[DEBUG   ] 12:21:45 ipcinterface:108 Checking if lockfile exists: /home/greylander/.config/deluge/ipc/deluge-gtk.lock
[DEBUG   ] 12:21:45 component:99 Registered TrackerIcons with ComponentRegistry..
[DEBUG   ] 12:21:45 component:99 Registered MainWindow with ComponentRegistry..
[DEBUG   ] 12:21:45 configmanager:111 Getting config 'gtkui.conf'
[DEBUG   ] 12:21:46 config:287 Registering function for show_rate_in_title key..
[DEBUG   ] 12:21:46 menubar:53 MenuBar init..
[DEBUG   ] 12:21:46 component:99 Registered MenuBar with ComponentRegistry..
[DEBUG   ] 12:21:46 configmanager:111 Getting config 'gtkui.conf'
[DEBUG   ] 12:21:46 config:287 Registering function for classic_mode key..
[DEBUG   ] 12:21:46 component:99 Registered ToolBar with ComponentRegistry..
[DEBUG   ] 12:21:46 toolbar:51 ToolBar Init..
[DEBUG   ] 12:21:46 configmanager:111 Getting config 'gtkui.conf'
[DEBUG   ] 12:21:46 config:287 Registering function for classic_mode key..
[DEBUG   ] 12:21:46 component:99 Registered TorrentView with ComponentRegistry..
[DEBUG   ] 12:21:46 listview:136 ListView initialized..
[DEBUG   ] 12:21:46 listview:247 Loading ListView state file: torrentview.state
[DEBUG   ] 12:21:46 torrentview:159 TorrentView Init..
[DEBUG   ] 12:21:46 component:99 Registered TorrentDetails with ComponentRegistry..
[DEBUG   ] 12:21:46 torrentdetails:430 Loading TorrentDetails state file: tabs.state

```

---

### Post by greylander on 2009-11-20
(my last post was prior to seeing the preceding two posts)

I'll try reverting to earlier version, but I think this problem started when I was in 1.1.6 (six not nine), but since I was originally just trying to get magnet links to work, it may be that not all the symptoms I have described existed prior to updating to 1.2.0-rc3.

The deluge website shows the above the be the "current release", so I though it would be fine -- followed instructions from them as far as adding the repository.  I think that before I did this, I looked for a later version in synaptic and 1.1.6 was the highest that I saw.

Anyway, let me tinker with repositories & see if I can get 1.1.9 installed.

---

### Post by Vaphell on 2009-11-20
i find it quite amusing that they let such a fat bug slip through. I also installed 1.2 from ppa and started to have problems with autolaunching deluge+autoadding torrent (it doesn't start torrent, adding .torrent when deluge is opened often results in a 'frozen' state where you don't see the progress, up and down speeds changing and have to restart to get it right)
I get that it's beta, but don't they test such basic usage patterns at all?

---

### Post by greylander on 2009-11-20
OK I disabled the delute-team repositories, and now synaptic shows 1.1.6 as the latest version.  Now I will try to get 1.1.9 form getdeb.

---

### Post by greylander on 2009-11-20
OK, now I feel like I've gone down the rabbit hole...

Found deluge-1.1.9-1 at [http://www.getdeb.net/updates/deluge](http://www.getdeb.net/updates/deluge)

It installs direct from firefox using apturl.  BUT... whatever gets installed is broken.  If I start deluge, a blank window opens and freezes -- if I try to close, it says "not responding" and I have to force quit.

Also, when I look in synaptic to see what is installed, it shows 1.1.6 (six not nine) installed.  I completely uninstalled this again (including config files) and reinstalled from getdeb again, just to be sure, and same thing happens.

---

### Post by greylander on 2009-11-20
getting stranger...

I tried to generate a debug log with "deluge -l logfile.txt -L debug", but all it did was print the version number, 1.1.6 (to the console, not the log file) and exit, just as if I had entered "deluge --version".

It is still broken in the same way now, even if I uninstall and re-install version 1.1.6 in synaptic.

---

### Post by greylander on 2009-11-20
I tried installing the version 1.1.9 found here:

[https://launchpad.net/~deluge-team/+archive/ppa/+packages](https://launchpad.net/~deluge-team/+archive/ppa/+packages)

to no avail.  Still completely broken.  I think installing 1.2.0-rc3 must have pulled in something (gtk libraries or ???) which is now incompatible with the older versions.

Any ideas on how I can revert back to a clean 1.1.x deluge?  Where should I even start looking?

---

### Post by greylander on 2009-11-20
Because this is now a new problem, I have started a new thread for it: [http://ubuntuforums.org/showthread.php?t=1332434](http://ubuntuforums.org/showthread.php?t=1332434)

---

### Post by P4man on 2009-11-20
try re-enabling that PPA, then uninstall and purge anything deluge
```

sudo apt-get remove --purge deluge
```

Then check system > adminstration > computer janitor 
for any references to deluge. Remove any, but be careful not to remove everything janitor suggests. Its VERY trigger happy

Only then remove the PPA, reload your sources, and try installing it again from the repo's.

 make sure deluge is not running while you do any of this.

---

### Post by greylander on 2009-11-20
OK, I did the purge one before restoring the PPA... once after...

deleted ~/.config/deluge

used janitor, but it did not find anything deluge related.

Then I decided to try installing 1.1.9 from [http://www.getdeb.net/app/Deluge](http://www.getdeb.net/app/Deluge) but it ended up installing 1.2.0-rc3!!

This is getting very strange.  I'm certain that I tried the getdeb install before and it gave me 1.1.6 instead of 1.1.9 (it clearly says 1.1.9).

One thing, I didn't disable the deluge developer PPA's... so it seems like fetching a package from the getdeb website somehow just grabs the latest version in my available repositories.  What is going on here?

so... I'm going to purge it again, then I'll disable the developer PPA, then I'm just going to install the latest version via synaptic (1.1.6), so hopefully I will be back to my starting point.

---

### Post by greylander on 2009-11-20
OK, I finally have deluge 1.1.6 working normally again.

I *think* that the problem that was breaking it was a that the deluge daemon (deluged) from version 1.2.0 was still running in the background, and I overlooked it somehow.  Now I can consistently start deluge and add torrents in the usual ways.

So now I am at my orginal starting point.  I have Deluge 1.1.6 on Jaunt 64-bit.  I want to get magnet links working from Firefox.

Question:  should 1.1.6 support magnet links?

If so, should the gconftools-2 commands above do the trick, and is "/usr/bin/deluge %s" the correct command string to use?

If not, what version?  Presumably 1.1.9.  What is the best way to get 1.1.9?

And again, the same questions about gconftools.

BTW, and thanks so much for all the help.  This is the single biggest problem, by far, that I have ever had with Ubuntu.

---

### Post by P4man on 2009-11-20
I have no idea how to configure it or what version of deluge is needed for magnet link support (I dont really see the point of it tbh), but 1.1.9 is the version in karmic's default repo's. Perhaps you can enable the backport repository in software sources, maybe they backported 1.1.9 to jaunty? If not, then I guess you can always try uninstalling deluge and grabbing a .deb of the latest **stable** release and give that a try. Now you know how to undo it :)

---

### Post by christopher.newell on 2009-11-20
Hi Greylander, I have been having similar problems getting rid of an unwanted version of Deluge.  In the end, I had to use a multifaceted approach.  I did a "complete removal" of any instance I could find for deluge within Synaptic package manager, then I used nautilus to find all files & folders named deluge.  I deleted all files (except the .png files and things like ebooks with "deluge" in the title).  Next, I opened my software sources and deselected the ppa for deluge.  Then I went to the Ubuntu Software Center (I'm using 9.10) and installed 1.1.9 from there.  No 1.2 any longer!  Unfortunately, I still couldn't initiate a torrent from Firefox, but I found a bug report for someone who had upgraded to Karmic, and couldn't replicate the bug on a fresh install.  I had upgraded, so I tried the advice:
> Can you add the following to /etc/apparmor.d/usr.bin.firefox-3.5:
  /usr/bin/deluge Ux,
  /usr/bin/mkfifo Ux,

Then reload the profile with:
```
sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox-3.5
```
I can load from Firefox again!

I wish I could help you with Magnet links.  Haven't used them since my Windows/Azureus days.  I hope this helps you get back up and running too.

---

### Post by slumbergod on 2009-11-20
I got burned using the latest Deluge versions so now I will only ever use the repo version, currently 1.1.9.

The devs for the project don't seem to understand the idea of keeping a testing version and a stable version. Instead, they only point to the testing version and these are usually very buggy. It wouldn't be such an issue if people were only downloading small files but if you are grabbing multimedia files the last thing you want to do is kill a torrent half way through.

---

### Post by kerry_s on 2009-11-20
you might want to think about switching to qbittorrent, so many sites are switching to those magnet links. it will still work even if unreachable. see pic

---

### Post by otrojake on 2009-11-20
I was having the exact same issue with Deluge.  It's fixed now.  A newer version of Deluge is in the PPA and it works fine again.

---

### Post by greylander on 2009-11-20
I think I'm going to not worry too much about magnet links for now... I only got interested because of the recent move by piratebay.  I didn't realize 1.1.9 was for karmic not jaunty, so until I make the move to karmic, I'll stick with 1.1.6, and maybe check out some other torrent clients.

I'm not even sure deluge 1.1.9 or 1.2.0 support magnet links, after reading some of the forum discussions on the deluge website.  There was a post here that indicated deluge supports it, and a list of features (I think it was on wikipedia) suggested magnet link support.

Does anyone know if any version of Deluge actually supports magnet links?

---

### Post by otrojake on 2009-11-21
I'm using the newest Deluge, so I can't speak to older versions, but I can affirm on my machine that Deluge 1.2.0(rc3) supports magnet links.

---

### Post by scouser73 on 2009-11-21
I've just had updates for Deluge 1.2.0-rc3, and where I was experiencing the same problem as the op in adding torrents, the updates have fixed this problem.

That was obviously just a quirk of the RC.

---

