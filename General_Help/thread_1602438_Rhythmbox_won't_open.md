---
title: "Rhythmbox won't open"
date: 2010-10-21
forum: General Help
---

### Post by ahmedm989 on 2010-10-21
Hello everyone,

I think this started after upgrading to 10.10. Rhythmbox won't open for some reason. It opens up for a second and closes. I only tried it because Banshee wasn't playing any songs. When I try to open a song it just closes the whole program. A few programs won't open for me actually, at all, including Liferea Feed Reader which I installed recently.

Any help would be appreciated.

---

### Post by matthew.parlette on 2010-10-21
I know this sounds pretty dumb, but I would check in the tray at the top-right to make sure it didn't start minimized there (not minimized as in in the taskbar at the bottom, but as it only the icon shows in the 'system tray' in the upper right).

Sometimes I have started the program and nothing showed up on my screen, but it just started in a state where it only showed that icon, then I could open it from there.

Does this make sense?

---

### Post by scouser73 on 2010-10-21
Sometimes a program will start and will not be visible, check what matthew.parlette and if no joy then check **System** [COLOR="Red"]**>**[/COLOR] **Administration** [COLOR="red"]**>**[/COLOR] **System Monitor** and click the Processes tab and check to see if Rhythmbox is running, if it is, highlight it and select **End Process**.

---

### Post by ahmedm989 on 2010-10-21
Yeah, I understand what you guys are saying, but I already tried that. It's not running. Even if that was the case, though, it doesn't explain the issue with Banshee. I don't get why it crashes after I try playing any song.

---

### Post by sikander3786 on 2010-10-21
Try opening it from the terminal and post the error message it returns.

```
rhythmbox
```

---

### Post by ahmedm989 on 2010-10-21
Rhythmbox:

> rhythmbox

(rhythmbox:6207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
** (rhythmbox:6207): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object
** (rhythmbox:6207): DEBUG: Loading the real store page

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3DAPU0HuBvk3MNHze%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1287680517%26oauth_token%3DlpQ9Xr0s2FPBhrngRZ97%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&pQ1Bn57PlDwHd9fkGd5THdJkm4xwwHTT67V9n7lQJXKVh33g4MGccxD9Wm84CSBSqx2Mk3KV8dVJ158j'

** (rhythmbox:6207): DEBUG: navigation requested to [https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=APU0HuBvk3MNHze&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1287680517&oauth_token=lpQ9Xr0s2FPBhrngRZ97&oauth_verifier=None&oauth_version=1.0&oauth_signature=leVCcino7aNcOvL5Tw2Nwj%2Fuoa0%3D](https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=APU0HuBvk3MNHze&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1287680517&oauth_token=lpQ9Xr0s2FPBhrngRZ97&oauth_verifier=None&oauth_version=1.0&oauth_signature=leVCcino7aNcOvL5Tw2Nwj%2Fuoa0%3D)
Segmentation fault


Liferea:

> liferea
set zoom: 1.00

Liferea did receive signal 11 (Segmentation fault).


It seems like a similar problem: segmentation fault, although I have no idea what that means in this case.

---

### Post by sikander3786 on 2010-10-21
Search for ubuntu-one-rhythmbox plugin in Software Center. Remove it if you don't need and you'll be good to go.

---

### Post by ahmedm989 on 2010-10-21
OK, that worked. Thanks.

Do you have any idea about the Banshee or Liferea problems? Banshee worked after I did that then suddenly started acting the same way: when I play a song it quits the program.

---

### Post by sikander3786 on 2010-10-22
You need to post the output for banshee as well.

```
banshee
```

---

### Post by ahmedm989 on 2010-10-23
OK, here it is for Banshee:
> banshee
[Info  01:59:30.180] Running Banshee 1.7.6: [Ubuntu maverick (development branch) (linux-gnu, i686) @ 2010-09-18 20:47:48 UTC]
[Info  01:59:37.754] Updating web proxy from GConf
[Info  01:59:37.927] All services are started 6.603896
[Info  01:59:42.824] nereid Client Started
[Warn  01:59:43.452] Failed to load media-player-info file for 

** (Banshee:2544): CRITICAL **: itdb_get_control_dir: assertion `mountpoint' failed
[Warn  01:59:48.101] Failed to load media-player-info file for 
Stacktrace:


Native stacktrace:

	banshee-1() [0x80d4d0b]
	banshee-1() [0x810ffeb]
	[0x36140c]

Debug info from gdb:

ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted


---

### Post by sikander3786 on 2010-10-23
You'll need to remove some Banshee extensions. See here.

[http://ubuntuforums.org/showthread.php?t=1554252](http://ubuntuforums.org/showthread.php?t=1554252)

---

### Post by ahmedm989 on 2010-11-07
Thanks for the help sikander3786. Sorry for the late reply. I'm still working out a few things, but was distracted with other life issues. :)

Thanks again.

---

