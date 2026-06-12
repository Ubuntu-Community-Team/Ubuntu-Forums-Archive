---
title: "Brasero Disc Write Error (ISO Burning)"
date: 2010-02-11
forum: General Help
---

### Post by xdemo on 2010-02-11
Heres a first for me:

Been using Ubuntu since 8.10 currently running Karmic(64bit), all upto date etc. Anyway, i downloaded Debian, always been wanting to test it out.

I downloaded the iso via Debians torrent tracker (debian-503-amd64-DVD-1.iso) and today i tried to burn it the disc, using the right click option "write to disc..." in nautilus.

Came up with an error, saying a bunch of stuff, though it was a naff disc. So i tried to reburn the iso at 4x speed, and came across the same error. Which i have pasted the logfile below in codebox...

I'm not sure why this has happened. As i recently burned an xubuntu cd using the same DVD-R discs, which installed fine on my laptop about a month ago.

If this helps, the discs i am using are from ASDA (4.7GB single sided 16 x speed DVD-R), however this is the first problem i have had using these discs.

Error Log:
```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_RBCT7U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_UWCT7U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage There is a checksum already 0
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
    growisofs
    -use-the-force-luke=notray
    -use-the-force-luke=4gms
    -dvd-compat
    -speed=4
    -use-the-force-luke=tracksize:2293576
    -use-the-force-luke=tty
    -Z
    /dev/sr0=/home/demo/Downloads/debian-503-amd64-DVD-1.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/demo/Downloads/debian-503-amd64-DVD-1.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 4.1x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=e0h failed with SK=5h/INVALID ADDRESS FOR WRITE]: Invalid argument
BraseroGrowisofs stderr: :-( write failed: Invalid argument
BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: updating RMA
BraseroGrowisofs stderr: /dev/sr0: closing disc
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 22
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)

```

What suggestions does anyone have? I am not sure whether to completely remove brasero, and reinstall the package after. Or whether my Debian ISO is corrupt...

Thanks in advance. ;)

---

### Post by mirosol on 2010-02-13
Brasero just killed two dvd-rs for me. But K3B burned both images without any problems. Both frontends use same growfs app, so my bet is on that bug is in latest (and earlier) ubuntu build of brasero. (won't even try to point out the bug from launchpad, even with dist-version, there's too many
[http://www.google.com/search?hl=en&q=launchpad+brasero+bug](http://www.google.com/search?hl=en&q=launchpad+brasero+bug) )

If kubuntu team doesn't kill usablity of KDE 4.4 (like it did on 4.3), i might seriously consider using it althogether.

So if brasero kills your discs, try K3B. Put in simple:
System -> Administration -> Synaptic -> Search and install k3b package (you might want/need "kubuntu-restricted-extras" too. It just adds mp3 support to k3b)

Or even simpler:
```
sudo apt-get install k3b kubuntu-restricted-extras
```

It will drag *A LOT* of dependencies if you are using all-gnome system, but still i think it's worth it.

---

### Post by xdemo on 2010-02-14
Thanks for reply, i am using GNOME desktop yes. I'll have a look into it though. Thanks for pointing out the problem.

---

