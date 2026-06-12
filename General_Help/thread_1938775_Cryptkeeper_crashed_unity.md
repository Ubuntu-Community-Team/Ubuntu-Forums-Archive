---
title: "Cryptkeeper crashed unity"
date: 2012-03-10
forum: General Help
---

### Post by 4042966262 on 2012-03-10
downloaded cyyptkeeper
sso apt-get install cryptkeper

then i ran these codes
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Skype', 'Cryptkeeper']" setsid unity
unity went crazy, i opened terinal and typed grun then unity. well it lanched something that looked like login screen!
i a on guest user right now. the desktop of normal user looks..almost like a stripped down version. what do i need to do to get ubuntu back to all its glory?

this is the tut i followed [http://www.makeuseof.com/tag/encrypt-protect-computer-files-cryptkeeper-linux/](http://www.makeuseof.com/tag/encrypt-protect-computer-files-cryptkeeper-linux/)

---

### Post by raja.genupula on 2012-03-10
have you tried 
```
unity --reset
```

if not then try it .

---

### Post by 4042966262 on 2012-03-10
[http://imageshack.us/photo/my-images/638/screenshotat20120310120.png/](http://imageshack.us/photo/my-images/638/screenshotat20120310120.png/)
well i typed that in. terminal spit out this code. (located below)
there is a stripped down verson of unity, almost like whats seen on Lubuntu
coffeegulpers@coffeegulpers:~$ reset --unity
reset: invalid option -- '-'
Usage: tset [options] [terminal]

Options:
  -c          set control characters
  -e ch       erase character
  -I          no initialization strings
  -i ch       interrupt character
  -k ch       kill character
  -m mapping  map identifier to type
  -Q          do not output control key settings
  -r          display term on stderr
  -s          output TERM set command
  -V          print curses-version
  -w          set window-size

coffeegulpers@coffeegulpers:~$ unity --reset
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done

Screen geometry changed:
   0x0x1280x800

unity-panel-service: no process found
Initializing unityshell options...done
DEBUG 2012-03-10 12:06:36 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1280 h=800
Initializing addhelper options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing debugspew options...done
Initializing extrawm options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing zoom options...done
Setting Update "main_menu_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x38001b1

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x38001ae

WARN  2012-03-10 12:07:14 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

---

### Post by raja.genupula on 2012-03-10
```
sudo apt-get install --reinstall ubuntu-desktop
```

what its giving to you ?

---

### Post by 4042966262 on 2012-03-10
oh right.. about that,
software mananger is haning issues, and im trying to resinstall it as well
so the code threw...

coffeegulpers@coffeegulpers:~$ sudo apt-get install --reinstall ubuntu-desktop
[sudo] password for coffeegulpers: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-desktop : Depends: software-center but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
coffeegulpers@coffeegulpers:~$

---

### Post by raja.genupula on 2012-03-10
do this ```
sudo apt-get install -f
sudo apt-get update
```

and try again

---

### Post by 4042966262 on 2012-03-11
this thread is solved. i created new user account.

---

