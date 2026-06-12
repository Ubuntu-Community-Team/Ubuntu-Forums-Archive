---
title: "Help me do that Who Do that You Do"
date: 2009-10-04
forum: General Help
---

### Post by mvelte54 on 2009-10-04
Okay I have looked and can't seem to find the answer to what I'm looking for so I'll post it here. I hope someone out there can help me.
I have a set of DVD-RW's that are from my Windblows days I would like to format them and rerecord them over. I haven't inserted any of them into my machine yet to see what will happen. I am running Jaunty 9.04 and have installed WINE, (but I've never used it).
My question is this, if I insert the disk then will I have to bring up GParted or will WINE take over? All that is on the disk is some music I wanted to hang on to, but I want to try and format the disk so they are usable again. Also I am having troubles sending files to my 4 Gig Pen drive. I have formated it with GParted and if I open nautulus and try to drag and drop into the pen drive it won't go. I have even right clicked the file and said send to. Nothing. :confused:

---

### Post by hansdown on 2009-10-04
Hi mvelte54.

You don't need wine to get your music files from your dvd.

Just insert the disk, and you should see everything on it.

Nautilus should let you drag the files to anywhere you wish.

---

### Post by mvelte54 on 2009-10-04
Thank you for that I only mentioned WINE in case it might rear it's ugly head and not having ever used it I would not know what to do with it. I can drag and drop files any where I wish as you stated just not to  my USB pen drive. I did insert one of the disks and yes I can see everything that's on it but I want to erase it. But how? When I close nautilus and go to my desktop I right click on it and I can "blank' it? So I tried that and after a minute it said it is "blank". I opened it with nautilus and everything is still there?

---

### Post by Vaphell on 2009-10-04
maybe try to do that in brasero or k3b, after all recording stuff is their job

---

### Post by mikewhatever on 2009-10-04
You can erase DVD-RWs with Bracero and then record new data. Neither wine nor Gparted are the tools.

---

### Post by hansdown on 2009-10-04
Close everthing, and click applications> sound and video> brasero.

Click tools, and it will give you an option to erase.

---

### Post by mvelte54 on 2009-10-04
By using Brasero and 'blanking' the DVD both fast and regular 'blanking' I try to burn it and get this error file:

Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_RVP10U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_T1Q10U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
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
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_VX500U.bin toc = none
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/mikey1/downloads/Cyote_0.0.2.i686-0.0.3.iso (size = 348555264)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) f523b031d974462fd7dc599c392b852d ( before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
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
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
    growisofs
    -use-the-force-luke=notray
    -use-the-force-luke=4gms
    -speed=4
    -use-the-force-luke=tracksize:170193
    -use-the-force-luke=tty
    -Z
    /dev/sr1=/home/mikey1/downloads/Cyote_0.0.2.i686-0.0.3.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/mikey1/downloads/Cyote_0.0.2.i686-0.0.3.iso of=/dev/sr1 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr1: "Current Write Speed" is 4.1x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=1f80h failed with SK=3h/WRITE ERROR]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: /dev/sr1: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr1: stopping de-icing
BraseroGrowisofs stderr: /dev/sr1: writing lead-out
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2602)

---

### Post by mvelte54 on 2009-10-04
I have used Brasero several times and burned several CD and DVD's so I know all is working properly it's just that these DVD+RW's are not co-operating. I think earlier I stated that they were -RW's when in fact they are +RW's if that makes a difference.

---

### Post by hansdown on 2009-10-04
> **mvelte54 said:**
> I have used Brasero several times and burned several CD and DVD's so I know all is working properly it's just that these DVD+RW's are not co-operating. I think earlier I stated that they were -RW's when in fact they are +RW's if that makes a difference.

Shouldn't make a difference.

May I ask what type of file you would like to burn?

---

### Post by mvelte54 on 2009-10-04
Oh course you can...
I have been messing around with Open SuSE Studio and have been trying my hand at creating my own OS. I can make a LiveCD.iso but then it's only usable once. Don't get me wrong I do not plan on removing Ubuntu but I like to get my hands dirty as it were and try and create my own OS and maybe one day wear the label of 'GEEK'. I have two machines this one which is named R2D2 and then I have another named C-3PO a little older and slower but great for experimenting. The reason I am attempting to create my own OS. My wife and son use this machine exclusively while C-3PO is all mine. And my wife hates when I try different distros on here all running from a live CD.

'How can I fix it if it ain't broke? I can't learn anything that way.'

---

### Post by sendblink23 on 2009-10-04
nosure why is your problem if those discs are indeed RW's it shoudl work perfectly fine to Erase those dics...

another idea... C3PO or R2D2 =P   and try  erasing it on another computer that has Windows.... if it fails.. it must be those dics are not RW's

---

### Post by hansdown on 2009-10-04
> **mvelte54 said:**
> Oh course you can...
I have been messing around with Open SuSE Studio and have been trying my hand at creating my own OS. I can make a LiveCD.iso but then it's only usable once. Don't get me wrong I do not plan on removing Ubuntu but I like to get my hands dirty as it were and try and create my own OS and maybe one day wear the label of 'GEEK'. I have two machines this one which is named R2D2 and then I have another named C-3PO a little older and slower but great for experimenting. The reason I am attempting to create my own OS. My wife and son use this machine exclusively while C-3PO is all mine. And my wife hates when I try different distros on here all running from a live CD.

'How can I fix it if it ain't broke? I can't learn anything that way.'

Ah... These are .img files?

Jaunty has a handy usb sartup disk creator.

Click system> administration> usb startup disk creator.

If you have the file saved, let's say, to your desktop, you can create

a bootable usb.

Hope I'm not misunderstanding you.

EDIT:

I see that you can make an .iso file.

Pay no attention to the man behind the curtain.

---

### Post by mvelte54 on 2009-10-04
To sendblink23 they are indeed +RW's I have used them many times when R2 was running Wind-Blows. I don't have access to a Wind-Blows machine anymore I have sworn that OS off! 
And to hansdown I have tried USB start up disk to install my experimental OS from my downloads file but it says, 'This is not a desktop install CD and thus cannot be used by this application.' apparently I need for example my 'Ubuntu CD' in order to create a USB start up. Which I guess would mean I have to burn my experimental OS to a CD to continue. Which brings me to the reason for wanting to use my +RW's.

---

### Post by hansdown on 2009-10-04
That first line in post #7 is consistent with a bug report filed for brasero.

[http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg130292.html](http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg130292.html)

Maybe try K9copy to see if it works better, although right clicking the file, and choosing burn to disk should have worked.

---

### Post by mvelte54 on 2009-10-04
Gentlemen I am giddy with pride I found my problem. The disk I was using appears to be defective however I have written to it many times and indeed there is still files on it. But in frustration I tried another disk from the same manufacturer and had also used many times. Well success I 'blanked' that one and it too said it had problem so I blanked it again and it erased the DVD???
I tried to burn my experimental distro to it and then installed it to C-3PO (it boots but that's about it for now so back to the studio as it were) I returned the DVD to R2D2 and told it to write another distro on top of the old and it did I am on my way to my lab as soon as I write this. Thank you again for all your help. 

I am still confused on the USB though. I have reformated them to ext3 and renamed them but still can not upload anything to them. Your thoughts?

---

### Post by hansdown on 2009-10-04
Glad you're moving along mvelte54.

The file extension for usb seems to be different.

.oem.tar.gz

[http://en.opensuse.org/How_to_use_downloaded_SUSE_Studio_appliances](http://en.opensuse.org/How_to_use_downloaded_SUSE_Studio_appliances)

---

### Post by mvelte54 on 2009-10-06
Thank you for that hansdown but I am still cornfused on the different file extensions. I purchased and also read  Keir Thomas's book Ubuntu Kung Fu. Which puts me light years away from where I was just 6 months ago, but it's still not clear for me about file extentions nor USB sticks. Can anyone suggest some reading that I might do?

---

### Post by hansdown on 2009-10-06
I admire your enthusiasm mvelte54.

My advise is not worth much, as I haven't mustered the courage to try this.

If you look at the first screenshot, you will see that it says to download the ```
.OEM.TAR.GZ file
```

Save it to your desktop, or where you prefer.

Next, to extract it, just rightclick the file, and a popup will give you an option to extract it.

Click extract, and it will create a```
 .RAW file
```

Here is where I'm on shaky ground.

In the first screenshot, you can see the```
 KIWI-TOOLS-IMAGWRITER
```

If you click the link beside this, you can search for this, and install.


```
*WARNING*
```

Please look at the scond screenshot, and decide if you wish to proceed.

The warnings are a little ominous.

I don't have a test machine, so please consider if you can afford to potentially lose your data.

Sorry I can't be more helpful.

---

### Post by mvelte54 on 2009-10-08
Thanks for that hansdown. I did peruse that web page the first time I saw it and the warnings made me a little nervous also. But that's what C-3 is for BREAK it then try and FIX it. I'm not worried about losing information (read DATA) I have wiped the hard drives more times than I can count and started over. I've even burned an Ubuntu Live CD twice. (I haven't used the second one yet but just in case). What truly makes me nervous is when I reformated my USB's. 15 mg, 1 gig and a 4 gig. I messed up the 15 mg pretty good it was unusable for a while but some how I got it working again so I tried to replicate what I had done with my 1 gig and I did it! I screwed that one up too... I still haven't figured out how I got that one working again. Oh well, "Hi Ho, Hi Ho, it's back to the lab I go..."

---

### Post by Chronon on 2009-10-08
> **mvelte54 said:**
> Thanks for that hansdown. I did peruse that web page the first time I saw it and the warnings made me a little nervous also. But that's what C-3 is for BREAK it then try and FIX it. I'm not worried about losing information (read DATA) I have wiped the hard drives more times than I can count and started over. I've even burned an Ubuntu Live CD twice. (I haven't used the second one yet but just in case). What truly makes me nervous is when I reformated my USB's. 15 mg, 1 gig and a 4 gig. I messed up the 15 mg pretty good it was unusable for a while but some how I got it working again so I tried to replicate what I had done with my 1 gig and I did it! I screwed that one up too... I still haven't figured out how I got that one working again. Oh well, "Hi Ho, Hi Ho, it's back to the lab I go..."

Just to be sure, the UMS devices weren't mounted when you formatted, were they?  That's a good way to break a file system IIUC.

---

### Post by mvelte54 on 2009-10-09
No Chronon they were not mounted at the time that is one thing that I am very careful about. Like I stated though both are working again but I am at a loss as to how or what I did to break them and then to get them working again, but I'll keep trying I'm sure I can break them again and if I can fix them again something will click and I will have learned another new trick.

---

### Post by hansdown on 2009-10-09
It's best to avoid formatting to a windows file system;(fat32, ntfs).

Formatting to a linux file system;(ext3), is better.

---

### Post by mvelte54 on 2009-10-11
Thanks again hansdown however if I remember correctly that is exactly how I got one of them to work again. They originally started life as fat32 then I reformated the 15 mg to ext2, no good so I tried ext3 still no good. After many frustrating attempts I decided to format back to fat32 still no good, so I formated one more time to ext3 and it just works. I did the 1 gig to ext3 from fat32 and it too was trashed all I could see when I mounted it was 'Lost and Found' it wouldn't hold anything either by drag and drop or just plain trying to load to it. Nothing. I kept formating it between ext2 and ext3 and finally it just works, like a charm I might add. But what I did I still haven't figured out but I'm getting there. Thank you every one who is involved in Ubuntu forums. I would have given up 6 months ago if not for all of you.

---

### Post by hansdown on 2009-10-11
Your steadfast determination will see you through mvelte54.

Stick with it, I'd like to see this work for you, so please keep posting.

---

