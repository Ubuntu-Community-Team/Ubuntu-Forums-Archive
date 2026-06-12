---
title: "Odd behaviour with Tracker"
date: 2009-08-17
forum: General Help
---

### Post by FokkerCharlie on 2009-08-17
Hi

Recently I have noticed that after my laptop has been running a little while, I can hear little bursts of HDD activity- after a bit of googling, it seems to me that it is associated with Tracker.

My ~/.local/share/tracker/trackerd.log fills up with this:

```

17 Aug 2009, 19:16:58: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:16:58: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:16:58: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:16:58: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:16:58: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:16:58: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:16:58: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:16:58: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:16:58: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:16:58: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:16:58: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:16:58: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:17:14: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:17:16: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:17:16: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed

17 Aug 2009, 19:17:20: GLib-GIO-Critical **: g_file_hash: assertion `G_IS_FILE (file)' failed
```

And tracker-indexer.log shows this:

```

17 Aug 2009, 14:17:45: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 14:18:22: Tracker-Warning **: constraint failed

17 Aug 2009, 15:05:23: Tracker-Warning **: constraint failed

17 Aug 2009, 15:05:23: Tracker-Warning **: constraint failed

17 Aug 2009, 15:05:23: Tracker-Warning **: constraint failed

17 Aug 2009, 18:00:38: Tracker-Warning **: constraint failed

17 Aug 2009, 18:00:38: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed

17 Aug 2009, 19:11:44: Tracker-Warning **: constraint failed
```

tracker-extract.log is empty.

I googled the messages in the files, but didn't turn up that much- a similar-looking bug in Red Hat:  [https://bugzilla.redhat.com/show_bug.cgi?id=489606]("https://bugzilla.redhat.com/show_bug.cgi?id=489606")  which doesn't seem to be resolved beyond 'remove the config and start again', and something close in Ubuntu : [http://https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/366262]("http://https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/366262"), although I'm not seeing serious problems with desktop responsiveness.

So, I can remove the config bits and do that, no problem.  However, is there something smarter to do?  Should I file a bug for this?

Thanks in advance for your advice.

Charlie

---

