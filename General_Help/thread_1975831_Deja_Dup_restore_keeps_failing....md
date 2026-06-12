---
title: "Deja Dup restore keeps failing..."
date: 2012-05-07
forum: General Help
---

### Post by memilanuk on 2012-05-07
So... I had Ubuntu 11.10 working okay, more or less, a few quirks/bugs in Unity / Dash were annoying the heck out of me.  So I decided to do a complete wipe and reinstall of 12.04.  On this particular machine I have it dual-booting with Vista, and for linux I have 20GB for /, ~50GB for /home, and ~215GB under /home/share where I store things like backups, iso images, and VirtualBox VMs.  The plan was to wipe & reformat / and /home, keep /windows and /home/share, and reinstall, followed by restoring stuff in my home directory from backups stored on /home/share/backups.

Initially things went well.  Unity is a bit 'heavier' than I want to run on this particular machine, so I decided to reinstall again, this time with Xubuntu 12.04.  I did another backup via Deja Dup, burned a new install disc, and rebooted.  

Everything seemed to go okay, but when I was restoring from backups, Deja Dup bombed out with what looks like a python error.  Since I had been simultaneously updating and installing new software (a lot of which was python related) I thought maybe something had gotten a little corrupted in the process.  So I reinstalled again, applied all the updates, then tried reinstalling.  Same errors (as near as I can tell).  So I reinstalled *again*... this time I tried restoring *before* downloading and applying all the updates... still no joy.  I tried restoring from the previous backup - which did work before, thinking it might be a problem with the backup files themselves - still nothing.

So at this point I'm getting a little ticked off... I've had to sit thru the reinstall and restore process way more times than I should have, and I'm still no closer to getting a stable and functional setup with all of my old files where they should be -in my home directory.

Here is the errors I'm getting (pardon any typos, I'm having to manually type it from one machine to another to post this...)

```

Traceback (most recent call last):
File "/usr/bin/duplicity", line 1403, in <module>
  with_tempdir(main)
File "/usr/bin/duplicity", line 1396, in with_tempdir 
  fn()
File "/usr/bin/duplicity", line 1330, in main 
  restore(col_stats)
File "/usr/bin/duplicity", line 623, in restore 
  restore_get_patched_rop_iter(col_stats)):
File "/usr/lib/python2.7/dist-packages/duplicity/
patchdir.py", line 495, in integrate_patch_iters
  final_ropath = patch_seq2ropath(normalize_ps(patch_seq)
)
File "/usr/lib/python2.7/dist-packages/duplicity/
patchdir.py", line 475, in patch_seq2ropath
  misc.copyfileobj(current_file, tempfp)
File "/usr/lib/python2.7/dist-packages/duplicity/misc.py",
line 166, in copyfileobj
  buf = infp.read(blocksize)
File "/usr/lib/python2.7/dist-packages/duplicity/librsync.py",
line 80, inread
  self, add_to_outbuf_once()
File "/usr/lib/python2.7/dist-packages/duplicity/librsync.py",
line 94, in _add_to_outbuf_once
  raise librsyncError(str(e))
librsyncError: librsync error 103 while in patch cycle

```

So... if I'm reading that right, librsync is coughing up an error, which is then raising all the way up thru the application code and causing Deja Dup to bomb out.  So whats causing librsync to fail?

Should I submit a bug report in the morning when I can get this machine connected to a network again?

In the mean time, how do I get my backups restored?!?

TIA,

Monte

---

### Post by memilanuk on 2012-05-08
Btt

---

### Post by enigmaingr on 2012-08-20
This is precisely the same thing that happened to me. I backed up my Home folder to Deja Dup while in Ubuntu 11.10. I then did a clean install from disk of Ubuntu 12.04 without a problem. When I went to restore my Home folder from the external hard drive, I got essentially the same text error as the original poster. Any suggestions?

---

### Post by Lunarts on 2012-11-22
[https://bugs.launchpad.net/duplicity/+bug/662442](https://bugs.launchpad.net/duplicity/+bug/662442)

A patch above which will ignore broken files.

---

