---
title: "Cannot burn any type of CD or DVD"
date: 2011-03-07
forum: General Help
---

### Post by gryphoninc on 2011-03-07
Hi
I cannot seem to burn anything , no cd or dvd

I have tried using K3b, keep getting errors in that one.
Tried Gnomebaker and it does not work
Tried Nero Linux 4 nothing
tried Brasero doesn't burn

Help
:confused:

---

### Post by nomko on 2011-03-07
It sounds like your burner is finished. It's no coincidence that you've got problems with all 4 burning tools. A question: if you burning a cd/dvd and it goes wrong, doen't you get any error messages? If so, can you please post them here?
 
What you can try also is this: try starting the program using the terminal. Just open a erminal and enter the program name. This way you can see what's wrong with your burning application or what kind of errors you migth have.

---

### Post by gryphoninc on 2011-03-07
Thanks for responding

It cannot be both DVD Drives, they worked fine when I was using Windows, I just installed Ubuntu 10.10 over the weekend and it has been great till now. Will not go back to Windows.

When I burn with Brasero, multi-session and normal DVD's or CD's I receive this error code:

[IMG]http://i21.photobucket.com/albums/b274/rapiertoledana/Workspace1_0023.png[/IMG]


As you can see I get some sort of error.

this is the log

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
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
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_last_session_address
BraseroChecksumFiles called brasero_job_get_medium
BraseroChecksumFiles no checksum file found
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_V0IASV.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroLibburn called brasero_job_get_action
BraseroLibburn creating input
BraseroLibburn called brasero_job_get_action
BraseroLibburn unsupported operation
BraseroLibburn deactivating
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage deactivating
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_last_session_address
BraseroGenisoimage called brasero_job_get_next_writable_address
BraseroGenisoimage called brasero_job_get_device
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
    /usr/bin/genisoimage
    -input-charset
    utf8
    -r
    -graft-points
    -path-list
    /tmp/brasero_tmp_OPWSRV
    -exclude-list
    /tmp/brasero_tmp_DUWSRV
    -V
    2011-02-20_0727
    -A
    Brasero-2.32.0
    -sysid
    LINUX
    -C
    1149328,1519456
    -M
    /dev/sr1
    -quiet
    -print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_fd_in
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: NO Rock Ridge present
BraseroGenisoimage stderr: Disabling Rock Ridge / XA / AA
BraseroGenisoimage stderr: Warning: Neither Rock Ridge (-R) nor TRANS.TBL (-T) 
BraseroGenisoimage stderr: name translations were found on previous session.
BraseroGenisoimage stdout: 359228
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stderr: ISO-9660 file names have been used instead.
BraseroGenisoimage stdout: HUP
BraseroGenisoimage stderr: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage Finished track successfully
BraseroGenisoimage called brasero_job_get_done_tracks
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage stopping
BraseroGenisoimage called brasero_job_get_done_tracks
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroLibburn called brasero_job_get_action
BraseroLibburn creating input
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_device
BraseroLibburn Drive (/dev/sr1) init result = 1
BraseroLibburn called brasero_job_get_flags
BraseroLibburn called brasero_job_get_media
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_input_type
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn Setting multi 1
BraseroLibburn Setting burnproof 1
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage linked to BraseroLibburn
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroChecksumImage
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_last_session_address
BraseroGenisoimage called brasero_job_get_next_writable_address
BraseroGenisoimage called brasero_job_get_device
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
    /usr/bin/genisoimage
    -input-charset
    utf8
    -r
    -graft-points
    -path-list
    /tmp/brasero_tmp_OH0WRV
    -exclude-list
    /tmp/brasero_tmp_NM0WRV
    -V
    2011-02-20_0727
    -A
    Brasero-2.32.0
    -sysid
    LINUX
    -C
    1149328,1519456
    -M
    /dev/sr1
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroGenisoimage called brasero_job_get_fd_in
BraseroGenisoimage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroGenisoimage stderr: NO Rock Ridge present
BraseroGenisoimage stderr: Disabling Rock Ridge / XA / AA
BraseroGenisoimage stderr: Warning: Neither Rock Ridge (-R) nor TRANS.TBL (-T) 
BraseroGenisoimage stderr: name translations were found on previous session.
BraseroGenisoimage stderr: ISO-9660 file names have been used instead.
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr1 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr1 ) is true
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn mmc_set_streaming: end_lba=2298495 ,  r=6021 ,  w=22160
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn dvd/bd Profile= 11h , obs= 32768 , obs_pad= 1
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD pre-track 01 : get_nwa(1519456), ret= 1 , d->nwa= 0
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD pre-track 01 : demand=735698944, cap=1594228736

BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): [3 73 03] Power calibration area error
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Libburn reported an error SCSI error on write(1519456,16): [3 73 03] Power calibration area error
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
    error        = 1
    message    = "SCSI error on write(1519456,16): [3 73 03] Power calibration area error"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroChecksumImage
BraseroChecksumImage stopping
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroLibburn
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroLibburn stopping
BraseroLibburn closing connection for BraseroLibburn
Session error : SCSI error on write(1519456,16): [3 73 03] Power calibration area error (brasero_burn_record brasero-burn.c:2862)

---

### Post by nomko on 2011-03-07
That's for both cd/dvd burners?? Or just 1?
I see that there's something going on on the moment when a *Power calibration area error* has to be performed. 
 
And what about the other programs? What kind of error messages you get from them?

---

### Post by gryphoninc on 2011-03-07
[SIZE=3]I cannot burn with both.

I tried K3b and the same thing I got this message.



p, li { white-space: pre-wrap; } [/SIZE] [FONT=Monospace][SIZE=3]Devices[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]-----------------------[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]SONY DVD RW DRU-820A 1.0c (/dev/sr1, CD-R,  CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R  DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual  Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential,  DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO,  SAO/R96P, SAO/R96R, Restricted Overwrite, Layer Jump] [%7][/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]HL-DT-ST DVD-RAM GH22NP20 1.03 (/dev/sr0, CD-R,  CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R  DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual  Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential,  DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW,  SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite,  Layer Jump] [%7][/SIZE][/FONT][SIZE=3]

[/SIZE]    [FONT=Monospace][SIZE=3]K3b::IsoImager[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]-----------------------[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]mkisofs print size result: 359509 (736274432 bytes)[/SIZE][/FONT][SIZE=3]

[/SIZE]    [FONT=Monospace][SIZE=3]System[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]-----------------------[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]K3b Version: 2.0.1[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]KDE Version: 4.5.1 (KDE 4.5.1)[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]QT Version:  4.7.0[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Kernel:      2.6.35-27-generic[/SIZE][/FONT][SIZE=3]

[/SIZE]    [FONT=Monospace][SIZE=3]Used versions[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]-----------------------[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]mkisofs: 1.1.10[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]cdrecord: 1.1.10[/SIZE][/FONT][SIZE=3]

[/SIZE]    [FONT=Monospace][SIZE=3]cdrecord[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]-----------------------[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]scsidev: '/dev/sr0'[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]devname: '/dev/sr0'[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]scsibus: -2 target: -2 lun: -2[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]=== last message repeated 4 times. ===[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]WARNING: /dev/sr0 seems to be mounted![/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]/usr/bin/wodim: Device or resource busy. [/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Cannot open SCSI driver![/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]For possible targets try 'wodim --devices' or 'wodim -scanbus'.[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]For possible transport specifiers try 'wodim dev=help'.[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]the wodim documentation.[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]TOC Type: 1 = CD-ROM[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Waiting for data on stdin...[/SIZE][/FONT][SIZE=3]

[/SIZE]    [FONT=Monospace][SIZE=3]cdrecord command:[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]-----------------------[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=16 -sao driveropts=burnfree -multi -waiti -data -tsize=359509s -[/SIZE][/FONT][SIZE=3]

[/SIZE]    [FONT=Monospace][SIZE=3]mkisofs[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]-----------------------[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Warning: creating filesystem that does not conform to ISO-9660.[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]NO Rock Ridge present[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Disabling Rock Ridge / XA / AA[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Warning: Neither Rock Ridge (-R) nor TRANS.TBL (-T) [/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]name translations were found on previous session.[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]ISO-9660 file names have been used instead.[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]359509[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Warning: creating filesystem that does not conform to ISO-9660.[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Warning: ISO-9660 filenames longer than 31 may cause buffer overflows in the OS.[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]I: -input-charset not specified, using utf-8 (detected in locale settings)[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]NO Rock Ridge present[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Disabling Rock Ridge / XA / AA[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Warning: Neither Rock Ridge (-R) nor TRANS.TBL (-T) [/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]name translations were found on previous session.[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]ISO-9660 file names have been used instead.[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]Using aaf-underbelly000.files.the.man.who. for   Underbelly.Files.The.Man.Who.Got.Away/Subs/aaf-underbelly.files.the.man.who.got.away.proper.dvdri   p.xvid-subs.sfv  (aaf-underbelly.files.the.man.who.got.away.proper.dvdri   p.xvid-subs.rar)[/SIZE][/FONT][SIZE=3]

[/SIZE]    [FONT=Monospace][SIZE=3]mkisofs calculate size command:[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]-----------------------[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]/usr/bin/genisoimage -cdrecord-params  1149344,1519456 -prev-session /dev/sr0 -gui -graft-points -print-size  -quiet -volid 2011_02_20_ -volset  -appid K3B THE CD KREATOR (C)  1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid  LINUX -volset-size 1 -volset-seqno 1 -sort  /tmp/kde-gryphon/k3bDS5969.tmp -rational-rock -hide-list  /tmp/kde-gryphon/k3bNa5969.tmp -joliet -joliet-long -hide-joliet-list  /tmp/kde-gryphon/k3bnX5969.tmp -no-cache-inodes -udf  -untranslated-filenames -max-iso9660-filenames -translation-table  -hide-joliet-trans-tbl -iso-level 3 -path-list  /tmp/kde-gryphon/k3byx5969.tmp[/SIZE][/FONT][SIZE=3]

[/SIZE]    [FONT=Monospace][SIZE=3]mkisofs command:[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]-----------------------[/SIZE][/FONT][SIZE=3]
[/SIZE]  [FONT=Monospace][SIZE=3]/usr/bin/genisoimage -cdrecord-params  1149344,1519456 -prev-session /dev/sr0 -gui -graft-points -volid  2011_02_20_ -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN  TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1  -volset-seqno 1 -sort /tmp/kde-gryphon/k3bZm5969.tmp -rational-rock  -hide-list /tmp/kde-gryphon/k3bLe5969.tmp -joliet -joliet-long  -hide-joliet-list /tmp/kde-gryphon/k3bjk5969.tmp -no-cache-inodes -udf  -untranslated-filenames -max-iso9660-filenames -translation-table  -hide-joliet-trans-tbl -iso-level 3 -path-list  /tmp/kde-gryphon/k3boB5969.tmp[/SIZE][/FONT][SIZE=3]




[/SIZE]     [FONT=Monospace][SIZE=3]And I took a sceen shot of what I get when I load the DVD and what happens when it doesn't burn.[/SIZE][/FONT][SIZE=3]
[/SIZE] 

[FONT=Monospace][IMG]http://i21.photobucket.com/albums/b274/rapiertoledana/p1.png[/IMG]
[/FONT]
 


and this one when it fails to burn.

[IMG]http://i21.photobucket.com/albums/b274/rapiertoledana/Workspace1_002-1.png[/IMG]

[SIZE=3]hope you can help, I know that it is something stupid but I cannot work it out.[/SIZE]

[SIZE=3]I did a search on Google and came across this :[/SIZE]

***hey David, the solution to your problem is to go to cdrecord's website and download the newest version of cdrecord. Lets say you download it to your Downloads folder. Unzip it, and in the terminal type (without quotes) "cd /home/david(you're user name I'm assuming)/Downloads/(the name of the cdr-tools folder, ex. cdrtools-2.01a) then type "sudo make", hit enter, it'll ask for your password, type it and hit enter. Then type "sudo make install".  Now type these commands, enter after each line. This will move out of the way the useless wodim files previously on your computer, you can copy and paste these lines to your terminal. sudo mkdir /opt/schily/replacedfiles sudo mv /usr/bin/cdrecord /opt/schily/replacedfiles sudo mv /usr/bin/genisoimage /opt/schily/replacedfiles sudo mv /usr/bin/mkisofs /opt/schily/replacedfiles sudo mv /usr/bin/readom /opt/schily/replacedfiles sudo mv /usr/bin/wodim /opt/schily/replacedfiles next you'll link your new files to where k3b will look, hit enter after each line, you can copy and paste sudo ln -s /opt/schily/bin/cdrecord /usr/bin/cdrecord sudo ln -s /opt/schily/bin/mkisofs /usr/bin/genisoimage sudo ln -s /opt/schily/bin/mkisofs /usr/bin/mkisofs sudo ln -s /opt/schily/bin/readcd /usr/bin/readom sudo ln -s /opt/schily/bin/cdrecord /usr/bin/wodim sudo ln -s /opt/schily/bin/readcd /usr/bin/readcd sudo ln -s /opt/schily/bin/mkhybrid /usr/bin/mkhybrid sudo ln -s /opt/schily/bin/cdda2wav /usr/bin/cdda2wav now install k3b and write in RAW mode. You'll be able to write cds now. The whole reason you had this problem was because Ubuntu does not come with an original version of cdrecord, but an inferior modified version. Please Ubuntu, in 10.04 please please please use the full original version of cdrecord.***

[SIZE=3]
So I went and downloaded the cdrtools file and tried to follow the instructions but I don't understand it . 

I need help Please[/SIZE]

---

### Post by sdowney717 on 2011-03-07
what happens when you put in a blank disc?
Does the CD Creator popup comeup?

If so, what I do is drag files into that and then burn with that. perhaps a right click shows burn files.

---

### Post by gryphoninc on 2011-03-07
well I just finished burning a blank Cd .

But multisession CD's or DvD I cannot.

same error code appears.

help

---

### Post by nomko on 2011-03-07
> **gryphoninc said:**
> 
[FONT=Monospace][SIZE=3]SONY DVD RW DRU-820A 1.0c[/SIZE][/FONT]
 
Hmmmm.....I am not very fond of Sony products. But that is not the main source of your issue.

---

