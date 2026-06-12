---
title: "Help with Rsync"
date: 2010-02-27
forum: General Help
---

### Post by utherpendragonfly on 2010-02-27
I need advice on backing up.
In the past I used rsync to backup /home to an external usb HD partition named 'Back-up'. It worked great, but permissions on the second user account in /home got a little messed up. 
I used this: sudo rsync -av --delete /home /media/Back-up
I have been looking for hours on many blogs and websites and found it a bit confusing. There are so many different ways to use rsync!

This is what I have come up with: sudo rsync -avpru --stats --delete /home /media/Back-up

I basically want to make a complete copy of /home and then only back up what has changed, deleting on the backup copy what has been deleted on the source. And I need to make sure everything on the other user account (Firefox and Thunderbird data, etc) gets copied. I thought using sudo should take care of that, right?

Can anyone tell me if this makes sense?

---

