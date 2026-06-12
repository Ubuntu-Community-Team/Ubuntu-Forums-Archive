---
title: "How Do I download Youtube videos?"
date: 2010-03-28
forum: General Help
---

### Post by sille777 on 2010-03-28
I would like to know how I can download youtube videos within Firefox?

In Windows I can use RealPlayer's download feature that works very well, but wanted to know if there was a similar way I could do the same thing usuing Ubuntu.

Thanks!

---

### Post by derekeverett on 2010-03-28
Check out the Firefox add-ons.

---

### Post by pbrane on 2010-03-28
You could try the Download Helper firefox addon.

---

### Post by bobcollard on 2010-03-28
```
Sudo youtube-dl “URL”
```  Where URL is the address of the video (without the quotes of course)

---

### Post by 1991sudarshan on 2010-03-28
Download Helper firefox addon is kinda slow

---

### Post by HomoGleek on 2010-03-28
Take a look at [http://www.omgubuntu.co.uk/2009/12/download-youtube-videos-ubuntu-easy.html](http://www.omgubuntu.co.uk/2009/12/download-youtube-videos-ubuntu-easy.html)

---

### Post by derekeverett on 2010-03-28
> **bobcollard said:**
> ```
Sudo youtube-dl “URL”
```  Where URL is the address of thevideo (without the quotes of course)

I think you have to install youtube-dl first don't you?

The firefox add-ons are easier and most allow you different file format options.

---

### Post by femngi on 2010-03-28
I'm pretty sure I have never needed to run youtube-dl with sudo

*Edited to add:
I have this script saved as 'yt' in my /home:

#!/bin/bash
mplayer "$(youtube-dl -g -f 18 $1)" &

Then I just use ./yt URL whenever someone sends me a link.

---

### Post by lisati on 2010-03-28
You do realize that this violates Youtube's terms and conditions?

[http://ubuntuforums.org/showthread.php?t=1165163](http://ubuntuforums.org/showthread.php?t=1165163)

---

### Post by derekeverett on 2010-03-28
> **lisati said:**
> You do realize that this violates Youtube's terms and conditions?

[http://ubuntuforums.org/showthread.php?t=1165163](http://ubuntuforums.org/showthread.php?t=1165163)

You can't step out of your house anymore without violating somebodies terms and conditions.

It's the internet. But censorship is still alive and well.

Soon when this thread gets closed you'll see that's true.

---

### Post by lisati on 2010-03-28
> **derekeverett said:**
> 
Soon when this thread gets closed you'll see that's true.

I've seen threads similar to this one closed........

---

### Post by l.billon on 2010-03-28
> **bobcollard said:**
> ```
Sudo youtube-dl “URL”
```  Where URL is the address of the video (without the quotes of course)

Wow! Didn't know that useful trick!
Thank you very much!

---

### Post by sille777 on 2010-03-28
Thanks!

Anyone recommend a good video to MP3 audio converter?

---

### Post by l.billon on 2010-03-28
> **sille777 said:**
> Thanks!

Anyone recommend a good video to MP3 audio converter?

My favorite:
```
ffmpeg -i video.flv -vn -ar 44100 -ac 2 -ab 192k -f mp3 audio.mp3
```

---

### Post by derekeverett on 2010-03-28
> **sille777 said:**
> Thanks!

Anyone recommend a good video to MP3 audio converter?

I mostly use paid software for that.. but VLC will do it.

VLC will do anything. VLC makes me waffles every morning.

---

### Post by overdrank on 2010-03-28
As stated before this is not a topic for this form. See [here]("http://ubuntuforums.org/showthread.php?t=1429211&highlight=youtube"). Thread closed

---

