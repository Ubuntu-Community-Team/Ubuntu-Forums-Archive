---
title: "File not saved before power off"
date: 2011-09-13
forum: General Help
---

### Post by CoyleTrydan on 2011-09-13
Hello,
I've set up an Ubuntu 10 installation on a desktop to record our church's sermons during our services. I'm relatively new to Ubuntu and Linux in general, so I'm pretty much learning as I go. For the time being I'm recording through the line in on the computer into Sound Recorder. (I'm very familiar with more advanced recording options, but this was a quick and sufficient setup for simply recording a talk.)

This past Sunday, the tech team recorded the sermon, and stopped the recording after it was over. However, the computer operator did not save the file - it was left with Sound Recording running but unsaved. There was a mix-up and power was cut to the computer before it ever was saved. I booted the computer back up to see if there was any kind of recovery, but I was unable to find any options.

I would REALLY like to be able to recover the recording of the sermon, if there's any way to do it? Any help is greatly appreciated!
Coyle

---

### Post by 2F4U on 2011-09-13
If the recordings are not saved there is probably not much to recover since nothing has been stored permanently. You may look through the /tmp folder if there still is something stored, but that folder's content is temporary.

---

### Post by CoyleTrydan on 2011-09-13
Yeah, that's pretty much what I figured. :( I had checked the tmp folder, but being unfamiliar with Linux I didn't really know what I was looking for, there were no audio filetypes though.
I just wondered based on experience with other recording solutions where data is saved to the HD as you go, and I didn't know if that was the case here or not.
Thanks for the response!

---

### Post by 2F4U on 2011-09-13
On Linux, everything user files would be saved to your /home folder. You can look through it if you find a folder which is named according to your recording software. This would be the place for configuration settings and, maybe, also for the temporarily stored files (but I doubt it). Such folders may be hidden, so use ls -al in a terminal or configure your file browser to also show hidden files.

---

